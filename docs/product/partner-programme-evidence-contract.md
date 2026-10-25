# Partner Programme Evidence Contract v1

Updated: 2026-10-25. Implementation: HT-331, following HT-332 governed access. This is an implementation contract, not product/privacy approval or launch acceptance.

## Access and API

Authenticated routes under `/api/partner/programmes/:id`:

- `GET /evidence?month=YYYY-MM&campaignId=N`: sponsor, programme manager and analyst with an active assignment to this exact programme.
- `GET /evidence/export`: the same filter contract, authorized independently at download time; returns an aggregate JSON review pack with definitions and generation time.
- `GET /evidence/definitions`: assigned active-programme users, including privacy auditors. Privacy auditors cannot view metrics or export participant evidence.

Partner and programme must be active. Administrator status does not confer partner access. Partner reporting mode and cohort reporting level must both be `aggregate_only`. Responses carry `Cache-Control: no-store`. Report views, definition views, exports and authorization denials use the existing HT-332 audit schema. Individual-resource denials remain unchanged.

## Runtime approval gate

Reporting is disabled by default. A deployment operator may set `PARTNER_EVIDENCE_APPROVED_PROGRAMME_IDS` to a comma-separated list of programme IDs only after recording HT-324 product/pilot interpretation and privacy approval. An unset or non-matching list returns `approval_required` with no participant data; export is denied. Setting this variable is not evidence of approval.

This change does not enable any production programme. HT-319 governance and HT-320 launch/rehearsal requirements remain independent.

## Population and consent

The denominator is the distinct current participant population in eligible programme campaign cohorts, joined before month end. Only onboarded, active or completed memberships with a linked user are eligible. Ambiguous duplicate enrolments within the programme are excluded, so a user cannot inflate totals or overlap campaign partitions.

All three current scopes are required: HomeTruth processing, aggregate analytics and partner reporting. Latest matching consent evidence wins, including withdrawal, expiry or supersession. Consent must match partner, cohort, member and user; user-only consent is insufficient. Withdrawal removes that participant and their historical events from subsequent reports. Previously downloaded files cannot be recalled by this implementation.

Events must match the programme, partner, campaign, cohort, member and user, carry aggregate-analytics consent context and fall within the selected month. Only approved event names and minimal counting fields are queried. No event metadata, feedback text/ratings, property identifiers or individual rows are returned.

Access, reporting mode, memberships, consents, campaign scope and cohort reporting settings are rechecked before results are returned. A detected calculation-time change returns a retryable 409 instead of stale evidence.

## Disclosure controls

Only complete, fixed UTC calendar months are supported; the default is the previous month. Arbitrary dates, sliding periods and unknown query keys are rejected. Programme selection comes from the authorized URL; campaign selection is checked within that programme.

Each campaign is a separate partition. Selecting all campaigns returns those same partitions, never a programme total. This prevents subtraction of a visible campaign from a programme total to reconstruct a suppressed campaign. Cohorts without a campaign do not contribute.

A partition with fewer than ten eligible participants returns no population total or metrics. Zero eligible participants returns `no_data`; small non-empty partitions return `suppressed`. For visible partitions, any metric whose non-zero numerator or complement is below five has both its count and rate suppressed. Suppressed values remain null, never zero.

These controls require privacy review before external reporting, including consideration of repeated exports, changes in population over time and knowledge available to a partner. They do not constitute a formal anonymity guarantee.

## Measures and coverage

All measures count distinct eligible participants with activity in the selected month, divided by the eligible population for the rate:

- Activation: `signup_completed`.
- Property setup: `property_setup_completed`.
- Document linking: `document_linked`.
- Task generation: `tasks_generated`.
- Task engagement: `task_completed`, `task_dismissed` or `task_not_relevant`.
- Property-aware questions: `property_chat_question`.
- Repeat use: `pilot_daily_activity` on two or more distinct UTC activity dates.
- Feedback participation: `user_feedback_submitted`; feedback content and ratings are excluded.

Definitions include sources, units, denominator, contract version and instrumented coverage. These are recorded engagement measures; missing events may reflect consent or instrumentation gaps. They do not establish prevention, claims, underwriting, pricing, credit, valuation or financial outcomes. They differ deliberately from the administrator pilot funnel and are not interchangeable with its success thresholds without HT-324 acceptance.

## Operational limits and verification

Queries fail closed if a member, consent or event result exceeds 100,000 rows. This bounds in-process aggregation and requires capacity review before a larger rollout. This implementation needs no schema migration.

Local evidence is recorded in HT-331: contract checks, real MySQL fixture smokes, existing access/acquisition/lifecycle/reporting checks, frontend tests, production build and isolated browser/mobile validation. Target-environment deployment and end-to-end rehearsal remain outstanding.
