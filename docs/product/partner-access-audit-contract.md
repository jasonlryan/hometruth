# Partner Access And Audit Contract

**Status:** Active shared-core contract
**Owner:** Jason Ryan
**Last updated:** 2026-08-03
**Related tickets:** HT-328, HT-332, HT-331

## Purpose

Define the programme-scoped authorization and audit boundary used by insurers, mortgage providers, home developers and other B2B clients. This contract governs partner staff access; it does not make a partner a homeowner record owner or introduce an insurer-specific path.

## Identity And Scope

- A partner staff member authenticates as an existing verified HomeTruth user and receives an explicit partner-programme access assignment.
- An assignment belongs to exactly one partner and one programme. Access to a second programme requires a second assignment.
- Assignment state, programme state and the requested capability are checked by the server on every partner request.
- Cohort membership and partner staff access are separate concepts. An access assignment never creates a PropertyPerson, cohort member or consent record.
- HomeTruth administrator status does not silently create partner access. Operator endpoints and partner endpoints remain separate.

## Role Matrix

| Role | Programme summary | Aggregate evidence | Aggregate export | Programme audit | Configuration | Individual homeowner data |
| --- | --- | --- | --- | --- | --- | --- |
| Sponsor | Allowed | HT-331, when enabled | HT-331, when enabled | Denied | Denied | Denied |
| Programme manager | Allowed | HT-331, when enabled | HT-331, when enabled | Allowed | Denied in HT-332 | Denied |
| Analyst | Allowed | HT-331, when enabled | HT-331, when enabled | Denied | Denied | Denied |
| Privacy auditor | Allowed | Metric definitions/coverage only in HT-331 | Denied | Allowed | Denied | Denied |

HomeTruth operators grant, change and revoke assignments. SSO, SCIM, partner-created users and partner self-service programme configuration require a separately accepted product need.

## Lifecycle And Consent

- An active assignment is required for every partner capability.
- Active programmes can expose capabilities allowed by the role.
- Paused and closed programmes deny operational and reporting capabilities immediately.
- An authorised programme manager or privacy auditor may review historical programme audit evidence after pause or closure.
- Programme access never overrides homeowner consent. HT-331 reporting must include only consent-eligible, thresholded aggregate evidence and must react to withdrawal according to the approved policy.

## Fail-Closed Resource Boundary

Partner APIs do not return homeowner, property, document, task, profile, chat or behavioural-event rows. Requests for those resource classes are denied without confirming whether a record exists. No role in this contract allows an individual report.

## Audit Evidence

The shared audit log records assignment grant, role change and revocation; programme and audit views; future aggregate report views and exports; and denied partner attempts. Each event records the programme, access assignment where applicable, action, resource class, outcome, reason code, actor and timestamp. Partner-visible audit responses exclude homeowner identifiers and arbitrary request metadata.

## HT-331 Handoff

HT-331 must reuse this policy rather than introducing dashboard-specific authorization. Its report and export routes must check the assigned role, programme lifecycle, aggregate-consent basis, minimum threshold and suppression rules before returning any metric.
