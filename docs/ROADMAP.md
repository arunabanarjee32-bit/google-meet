# Development roadmap and contributor work packages

**All phases are proposed unless linked to completed code/tests.** Milestone durations are intentionally omitted until staffing, budgets and dependency choices are known. Each stage needs an owner, acceptance tests and written go/no-go decision.

## Phase 0 — Foundation, legal and validation (first)

- Confirm target audience, first customer segment and product name.
- Decide whether original code will be open-source, source-available or proprietary; publish appropriate LICENSE and contribution terms.
- Audit LiveKit Meet, LiveKit server/components/ingress/egress, and shortlisted dependencies for exact licenses, maintenance, security and integration effort.
- Write architecture decision records (ADR), threat model, initial cost model and vendor comparison.
- Determine MVP measurable outcomes and test device/browser matrix.
- Create repo issue templates, pull request workflow and CI design.

**Gate:** licensed component shortlist; owner-approved architecture; no unresolved high-risk reuse claims.

## Phase 1 — Working small meeting

- Create a reproducible TypeScript monorepo and deployable Next.js web app, based on licensed upstream LiveKit Meet design/code only after the audit.
- Introduce environment schema validation, lint/type/test pipeline, logging and observability.
- Server-side session/token issuance, basic accounts and meeting creation/join.
- Camera, microphone, screen sharing, participant roster and host permissions.
- Reconnect handling, device/browser compatibility tests, security baseline.

**Gate:** reproducible local/demo run; two actual browsers can meet securely; permissions and smoke tests pass.

## Phase 2 — Competitive meeting experience

- Scheduling/calendar integrations and invites.
- Persistent moderated meeting chat, reactions, raise hand, polls and Q&A.
- Recording/Egress with informed consent, artifact policies and playback.
- Whiteboard, collaborative notes, captions/a11y, keyboard and screen-reader testing.
- Quality improvements: network adaptation, device switching, low-bandwidth mode.

**Gate:** feature flows work end-to-end, accessibility and privacy checks pass.

## Phase 3 — Large-event MVP

- Separate event and stage roles with signed viewer admission.
- Egress-to-CDN broadcast, health checks, adaptive streaming, regional delivery.
- Scalable chat/Q&A/polls, stage promotion, moderation and analytics.
- Explicit latency modes and graceful fallbacks.
- Load-test gate with 100–1K viewers and step up to 10K.

**Gate:** event operations runbook, validated 10K audience test and cost model. This is not yet 100K.

## Phase 4 — Organization, AI and business

- Workspace administration, SSO/SCIM evaluation, policies, audit logs and retention.
- Optional consent-based transcripts, summaries, translated captions.
- API/webhooks, usage metering, billing and customer support tooling.
- Mobile apps; desktop packaging only if demanded by users.

**Gate:** enterprise security and privacy review; customer trial and operational support.

## Phase 5 — 100K event hardening and launch

- Load/failure drills at 50K and 100K actual stream viewers in approved regions.
- Provider quota confirmation, reliability SLO, autoscaling tests, anti-abuse and incident response.
- Production deployment, backups, restore tests, support rotation, billing alerts and legal review.

**Gate:** reproducible, independently reviewed, real viewer-capacity evidence and budget approval; only then market the tested capacity.

## Good first issues for contributors

- Audit and document current upstream version/license inventory.
- Create ADR proposals for self-hosted vs managed delivery and latency modes.
- Build a minimal repository skeleton with one web app and tests (after owner license decision).
- Define JSON schemas for join token and stage-role actions, with server-side authorization.
- Implement a read-only developer-facing architecture and threat-model review.
- Define a load-test method that distinguishes real playback from synthetic clients.

## How to prioritize work

Issue proposals should include: user problem, milestone, proposed reuse, dependency/license evidence, scope, acceptance tests, risk, cost, and an out-of-scope section. Prefer vertical slices shipped behind feature flags over hundreds of empty folders. See [Contributing](../CONTRIBUTING.md).
