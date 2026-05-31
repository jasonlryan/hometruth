# Pilot Support And Incident Runbook

**Status:** Draft, blocked on named owners
**Owner:** TBD
**Last updated:** 2026-05-31
**Related tickets:** HT-318, HT-322

## Purpose

This runbook defines how HomeTruth handles support and incidents during the 500-user partner cohort pilot.

It is not launch-ready until the owner fields are completed and accepted.

## Required Human Inputs

- Pilot support owner: TBD
- Technical escalation contact: TBD
- Incident owner: TBD
- Support contact route: TBD
- Support hours: TBD
- First-response target: TBD

## Issue Categories

- Invite failure: invalid, expired, already-used or missing invite code.
- Signup/login: registration, login, token, redirect or account access issue.
- Consent question: user asks what is required, optional or shared with partner.
- Property setup: address, tenure, property type or relationship issue.
- Document/task issue: upload failure, document link issue, missing actions, unexpected task.
- Data deletion/withdrawal: user wants to withdraw consent, delete data or understand privacy rights.
- Incident: security, privacy, outage, repeated production failure or partner-impacting issue.

## Severity Levels

**SEV1: Critical**

- suspected data leak or cross-user access
- security incident
- partner-visible privacy issue
- sustained outage blocking all cohort users

Response: immediate incident owner and technical escalation. Pause pilot invites if needed.

**SEV2: High**

- onboarding flow broken for many users
- consent capture failure
- document upload unavailable
- admin reporting privacy boundary concern

Response: same business day escalation. Product owner decides whether to pause pilot comms.

**SEV3: Medium**

- individual user cannot complete setup
- individual upload/document/task issue
- confusing consent or product copy

Response: support owner triages and escalates if repeated.

**SEV4: Low**

- general question, typo, minor UI confusion, enhancement request

Response: support owner logs for pilot review.

## Escalation Rules

- Any SEV1 goes to incident owner and technical escalation immediately.
- Any issue involving possible personal data exposure is SEV1 until disproven.
- Three or more similar SEV3 issues in 24 hours escalate to SEV2.
- Any partner communication request goes through the pilot owner before sending.
- Any deletion or consent withdrawal request follows the HT-319 runbook.

## Holding Replies

Invite issue:

```text
Thanks for flagging this. We are checking your pilot invite and will come back to you as soon as possible. Please do not create a second account while we investigate.
```

Consent question:

```text
HomeTruth uses your information to provide the service to you. Your partner receives aggregate pilot insight only by default. Individual information is not shared unless you explicitly agree to that. We can help explain any consent option before you continue.
```

Document upload issue:

```text
Thanks for trying to upload your document. Your property setup is still saved. We are checking the upload issue and will let you know whether to retry or use another route.
```

Deletion or withdrawal:

```text
We have received your request. Before making changes to your account or data, we need to verify your identity and confirm exactly which consent or deletion action you want us to take.
```

Incident:

```text
We are investigating a HomeTruth pilot issue and have paused the affected process while we check it. We will update you when we know more.
```

## Monitoring References

- Admin cohort report: `/api/admin/pilot/cohort-report`
- Pilot events table: `pilot_events`
- Invite/onboarding events: `invite_viewed`, `signup_completed`, `consent_recorded`, `property_setup_completed`
- Engagement events: `document_linked`, `fact_created`, `tasks_generated`, `task_completed`, `task_dismissed`, `task_not_relevant`, `user_feedback_submitted`

## Launch Blockers

- Support owner not named.
- Technical escalation contact not named.
- Incident owner not named.
- Support route and response time not approved.
