# Data Deletion And Consent Withdrawal Runbook

**Status:** Draft, blocked on legal/privacy review
**Owner:** TBD
**Last updated:** 2026-05-31
**Related tickets:** HT-319, HT-321, HT-322

## Purpose

This runbook defines the operational handling for consent withdrawal and deletion requests during the 500-user partner cohort pilot.

It is not launch-ready until reviewed by the privacy/legal owner.

## Required Human Inputs

- Privacy/legal owner: TBD
- Request intake route: TBD
- Identity verification method: TBD
- Target handling time: TBD
- Escalation owner: TBD
- Delete versus anonymise policy approval: TBD

## Consent Scopes

`hometruth_processing`

- If withdrawn, HomeTruth should stop processing the user's property/documents for service delivery where legally and technically possible.
- Product implication: partner pilot participation may no longer be possible.
- Operational action: verify identity, confirm account scope, then follow deletion or service-offboarding path.

`partner_reporting`

- If withdrawn, stop attaching partner-reportable context to future events or reports for that user.
- Existing aggregate reports may need review depending on legal policy.

`aggregate_analytics`

- If withdrawn, future events should not attach partner/cohort analytics context unless another lawful basis is confirmed.
- Internal operational events may still be retained if required for audit/support, subject to legal review.

`individual_report_access`

- If withdrawn, revoke any individual report-sharing path.
- V1 has no default individual report access, so this should usually be a no-op unless future sharing is implemented.

`partner_contact_servicing`

- If withdrawn, partner/contact servicing communications should stop unless another lawful basis applies.

## Process States

- Requested: user request received.
- Verified: identity and request scope confirmed.
- In progress: operational actions underway.
- Completed: user notified and internal log updated.
- Rejected: request cannot be fulfilled as stated; reason recorded.
- Escalated: privacy, technical or incident owner needed.

## Data Object Handling

Users:

- Decision needed: delete, anonymise or retain minimal audit record.

Cohort members:

- Keep opaque cohort/member relationship only if required for aggregate audit, otherwise unlink/anonymise after review.

Consent records:

- Retain consent history unless legal review says otherwise, because withdrawal status and timestamps are audit evidence.

Property records:

- Delete or anonymise property profile data when HomeTruth processing is withdrawn or account deletion is requested.
- Remove relationship links where appropriate.

User documents:

- Soft-delete or delete DB records according to approved policy.
- Delete physical file if stored locally/object storage.
- Delete Qdrant chunks by `document_id` plus `user_id`.

Property documents:

- Remove active property/document links.
- This immediately removes property-scoped retrieval access because V1 authorises through MySQL links.

Property facts and evidence:

- Delete or anonymise facts and evidence sources tied to the user/property according to approved policy.

Property tasks:

- Delete or anonymise tasks and task status events tied to the user/property according to approved policy.

Pilot events:

- Keep aggregate operational counts only if privacy/legal approves anonymised retention.
- Remove partner/cohort fields for withdrawn aggregate consent if required.
- Do not expose individual events to partner reporting.

Qdrant:

- Delete one document's chunks by both `document_id` and `user_id`.
- Delete all user document chunks by `user_id` for full account deletion.
- If future retrieval relies on Qdrant `property_id`, run an idempotent metadata backfill or deletion verification job.

## Manual Checklist

1. Receive request and assign owner.
2. Verify identity.
3. Confirm requested scope: consent withdrawal, partner reporting withdrawal, full deletion or partial deletion.
4. Freeze partner reporting for the user while request is in progress if needed.
5. Update consent record status to withdrawn where applicable.
6. Remove or anonymise partner/cohort reporting context according to approved policy.
7. Delete/anonymise property, document, fact, task and evidence data as approved.
8. Delete Qdrant chunks.
9. Verify no property-aware retrieval returns withdrawn/deleted content.
10. Record completion and notify the user.

## Follow-Up Tooling Candidates

- Admin workflow for deletion/withdrawal requests.
- Qdrant deletion verification script.
- Consent withdrawal event in pilot analytics.
- Report exclusion check for withdrawn aggregate consent.

## Launch Blockers

- Legal/privacy owner not named.
- Delete versus anonymise policy not approved.
- Identity verification route not approved.
- Manual DB/admin steps not reviewed.
