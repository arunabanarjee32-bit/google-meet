# MegaMeet foundation audit and source investigation — 2026-11-15

**Status:** evidence pack / proposal. This document does not approve G00/G01 gates and does not mark backlog tasks complete.

**Backlog alignment:** MM-01-01, MM-01-02 and MM-01-03 evidence; related to issues #1, #2 and #3.

## Executive decision

Keep the existing modular-monorepo strategy. Do not combine several conferencing engines.

Recommend exactly two primary foundations:

1. **LiveKit Meet** — https://github.com/livekit-examples/meet — reviewed commit c3a16bdc7be03e201615779e8f2f6ee61d41ec91 — Apache-2.0 repository license. Use as a frontend/reference foundation for meeting interaction patterns, not as a production authorization backend and not as MegaMeet branding.
2. **LiveKit Server** — https://github.com/livekit/livekit — release v1.13.11, commit 385aa40f9292fe1db8caad87301e4b285b7c198a — Apache-2.0 with LICENSE and NOTICE. Use as the real-time media/SFU infrastructure through SDK/API boundaries.

Jitsi Meet and BigBlueButton remain valuable reference systems, but neither should be a second conferencing engine beside LiveKit.

The repository's original-code license/contributor policy is still unresolved in issue #1. Product source code therefore remains blocked by the repository's own AGENTS.md, CONTRIBUTING.md and docs/LICENSING.md. This audit intentionally imports no upstream source.

## A. Repository audit

### Actual default-branch contents

The current main branch contains only governance/planning material:

- .github/
  - ISSUE_TEMPLATE/architecture_review.md
  - ISSUE_TEMPLATE/bug_report.md
  - ISSUE_TEMPLATE/feature_request.md
  - PULL_REQUEST_TEMPLATE.md
- AGENTS.md
- CONTRIBUTING.md
- PUBLIC_REPOSITORIES_TO_STUDY.txt
- README.md
- SECURITY.md
- docs/
  - ARCHITECTURE.md
  - CODEX_CREDIT_POLICY.md
  - CODEX_TASKS.md
  - COST_MODEL.md
  - DECISIONS/
    - 0001-modular-monorepo.md
    - 0002-interactive-and-broadcast.md
    - README.md
  - DEFINITION_OF_DONE.md
  - DELIVERY_MASTER_PLAN.md
  - DEVELOPMENT.md
  - FIRST_SPRINT.md
  - ISSUE_INDEX.md
  - LICENSING.md
  - PRODUCT_REQUIREMENTS.md
  - PROJECT_VISION.md
  - ROADMAP.md
  - SCALABILITY_100K.md
  - SECURITY_PRIVACY.md
  - TASK_BACKLOG.csv
  - TASK_BACKLOG.md
  - TECH_STACK.md

No application package, source tree, package lockfile, test suite, Docker configuration, database migration, environment schema, deployment manifest or GitHub Actions workflow exists on main.

### Git history and GitHub work state

Seven commits exist and all are documentation/governance changes. The newest commit catalogued the 30 public repositories. There are currently no pull requests.

Open issues #1-#20 cover the license blocker, upstream audit, architecture, security/scale design and the G00-G13 epics.

### What actually works today

- Repository onboarding and planning documents render and cross-reference the intended product.
- The 178-task backlog and 14 gated phases exist.
- Contributor and security guidance exists.
- Two architecture ADRs are proposed.
- GitHub issue and PR templates exist.

There is **no runnable MegaMeet meeting application today**. No browser flow, authentication, meeting creation, LiveKit connection, CI, tests, recording, broadcast, chat or persistence can be claimed working.

### Missing application modules

For the first real vertical slice, the missing minimum is:

- apps/web Next.js/React/TypeScript application.
- package manager/version and lockfile.
- packages/config runtime environment validation.
- packages/contracts shared schemas once API contracts are approved.
- authentication/session boundary.
- meeting persistence and tenant-aware authorization.
- server-side media grant service.
- LiveKit client integration.
- camera/microphone/screen-share UI.
- unit/integration/browser test infrastructure.
- GitHub Actions build/lint/type/test workflow.
- local developer instructions backed by real commands.

Do not scaffold long-term services such as chat, AI, broadcast, mobile, billing or admin as empty directories merely to match diagrams.

### Documentation completeness and inconsistencies

The high-level documentation is unusually explicit about what is proposed versus implemented. The architecture, delivery plan, first sprint, licensing document and ADRs agree on the major principles:

- modular monorepo,
- one conferencing/media engine rather than several,
- LiveKit as the proposed interactive-media foundation,
- server-side authorization,
- separate large-event broadcast delivery,
- no 100K production claim without tests,
- no substantive source import before the original-code licensing decision.

The main inconsistency is not architectural; it is maturity. Several documents describe future service directories and technology candidates in detail, while the repository contains no product code. New contributors must continue treating those paths as future design, not existing modules.

A second gap is that ADR-0001 and ADR-0002 remain Proposed. There is no approved ADR yet selecting the two primary upstream foundations or documenting the exact reviewed versions.

### Security gaps

No security controls are implemented because no application exists. Before commercial deployment the control plane must implement, at minimum:

- authenticated or cryptographically ticketed meeting admission,
- tenant isolation,
- immutable internal participant identity,
- server-derived roles and capabilities,
- short-lived media credentials,
- rejection of cross-room/cross-tenant grants,
- no client-controlled role elevation,
- CSRF/origin protection for session-bound mutation endpoints,
- request validation and bounded metadata,
- abuse/rate controls,
- room capacity/lock/lobby checks,
- audit events for role, admission, moderation and recording actions,
- webhook signature verification,
- secret redaction and safe logging,
- recording/transcription consent and retention enforcement,
- dependency/SBOM/security scanning in CI.

### Dependency gaps

No dependencies are installed yet. That is good: the project can still select exact versions deliberately.

A notable upstream caveat: the reviewed LiveKit Meet package.json directly includes @livekit/krisp-noise-filter 0.4.6. npm identifies that package's license as “SEE LICENSE IN https://livekit.io/legal/terms-of-service”, not Apache-2.0. MegaMeet should not inherit it automatically. Omit it from the initial product dependency set unless its terms are separately reviewed and approved.

### Missing tests and CI

No MegaMeet test runner or CI workflow exists.

The first implementation milestone must add reproducible checks for build, lint, type checking, unit/integration tests and eventually browser tests. Authorization tests are a release blocker, not optional polish.

### Immediate implementation blockers

1. **Issue #1 / MM-00-07:** owner has not chosen the license/contributor terms for original MegaMeet code.
2. G00/G01 architecture decisions are not accepted.
3. Identity/tenant model is not yet a versioned contract.
4. No approved exact dependency BOM exists.
5. No development LiveKit endpoint/credentials are committed or expected; secrets must remain external.

### Exact next executable work order

Continue the existing plan, do not replace it.

- Decision work: finish MM-00-07 and owner approval in issue #1.
- Architecture evidence: this document supports MM-01-01/02/03 but those tasks should not be marked complete before their stated dependencies and review are satisfied.
- After the G00/G01 gate, the first product-code task remains **MM-02-01: Initialize Next.js TypeScript monorepo**.
- Do not jump directly to MM-04-01 media integration before secure identity/meeting authorization exists.

## B. Exactly two primary repositories

### 1. LiveKit Meet — frontend/reference foundation

Repository: https://github.com/livekit-examples/meet

Reviewed commit: https://github.com/livekit-examples/meet/commit/c3a16bdc7be03e201615779e8f2f6ee61d41ec91

Reviewed on: 2026-11-15

License: Apache-2.0 repository LICENSE; no root NOTICE observed at this commit.

Maintenance evidence: current HEAD was committed 2026-11-14. The commit updates @livekit/krisp-noise-filter to 0.4.6.

Build/application shape at the reviewed commit:

- Next.js application.
- TypeScript.
- pnpm 10.18.2.
- Node >=18.
- React 18.3.1.
- Next 15.5.21.
- livekit-client 2.24.0.
- livekit-server-sdk 2.19.3.
- @livekit/components-react 2.9.25.
- Vitest.
- ESLint/Prettier.
- app/api, app/custom, app/rooms, lib, public and styles.
- Upstream CI runs lint, formatting and tests; the reviewed workflow does not run an explicit production build/typecheck step.

What to reuse:

- prejoin/device interaction patterns,
- room connection lifecycle patterns,
- LiveKit Components integration approaches,
- camera/microphone settings ideas,
- screen-share and layout interaction patterns,
- reconnect/error UX concepts,
- test/build organization as reference.

What to custom-build:

- MegaMeet design system and branding,
- account/session integration,
- meeting scheduling and persistence,
- tenant-aware authorization,
- room admission/lobby,
- server-side role/capability policy,
- moderation/audit workflows,
- recording consent and access control,
- business/domain APIs,
- analytics/privacy controls.

What not to copy unchanged:

- LiveKit logos/assets/branding,
- demo/debug token entry flows,
- app/api/connection-details authorization behavior,
- recording start/stop routes,
- any package with non-approved separate terms,
- broad demo environment switches that expose arbitrary server URLs or tokens to normal users.

#### Critical token endpoint review

At the reviewed commit, app/api/connection-details/route.ts:

- is a GET endpoint,
- accepts roomName, participantName, metadata and region from the request,
- authenticates no user,
- checks no organization/tenant membership,
- checks no invitation or lobby state,
- accepts caller-controlled metadata,
- derives identity from the display name plus a random cookie suffix,
- issues a five-minute token,
- grants roomJoin, canPublish, canPublishData and canSubscribe to every caller.

That is appropriate for a demo, not a commercial authorization boundary.

Before MegaMeet deployment, replace it with a server-owned grant flow that:

1. Accepts an authenticated application session or signed guest invitation/ticket.
2. Looks up the MegaMeet meeting by an opaque public ID.
3. Resolves the internal LiveKit room name server-side.
4. Verifies tenant, membership/invite, meeting status, lock state, lobby/admission state, capacity and bans.
5. Derives a stable internal participant identity from the authenticated principal or guest ticket; display name stays separate.
6. Derives role server-side: host, moderator, speaker, attendee or viewer.
7. Maps that role to least-privilege media grants. A viewer must not publish. Screen sharing should require an explicit capability. Data publishing should be scoped to product need.
8. Uses short token lifetime and a controlled refresh/rejoin path; never puts provider secrets in the browser.
9. Adds per-principal, per-IP and per-meeting rate limits plus abuse telemetry.
10. Returns no-store responses and keeps tokens out of URLs/application logs.
11. Audits grant issuance, admission, denial and role changes without logging raw tokens.
12. Supports revocation/kick/permission updates through the backend.
13. Has negative tests for expiry, wrong room, wrong tenant, revoked invite and role elevation.

The reviewed recording start/stop routes explicitly warn that they do not authenticate users and allow anyone who knows a room name to control recording. MegaMeet must replace them with authenticated, consent-aware, role-authorized mutations.

### 2. LiveKit Server — media/SFU foundation

Repository: https://github.com/livekit/livekit

Pinned release: https://github.com/livekit/livekit/releases/tag/v1.13.11

Pinned commit: https://github.com/livekit/livekit/commit/385aa40f9292fe1db8caad87301e4b285b7c198a

Release date: 2026-10-25

License: Apache-2.0. The reviewed release contains root LICENSE and NOTICE files; pkg/sfu also contains a NOTICE.

Maintenance evidence: active Go repository with current work in November 2026; v1.13.11 includes SFU retransmission controls, TURN credential handling, signaling/RTC fixes, security-related base-image/toolchain updates and tests.

Source boundaries observed at v1.13.11:

- pkg/routing — local/Redis routing, nodes, selectors, room routing.
- pkg/service — auth, room service, RTC service, Redis store, signaling, web transport, TURN, egress/ingress integration.
- pkg/rtc — rooms, participants, media tracks, subscriptions, transport, signaling.
- pkg/sfu — receivers, downtracks, forwarding, bandwidth estimation, pacing, stream allocation and RTP logic.
- test — single-node and multi-node integration tests, webhooks and signaling tests.

Deployment/operations:

- Single node has no external cluster dependency.
- Distributed mode uses Redis for room state/routing/message bus.
- Each self-hosted room currently fits on one node; multi-node scale primarily increases concurrent rooms.
- Production guidance recommends compute-oriented instances and 10 Gbps or faster networking.
- API/WebSocket traffic uses 7880 behind TLS termination/load balancing.
- WebRTC media normally uses UDP, with ICE/TCP fallback; documented defaults include 50000-60000/UDP and 7881/TCP.
- Embedded TURN can provide UDP/TLS fallback; external TURN is also supported.
- Prometheus metrics are available.
- Planned draining is supported for node shutdown.
- Egress is a separate service when self-hosted.

MegaMeet responsibility is **not** to fork and maintain the SFU. Use LiveKit Server as an external media engine, pin releases, preserve required notices, monitor upgrades and vulnerabilities, and keep MegaMeet authorization/business state in MegaMeet services.

## Serious alternative comparison

### Jitsi Meet

Repository: https://github.com/jitsi/jitsi-meet

Current stable release observed: stable/jitsi-meet_11248, published 2026-09-14.

License: Apache-2.0.

Strengths:

- mature complete conferencing application,
- active maintenance,
- web and React Native experience,
- Jitsi Videobridge SFU ecosystem,
- Jicofo orchestration,
- Prosody/XMPP integration,
- Jibri recording/streaming ecosystem,
- broad deployment history.

Why not selected as a main foundation:

- its client repo already spans web, Android, iOS, React Native, Debian packaging, custom modules and a large dependency surface;
- production deployment is a coordinated stack rather than one narrow media engine;
- adopting it would push MegaMeet toward customizing a complete Jitsi product architecture instead of owning a clean Next.js/control-plane design;
- running Jitsi beside LiveKit would duplicate SFU, signaling, recording and operational responsibilities.

Security note: Jitsi publishes a security policy and advisories. Its jitsi-meet advisory list includes past authentication, OAuth redirect, polling and E2EE-cue issues. This is evidence of a maintained security process, not a statement that current stable Jitsi is insecure. Exact deployed versions still require advisory checks.

### BigBlueButton

Repository: https://github.com/bigbluebutton/bigbluebutton

Pinned comparison release: v4.0.2, commit f31e684f6eb30722acd09fe457fa34d8ee4d7796, published 2026-11-06.

License: LGPL-3.0 repository metadata/license; distribution and component-level obligations require legal review.

Strengths:

- exceptionally rich virtual-classroom workflows,
- recording/playback,
- polls, shared notes, whiteboard and breakout-room patterns,
- mature moderator/teacher use cases,
- active 4.0 maintenance.

Why not selected as a main foundation:

- very large multi-service product architecture,
- education-first domain assumptions,
- broad operational/security surface,
- LGPL diligence is more involved than the selected Apache-2.0 foundations,
- using it beside LiveKit would duplicate product/media responsibilities rather than simplify MegaMeet.

BigBlueButton's 4.0 repository includes a bbb-livekit placeholder/integration path, which further supports treating LiveKit as a lower-level reusable media technology rather than adopting the entire classroom system.

Security note: BigBlueButton maintains an explicit security policy and has published multiple 2026 advisories, including high/critical issues in older or pre-patch versions. This demonstrates both a large attack surface and active disclosure/patching. Any BBB deployment would require strict supported-version tracking.

## Scored engineering comparison

Scores are engineering judgment for MegaMeet, 10 = best fit. “Cost” scores lower expected platform/operations burden; “integration” scores ease of integrating into MegaMeet's proposed architecture. They are not benchmarks.

| Criterion | LiveKit Meet | LiveKit Server | Jitsi Meet | BigBlueButton |
| --- | ---: | ---: | ---: | ---: |
| Engineering fit | 9 | 10 | 7 | 5 |
| Commercial-license fit | 8 | 9 | 9 | 6 |
| Maintenance | 9 | 10 | 9 | 9 |
| Security fit / controllability | 5 | 8 | 7 | 6 |
| Cost fit | 9 | 8 | 6 | 5 |
| Scalability fit | 7 | 9 | 8 | 7 |
| Integration simplicity | 9 | 9 | 5 | 3 |
| Extensibility | 9 | 9 | 7 | 7 |
| Expected implementation time saved | 9 | 10 | 7 | 6 |
| **Average** | **8.2** | **9.1** | **7.2** | **6.0** |

LiveKit Meet's security score is intentionally lower because the demo API boundaries are not production authorization. The score rises only after MegaMeet replaces those boundaries.

## C. Original MegaMeet architecture decision

### Physical repository shape for the first milestones

Preserve the long-term modular-monorepo ADR, but start smaller than the future diagram:

~~~text
apps/
  web/            # Next.js UI plus thin server/BFF routes for the first vertical slice
packages/
  config/         # runtime environment validation
  contracts/      # versioned schemas once contracts are approved
  authz/          # add when authorization code is real, not as an empty placeholder
docs/
infra/            # only concrete local/deployment assets that are actually used
~~~

Do not create services/api, services/chat, services/ai, services/broadcast, mobile or desktop packages until an implemented feature needs independent runtime scaling/release ownership.

### Control plane

For the first vertical slice, the Next.js server boundary can host the meeting-control API. Extract a separate API service only when load, runtime isolation, language/tooling or independent deployment needs justify it.

Canonical state:

- PostgreSQL: users, organizations, memberships, meetings, invitations, admission decisions, roles, recordings metadata, audit events.
- Valkey/Redis-compatible store: add later for ephemeral shared state, rate limits, fanout coordination and self-hosted distributed LiveKit.
- Object storage: recordings/exports later.
- Provider state is never the canonical source of MegaMeet authorization.

### Identity and roles

Use OIDC for account identity, but keep product authorization in MegaMeet.

Roles:

- host,
- moderator,
- speaker,
- attendee,
- viewer.

A role is an application authorization decision, not a string accepted from a browser.

Suggested trust flow:

~~~text
browser
  -> authenticated session OR signed guest invitation
  -> MegaMeet meeting/admission service
  -> tenant + meeting + invite + lobby + role policy
  -> scoped short-lived LiveKit token
  -> LiveKit Server
~~~

### Initial domain model

- User
- Organization
- Membership
- Meeting
- MeetingPolicy
- Invitation / GuestTicket
- AdmissionRequest
- ParticipantSession
- RoleAssignment
- Recording
- AuditEvent
- LargeEvent
- StageRequest
- BroadcastSession

Do not persist raw LiveKit JWTs. Persist grant/audit metadata if needed: subject, meeting, role, capability set, issued-at/expiry, provider identity and revocation/action state.

### API boundary

Representative contracts to define in MM-01-06:

- POST /api/meetings
- GET /api/meetings/{meetingId}
- POST /api/meetings/{meetingId}/join-requests
- POST /api/meetings/{meetingId}/admissions/{requestId}
- POST /api/meetings/{meetingId}/media-grants
- POST /api/meetings/{meetingId}/role-assignments
- POST /api/meetings/{meetingId}/remove-participant
- POST /api/meetings/{meetingId}/recordings
- DELETE /api/meetings/{meetingId}/recordings/{recordingId}

Mutations must be idempotent where retries are likely. Grant responses should be Cache-Control: no-store.

### Event contracts

Version and audit at least:

- meeting.created
- meeting.started
- join.requested
- participant.admitted
- participant.joined
- participant.left
- media.grant.issued
- participant.role.changed
- participant.removed
- stage.requested
- stage.approved
- stage.revoked
- recording.started
- recording.stopped
- broadcast.started
- broadcast.degraded
- broadcast.failed
- meeting.ended

High-frequency media statistics should not become canonical database rows by default.

### Monitoring

- structured logs with correlation/request/event IDs,
- explicit secret/token redaction,
- OpenTelemetry-compatible traces for application services,
- application metrics for grant/admission/rate-limit failures,
- LiveKit Prometheus metrics when self-hosted,
- browser media-quality telemetry sampled with privacy controls,
- synthetic join tests in staging,
- alerts on token issuance anomalies, cross-tenant denials, reconnect spikes, egress failures and broadcast health.

## D. Reuse/build/defer matrix

| Capability | Classification | Decision |
| --- | --- | --- |
| WebRTC protocol/SFU | Integrate approved dependency | LiveKit Server; do not rebuild |
| Meeting frontend patterns | Integrate/reference approved dependency | LiveKit Meet patterns + LiveKit Components, with original MegaMeet UX |
| Product design system/branding | Build original | MegaMeet-owned |
| Identity protocol | Integrate dependency | OIDC; provider choice remains gated |
| Tenant/meeting authorization | Build original | Server-side MegaMeet policy |
| LiveKit token issuance | Build original boundary using SDK | Never reuse demo endpoint unchanged |
| Device preview/A-V controls | Integrate dependency + original UX | LiveKit client/components |
| Screen sharing | Integrate dependency + original policy/UX | LiveKit SDK |
| Recording/export | Integrate approved dependency later | LiveKit Egress after consent policy |
| TURN | Integrate existing capability | Prefer LiveKit embedded TURN first; evaluate coturn only for proven need |
| Chat/Q&A/polls | Build product logic; reuse transport if justified | Do not add Centrifugo until scale/persistence requirements warrant it |
| Whiteboard | Integrate dependency later | Excalidraw is the cleaner permissive candidate; audit exact package |
| Collaborative notes | Integrate dependency later | Yjs candidate; verify exact package/license |
| Calendar UI | Integrate dependency later | FullCalendar standard/core only unless premium separately approved |
| Enterprise OIDC/SSO admin | Build product policy; integrate IdP | Keycloak is possible but operationally heavy for first MVP |
| Cache/ephemeral state | Integrate later | Valkey/Redis-compatible |
| Transcription | Defer | Consent/cost benchmark first; Whisper is a candidate, not a mandate |
| AI summaries/translation | Defer | After recording/transcription governance |
| Mobile | Defer | LiveKit React Native SDK later |
| Billing | Defer | Do not introduce Kill Bill before product-market need |
| Product analytics | Defer/optional | Privacy-gated; Umami candidate |
| API/WS load tests | Integrate tool later | Locust is permissive; does not prove media playback |
| 100K broadcast origin/CDN | Integrate managed provider first | Separate from LiveKit interactive SFU |
| 100K synthetic socket load only | Insufficient | Must include real playback validation |

## All 30 study repositories — broad screening

This table is a current screening, not an approval to install. “Recent push” is GitHub repository metadata observed 2026-11-15. Adoption-level security and transitive-license review is required again at the exact chosen version.

| # | Repository | License signal / legal files | Recent push | Primary role | Dev/ops burden | Cost shape | Integration / overlap | Decision |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | livekit-examples/meet | Apache-2.0; LICENSE | 2026-11-14 | Meeting web app/reference | Medium | Low app hosting | Strong fit; demo auth must be replaced | **MAIN #1** |
| 2 | livekit-examples/livestream | No root license observed | 2026-10-29 | Livestream reference | Low | Low | License blocks code reuse; overlaps broadcast UI reference | Reference only |
| 3 | livekit/livekit | Apache-2.0; LICENSE + NOTICE | 2026-11-15 | SFU/media server | High if self-hosted | Compute + bandwidth or managed service | Core media engine | **MAIN #2** |
| 4 | livekit/egress | Apache-2.0; LICENSE + NOTICE | 2026-11-15 | Recording/stream export | Medium-high | CPU/GPU + storage/network | Supports LiveKit; not a CDN | Integrate later |
| 5 | livekit/ingress | Apache-2.0; LICENSE + NOTICE | 2026-11-15 | RTMP/WHIP/SRT ingest | Medium | Transcoding compute | Only needed for external encoders/sources | Conditional |
| 6 | livekit/components-js | Apache-2.0; LICENSE + NOTICE | 2026-11-14 | React media UI components | Low | None beyond app | Supports main UI; not a primary repo | Integrate |
| 7 | livekit/client-sdk-react-native | Apache-2.0; LICENSE + NOTICE | 2026-11-13 | Mobile media SDK | Medium | Mobile engineering | Duplicates no web feature; later platform | Defer |
| 8 | livekit/agents | Apache-2.0; LICENSE + NOTICE | 2026-11-15 | AI agent framework | Medium-high | Model/compute/vendor usage | Optional AI; separate 2026 advisory requires version care | Defer |
| 9 | jitsi/jitsi-meet | Apache-2.0; LICENSE | 2026-11-14 | Complete conferencing stack/client | High | Multi-service compute/network | Competes with LiveKit stack | Reference alternative |
| 10 | bigbluebutton/bigbluebutton | LGPL-3.0; LICENSE | 2026-11-15 | Complete classroom platform | Very high | Multi-service compute/storage | Competes with product/media stack | Reference alternative |
| 11 | owncast/owncast | MIT; LICENSE | 2026-11-15 | Self-hosted one-to-many live video | Medium | Origin/bandwidth | Broadcast reference, not meeting SFU | Reference |
| 12 | OvenMediaLabs/OvenSpace | MIT; LICENSE | 2026-01-20 | Demo/client for Oven ecosystem | Medium | Depends on media backend | Weaker maintenance signal; broadcast reference | Reference |
| 13 | OvenMediaLabs/OvenMediaEngine | AGPL-3.0; LICENSE + third-party license file | 2026-11-15 | Low-latency media origin/server | High | Compute/network | Broadcast alternative; AGPL obligations | Avoid default |
| 14 | ossrs/srs | MIT; LICENSE | 2026-11-14 | Streaming origin/server | High | Compute/network/CDN | Self-host broadcast-origin candidate | Conditional |
| 15 | excalidraw/excalidraw | MIT; LICENSE | 2026-11-15 | Whiteboard | Medium | App/realtime persistence | Strong whiteboard candidate | Conditional |
| 16 | yjs/yjs | Source LICENSE present; GitHub metadata NOASSERTION | 2026-11-14 | CRDT collaboration | Medium | Realtime persistence/fanout | Notes/whiteboard collaboration | Conditional |
| 17 | keycloak/keycloak | Apache-2.0; LICENSE.txt | 2026-11-15 | Identity/OIDC/SSO | High | JVM/DB/ops | Full IdP; potentially heavy early | Conditional |
| 18 | centrifugal/centrifugo | Apache-2.0; LICENSE | 2026-11-15 | Realtime fanout gateway | Medium | Service + Redis/DB depending design | Could power chat/presence; don't add before need | Conditional |
| 19 | fullcalendar/fullcalendar | MIT core; LICENSE.md; premium separate | 2026-11-12 | Calendar UI | Low | None for core | Scheduling UI only | Conditional |
| 20 | valkey-io/valkey | BSD-3-Clause metadata; COPYING/LICENSES | 2026-11-15 | Cache/ephemeral state | Medium | Memory service | Useful with distributed state | Conditional |
| 21 | openai/whisper | MIT; LICENSE | 2026-08-31 | Speech-to-text | High compute | CPU/GPU | Optional transcription | Defer |
| 22 | novuhq/novu | Mixed MIT/enterprise files | 2026-11-15 | Notification platform | Medium-high | Service/DB/queue | Avoid early platform overhead | Defer |
| 23 | umami-software/umami | MIT; LICENSE | 2026-11-15 | Product analytics | Medium | App/DB | Privacy-gated analytics | Defer |
| 24 | killbill/killbill | Apache-2.0; LICENSE | 2026-11-13 | Billing platform | High | JVM/DB/ops | Excessive for first release | Defer |
| 25 | locustio/locust | MIT; LICENSE | 2026-11-15 | Load testing | Low-medium | Test infrastructure | Useful for API/WS, not real media proof | Integrate later |
| 26 | coturn/coturn | LICENSE + AUTHORS; GitHub metadata NOASSERTION | 2026-11-13 | TURN/STUN | Medium-high | Relay bandwidth | Duplicates LiveKit embedded TURN unless special need | Conditional |
| 27 | tldraw/tldraw | LICENSE.md + TRADEMARKS; commercial terms need review | 2026-11-15 | Whiteboard SDK | Medium | License/commercial | Overlaps Excalidraw | Reference/conditional |
| 28 | calcom/cal.diy | MIT; LICENSE | 2026-11-13 | Scheduling reference | High if whole app | App/DB/integrations | Do not embed whole scheduler | Reference |
| 29 | zitadel/zitadel | AGPL-3.0; LICENSE | 2026-11-13 | Identity platform | High | Service/DB | Overlaps Keycloak/OIDC options; AGPL diligence | Reference |
| 30 | grafana/k6 | AGPL-3.0; LICENSE.md | 2026-11-14 | Load testing | Low-medium | Test infrastructure | Overlaps Locust; licensing less simple for project tooling | Reference |

### Security-screen interpretation

- LiveKit Server: GitHub currently shows no published repository security advisories; GitHub also reports no SECURITY.md in that repository. **Absence of advisories is not proof of absence of vulnerabilities.** Keep dependency/container scanning and release monitoring.
- LiveKit Agents: a 2026 moderate advisory covered plugin API keys leaking into logs in versions <=1.6.9; it is deferred anyway.
- Jitsi Meet: publishes a security policy and historical advisories.
- BigBlueButton: publishes a security policy and multiple 2026 advisories; only supported/patched releases should ever be evaluated.
- Every conditional candidate requires an exact-version GHSA/CVE and transitive dependency scan before installation.

## E. Implementation sequence mapped to the existing backlog

Do not rewrite the 178 tasks. Use this dependency-respecting sequence:

1. **MM-00-07** — owner selects original-code license/contribution strategy.
2. **MM-00-08** — commercial licensing review of the selected strategy and upstream integration model.
3. **MM-01-01 / MM-01-02 / MM-01-03** — review this evidence pack, verify exact dependency plan, approve reuse/build/defer.
4. **MM-01-04 / MM-01-05** — finalize interactive-vs-broadcast and control-plane/realtime boundary ADRs.
5. **MM-01-06 / MM-01-07 / MM-01-08** — version API/events, data model/tenant boundaries, threat model.
6. **MM-01-09 / MM-01-11 / MM-01-12** — managed broadcast cost/reliability comparison, red-team review, human architecture acceptance.
7. **MM-02-01** — create the first runnable Next.js/TypeScript monorepo slice.
8. **MM-02-02 through MM-02-06** — lock package manager, env validation, lint/typecheck, tests and least-privilege CI.
9. **G03** — identity, organizations, secure meeting APIs and tickets.
10. **MM-04-01 / MM-04-02** — LiveKit client integration plus secure server-side media grants.
11. **MM-04-03 through MM-04-14** — device handling, lobby, controls, screen share, reconnect, adaptive media, interoperability and TURN validation.
12. Only after G04: collaboration/recording. Only after those gates: large-event/broadcast work.

## F. Actual implementation in this audit pass

No product code was added because the repository's own license/contribution gate is unresolved.

The safe implementation contribution for this pass is documentation-only:

- this reproducible repository/source audit,
- an ADR proposal selecting the two primary foundations,
- a continuation handoff for the next agent.

No source from LiveKit, Jitsi, BigBlueButton or another upstream project is copied into MegaMeet.

## G. Verification performed

Verified against the actual GitHub repository rather than architecture diagrams:

- default branch and repository permissions,
- complete root/docs/.github directory listings,
- named planning documents,
- proposed ADRs,
- seven-commit history,
- issues #1-#20,
- no existing PRs,
- no app source/package/lockfile/tests/workflows,
- all 30 study-repository current metadata and root legal-file signals,
- LiveKit Meet current package.json, source layout, CI, token route and recording routes,
- LiveKit Server v1.13.11 tag/commit, source module boundaries, config/deployment/TURN/Redis model and tests,
- Jitsi stable source/package shape,
- BigBlueButton v4.0.2 source shape and current platform positioning.

Not verified as working MegaMeet behavior:

- no build can be run because MegaMeet has no package.json,
- no tests can be run because MegaMeet has no test suite,
- no media call can be made because MegaMeet has no application,
- no 100K load test has been run,
- no production provider quota or budget has been approved.

## H. Large-event architecture and cost envelope

### Interactive meeting mode

Use LiveKit SFU for bounded, bidirectional meetings.

- WebRTC for speakers/participants.
- Adaptive subscription/simulcast behavior through LiveKit.
- TURN/TLS fallback for restrictive networks.
- Meeting/role policy remains in MegaMeet.
- Do not equate LiveKit cluster room count with unlimited participants in one self-hosted room.

### Large-event mode

One logical MegaMeet event, two media planes:

~~~text
approved presenters
  -> LiveKit stage room
  -> LiveKit Egress
  -> managed broadcast ingest/origin
  -> provider/CDN playback
  -> authenticated audience

audience
  -> MegaMeet realtime interaction plane
  -> chat / polls / Q&A / hand raise / stage requests
~~~

Initial design assumption for testing, not a capacity claim: keep the live stage deliberately small (for example, tens of connected presenters and materially fewer simultaneous camera publishers) while the audience is playback-only. Exact limits must be measured and approved.

### Viewer authentication

- MegaMeet authenticates the event ticket/session.
- Backend returns a provider-specific short-lived playback authorization or signed URL/cookie where supported.
- Playback authorization must not authorize presenter-stage publishing.
- Chat/Q&A tokens are separately scoped to event channels.
- Revocation/ban must affect both playback eligibility and interaction access according to policy.

### Failover

- Planned LiveKit node shutdown can drain active rooms; an unexpected room-host node loss should be treated as disruptive in self-hosted mode unless separately proven otherwise.
- Egress failure must surface a broadcast-degraded state and bounded restart policy.
- Broadcast-provider outage should initially fail explicitly; dual-provider active/standby is a later cost/complexity decision, not an automatic first-release feature.
- Keep stage state and event interaction state outside the broadcast provider so the audience can see a hold/retry state instead of losing the logical event.

### Latency

- Presenter stage: WebRTC interactive latency.
- Audience: choose provider/protocol by product need. LL-HLS commonly trades several seconds of latency for global scalability; provider WebRTC/WHEP delivery can reduce latency but changes cost/capacity assumptions.
- Audience-to-stage promotion must mute/stop audience playback before joining the interactive stage to avoid echo and duplicate audio.

### Recording

- Recording/export starts only through an authorized MegaMeet backend action.
- Consent state and visible indicators are product requirements.
- Storage region, retention, deletion and signed playback access are MegaMeet policy.
- LiveKit Egress is an exporter/recorder, not a global audience CDN.

### Illustrative 100K viewer-hour pricing snapshot

These are public list-price examples checked 2026-11-15, not approved budgets or quotes. Enterprise discounts, geography, taxes, ingest, storage, recording and support can change totals.

- Cloudflare Stream: $1 per 1,000 delivered minutes. 100,000 viewers watching 60 minutes = 6,000,000 delivered minutes, about **$6,000 delivery**. Bandwidth is included in the delivered-minute price. Source: https://developers.cloudflare.com/stream/pricing/
- Mux: published starting delivery is $0.0008/min up to 720p and $0.001/min at 1080p, with 100,000 free monthly delivery minutes on listed plans. A single 6,000,000-minute event is roughly **$4,720 at the starting 720p delivery rate** or **$5,900 at the listed 1080p rate** after that free allowance, before live-input costs and before any volume discount. Source: https://www.mux.com/pricing
- Amazon IVS low-latency: North America HD output is tiered. At 100,000 delivered viewer-hours using the published first three HD tiers, the illustrative output total is about **$6,360**, plus channel input; Full HD would be materially higher. Other viewer regions have different rates. Source: https://aws.amazon.com/ivs/pricing/

These list-price examples justify a managed-provider proof-of-concept before self-hosting a global audience CDN. They do **not** prove that any provider will grant 100K concurrency for this account/event. Quotas and enterprise capacity must be confirmed.

## I. Handoff / exact next task

The next exact task is **MM-00-07: produce and obtain the owner's written original-code license and contributor-policy decision in issue #1**.

Until that human decision is recorded, another coding agent should not create substantive MegaMeet product source.

After issue #1 is approved and G01 is accepted, the first coding task is **MM-02-01: initialize the minimal Next.js/TypeScript monorepo**, with no copied LiveKit Meet source and no unapproved Krisp dependency.
