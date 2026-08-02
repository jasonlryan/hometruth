# HomeTruth Agent Delivery Playbook

**Status:** Active working agreement
**Owner:** Jason Ryan
**Last updated:** 2026-08-02
**Applies to:** HT-328 onward and all subsequent HomeTruth work

## Purpose

This is the persistent handoff for agents working in the HomeTruth workspace. It records the delivery flow already established here so that a new session can continue without recreating process, branch or review decisions.

## Workspace And Source Of Truth

| Repository | Role |
| --- | --- |
| HomeTruth_BE-staging | Backend implementation |
| HT_Frontend-staging | Frontend implementation |
| HomeTruth-tickets | Ticket objectives, scope, acceptance criteria, verification and decision log |
| hometruth DOCS | Product, strategy, technical and operating documentation |

Treat the ticket and linked product document as the contract for a workstream. Read the surrounding completed tickets and relevant implementation before changing code. Do not replace current product boundaries with assumptions from legacy product material.

## HT-328 Handoff

HT-328 is a scope and acceptance ticket, not a code ticket. The authoritative product scope is [B2B2C Partner Programme Scope](b2b2c-partner-programme-scope.md).

Current state:

- the B2B2C scope, shared core, vertical-pack boundary and HT-329 through HT-334 backlog are documented
- insurer-sponsored prevention and engagement is the proposed first wedge because it reuses the existing partner/cohort/consent pilot foundation
- the only open HT-328 acceptance criterion is product-owner confirmation of the initial design-partner route

For HT-328:

1. Read the scope, HT-314 through HT-317, HT-320, HT-324 and HT-326.
2. Verify that a proposed change preserves homeowner-first value, aggregate-only default partner reporting and explicit consent for any individual sharing.
3. Do not invent a committed partner, commercial term, legal approval or data-sharing agreement.
4. When Jason confirms the first design-partner route, record that decision, update the scope gate and move HT-328 to completed.
5. HT-328 documentation and ticket updates go directly to main. They do not need a PR.

HT-329 is the first planned code work only after that scope gate is accepted.

## Branch And PR Policy

There are two distinct paths.

### Documentation And Tickets

- Documentation-only and ticket-only changes are committed and pushed directly to the relevant repository main branch.
- Do not create a PR solely for docs or ticket changes.
- Stage only intended files, run git diff --check, commit with the relevant HT number, push, and verify a clean status.
- Record decisions, verification, blockers and changed acceptance criteria in the ticket.

### Backend And Frontend Features

- Every code feature starts from a ticket with objective, scope, out-of-scope boundary, acceptance criteria and required verification.
- Use a ticket-named feature branch and one draft PR per feature.
- The branch is the only place code changes and review fixes are made.
- The pull request targets the repository-authoritative integration branch. Main is the current expected target for HomeTruth, but agents must inspect rather than assume; a repository may use dev in a different context.
- Never commit, push or repair feature code directly on the target branch.
- Never create a second PR to avoid reviewing or fixing the first.

## Required PR Review Loop

Use the installed pr-review-fix-loop skill for every HomeTruth code ticket. It is intentionally generic and must not be edited for HomeTruth-specific branch names.

1. Read current instructions, ticket and repository conventions.
2. Inspect git status, worktrees, branch/upstream, remotes, existing PRs and the target branch.
3. Identify a clean base-review worktree and a separate feature worktree. Preserve unrelated dirty work; never reset or discard it.
4. Fetch and fast-forward the base branch. Record its SHA.
5. Reconcile the base into the feature branch when it advances. Do not rebase a pushed feature branch unless Jason explicitly asks.
6. Implement and validate on the feature branch only.
7. Commit intentional files, push and create or update one draft PR.
8. Review the complete three-dot diff from the clean base worktree, including callers, migrations, authorization/privacy, regressions, UX and test quality.
9. Fix every actionable finding only on the feature branch. Add a regression sensor where appropriate. Push and repeat the base-to-feature review.
10. Keep the PR draft through the internal review/fix loop. Make it ready once, only after the final local gate passes; then inspect the resulting CI run.
11. Call a PR clear to merge only when it is current with its base, mergeable, reviewed with no actionable findings, clean, fully pushed, validated and supported by accurate ticket evidence.

After merge, switch the implementation worktree to the target branch, pull the merge result, verify the expected commit is present and update ticket evidence. Do not delete branches or worktrees that contain user changes.

## Tools And Skills

Use the smallest reliable tool for the job:

- rg and rg --files for repository discovery.
- git status -sb, git worktree list --porcelain, git log, git diff --check, and non-interactive git commands for repository state.
- The GitHub tools or gh for PR state, checks, review threads and mergeability.
- The pr-review-fix-loop skill for the complete feature-to-PR loop.
- github:gh-address-comments for actionable review feedback.
- github:gh-fix-ci for GitHub Actions failures.
- playwright or the browser-control skill for frontend feature validation. Bind any local server to the feature worktree and prove the tested browser is serving that exact head.

Use existing repository scripts for builds, migrations and tests. For any migration or retrieval change, test both the narrow logic and the real configured dependency path when credentials/services are available. Describe unavailable target-environment checks as gaps, never as passes.

## Review Standards

Reviews must lead with findings, in severity order and with precise file/line evidence. A statement of no findings means the full diff and surrounding behaviour were inspected; passing tests alone do not satisfy review.

Every review checks, where applicable:

- correctness and failure paths
- authorization, privacy and consent boundaries
- persistence, migration and rollback safety
- API and backward-compatibility contracts
- property/user/partner data isolation
- UI states, accessibility and exact-head browser behaviour
- observability, reporting accuracy and no-data behaviour
- scope discipline and test quality

## HomeTruth Product Guardrails

- Homeowner value comes first.
- A partner receives aggregate-only evidence by default.
- Individual property, document, task, profile or behavioural access requires explicit consent, approved purpose and a separate intentional product path.
- Do not introduce claims, underwriting, pricing, credit, valuation or regulated-advice assertions without approved evidence and copy.
- Build a common partner-programme core before vertical-specific customisation.
- Insurer is the first proposed pack; mortgage-provider and new-build packs remain future validation work, not parallel implementation.

## Completion Evidence

For every ticket, keep the ticket accurate:

- implementation and verification performed
- focused and broader checks with results
- PR URL and base/head SHA where code changed
- review result, follow-up fixes and CI outcome
- remaining limitations, target-environment gaps or external decisions

Do not mark a ticket complete, a PR clear to merge, or a release ready beyond the available evidence.
