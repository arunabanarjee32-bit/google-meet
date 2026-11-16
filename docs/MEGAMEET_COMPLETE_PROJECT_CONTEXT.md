# MEGAMEET — Complete project context and AI/developer handoff

> **Snapshot:** 2026-11-16 | **Status:** documentation and architecture planning; no runnable MegaMeet app on the inspected main branch | **Read first after an interrupted ChatGPT/Codex session.**

## 0. How to use this file

This is a **durable, GitHub-readable continuation document**. It consolidates the project objective, current repository evidence, research findings, selected two main foundations, 30 reference links, system diagrams, engineering priorities, approvals, and an exact first work order. It links to an **original 965-line uploaded prompt**, **five full-text snapshots containing 30 existing source files**, and the **recoverable chat excerpts**. The living original files remain authoritative.

**For a new developer or AI session:**
1. Read [AGENTS.md](../AGENTS.md) and [CONTRIBUTING.md](../CONTRIBUTING.md); obey their approval gates.
2. Read this file, then [docs/TASK_BACKLOG.md](TASK_BACKLOG.md), [docs/PROJECT_VISION.md](PROJECT_VISION.md), and [docs/LICENSING.md](LICENSING.md).
3. Read [the 30-repository reference catalog](../PUBLIC_REPOSITORIES_TO_STUDY.txt), [the research evidence pack in draft PR #21](https://github.com/arunabanarjee32-bit/google-meet/pull/21), and [the licensing worksheet in draft PR #22](https://github.com/arunabanarjee32-bit/google-meet/pull/22).
4. Inspect the actual CURRENT main branch, open PRs/issues, dependency versions and tests before coding. This is a **dated snapshot**, never proof that later changes do not exist.
5. Work on **one exact backlog task and one reviewable branch/PR at a time**. Never change architecture, choose a license, spend money or merge security-sensitive code by assumption.

### What is archived, and what cannot be reconstructed

| Material | Where saved | Completeness |
|---|---|---|
| Owner-uploaded master engineering brief | [Verbatim 965-line original prompt](CONTEXT_ARCHIVE/ORIGINAL_MASTER_ENGINEERING_PROMPT_2026-11-16.txt) | Exact text checked by read-back |
| GitHub default-branch project documentation | [Snapshots 1](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_01.md), [2](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_02.md), [3](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_03.md), [4](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_04.md) | Full text of 24 original files; see the copies for source paths |
| Catalog, CSV backlog, PR #21 research/ADR/handoff and PR #22 license worksheet | [Snapshot 5](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_05.md) | Full text of 6 files, with unmerged-PR flags |
| Older ChatGPT conversation messages that are actually visible | [Known chat history excerpts](CONTEXT_ARCHIVE/KNOWN_CHAT_HISTORY_EXCERPTS_2026-11-16.md) | **Partial only**; inaccessible past messages and assistant replies were not fabricated |
| Current engineering conclusions, links and Mermaid charts | This master handoff | Consolidated synthesis, not verbatim transcript |

**Access limitation:** This AI session does **not** have all complete previous ChatGPT conversations, so no one can truthfully claim this is a byte-for-byte export of every historical message. The user can later export/upload missing old chats, and they can be appended to the archive. The GitHub repo and uploaded engineering prompt are recoverable sources, unlike absent chat turns.

## 1. Product identity and mission

**Product:** MegaMeet (working name, not trademark-cleared). **GitHub repository:** https://github.com/arunabanarjee32-bit/google-meet. The historical repository name does **not** imply affiliation with Google.

**Goal:** Build an independently designed, commercially viable, reliable and secure video meeting/collaboration platform that can grow into a credible competitor to Google Meet, Zoom and Microsoft Teams. Own the **original MegaMeet application, design, business logic, authorization, product workflows, branding and architecture**; third-party open-source projects keep their own copyright and license obligations.

**Long-term capabilities:** secure rooms and meeting links; browser camera/microphone, screen share and device selection; host/co-host moderation; chat, Q&A, polls and reactions; scheduling, notifications, whiteboard, shared notes and recordings; accessibility; optional transcription/translation/AI with visible consent; organizations, SSO and administrative policies; later mobile; APIs/integrations; and large events.

**Differentiation to validate:** seamless transition from small interactive meetings to moderated large events; operational/cost transparency; accessibility and multilingual participation; developer-friendly APIs; trust and security by default. These are hypotheses, NOT achieved competitive features.

**Non-goals for first milestone:** a custom WebRTC SFU, mixing multiple conferencing engines, implementing all enterprise/AI/mobile/billing features, or promising 100,000 people simultaneously publishing cameras.

## 2. Repository facts verified on 2026-11-16

- Default branch: **main**. Inspected tree SHA: **dd2284f26f7822c086bef5070839364e42c01d8f**.
- That tree includes governance/docs, the 30-project catalog, issue/PR templates, 178-task Markdown/CSV backlog, architecture/roadmap/license/privacy/planning documents, and ADR-0001/0002.
- **No app source, package.json, lockfile, Next.js application, running backend, auth, WebRTC meeting, database migration, Docker configuration, GitHub Actions build/test workflow or production deploy exists on main at this snapshot.**
- Therefore video calls, recording, chat, 100K events, latency/scale results and build/tests are **NOT IMPLEMENTED/NOT EXECUTED**, regardless of what planning diagrams describe.
- Owner has linked GitHub access with admin/push permissions, but repo rules still require review and human decisions.
- **Draft PR #21:** [docs: audit repository and propose LiveKit foundations](https://github.com/arunabanarjee32-bit/google-meet/pull/21). Branch: audit/livekit-foundations-2026-11-15. Includes research, ADR-0003, continuation. Unmerged at capture.
- **Draft PR #22:** [MM-00-07 original-code license worksheet](https://github.com/arunabanarjee32-bit/google-meet/pull/22). Branch: docs/mm-00-07-license-decision-worksheet-2026-11-16. Unmerged at capture. Commit: fc860da4a32a3e72f6e4513d9e15580ccb7adfba.
- **Issue #1:** [Choose original-code license and contributor terms](https://github.com/arunabanarjee32-bit/google-meet/issues/1). Open/unresolved at capture.
- This context-archive branch is a **documentation contribution**, NOT evidence that G00/G01 were approved or that coding began.

### Status matrix

| Workstream | Snapshot classification | Evidence/next action |
|---|---|---|
| Vision, roadmap, project requirements | Documented | See living docs |
| 178-task, 14-phase plan | Documented | Backlog Markdown + CSV |
| 30-project research catalog | Documented | PUBLIC_REPOSITORIES_TO_STUDY.txt |
| Detailed two-main-foundation audit | Draft PR, unmerged | PR #21 / ADR-0003 |
| Original-code license and contributor rights | BLOCKED | Issue #1 / PR #22 |
| Next.js web frontend | MISSING | After gates: MM-02-01 |
| Auth / tenant data / secure join | MISSING | G03/G04 |
| Live video with 2 browsers | MISSING | MM-04-01/02 tests |
| CI / typecheck / test harness | MISSING | G02 |
| Chat/recordings/mobile/AI | PLANNED | G05/G06/G10 |
| Large event with 100K actual viewers | PLANNED, NOT PROVEN | G07/G08 real media testing |

## 3. Exactly TWO primary open-source foundations (proposed, not approved)

### Main foundation #1 — LiveKit Meet
- URL: https://github.com/livekit-examples/meet
- Inspected commit: **c3a16bdc7be03e201615779e8f2f6ee61d41ec91**
- Reviewed repository license signal: **Apache-2.0**; check exact notices/assets/dependencies before reuse.
- Reviewed app technologies: Next.js 15.5.21; React 18.3.1; TypeScript; pnpm 10.18.2; livekit-client 2.24.0; livekit-server-sdk 2.19.3; LiveKit Components React 2.9.25; Vitest.
- Useful source files/directories: app/rooms/[roomName]/PageClientImpl.tsx; app/custom/VideoConferenceClientImpl.tsx; lib/CameraSettings.tsx; lib/MicrophoneSettings.tsx; lib/SettingsMenu.tsx; app/api/connection-details/route.ts (ONLY as a security anti-pattern); app/api/record/start/route.ts and stop/route.ts (ONLY as security anti-patterns).
- **Reuse/study:** prejoin UX, device selectors, media controls, room connection lifecycle, gallery/active-speaker layouts, error/reconnect patterns and components integrations.
- **Build our own:** MegaMeet UI and branding, sessions, meetings, invitations, membership, host roles, audit logs, recording consent, persistence and authorized APIs.
- **NEVER copy demo server logic unchanged:** inspected app/api/connection-details/route.ts is a GET endpoint accepting caller-provided room/name/metadata with no authenticated meeting admission and broad roomJoin/canPublish/canPublishData/canSubscribe grants. Its recording start/stop routes explicitly warn they do not authenticate users. These are not production security boundaries.
- **Dependency warning:** upstream includes @livekit/krisp-noise-filter 0.4.6 with separate license/terms: OMIT until specifically approved. Do not copy branded images/logos/assets without rights.

### Main foundation #2 — LiveKit Server
- URL: https://github.com/livekit/livekit
- Pinned reviewed tag: **v1.13.11**, commit **385aa40f9292fe1db8caad87301e4b285b7c198a**
- Reviewed repository license signal: **Apache-2.0** with LICENSE and NOTICE.
- Go WebRTC SFU; major inspected directories: pkg/routing, pkg/service, pkg/rtc, pkg/sfu, test.
- **Use as an external media infrastructure service** through official SDKs/room APIs; do not fork/maintain an entire proprietary SFU.
- WebRTC signaling and media; local single-node deployment is simpler; distributed deployment needs Redis and appropriate networking, TURN, metrics, region/capacity monitoring and upgrade plans.
- A normal self-hosted media room should not be assumed to span every node or accept 100K publishers. Design large-event playback through a separate egress-to-origin/CDN path.
- Upgrades: pin releases, review release notes/security/dependency BOM, smoke-test AV/reconnect/permissions, and document rollback.

### Why Jitsi/BigBlueButton are alternatives, not additional main foundations

- [Jitsi Meet](https://github.com/jitsi/jitsi-meet) offers mature conferencing UX, but adopting Jitsi Videobridge/Jicofo/Prosody/Jibri beside LiveKit would duplicate media and operational stacks. Study UX and architecture.
- [BigBlueButton](https://github.com/bigbluebutton/bigbluebutton) is rich in classroom moderation/whiteboards/recordings, but has a much larger multi-service deployment and LGPL/component-level due diligence. Study workflows, do not wholesale merge.
- The other 26 catalog entries are supporting services, later features, tools, or comparisons, not equal primary foundations.
- This **exactly-two** decision is a research proposal in ADR-0003; owner/engineering approval remains required.

## 4. All THIRTY previously listed public GitHub repositories and intended roles

These are reference-catalog entries, not 30 installed dependencies. Classification is a screening decision; packages/modules may have distinct terms. Source: [existing catalog](../PUBLIC_REPOSITORIES_TO_STUDY.txt) and [audit PR #21](https://github.com/arunabanarjee32-bit/google-meet/pull/21).

| # | GitHub repository | Use to study / classification |
|---:|---|---|
| 01 | [livekit-examples/meet](https://github.com/livekit-examples/meet) | **MAIN #1** — web frontend patterns |
| 02 | [livekit-examples/livestream](https://github.com/livekit-examples/livestream) | Livestream UX reference; license check |
| 03 | [livekit/livekit](https://github.com/livekit/livekit) | **MAIN #2** — SFU media service |
| 04 | [livekit/egress](https://github.com/livekit/egress) | Future recording/export/speaker-feed egress |
| 05 | [livekit/ingress](https://github.com/livekit/ingress) | Optional RTMP/WHIP / encoder ingest |
| 06 | [livekit/components-js](https://github.com/livekit/components-js) | React media UI components/SDK |
| 07 | [livekit/client-sdk-react-native](https://github.com/livekit/client-sdk-react-native) | Later Android/iOS |
| 08 | [livekit/agents](https://github.com/livekit/agents) | Later opt-in AI agents |
| 09 | [jitsi/jitsi-meet](https://github.com/jitsi/jitsi-meet) | Complete meeting architecture/UX alternative |
| 10 | [bigbluebutton/bigbluebutton](https://github.com/bigbluebutton/bigbluebutton) | Classroom/host moderation reference |
| 11 | [owncast/owncast](https://github.com/owncast/owncast) | Self-hosted broadcast community reference |
| 12 | [OvenMediaLabs/OvenSpace](https://github.com/OvenMediaLabs/OvenSpace) | Broadcast presenter/audience reference |
| 13 | [OvenMediaLabs/OvenMediaEngine](https://github.com/OvenMediaLabs/OvenMediaEngine) | Alternate low-latency origin; AGPL diligence |
| 14 | [ossrs/srs](https://github.com/ossrs/srs) | Optional streaming origin; not a global CDN |
| 15 | [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) | Whiteboard after package audit |
| 16 | [yjs/yjs](https://github.com/yjs/yjs) | Collaborative CRDT shared state |
| 17 | [keycloak/keycloak](https://github.com/keycloak/keycloak) | Optional enterprise OIDC/SSO |
| 18 | [centrifugal/centrifugo](https://github.com/centrifugal/centrifugo) | Chat/Q&A/poll fanout if justified |
| 19 | [fullcalendar/fullcalendar](https://github.com/fullcalendar/fullcalendar) | Calendar UI; premium terms separated |
| 20 | [valkey-io/valkey](https://github.com/valkey-io/valkey) | Ephemeral state, cache, distributed coordination |
| 21 | [openai/whisper](https://github.com/openai/whisper) | Future transcription, consent and compute plan |
| 22 | [novuhq/novu](https://github.com/novuhq/novu) | Future notification workflows; edition licenses |
| 23 | [umami-software/umami](https://github.com/umami-software/umami) | Later privacy-aware analytics |
| 24 | [killbill/killbill](https://github.com/killbill/killbill) | Future billing; likely too heavy for MVP |
| 25 | [locustio/locust](https://github.com/locustio/locust) | HTTP/WS load testing (not actual video proof) |
| 26 | [coturn/coturn](https://github.com/coturn/coturn) | TURN fallback if needed; license check |
| 27 | [tldraw/tldraw](https://github.com/tldraw/tldraw) | Drawing SDK reference; commercial license check |
| 28 | [calcom/cal.diy](https://github.com/calcom/cal.diy) | Scheduling reference (older calcom/cal.com URL moved) |
| 29 | [zitadel/zitadel](https://github.com/zitadel/zitadel) | Identity alternative; AGPL diligence |
| 30 | [grafana/k6](https://github.com/grafana/k6) | Load testing alternative; AGPL diligence |

**Other discussed providers, not extra source-repository entries:** [LiveKit Cloud](https://livekit.io/), [AWS IVS](https://aws.amazon.com/ivs/), [Cloudflare Stream](https://developers.cloudflare.com/stream/), and comparison with [Mux](https://www.mux.com/). Provider terms/prices/quotas must be reverified before paying or deploying.

## 5. Architecture and charts

### A. Production concept: control plane versus media plane

~~~mermaid
flowchart TD
  Browser["MegaMeet web / future mobile"]
  API["MegaMeet Next.js BFF / future control API"]
  OIDC["Session identity / OIDC provider"]
  Policy["Meeting authorization / roles / admission"]
  DB[("PostgreSQL canonical product data")]
  LK["LiveKit SFU / signaling / media"]
  Egress["LiveKit Egress (later)"]
  CDN["Approved streaming origin + CDN (later)"]
  Audience["Audience playback (later)"]
  Interaction["Chat / Q&A / polls (later)"]
  Browser -->|"Authenticated control requests"| API
  API --> OIDC
  API --> Policy
  Policy --> DB
  Policy -->|"Server-issued scoped media JWT"| Browser
  Browser <-->|"WebRTC tracks"| LK
  API -->|"Room/participant management SDK"| LK
  LK --> Egress
  Egress --> CDN
  CDN --> Audience
  Browser --> Interaction
  Audience --> Interaction
  Interaction --> DB
~~~

**Security boundary:** the browser never sees provider secrets. App server checks tenant + meeting + invitation/admission + ban + lobby + capacity + server-derived role before issuing a short-lived media credential. Provider room state does not replace MegaMeet's canonical authorization model.

### B. Secure participant join sequence

~~~mermaid
sequenceDiagram
  participant U as Browser
  participant A as MegaMeet app/API
  participant D as Product DB / policy
  participant L as LiveKit
  U->>A: Request join (session or guest invite)
  A->>D: Verify session / tenant / meeting / ticket / lobby
  alt Access denied or not admitted
    D-->>A: Denied / pending
    A-->>U: 401 / 403 / waiting state
  else Authorized
    D-->>A: Internal participant ID + server-derived role
    A->>A: Mint short-lived room-specific grants
    A-->>U: No-store URL + scoped JWT
    U->>L: Connect using server-issued token
    L-->>U: Media and participant tracks
  end
~~~

**Do not accept browser-provided host roles, raw room identities, arbitrary privileges or recording starts.** Do not put tokens in query strings or logs. Build rejoin/revocation semantics and audit events.

### C. Milestone dependencies

~~~mermaid
flowchart LR
 G00["G00: Owner/license"] --> G01["G01: Approved architecture"]
 G01 --> G02["G02: App + checks"]
 G02 --> G03["G03: Auth + meeting APIs"]
 G03 --> G04["G04: Real WebRTC meetings"]
 G04 --> G05["G05: Collaboration"]
 G04 --> G06["G06: Recordings / captions"]
 G04 --> G07["G07: Event MVP"]
 G07 --> G08["G08: Validated audience scale"]
 G04 --> G12["G12: Operational readiness"]
 G05 --> G13["G13: Staged release"]
 G12 --> G13
~~~

### D. Near-term repository structure — PROPOSED, not implemented

~~~text
google-meet/
  apps/
    web/
      app/                       Next.js screens and trusted server routes
      components/meeting/        Real LiveKit-powered components
      lib/                       Session, policy and provider adapters
      tests/                     Real assertions and browser tests
      package.json
  packages/
    contracts/                   Only after a real API contract exists
    config/                      Only when genuinely shared
  docs/                          This research, backlog and ADRs
  .github/workflows/             Minimal CI when implemented
  package.json
  pnpm-workspace.yaml
  pnpm-lock.yaml
~~~

Do not create dozens of empty service directories or a competing media engine merely to match a large-system diagram.

## 6. Domain and API boundaries to implement after approval

**Canonical entities:** User, Organization, Membership, Meeting, MeetingPolicy, Invitation/GuestTicket, AdmissionRequest, ParticipantSession, RoleAssignment, Recording, AuditEvent. Add LargeEvent, StageRequest and BroadcastSession only when building G07.

**Roles:** host, moderator, speaker, attendee, viewer. These are **server-derived capabilities**, not input fields accepted as authority.

**Candidate versioned endpoints (design proposal, not implemented):**
- POST /api/meetings — create meeting under identity/tenant policy.
- GET /api/meetings/{meetingId} — authorized meeting details.
- POST /api/meetings/{meetingId}/join-requests — initiate admission.
- POST /api/meetings/{meetingId}/admissions/{requestId} — host/moderator approval.
- POST /api/meetings/{meetingId}/media-grants — short-lived least-privilege LiveKit grant.
- POST /api/meetings/{meetingId}/role-assignments — audited server-validated role change.
- POST /api/meetings/{meetingId}/remove-participant — revoke/expel.
- POST /api/meetings/{meetingId}/recordings — role+consent-gated start.
- DELETE /api/meetings/{meetingId}/recordings/{recordingId} — role+policy-gated stop/deletion.

**Security tests:** expired/revoked invite; wrong tenant; wrong meeting; guessed meeting ID; caller-supplied host role; unauthenticated recording start/stop; banned user; closed/locked room; forged participant identity; CSRF on session mutations; recording without consent; abuse-rate limits; token caching and logging; webhook signature failure.

## 7. 100K audience ambition — separate broadcast path

**Target:** eventually 100,000+ **viewers** in one logical event with a deliberately bounded group of WebRTC presenters. Do NOT model 100,000 interactive publishers, a 100K-member LiveKit SFU room or a proven 100K capacity today.

~~~mermaid
flowchart LR
  Stage["Approved LiveKit speakers"] --> Export["LiveKit Egress"]
  Export --> Origin["Broadcast provider / origin"]
  Origin --> CDN["CDN / distributed edge"]
  CDN --> Viewers["Signed audience playback"]
  Viewers --> Realtime["Moderated interaction service"]
  Realtime --> Mods["Host Q&A / polls / stage promotion"]
  Mods --> Stage
~~~

**Bandwidth illustration:** 100K viewers at 1 Mbps average = 100 Gbps aggregate delivery; a 60-minute event is ~45 TB decimal payload before overhead. At 2 Mbps, ~200 Gbps and ~90 TB/h. These are rough capacity **planning arithmetic**, NOT proof, vendor quotas or cost quotes. See [SCALABILITY_100K.md](SCALABILITY_100K.md).

**Dated provider price examples from the Nov 15 draft audit, not current quotes:** Cloudflare Stream list-price example 6 million delivered minutes at $1/1000 minutes ≈ $6,000; Mux and AWS IVS estimates in the audit differ by tier, region and free allowances. Recheck official [Cloudflare pricing](https://developers.cloudflare.com/stream/pricing/), [Mux pricing](https://www.mux.com/pricing), [AWS IVS pricing](https://aws.amazon.com/ivs/pricing/) before budgets. Availability/100K quotas are not established.

**Verification ladder:** 2–25 real interactive participants; 100–1K, then 10K, 50K and 100K real **audience playback** clients, with browser/network/region, provider quota, buffering, latency, QoS and invoice evidence. Synthetic HTTP/WS load cannot prove video playback capacity.

## 8. Authoritative development backlog — 178 tasks / 14 gated phases

[Complete backlog](TASK_BACKLOG.md) and [CSV](TASK_BACKLOG.csv) are the **source of truth** for every specific task ID and acceptance condition. Never quietly replace or renumber them. The archived full text is in [snapshot part 3](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_03.md); CSV is in [part 5](CONTEXT_ARCHIVE/GITHUB_SOURCE_SNAPSHOT_PART_05.md).

| Gate | Focus | Count |
|---|---|---:|
| G00 | Product, ownership, governance | 10 |
| G01 | Architecture, reuse and contracts | 12 |
| G02 | Monorepo, CI and developer experience | 12 |
| G03 | Accounts, organizations, scheduling, core APIs | 12 |
| G04 | Reliable real-time video | 16 |
| G05 | Collaboration, moderation, accessibility | 13 |
| G06 | Recording, playback, captions and optional AI | 12 |
| G07 | Webinars / 100K-event product architecture | 16 |
| G08 | 100K testing/security/resilience | 12 |
| G09 | Enterprise security/SSO/integrations | 12 |
| G10 | Mobile and desktop strategy | 10 |
| G11 | Monetization, analytics and integrations | 13 |
| G12 | Production security, quality and SRE | 18 |
| G13 | Beta, commercial launch and improvements | 10 |
| **TOTAL** | **46 Chat + 115 Sol + 17 Astra work orders** | **178** |

### Credit-conscious agent responsibilities (already established in the repository)
- **Chat GPT-6:** specs, research tables, documentation, test cases and small isolated code drafts.
- **Codex GPT-6.1 Sol:** default for narrow implementation, dependency integration, tests/CI and reproducible verification; one task/PR at a time.
- **Astra in Codex/Work:** targeted review of hard security, role escalation, distributed media/CDN, races, failure/incident cases, not a blanket rewrite.
- **Owner/human:** license, contributors, paid vendor budgets, privacy/retention policy, architecture/security release gates and launch claims.
- No invented credit totals or unsupported results. Follow [CODEX_CREDIT_POLICY.md](CODEX_CREDIT_POLICY.md).

### Specific dependency-ordered tasks

| Order | Task ID | Prerequisite / work / acceptance |
|---:|---|---|
| 1 | MM-00-07 | Written owner decision on original-code license and contribution policy; [issue #1](https://github.com/arunabanarjee32-bit/google-meet/issues/1) |
| 2 | MM-00-08 | Legal/commercial review of license and upstream reuse |
| 3 | MM-01-01/02/03 | Review repository inventory, exact version/license BOM and reuse/build/defer; evidence pack in draft PR #21 |
| 4 | MM-01-04/05/08/12 | Approve media vs broadcast boundaries, threat model, and implementation architecture |
| 5 | MM-02-01 | First real Next.js/TypeScript web app, working local run and lockfile |
| 6 | MM-02-02 to 06 | pnpm pinning, environment schema, lint/typecheck/unit tests and least-privilege GitHub Actions |
| 7 | MM-03-01 / MM-03-06 / MM-03-07 | Identity, meeting CRUD, secure invitation/admission tickets |
| 8 | MM-04-01 / MM-04-02 | Actual LiveKit SDK and server-authorized short-lived grants; two browsers see/speak |
| 9 | MM-04-03 through MM-04-16 | Device selection, screen sharing, moderation, network recovery, browser compatibility, negative permission tests |
| 10 | G05 / G06 | Chat, Q&A, whiteboard, recording, consent and captions after secure meeting flow |
| 11 | G07 then G08 | Dedicated broadcast MVP, progressive **real playback** tests, approved quotas/budget |
| 12 | G09–G13 as gated | Enterprise/mobile/billing, SRE/production, pilots, launch |

**Roadmap improvement proposal:** enable the smallest identity/meeting authorization necessary for a secure two-browser MVP rather than completing every enterprise/scheduling feature first. Review MM-04-01/02 together to avoid exposing an unauthenticated token endpoint; keep their official backlog IDs.

## 9. First real coding task (blocked today)

**Task:** MM-02-01 — Initialize the minimal Next.js/TypeScript monorepo. **Do not mark complete because files were described in a plan.**

**Prerequisites:** owner chooses original-code/contribution license (MM-00-07/issue #1); G00/G01 gate approvals; approved dependency versions and owner-approved architecture. There is **no approval in these docs**.

**Intended initial files:** apps/web/app/page.tsx; apps/web/app/layout.tsx; apps/web/package.json; apps/web/tsconfig.json; root package.json; pnpm-workspace.yaml; pnpm-lock.yaml; minimal setup changes in README. Follow-on tasks add .env.example/environment schema, tests and CI. Do not import LiveKit Meet wholesale or include Krisp without approval.

**Acceptance:** fresh clone can install pinned dependencies, start the web app, render an original MegaMeet-branded page, and pass intended checks after the scripts exist:

~~~bash
pnpm install --frozen-lockfile
pnpm lint
pnpm typecheck
pnpm test
pnpm build
~~~

**Verification status as of snapshot:** NOT EXECUTED; there is no main-branch app/package/test harness. For later MM-04 tasks require true two-browser WebRTC audio/video plus authorization rejection tests; UI-only participant cards are not sufficient.

## 10. Licensing, safety and operations approval gates

- **Issue #1 remains unresolved** at archive time: choose proprietary/open-source/source-available/dual terms for original code, external contributor rights (no outside contributions/DCO/CLA), ownership, trademark and review.
- [PR #22 worksheet](https://github.com/arunabanarjee32-bit/google-meet/pull/22) compares choices, but neither it nor this document selects one.
- Apache-2.0 source reuse still requires exact notice/license/dependency audit; public GitHub is not blanket permission. No exclusive upstream ownership.
- Never commit secrets, recording artifacts, personal data, credentials, sensitive meeting URLs or vendor tokens to this public repo.
- No paid LiveKit/IVS/Stream deployments, AI inference runs or high-concurrency load tests without provider, region, budget, shutdown and owner authorization.
- Sensitive actions: server-enforced RBAC/tenant checks, tokens short-lived, no role strings trusted from clients, signed webhook verification, rate limiting, consent visible for recording/AI, deletion/retention, audit logging.
- Accessibility and stable release verification are requirements, not postlaunch polish.
- Maintainer review remains required before merging draft PRs or moving stage gates.

## 11. Main living documents and direct links

| Area | Canonical reference |
|---|---|
| Overview and live status | [README.md](../README.md) |
| AI/coding rules | [AGENTS.md](../AGENTS.md) |
| Contributor process | [CONTRIBUTING.md](../CONTRIBUTING.md) |
| Project vision | [PROJECT_VISION.md](PROJECT_VISION.md) |
| Product requirements | [PRODUCT_REQUIREMENTS.md](PRODUCT_REQUIREMENTS.md) |
| Architecture | [ARCHITECTURE.md](ARCHITECTURE.md) |
| Technical reuse/stack | [TECH_STACK.md](TECH_STACK.md) |
| Roadmap | [ROADMAP.md](ROADMAP.md) |
| Master delivery gates | [DELIVERY_MASTER_PLAN.md](DELIVERY_MASTER_PLAN.md) |
| Complete 178-task backlog | [TASK_BACKLOG.md](TASK_BACKLOG.md) and [TASK_BACKLOG.csv](TASK_BACKLOG.csv) |
| Codex credit model | [CODEX_CREDIT_POLICY.md](CODEX_CREDIT_POLICY.md) |
| Scoped Codex work orders | [CODEX_TASKS.md](CODEX_TASKS.md) |
| First sprint | [FIRST_SPRINT.md](FIRST_SPRINT.md) |
| Licensing/legal strategy | [LICENSING.md](LICENSING.md) |
| Security/privacy | [SECURITY_PRIVACY.md](SECURITY_PRIVACY.md), [SECURITY.md](../SECURITY.md) |
| 100K streaming scale | [SCALABILITY_100K.md](SCALABILITY_100K.md) |
| Cost assumptions | [COST_MODEL.md](COST_MODEL.md) |
| Developer guidelines | [DEVELOPMENT.md](DEVELOPMENT.md) |
| Definition of done | [DEFINITION_OF_DONE.md](DEFINITION_OF_DONE.md) |
| Github issue index | [ISSUE_INDEX.md](ISSUE_INDEX.md) |
| Baseline ADRs | [DECISIONS/0001-modular-monorepo.md](DECISIONS/0001-modular-monorepo.md), [DECISIONS/0002-interactive-and-broadcast.md](DECISIONS/0002-interactive-and-broadcast.md) |
| 30 reference GitHub repositories | [PUBLIC_REPOSITORIES_TO_STUDY.txt](../PUBLIC_REPOSITORIES_TO_STUDY.txt) |
| Draft audited architecture and 30-repo screening | [PR #21](https://github.com/arunabanarjee32-bit/google-meet/pull/21), [FOUNDATION_AUDIT](https://github.com/arunabanarjee32-bit/google-meet/blob/audit/livekit-foundations-2026-11-15/docs/FOUNDATION_AUDIT_2026-11-15.md), [ADR-0003 proposed](https://github.com/arunabanarjee32-bit/google-meet/blob/audit/livekit-foundations-2026-11-15/docs/DECISIONS/0003-livekit-foundations.md) |
| Draft licensing decision | [PR #22](https://github.com/arunabanarjee32-bit/google-meet/pull/22), [worksheet](https://github.com/arunabanarjee32-bit/google-meet/blob/docs/mm-00-07-license-decision-worksheet-2026-11-16/docs/LICENSING_DECISION_WORKSHEET.md) |
| Complete versioned text snapshot | [Archive parts 1–5](CONTEXT_ARCHIVE/README.md) |
| Accessible prior user-chat excerpts | [KNOWN_CHAT_HISTORY_EXCERPTS_2026-11-16.md](CONTEXT_ARCHIVE/KNOWN_CHAT_HISTORY_EXCERPTS_2026-11-16.md) |
| Exact uploaded instruction source | [ORIGINAL_MASTER_ENGINEERING_PROMPT_2026-11-16.txt](CONTEXT_ARCHIVE/ORIGINAL_MASTER_ENGINEERING_PROMPT_2026-11-16.txt) |

## 12. Evidence and verification ledger (do not overclaim)

**Verified in GitHub for this archive:** root/docs/.github tree and main-branch documentation-only inventory; license issue #1; open PRs #21/#22; 30 catalog entries; 178-work-order backlog; direct LiveKit Meet source files and dependency manifest; LiveKit Server tagged source layout; license-risk observations; source files copied into archive and read back. The original uploaded prompt was read and archived without text edits.

**Research conclusions, not approved choices:** exactly two main foundations; use Next.js/TypeScript + LiveKit; minimal BFF and future database; large-event egress/CDN mode; optional supporting libraries and vendor choices.

**Not executed / not present:** npm/pnpm installs, local app build/lint/types/tests, browser WebRTC verification, app deployment, 100K playback measurements, vendor quota approvals, security certification, cost invoices, merged PR approval.

**Further study needed before dependency adoption:** current package versions, complete transitive licenses, SECURITY advisories, API compatibility, exact media grants, TURN/network limitations, host/guest threat model, and production cost.

## 13. Copyable continuation prompt for a fresh AI / Codex session

> You are continuing the MegaMeet project. Repository: https://github.com/arunabanarjee32-bit/google-meet. **First inspect the current branch and open PRs/issues**, then read AGENTS.md and docs/MEGAMEET_COMPLETE_PROJECT_CONTEXT.md plus docs/TASK_BACKLOG.md. For missing older ChatGPT context, consult docs/CONTEXT_ARCHIVE/README.md, the 965-line uploaded master prompt archive and full source snapshots. Do not invent unavailable chat history. Keep the 178 task IDs, 14 approval gates and exactly two proposed main foundations (LiveKit Meet frontend reference, LiveKit Server SFU) unless evidence and owner approval justify a change. As of the 2026-11-16 archive, main is docs-only, PR #21 audit and PR #22 licensing worksheet are open drafts, and issue #1 license authorization is unresolved. Do not start substantive product source or merge high-risk changes before required gate approval. Choose one smallest nonblocked backlog task; report exact files, dependencies, expected tests, verification actually run and the next action. Avoid unnecessary Astra/paid infrastructure credits.

## 14. Maintenance protocol for future sessions

At the end of every meaningful session:
1. Update this master document's date and the **verified** implementation status, without overwriting historical facts.
2. Add a short dated entry to the [archive index](CONTEXT_ARCHIVE/README.md) linking PRs/commits, tests, decisions, open blockers and the next backlog task.
3. Preserve any new user-uploaded master prompts or exported chat files under CONTEXT_ARCHIVE with source provenance and without secrets. **Do not claim unavailable conversations were recovered.**
4. Keep the 178-task backlog and canonical docs authoritative; do not make unreviewed architecture changes or create duplicate task lists.
5. Use branches and PR review for proposed document/code changes; do not silently bypass required owner approval.

---

**Single highest-priority current action:** MM-00-07 — owner records and reviews original-code licensing and contributor-policy decision at [issue #1](https://github.com/arunabanarjee32-bit/google-meet/issues/1). **After G00/G01 acceptance:** MM-02-01 minimal runnable Next.js/TypeScript app and real test harness.