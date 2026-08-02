# B2B2C Partner Programme Scope

**Status:** Draft, proposed next project phase
**Owner:** Jason Ryan
**Last updated:** 2026-08-02
**Related tickets:** HT-328, HT-329, HT-330, HT-331, HT-332, HT-333, HT-334

## Objective

Make HomeTruth a repeatable B2B2C programme sold to property-adjacent organisations. Partners sponsor a useful homeowner experience; homeowners retain control of their records, documents and choices; partners receive only approved, privacy-protected programme evidence.

This is not a pivot to a partner-controlled property database. The homeowner product remains the source of value: a useful home record, understandable documents, practical actions and property-aware answers.

## Scope Boundary

The current platform supports an insurer cohort technically through partner, cohort, membership and consent models. This next phase turns that foundation into a defined B2B2C product rather than a one-off insurer implementation.

Initial target segments:

- insurers: prevention, policy-document understanding and customer engagement
- mortgage providers: completion-to-remortgage homeowner support and property-document continuity
- new-build companies: handover packs, warranties, snagging and early-ownership guidance

Initial commercial wedge: insurer-sponsored homeowner prevention and engagement. It reuses the existing pilot foundation and should validate the common programme model before a mortgage-provider or new-build pack is built.

## Partner And Homeowner Value

| Audience | Outcome |
| --- | --- |
| Homeowner | Organise important property information, understand documents, take useful actions and get property-aware help. |
| Partner sponsor | Offer a valuable customer programme with a credible, governed evidence base. |
| Partner programme manager | Launch and manage a defined cohort or campaign without bespoke engineering. |
| Partner marketing/CRM lead | Use approved co-branded acquisition material and understand aggregate activation. |
| Partner analyst | Review thresholded aggregate engagement and outcome measures. |
| Partner privacy lead | Verify consent purpose, data boundaries and audit evidence. |
| HomeTruth operator | Configure programmes, support participants and manage exceptions during early pilots. |

## Non-Negotiable Product Principles

- Homeowner value comes first; partner value is downstream of voluntary homeowner use.
- Partner access is aggregate-only by default.
- Individual property, document, task, profile and behavioural data requires a separate explicit consent, an approved purpose and a deliberately designed product path.
- A partner is not a default PropertyPerson and cannot control homeowner tasks or records.
- Partner references remain opaque where possible; do not ingest unnecessary policy, mortgage or purchaser PII.
- The shared platform comes before vertical bespoke features.
- Do not claim claim reduction, premium reduction, credit outcomes, property-value outcomes or regulatory compliance unless evidence and approved copy support the claim.

## Common Partner Programme Story Map

Commercial agreement -> programme configuration -> approved branded invitation -> attributed signup and consent -> homeowner gets first value -> ongoing homeowner actions -> privacy-protected aggregate evidence -> partner renewal, expansion or stop decision

### Stories

1. As a partner sponsor, I can agree a defined programme objective, audience, success measures and data boundary before launch.
2. As a HomeTruth operator, I can configure a partner, programme, cohort, dates, entitlement, approved copy and invite route without code changes.
3. As a partner CRM lead, I can send or host an approved co-branded route and understand aggregate invitation and activation performance.
4. As a homeowner, I can understand why I was invited, receive value without granting partner data access, and make separate consent choices.
5. As a partner programme manager, I can see aggregate cohort health and exceptions without seeing an individual's property record.
6. As a partner analyst, I can review thresholded aggregate activation, setup, engagement, repeat use and agreed outcome measures with clear metric definitions.
7. As a partner privacy lead, I can verify the applicable consent versions, processing purposes, access boundary and audit trail.
8. As a HomeTruth operator, I can support a programme and suspend, correct or close it without losing the homeowner's independent HomeTruth record.

## Delivery Plan

### Phase 0: Define The Repeatable Offer

HT-328 establishes the B2B2C proposition, personas, jobs, story map, commercial assumptions, common data contract and priority order. It chooses insurer as the first implementation wedge and states the evidence required to move to other segments.

Exit: the scope is accepted and the Phase 1 tickets are sequenced against an insurer design partner or a clearly defined internal pilot.

### Phase 1: B2B Pilot Kit

HT-329 and HT-330 provide a controlled, HomeTruth-operated programme flow:

- configure a partner programme and cohort
- run approved co-branded acquisition and consent
- measure programme evidence through the existing HomeTruth-operated reporting route

This phase does not require a broad self-service partner portal. Configuration can remain operator-led while the model is proven.

### Phase 2: Governed Partner Operations

HT-332 adds partner roles, data-access boundaries, audit evidence and lifecycle controls. HT-331 then exposes the repeatable, privacy-protected partner programme dashboard. Together, they are the minimum safe basis for partner self-service.

### Phase 3: Integration And Vertical Packs

HT-333 defines stable integration contracts. HT-334 delivers the insurer pack first. Mortgage-provider and new-build packs are only created after their distinct document types, homeowner moments, partner jobs and commercial measures are validated.

## Shared Core Versus Vertical Packs

| Shared core | Insurer pack | Mortgage-provider pack | New-build pack |
| --- | --- | --- | --- |
| Partner, programme, cohort, campaign, consent, attribution, aggregate reporting, roles, audit and lifecycle management | Policy and prevention document prompts; maintenance actions; engagement evidence | Completion, mortgage and remortgage document prompts; ownership continuity actions | Handover pack, warranty, snagging and early-ownership document prompts |

The segment column changes content, document taxonomy, prompts, task rules and agreed measures. It must not bypass the shared consent or access model.

## Out Of Scope For This Phase

- A generic marketplace, contractor booking or service-payment product.
- Partner access to individual homeowner records by default.
- Full multi-tenant enterprise administration, SSO or external APIs before a validated partner need.
- Credit, underwriting, claims, valuation or regulated advice decisions.
- Building all insurer, mortgage-provider and new-build packs in parallel.

## Phase Gates

1. **Scope gate:** insurer wedge, target partner role, homeowner promise, pricing hypothesis, data boundary and measures are accepted.
2. **Pilot-kit gate:** an operator can configure and run a complete programme without a code change.
3. **Governance gate:** reporting is thresholded, consent-aware and auditable; individual data is inaccessible by default.
4. **Expansion gate:** a second segment has a validated buyer, homeowner moment and evidence need that cannot be met by configuration alone.

## Success Measures

- A partner programme can be created and launched repeatably.
- Homeowners reach useful first-session value without being required to share personal property data.
- Partner reporting is measurable, aggregate, consent-aware and understandable.
- A pilot produces evidence sufficient for a renewal, expansion or stop decision.
- New vertical requests are implemented as constrained packs on the common model, not bespoke forks.
