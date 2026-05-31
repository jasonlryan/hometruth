# Property-Aware Retrieval Architecture

**Status:** Implemented V1
**Owner:** Product / engineering
**Last updated:** 2026-05-31
**Related tickets:** HT-307, HT-308, HT-312, HT-314, HT-316, HT-319, HT-321

## Purpose

HomeTruth needs one assistant context layer that can combine general HomeTruth guidance, private uploaded documents and selected property context without crossing user, property or consent boundaries.

V1 implements that layer in the backend as `UnifiedRetrievalService`. MySQL remains the source of truth for ownership and property access. Qdrant remains a retrieval index.

## Retrieval Order

For an authenticated assistant request, V1 assembles context in this order:

1. Uploaded user document chunks from Qdrant `user_documents`, always filtered by the authenticated `user_id`.
2. If a property is selected, uploaded document chunks are further constrained to documents linked through active `property_documents` rows for that property and owned by the current user.
3. Selected property context from MySQL: current address, the user's active relationship, linked documents visible to the user, current property facts and open property tasks.
4. General HomeTruth guidance from Qdrant `home_truth_documents`.
5. External/web context only when the caller explicitly requests web search.

The prompt receives labelled source classes:

- uploaded user document
- property record
- HomeTruth guidance
- external/web source

The assistant should use those labels to keep the answer grounded, but should not expose raw retrieval scores or internal metadata.

## No Property Selected

V1 decision: if no `propertyId` / `property_id` is supplied, the authenticated assistant searches all active uploaded documents owned by the current user, plus the general HomeTruth knowledge base.

Reasoning:

- Existing users can upload documents that are not yet linked to a property.
- HT-312 intentionally kept property linking optional for general users.
- Requiring a property selection before every assistant question would make existing non-property document behaviour worse.

The response metadata records this as `scope.userDocumentScope = "all_current_user_documents"`.

## Property Scoping

V1 property scoping is resolved through MySQL before Qdrant search:

1. Confirm the user has an active `property_people` relationship for the selected property.
2. Load active `property_documents` rows for that property.
3. Load only linked `userDocuments` rows owned by the authenticated user.
4. Query Qdrant `user_documents` with both:
   - required `user_id` match
   - allowed `document_id` match-any filter

If the property has no linked documents owned by the user, retrieval returns no private chunks for that property. It does not fall back to all user documents.

New uploads that are linked to a property include `property_id` and `property_ids` payload metadata in Qdrant for future indexing/backfill options, but V1 retrieval does not rely on that metadata for authorization.

## Boundary Rules

- General HomeTruth guidance is shared product knowledge.
- Uploaded user documents are private and must always include a `user_id` Qdrant filter.
- A selected property must be visible to the authenticated user through an active property relationship.
- Property-scoped private retrieval must use the MySQL property/document link set before searching Qdrant.
- Partner and insurer users do not receive individual document, property, fact, task or answer-level access by default.
- Aggregate pilot analytics stay separate from individual retrieval.

## Deletion And Withdrawal

Deletion and withdrawal must affect both MySQL and Qdrant:

- Deleting one uploaded document should soft-delete `userDocuments` and delete its Qdrant chunks by `document_id` plus `user_id`.
- Deleting or withdrawing a user should delete all user document chunks from Qdrant by `user_id`.
- Removing a property/document link should remove property context from MySQL immediately. V1 retrieval uses the MySQL link set, so stale `property_id` payload metadata cannot grant access.
- If future retrieval relies directly on Qdrant `property_id` / `property_ids`, an idempotent payload backfill or reindex job must be added before that change ships.

HT-319 should own the full operational runbook for user deletion, consent withdrawal, partner cohort exit and Qdrant propagation verification.

## Pilot Scale

V1 target assumptions:

- 500 users
- 1-3 properties per active user
- 5-20 uploaded documents per user
- 10-50 chunks per document
- roughly 25,000-500,000 private vectors in the first pilot

This volume is viable for Qdrant. The main operational risks remain synchronous embedding during upload, long-running file processing, idempotent reindexing after metadata changes, deletion propagation and combined retrieval latency.

V1 avoids a rewrite by keeping the retrieval service as a single orchestration point and keeping Qdrant filters explicit. Queue-based ingestion, hosted Qdrant and metadata backfill can be added behind the same service contract.
