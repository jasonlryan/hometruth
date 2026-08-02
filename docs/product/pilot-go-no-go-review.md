# Pilot Go/No-Go Review

**Status:** Draft decision: no_go
**Owner:** TBD
**Last updated:** 2026-08-02
**Related tickets:** HT-318, HT-319, HT-320, HT-322

## Purpose

This review records whether HomeTruth is ready to launch a 500-user partner cohort.

Current recommendation: `no_go` until named support ownership, deletion/withdrawal handling, target environment setup and end-to-end smoke testing are accepted.

## Launch Configuration

- Target environment: TBD
- Partner record configured: TBD
- Cohort record configured: TBD
- Target cohort size: 500
- Invite mode: TBD, cohort code, individual invite codes or both
- Cohort start date: TBD
- Cohort end date: TBD
- Consent copy version: TBD

## Required Consent Scopes

Required before partner-linked onboarding:

- `hometruth_processing`

Review required:

- `partner_reporting`
- `aggregate_analytics`
- `individual_report_access`
- `partner_contact_servicing`

Default stance: aggregate analytics only by explicit consent; individual report access is off unless explicitly granted in a future flow.

## End-To-End Smoke Test

Required target-environment smoke path:

1. Validate invite.
2. Sign up or log in.
3. Capture consent.
4. Create property profile.
5. Upload or link a document to the property.
6. Generate property tasks.
7. Ask a property-aware assistant question using selected property context.
8. Submit feedback.
9. View admin cohort report.
10. Confirm report is aggregate-only and does not expose names, emails, addresses, document names, raw facts, task descriptions or individual rows.

## Technical Readiness Checklist

- Backend migrations up in target environment: TBD
- Qdrant `home_truth_documents` exists with expected vector size: TBD
- Qdrant `user_documents` exists with expected vector size: TBD
- OpenAI key configured for embeddings and chat: TBD
- Document upload path tested with realistic files: TBD
- Property-aware retrieval tested with selected property: TBD
- Admin pilot report tested: TBD
- Error monitoring/log access confirmed: TBD

## Operational Readiness Checklist

- HT-318 support runbook accepted: no
- HT-319 deletion/withdrawal runbook accepted: no
- Support owner named: no
- Technical escalation contact named: no
- Incident owner named: no
- Legal/privacy review completed: no
- Partner launch copy approved: no
- Success thresholds approved: no
- Aggregate reporting privacy review completed: no
- HT-324 technical reporting coverage and local representative-data smoke: yes
- Repeat-use metric merged and locally smoke-tested: yes
- Repeat-use target-environment migration and smoke: no

## Open Risks

- Users may not reach value if the first-session guided path is not tightened in product.
- Property-aware backend retrieval exists and the frontend handoff is implemented, but it still needs target-environment smoke verification.
- Synchronous document embedding may cause slow uploads at pilot scale.
- Deletion/withdrawal process is not legally accepted.
- Support ownership is not assigned.
- Target production/staging environment has not been smoke-tested.
- HT-326 migration is merged but not yet applied or verified in the target environment.

## Decision

Current decision: `no_go`

Owner/date: TBD

Decision rationale: the core platform mechanics are implemented, but operational ownership, privacy/deletion handling and target-environment validation are not complete.

## Conditions To Move To Go With Monitoring

- HT-318 accepted with named owners.
- HT-319 accepted with legal/privacy review.
- HT-323 or equivalent frontend property-aware chat handoff smoke-tested in the target environment.
- Target environment smoke test passes.
- Partner launch copy and support route are approved.
- Admin aggregate reporting is reviewed for privacy leakage.
- HT-326 target-environment migration and repeat-use smoke pass.
- HT-324 accepted or equivalent reporting/privacy sign-off recorded.

## Conditions To Move To Go

- All `go_with_monitoring` conditions are met.
- No SEV1/SEV2 open risks.
- Upload/retrieval latency is acceptable under realistic pilot input.
- Success thresholds and intervention triggers are accepted by product/pilot owner.
