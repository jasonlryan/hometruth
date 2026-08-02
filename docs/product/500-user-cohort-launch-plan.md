# 500-User Cohort Launch Plan

**Status:** Draft
**Owner:** Product / pilot owner
**Last updated:** 2026-05-31
**Related tickets:** HT-315, HT-316, HT-317, HT-318, HT-319, HT-320, HT-321, HT-322, HT-324

## Purpose

This plan defines how a 500-person partner cohort should be introduced to HomeTruth, what users should do in their first session, how they should see value, and what success should mean before launch starts.

The product promise must stay homeowner-first. The partner introduces the cohort, but the user experience is not an insurer compliance checklist.

## User Promise

HomeTruth helps you build a useful record for your home, understand the documents that matter, and get practical actions before small home admin or maintenance issues become harder to manage.

Plain-English value:

- Keep important property documents in one place.
- Know what each document means and when something needs attention.
- Ask questions using your own property record and uploaded documents.
- Get practical actions for maintenance, renewals, missing evidence and known issues.
- Make future home admin, maintenance, selling, remortgaging or claims less painful.

## Partner Introduction

Recommended partner message:

```text
We are inviting a limited group of customers to try HomeTruth, a property assistant that helps you organise key home documents, understand what matters, and spot useful maintenance actions.

You can create a secure home record, add important documents such as policies, EPCs, surveys or service certificates, and ask questions about your property.

HomeTruth will use your information to provide the service to you. We will receive aggregate pilot insight only unless you explicitly agree to share more.
```

Required partner copy elements:

- why the user is being invited
- what HomeTruth helps them do
- expected setup time: 10-15 minutes for first setup
- documents worth having nearby
- privacy boundary: aggregate pilot insight only by default
- support contact route
- participation incentive, or explicit no-incentive decision

## HomeTruth Landing Copy

Recommended first-screen promise:

```text
Set up your home record in a few minutes.

Add your property, upload a couple of useful documents, and HomeTruth will help you understand what matters and what to do next.
```

Supporting copy:

```text
You stay in control of your information. HomeTruth uses your property record and uploaded documents to help you. Your partner receives aggregate pilot insight only unless you explicitly consent to individual sharing.
```

## First-Session Journey

Target outcome: the user leaves the first session with a property record, at least one useful evidence source, generated actions and one answered question.

1. **Invite validation**
   The user opens the partner link or enters an invite code. Invalid, expired and already-used states are handled before signup.

2. **Signup or login**
   New users register. Existing users log in. Partner/cohort attribution survives the transition.

3. **Consent**
   The user sees required HomeTruth processing consent and optional partner/reporting scopes. Individual sharing is not assumed.

4. **Property setup**
   The user adds or confirms:
   - address
   - property type
   - tenure
   - relationship to the property

5. **Document prompt**
   The user is asked to add two or three useful documents. Recommended prompts:
   - insurance policy
   - EPC
   - survey
   - boiler or service certificate
   - warranty or maintenance record
   - evidence for a known issue

6. **Action generation**
   HomeTruth generates initial property actions from missing baseline data, document expiry dates, facts or evidence.

7. **Property-aware assistant question**
   The user is prompted to ask one question such as:
   - What should I check next for this property?
   - What does this document suggest I should do?
   - Are any documents missing for this home record?
   - What actions are most urgent?

8. **First value summary**
   HomeTruth shows:
   - documents added
   - facts or evidence detected
   - open actions
   - one recommended next step

## Empty And Failure States

- No documents uploaded: show examples and let the user continue with property-only actions.
- Upload fails: preserve property setup and give a retry path.
- No actions generated: explain that actions improve after documents/facts are added.
- No property selected in chat: make clear the assistant is using all current-user documents plus HomeTruth guidance.
- Consent declined: explain which pilot capabilities require consent and route to non-partner HomeTruth flow where appropriate.

## Pilot Metrics

Starting thresholds to review before launch:

- 60% invite-to-signup activation.
- 70% signup-to-property-complete rate.
- 2+ documents linked per activated user.
- 1+ generated action viewed per activated user.
- 25% of activated users complete, dismiss or mark not relevant at least one action.
- 20% of activated users ask at least one property-aware assistant question.
- Average feedback rating of 4/5 or better.

Drop-off triggers:

- invite validation failures above 10%
- signup-to-consent drop-off above 40%
- property setup completion below 50%
- document upload failure above 5%
- zero task generation for more than 30% of completed properties

Pilot event map:

- Invite-to-signup activation: `metrics.activationRate`, calculated from distinct cohort members with `signup_completed` divided by invited members.
- Signup-to-property completion: `metrics.propertySetupCompletionRate`, calculated from distinct cohort members with `property_setup_completed` divided by completed signups.
- Consent completion: `metrics.consentRate`, calculated from distinct cohort members with `consent_recorded` divided by completed signups.
- Documents linked per activated user: `metrics.documentLinksPerActivatedMember`, calculated from `document_linked` events divided by completed signups.
- Task generation and action engagement: `metrics.tasksGenerated`, `metrics.taskActionedMembers` and `metrics.taskActionEngagementRate`, using `tasks_generated`, `task_completed`, `task_dismissed` and `task_not_relevant`.
- Feedback score: `metrics.averageFeedbackRating` from `user_feedback_submitted` rating metadata only.
- Property-aware assistant usage: `metrics.propertyChatQuestionedMembers` and `metrics.propertyChatUsageRate`, from consent-bound `property_chat_question` events. Chat content is not stored in pilot analytics.
- Repeat use: `metrics.repeatActiveMembers` and `metrics.repeatUseRate`, calculated from consent-bound `pilot_daily_activity` events on at least two distinct UTC dates. The frontend emits no route, property, document, chat or free-text metadata.

The admin response includes `metricCoverage`, which marks each metric as `measured` or `not_instrumented`. It must not substitute a proxy for a metric with no valid source.

## Partner Aggregate Reporting Pack

The partner-facing pack should include aggregate-only views:

- invited users
- invite views
- signups
- consent completion
- property setup completion
- documents linked
- tasks generated
- task statuses in aggregate
- assistant usage count
- feedback rating summary
- drop-off points
- support issue categories

The pack must not include names, emails, addresses, document names, raw facts, task descriptions, individual chat content or individual user rows.

Technical report-boundary evidence recorded 2026-08-02:

- The cohort-report response was smoke-tested against a disposable five-member MySQL cohort.
- The response exposed aggregate counts, rates, drop-off totals and metric coverage only.
- The smoke asserted that user/member/property IDs, document names, raw fact values, feedback text and chat content were absent.
- Product/pilot and privacy/compliance approval remain required before this pack is shared externally.
- HT-326 implementation is awaiting code-review completion in backend PR #4 and frontend PR #2.

## Open Decisions

- Partner-approved launch copy.
- Support owner and support contact route.
- Participation incentive or explicit no-incentive decision.
- Final success thresholds.
- Target environment for launch smoke.
- Final go/no-go owner.
