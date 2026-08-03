# Partner Acquisition And Consent Contract

**Status:** HT-330 implementation contract
**Owner:** Jason Ryan
**Last updated:** 2026-08-03
**Related tickets:** HT-319, HT-328, HT-329, HT-330, HT-331, HT-332

## Purpose

Define the reusable HomeTruth-hosted invitation and consent boundary for insurer, mortgage-provider, home-developer and other B2B partner programmes. This is shared-core behaviour. A partner type can select approved content and later vertical-pack capabilities, but it cannot replace the HomeTruth identity, weaken consent or create a bespoke access path.

## Authoritative Programme Configuration

The active campaign attached to an eligible cohort supplies approved plain-text acquisition configuration:

- homeowner eyebrow, headline and promise
- expected setup steps
- privacy summary
- support label and route
- optional approved partner logo URL and alternative text
- consent contract version and approved scope copy

HomeTruth validates and normalises this configuration on the server. Support and logo destinations are restricted to internal paths, HTTPS URLs or mailto links. The server-derived consent version, required status and text hash are authoritative; the browser cannot override them.

## Consent Boundary

| Scope | Required | Purpose |
| --- | --- | --- |
| `hometruth_processing` | Yes | Create and operate the homeowner-controlled HomeTruth record and the product actions the homeowner requests. |
| `aggregate_analytics` | No | Include de-identified use in grouped programme analytics. |
| `partner_reporting` | No | Include progress in thresholded aggregate reporting to the sponsoring partner. |
| `partner_contact_servicing` | No | Permit partner follow-up about the programme without granting record access. |

Every scope is shown separately. All choices begin off. A homeowner must actively grant HomeTruth processing to continue and can decline every partner-facing choice without losing the HomeTruth journey.

`individual_report_access` is deliberately excluded. HT-330 does not offer or infer partner access to an individual property, document, task, profile or behaviour record. Any future individual access requires the governed-access product path, a specific approved purpose and separate explicit consent.

## Invite Resolution And Public Privacy

Both cohort-code and individual-invite routes resolve through the active partner, programme, campaign and cohort. Valid routes return the approved acquisition contract. Invalid, expired, paused, closed, ineligible and already-used routes return safe lifecycle states.

Before authentication, an individual invite may reveal only its eligibility state. Public responses do not expose member, user or property identifiers. After authentication, claim and property handoff reuse the existing cohort membership and property relationship controls.

## Aggregate Attribution

Acquisition events may store stable internal partner, programme, campaign and cohort identifiers. Anonymous invitation views contain no user or member identifier. Authenticated activity receives partner attribution only after aggregate-analytics consent is granted.

Browser-authored onboarding metadata is restricted to approved categorical values. Free text, contact details, policy numbers, mortgage references, purchaser data and similar partner PII are not accepted as attribution metadata.

## Operational And Launch Boundary

HT-330 provides the non-destructive technical journey and consent evidence. HT-319 remains a live-launch dependency for approved consent withdrawal, identity verification, deletion/anonymisation policy and handling times. No production partner programme should be declared launch-ready until those governance decisions and the target-environment checks are complete.
