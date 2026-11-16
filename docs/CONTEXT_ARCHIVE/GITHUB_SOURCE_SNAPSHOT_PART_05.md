# MegaMeet source-document snapshot — Part 5 of 5

**Captured:** 2026-11-16. This part preserves the full 30-repository catalog and machine-readable task backlog from main, plus full text of **unmerged draft** PR #21 (foundation audit, ADR-0003, continuation) and PR #22 (licensing worksheet). Draft content MUST NOT be treated as merged, approved or implemented. Check current GitHub state before relying on it.

## PUBLIC_REPOSITORIES_TO_STUDY.txt — main

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/PUBLIC_REPOSITORIES_TO_STUDY.txt  
Git blob SHA: 94b7f5339bb0e02fc6332f3ddbfbb74bc8cf6b70  
Review state at snapshot: baseline documentation.

~~~~text
MEGAMEET - PUBLIC GITHUB REPOSITORIES TO STUDY
==============================================
Reference date: 2026-11-15
Project: https://github.com/arunabanarjee32-bit/google-meet
Document purpose: a complete consolidated inventory of the public GitHub projects
previously discussed for planning the MegaMeet product.

IMPORTANT BEFORE YOU USE ANY CODE
---------------------------------
* These repositories are candidates to STUDY, not code already imported into MegaMeet.
* A public GitHub repository is not automatically free to reuse commercially.
* "License" below is a snapshot of GitHub repository metadata checked on
  2026-11-15, except Yjs (source LICENSE checked separately). A license that is
  missing, complex, or not machine-recognized is listed as CHECK FIRST.
* Read the LICENSE, NOTICE, COPYING, dependency/module licenses and relevant
  edition terms for the EXACT version you deploy. Verify trademarks/assets too.
* MegaMeet's own original-code/contribution license still needs an owner decision.
* Avoid copying unrelated complete apps or combining incompatible conferencing
  engines. Prefer SDKs and well-defined service APIs.
* "100,000 participants" means one logical event with a bounded interactive
  speaker stage plus 100,000+ concurrent VIEWERS through a separately scalable
  broadcast path. This is a target, NOT a verified capacity.

RECOMMENDATION KEY
------------------
PRIMARY       = strongest proposed part of initial software architecture.
CONDITIONAL   = use when product requirements justify it; compare alternatives.
REFERENCE     = study UX, architecture, APIs or tradeoffs; do not wholesale merge.
LICENSE CHECK = don't import or commercially embed until licensing is cleared.

SECTION A - LIVEKIT / REAL-TIME MEETING FOUNDATION
--------------------------------------------------
01. LiveKit Meet [PRIMARY]
    URL: https://github.com/livekit-examples/meet
    GitHub license: Apache-2.0
    Study: Next.js video meeting frontend, browser join flow, gallery UI.
    Plan: candidate starting app; customize under an approved license plan.

02. LiveKit Livestream [REFERENCE / LICENSE CHECK]
    URL: https://github.com/livekit-examples/livestream
    GitHub license: NOT REPORTED; root LICENSE was not found in this check.
    Study: audience viewing, host/stage concept, broadcasting UX.
    Plan: study patterns; do not copy source before permission/license confirmation.

03. LiveKit Server [PRIMARY]
    URL: https://github.com/livekit/livekit
    GitHub license: Apache-2.0
    Study: SFU, rooms, real-time audio/video, transport and scaling limits.
    Plan: integrate as a media service, not a new SFU authored by Codex.

04. LiveKit Egress [PRIMARY]
    URL: https://github.com/livekit/egress
    GitHub license: Apache-2.0
    Study: recording, compositing and video export.
    Plan: recording and speaker-stage feed export; NOT a viewer CDN.

05. LiveKit Ingress [CONDITIONAL]
    URL: https://github.com/livekit/ingress
    GitHub license: Apache-2.0
    Study: RTMP/WHIP input and OBS/encoder workflows.
    Plan: add only for external presenter/producer ingestion.

06. LiveKit Components (React) [PRIMARY]
    URL: https://github.com/livekit/components-js
    GitHub license: Apache-2.0
    Study: device selectors, audio/video controls, media UI components.
    Plan: reuse instead of coding all meeting controls from scratch.

07. LiveKit React Native SDK [CONDITIONAL]
    URL: https://github.com/livekit/client-sdk-react-native
    GitHub license: Apache-2.0
    Study: Android/iOS real-time media, permissions and platform constraints.
    Plan: mobile phase, not initial web MVP.

08. LiveKit Agents [CONDITIONAL]
    URL: https://github.com/livekit/agents
    GitHub license: Apache-2.0
    Study: real-time speech/AI agent pipelines.
    Plan: add only with explicit AI privacy, consent and cost gates.

SECTION B - COMPLETE MEETING AND LIVESTREAM APPS TO STUDY
--------------------------------------------------------
09. Jitsi Meet [REFERENCE]
    URL: https://github.com/jitsi/jitsi-meet
    GitHub license: Apache-2.0
    Study: browser meeting UX, controls, conferencing features.
    Plan: architecture and product benchmark; do not merge its meeting engine
    alongside LiveKit without a separately approved redesign.

10. BigBlueButton [REFERENCE / LICENSE CHECK]
    URL: https://github.com/bigbluebutton/bigbluebutton
    GitHub license: LGPL-3.0 (repo metadata; examine full distribution terms).
    Study: classrooms, moderator workflows, presentation and collaboration.
    Plan: alternative complete system; NOT a drop-in LiveKit plugin.

11. Owncast [REFERENCE]
    URL: https://github.com/owncast/owncast
    GitHub license: MIT
    Study: self-hosted livestream UX, chat and community tools.
    Plan: learn event presentation and moderation tradeoffs.

12. OvenSpace [REFERENCE]
    URL: https://github.com/OvenMediaLabs/OvenSpace
    GitHub license: MIT (app repo); linked server has different licensing.
    Study: sub-second broadcasting demo and audience/presenter flow.
    Plan: reference only until all bundled/external components are vetted.

SECTION C - BROADCASTING / VIDEO DELIVERY OPTIONS
-------------------------------------------------
13. OvenMediaEngine [REFERENCE / LICENSE CHECK]
    URL: https://github.com/OvenMediaLabs/OvenMediaEngine
    GitHub license: AGPL-3.0
    Study: WebRTC / LL-HLS broadcasting at scale.
    Plan: evaluate architecture, obligations and operating costs. Do not
    silently embed AGPL software in a proprietary distribution.

14. SRS (Simple Realtime Server) [CONDITIONAL]
    URL: https://github.com/ossrs/srs
    GitHub license: MIT
    Study: RTMP, WebRTC, HLS, media origin and streaming protocols.
    Plan: possible self-hosted origin. An origin alone does NOT supply global
    CDN capacity or prove 100,000 real concurrent viewers.

SECTION D - COLLABORATION, IDENTITY, DATA AND SCHEDULING
-------------------------------------------------------
15. Excalidraw [CONDITIONAL]
    URL: https://github.com/excalidraw/excalidraw
    GitHub license: MIT
    Study: embeddable whiteboard/drawing collaboration.
    Plan: integrate vetted package(s), not rewrite a drawing engine.

16. Yjs [CONDITIONAL]
    URL: https://github.com/yjs/yjs
    License: MIT in repository LICENSE; GitHub API metadata says NOASSERTION.
    Study: CRDT collaborative notes, whiteboard/shared state syncing.
    Plan: verify exact package/dependencies and fit to transport design.

17. Keycloak [CONDITIONAL]
    URL: https://github.com/keycloak/keycloak
    GitHub license: Apache-2.0
    Study: OIDC, enterprise SSO, identity/tenant administration.
    Plan: candidate identity service; weigh setup/maintenance overhead.

18. Centrifugo [CONDITIONAL]
    URL: https://github.com/centrifugal/centrifugo
    GitHub license: Apache-2.0
    Study: real-time messaging, authorized channels and fanout.
    Plan: transport for chat, Q&A, polls and presence. Persistent chat,
    moderation and tenant policy still need application services.

19. FullCalendar [CONDITIONAL]
    URL: https://github.com/fullcalendar/fullcalendar
    GitHub license: MIT (core repo; premium features separately licensed).
    Study: calendar scheduling UI, date/timezone interactions.
    Plan: build meeting scheduling UI on approved components.

20. Valkey [CONDITIONAL]
    URL: https://github.com/valkey-io/valkey
    GitHub license: BSD-3-Clause
    Study: cache, short-lived state and Redis-compatible data structures.
    Plan: add when real-time/session needs justify a separate service.

SECTION E - AI, NOTIFICATIONS, PRODUCT AND BILLING
--------------------------------------------------
21. Whisper [CONDITIONAL]
    URL: https://github.com/openai/whisper
    GitHub license: MIT
    Study: speech recognition, transcript formats and model serving cost.
    Plan: optional captions/transcription with opt-in and capacity planning.

22. Novu [CONDITIONAL / LICENSE CHECK]
    URL: https://github.com/novuhq/novu
    GitHub license: NOASSERTION; edition/modules may have separate terms.
    Study: notifications workflows, email/push and delivery monitoring.
    Plan: evaluate before integrating; avoid carrying a heavy platform into MVP.

23. Umami [CONDITIONAL]
    URL: https://github.com/umami-software/umami
    GitHub license: MIT
    Study: privacy-aware product/web analytics.
    Plan: later analytics under a documented data/consent policy.

24. Kill Bill [CONDITIONAL]
    URL: https://github.com/killbill/killbill
    GitHub license: Apache-2.0
    Study: subscriptions, billing ledger and lifecycle.
    Plan: compare with managed billing; may be too complex for early launch.

SECTION F - PERFORMANCE, NETWORKING AND LICENSE-CAUTION ALTERNATIVES
-------------------------------------------------------------------
25. Locust [CONDITIONAL]
    URL: https://github.com/locustio/locust
    GitHub license: MIT
    Study: reproducible API/HTTP/WebSocket load testing.
    Plan: good for control-plane stress; NOT evidence of 100K real video
    playback without actual media client measurement.

26. Coturn [CONDITIONAL / LICENSE CHECK]
    URL: https://github.com/coturn/coturn
    GitHub license: NOASSERTION (verify exact copyright/license files).
    Study: STUN/TURN NAT traversal and relay performance.
    Plan: evaluate if using a self-hosted WebRTC infrastructure.

27. tldraw [REFERENCE / LICENSE CHECK]
    URL: https://github.com/tldraw/tldraw
    GitHub license: NOASSERTION; commercial SDK/production terms apply.
    Study: infinite canvas UX and whiteboard SDK.
    Plan: do not assume commercial embedding is covered by MIT.

28. Cal.com (formerly referenced as calcom/cal.com) [REFERENCE]
    Current URL: https://github.com/calcom/cal.diy
    Historical URL: https://github.com/calcom/cal.com (moved)
    GitHub license for current cal.diy repo: MIT; verify exact modules/versions.
    Study: booking/calendar architecture, availability, scheduling and invites.
    Plan: reference, not a requirement to merge a full scheduling app.

29. ZITADEL [REFERENCE / LICENSE CHECK]
    URL: https://github.com/zitadel/zitadel
    GitHub license: AGPL-3.0
    Study: cloud-native multi-tenant identity/authorization patterns.
    Plan: compare with Keycloak; check AGPL/network terms before adoption.

30. Grafana k6 [REFERENCE / LICENSE CHECK]
    URL: https://github.com/grafana/k6
    GitHub license: AGPL-3.0 (current repo metadata).
    Study: performance-test scripts and load generator architecture.
    Plan: tool evaluation; check licensing before redistribution.

SECTION G - NON-GITHUB-SOURCE PRODUCTS / SERVICES WE ALSO DISCUSSED
-------------------------------------------------------------------
These are NOT additional repository entries; compare their terms, features,
prices, quotas and regional availability before using them.

* LiveKit Cloud: https://livekit.io/
  Managed LiveKit infrastructure; differs from self-hosting limits and costs.
* AWS IVS: https://aws.amazon.com/ivs/
  Managed large-audience live video delivery option.
* Cloudflare Stream: https://developers.cloudflare.com/stream/
  Managed encoding/video delivery option; validate its current protocol,
  latency and concurrency offerings for the chosen product tier.
* PostgreSQL, Next.js, React/React Native, container orchestration, and
  message brokers were discussed as technologies, not previously selected
  public repositories to copy wholesale into MegaMeet.

RECOMMENDED STUDY / IMPLEMENTATION ORDER
----------------------------------------
1. Read MegaMeet README, docs/PROJECT_VISION.md and docs/TASK_BACKLOG.md.
2. Verify owner code license and review upstream third-party notices.
3. Inspect LiveKit Meet + Components + Server (items 01, 03, 06).
4. Inspect recording/export (item 04), and optional input (item 05).
5. Compare managed broadcast providers versus SRS (item 14) for
   100,000+ audience delivery and define real playback load tests.
6. Add identity (item 17) only after deciding product/tenant needs.
7. Add collaboration (items 15, 16, 18, 19) as complete user flows.
8. Evaluate mobile (07), AI (08/21), analytics/billing (23/24) when needed.
9. Study alternate entire apps (09-12) only for patterns/features;
   do not merge whole stacks into the core system.
10. Use performance tools (25/30) with clear claims and safe paid budgets.

WHAT A CODEX / HUMAN CONTRIBUTOR SHOULD REPORT BEFORE ADOPTING ANY REPO
-----------------------------------------------------------------------
- Candidate URL and exactly pinned package/tag/commit
- License text, NOTICE, trademark/assets and transitive licensing
- Build-versus-reuse decision and why
- Integration contract + expected failure modes
- Security, privacy, data residency and operational costs
- Versioned tests and rollback plan
- Whether this is just reference study, a service integration, or code reuse

Useful existing documentation:
README.md
docs/TECH_STACK.md
docs/ARCHITECTURE.md
docs/LICENSING.md
docs/SCALABILITY_100K.md
docs/TASK_BACKLOG.md
docs/CODEX_CREDIT_POLICY.md
AGENTS.md

END OF CATALOG - 30 UNIQUE GITHUB REPOSITORIES LISTED

~~~~

---

## docs/TASK_BACKLOG.csv — main

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/TASK_BACKLOG.csv  
Git blob SHA: d887be0513a882378f6b876c50ad6c1cd2cf8a1d  
Review state at snapshot: baseline documentation.

~~~~csv
id,phase,owner,effort,prerequisite,task,acceptance,status
"MM-00-01","G00","Chat GPT-6","S","none","Interview plan and customer personas","Interview script and 3 prioritized buyer personas","Not started"
"MM-00-02","G00","Chat GPT-6","S","none","Competitive capability matrix","Dated, sourced matrix of Zoom, Meet, Teams and webinar features","Not started"
"MM-00-03","G00","Chat GPT-6","S","none","Define launch positioning and differentiators","One-sentence value proposition and measurable hypotheses","Not started"
"MM-00-04","G00","Chat GPT-6","S","none","Define first customer segment and MVP constraints","Named segment, must-have workflows and exclusions","Not started"
"MM-00-05","G00","Chat GPT-6","S","none","Write user journeys for host, guest, moderator, viewer","Each journey has success, failure and accessibility paths","Not started"
"MM-00-06","G00","Chat GPT-6","S","none","Draft privacy and data-retention policy decisions","Decision sheet identifies unresolved legal questions","Not started"
"MM-00-07","G00","Chat GPT-6","S","none","Draft original-code license options","Tradeoffs for proprietary/open-source, upstream notices and CLA/DCO","Not started"
"MM-00-08","G00","Codex/Work GPT-6 Astra","S","MM-00-07","Review commercial licensing architecture","Identify risky source imports and commercialization blockers","Not started"
"MM-00-09","G00","Chat GPT-6","S","none","Define project naming and trademark check plan","Brand-selection checklist; no affiliation implied","Not started"
"MM-00-10","G00","Chat GPT-6","S","MM-00-04","Define price/customer research experiments","Research hypotheses and testable pricing assumptions","Not started"
"MM-01-01","G01","Chat GPT-6","S","G00","Inventory current repository and planned features","Diff between actual files and desired capabilities; no invented code","Not started"
"MM-01-02","G01","Chat GPT-6","S","MM-01-01","Upstream version, license and security spreadsheet","Exact tags, license/NOTICE, dependencies and maintenance evidence","Not started"
"MM-01-03","G01","Chat GPT-6","S","MM-01-02","Reuse/build/defer decision for each feature","Approved decision table cites mature libraries and reasons","Not started"
"MM-01-04","G01","Codex/Work GPT-6 Astra","M","MM-01-03","Interactive media versus broadcast architecture ADR","Signed-off stage, audience, egress, latency and failure model","Not started"
"MM-01-05","G01","Codex/Work GPT-6 Astra","M","MM-01-04","Control-plane and realtime state boundaries","Event/domain graph prevents cross-room permissions and hot keys","Not started"
"MM-01-06","G01","Chat GPT-6","S","MM-01-05","API and event naming/specification","Versioned OpenAPI draft and event schemas without code","Not started"
"MM-01-07","G01","Chat GPT-6","S","MM-01-05","Domain data model and tenant boundaries","ERD for users, orgs, rooms, events, tickets and assets","Not started"
"MM-01-08","G01","Codex/Work GPT-6 Astra","S","MM-01-05","Threat model and trust boundary review","Abuse cases for tokens, admin, viewers, recordings and AI","Not started"
"MM-01-09","G01","Chat GPT-6","S","MM-01-04","Managed broadcast/CDN versus SRS comparison","Latency, quality, quotas, ops and monthly cost assumptions","Not started"
"MM-01-10","G01","Chat GPT-6","S","MM-01-03","Browser and mobile support matrix","Versions, capabilities, accessibility and test devices listed","Not started"
"MM-01-11","G01","Codex/Work GPT-6 Astra","S","MM-01-08","Architecture cost/reliability red-team review","Written risks, fallbacks and decision owners","Not started"
"MM-01-12","G01","Chat GPT-6","S","MM-01-04","Approve implementation architecture and gates","Decision records reviewed by human maintainer","Not started"
"MM-02-01","G02","Codex GPT-6.1 Sol","M","G01","Initialize Next.js TypeScript monorepo","Minimal running app and lockfile; no placeholder microservices","Not started"
"MM-02-02","G02","Codex GPT-6.1 Sol","S","MM-02-01","Package manager and workspace tooling","Version pinned and clean install documented","Not started"
"MM-02-03","G02","Codex GPT-6.1 Sol","S","MM-02-01","Environment schema and redacted sample","Missing/invalid values fail fast; no secrets committed","Not started"
"MM-02-04","G02","Codex GPT-6.1 Sol","S","MM-02-01","ESLint formatting and typecheck scripts","Checks run locally and in CI with recorded output","Not started"
"MM-02-05","G02","Codex GPT-6.1 Sol","S","MM-02-01","Unit and integration test harness","Sample meaningful tests run in CI","Not started"
"MM-02-06","G02","Codex GPT-6.1 Sol","S","MM-02-04","GitHub Actions build/test workflow","PR checks run with least-privilege permissions","Not started"
"MM-02-07","G02","Codex GPT-6.1 Sol","S","MM-02-03","Docker development configuration","Minimum required services start with documented teardown","Not started"
"MM-02-08","G02","Codex GPT-6.1 Sol","S","MM-01-06","Typed API contract package","Client/server contract compiles with schema validation","Not started"
"MM-02-09","G02","Codex GPT-6.1 Sol","S","MM-02-01","Structured error and log helpers","Correlation IDs and sensitive fields redacted","Not started"
"MM-02-10","G02","Chat GPT-6","S","MM-02-07","Write exact local setup and troubleshooting","New developer guide tested against fresh clone","Not started"
"MM-02-11","G02","Codex GPT-6.1 Sol","S","MM-02-06","Dependabot/security scanning and lockfile audit","Version pinning and actionable dependency alerts","Not started"
"MM-02-12","G02","Codex GPT-6.1 Sol","S","MM-02-06","Preview deployment and branch protections proposal","Nonproduction preview with safe secrets and rollback notes","Not started"
"MM-03-01","G03","Codex GPT-6.1 Sol","M","G02","Integrate chosen identity provider/OIDC","Signup/login/logout/guest flow verified","Not started"
"MM-03-02","G03","Codex GPT-6.1 Sol","S","MM-03-01","Session lifecycle and CSRF protections","Expiry, logout, refresh and anti-CSRF tests pass","Not started"
"MM-03-03","G03","Codex GPT-6.1 Sol","S","MM-03-01","User profile and preferences persistence","Users update valid profile fields without tenant leakage","Not started"
"MM-03-04","G03","Codex GPT-6.1 Sol","M","MM-03-01","Organization/workspace entities","Create/join/invite with strict membership checks","Not started"
"MM-03-05","G03","Codex/Work GPT-6 Astra","S","MM-03-04","Review tenant RBAC and resource authorization","Adversarial permission matrix with denied escalation tests","Not started"
"MM-03-06","G03","Codex GPT-6.1 Sol","M","MM-03-04","Meeting create, edit, cancel and list APIs","Idempotent APIs, ownership checks and validation","Not started"
"MM-03-07","G03","Codex GPT-6.1 Sol","S","MM-03-06","Secure meeting links and invitation tickets","Unpredictable ID, expiry and revoked ticket denial","Not started"
"MM-03-08","G03","Codex GPT-6.1 Sol","S","MM-03-06","Meeting schedule with timezone/DST handling","Cross-timezone test cases and valid recurrence approach","Not started"
"MM-03-09","G03","Codex GPT-6.1 Sol","S","MM-03-08","Calendar UI with selected licensed library","Calendar CRUD + keyboard support","Not started"
"MM-03-10","G03","Chat GPT-6","S","MM-03-07","Invitation email text, policy and templates","Localized, accessible and unambiguous join copy","Not started"
"MM-03-11","G03","Codex GPT-6.1 Sol","M","MM-03-06","Meeting dashboard, history and search","Only authorized meetings show; pagination tested","Not started"
"MM-03-12","G03","Codex GPT-6.1 Sol","S","MM-03-06","Audit events for meeting control actions","Structured create/join/revoke/end evidence persisted","Not started"
"MM-04-01","G04","Codex GPT-6.1 Sol","M","G03","Integrate LiveKit meeting SDK/Components","Real bidirectional audio/video between two browsers","Not started"
"MM-04-02","G04","Codex GPT-6.1 Sol","S","MM-04-01","Server-generated short-lived LiveKit grants","Client cannot forge speaker/host roles","Not started"
"MM-04-03","G04","Codex GPT-6.1 Sol","S","MM-04-01","Device preview and permissions handling","Camera/mic denied, changed and unplugged cases handled","Not started"
"MM-04-04","G04","Codex GPT-6.1 Sol","M","MM-04-02","Join/leave/lobby/deny workflow","Host admission and guest join policies enforced server-side","Not started"
"MM-04-05","G04","Codex GPT-6.1 Sol","S","MM-04-01","Media mute, camera toggle and device switching","UI reflects actual track state on both peers","Not started"
"MM-04-06","G04","Codex GPT-6.1 Sol","M","MM-04-02","Share entire screen/window/tab","Presenter-only share permission and browser fallback tested","Not started"
"MM-04-07","G04","Codex GPT-6.1 Sol","S","MM-04-01","Grid, active speaker and spotlight layouts","Responsive with keyboard/screen-reader affordances","Not started"
"MM-04-08","G04","Codex GPT-6.1 Sol","S","MM-04-01","Participant roster and speaking indicators","Role/state correct under reconnect and departure","Not started"
"MM-04-09","G04","Codex GPT-6.1 Sol","S","MM-04-02","Host kick, mute request, lock and co-host grants","Unauthorized attempts fail and events are audited","Not started"
"MM-04-10","G04","Codex GPT-6.1 Sol","S","MM-04-08","Reactions and raise hand in small meetings","Events not lost across short reconnect","Not started"
"MM-04-11","G04","Codex GPT-6.1 Sol","M","MM-04-05","Reconnect and unstable network UX","Recovery, offline, retry and track reset behavior tested","Not started"
"MM-04-12","G04","Codex GPT-6.1 Sol","S","MM-04-01","Bandwidth adaptation and low-data mode","Measured under throttled network and weak CPU","Not started"
"MM-04-13","G04","Codex GPT-6.1 Sol","S","MM-04-04","Share-link guest browser interoperability test","Chromium, Firefox, Safari differences documented","Not started"
"MM-04-14","G04","Codex GPT-6.1 Sol","S","MM-04-01","SIP/TURN decision and NAT traversal smoke","Known network restrictions and TURN costs documented","Not started"
"MM-04-15","G04","Codex/Work GPT-6 Astra","S","MM-04-09","Media permission and failure review","Host privilege, revoked token, SFU failure cases assessed","Not started"
"MM-04-16","G04","Chat GPT-6","S","MM-04-12","Meeting UX acceptance script and bug matrix","Human QA can reproduce every critical scenario","Not started"
"MM-05-01","G05","Chat GPT-6","S","G04","Define chat/Q&A/polls privacy and UX rules","User stories cover history, retention, spam and moderation","Not started"
"MM-05-02","G05","Codex GPT-6.1 Sol","M","MM-05-01","Select and integrate realtime transport","Authorized channels, reconnect and fanout metrics work","Not started"
"MM-05-03","G05","Codex GPT-6.1 Sol","M","MM-05-02","Persist meeting chat with pagination","Ordered history, retention and room access tests","Not started"
"MM-05-04","G05","Codex GPT-6.1 Sol","S","MM-05-03","Chat moderation, spam limits and abuse reports","Rate limits and deletion/ban actions tested","Not started"
"MM-05-05","G05","Codex GPT-6.1 Sol","S","MM-05-03","Meeting reactions and pinned messages","Consistent updates and screen-reader announcements","Not started"
"MM-05-06","G05","Codex GPT-6.1 Sol","M","MM-05-02","Polling create/vote/close/results","One eligible vote per poll setting; role checks","Not started"
"MM-05-07","G05","Codex GPT-6.1 Sol","M","MM-05-02","Moderated Q&A submit, vote, answer and archive","Host moderation, per-event limits and persistence","Not started"
"MM-05-08","G05","Codex GPT-6.1 Sol","S","MM-05-07","Hand-raise queue and speaker requests","Deterministic queue order and moderator controls","Not started"
"MM-05-09","G05","Codex GPT-6.1 Sol","M","MM-05-01","Whiteboard integration and permissions","Board edits isolated per meeting; export works","Not started"
"MM-05-10","G05","Codex GPT-6.1 Sol","S","MM-05-09","Collaborative notes with Yjs or vetted alternative","Concurrent edits converge; permissions validated","Not started"
"MM-05-11","G05","Chat GPT-6","S","MM-05-06","Accessibility audit and text alternatives","WCAG-oriented keyboard/contrast/screen-reader checklist","Not started"
"MM-05-12","G05","Codex GPT-6.1 Sol","S","MM-05-03","File/link sharing metadata and safety policy","Access checks, upload limits and safe previews","Not started"
"MM-05-13","G05","Codex GPT-6.1 Sol","S","MM-05-04","Chat/Q&A flood and reconnect tests","Backpressure, ordering and data integrity verified","Not started"
"MM-06-01","G06","Chat GPT-6","S","G04","Recording consent and data lifecycle policy","Owner-approved retention, disclosure and permissions rules","Not started"
"MM-06-02","G06","Codex GPT-6.1 Sol","M","MM-06-01","Integrate LiveKit Egress recording jobs","Start/stop/state, errors and artifacts tracked","Not started"
"MM-06-03","G06","Codex GPT-6.1 Sol","S","MM-06-02","Recording consent and visible indicator UX","Every participant sees enabled status and policy","Not started"
"MM-06-04","G06","Codex GPT-6.1 Sol","M","MM-06-02","Secure recording storage and signed playback","Tenant isolation, expiry and access tests","Not started"
"MM-06-05","G06","Codex GPT-6.1 Sol","S","MM-06-04","Recording search, share, delete and retention job","Allowed actions and deletion verified end-to-end","Not started"
"MM-06-06","G06","Codex GPT-6.1 Sol","S","MM-06-03","Caption UI and transcript format ingestion","Timing, speaker labeling and accessibility tested","Not started"
"MM-06-07","G06","Chat GPT-6","S","MM-06-06","Evaluate transcription engines and costs","Benchmarks of languages, quality, privacy and expense","Not started"
"MM-06-08","G06","Codex GPT-6.1 Sol","M","MM-06-07","Consent-gated transcription pipeline","Secrets, retries, opt-in and deletion handled","Not started"
"MM-06-09","G06","Codex GPT-6.1 Sol","M","MM-06-08","Summary, action item and transcript search","Grounded output with source timestamps and edit option","Not started"
"MM-06-10","G06","Chat GPT-6","S","MM-06-08","AI translation quality and policy benchmark","Languages/latency/cost and consent requirements documented","Not started"
"MM-06-11","G06","Codex/Work GPT-6 Astra","S","MM-06-08","Review AI data exposure and recording threat model","Negative access tests, misuse and third-party data flow risks","Not started"
"MM-06-12","G06","Codex GPT-6.1 Sol","S","MM-06-08","Recording and AI quota/cost kill switches","Usage limits and shutdown tested in staging","Not started"
"MM-07-01","G07","Chat GPT-6","S","G04","Define webinar tiers, latency and attendee UX","Document viewer/speaker differences and transition states","Not started"
"MM-07-02","G07","Codex GPT-6.1 Sol","M","MM-07-01","Event domain entities and participant roles","Event != SFU room; tickets and role policy tested","Not started"
"MM-07-03","G07","Codex GPT-6.1 Sol","S","MM-07-02","Large-event creation and registration API","Capacity, invite/approval and signed admission tested","Not started"
"MM-07-04","G07","Codex/Work GPT-6 Astra","M","MM-07-02","Review speaker promotion transaction design","Race/replay/echo/rollback rules and security tests","Not started"
"MM-07-05","G07","Codex GPT-6.1 Sol","M","MM-07-02","Bounded LiveKit speaker-stage workflow","Only authorized presenters can publish","Not started"
"MM-07-06","G07","Codex GPT-6.1 Sol","M","MM-07-05","Egress program feed to chosen broadcast provider","Real stage playback on at least two viewer devices","Not started"
"MM-07-07","G07","Codex GPT-6.1 Sol","S","MM-07-06","Broadcast provider adapter and health states","Start/stop/retry, status and normalized errors verified","Not started"
"MM-07-08","G07","Codex GPT-6.1 Sol","S","MM-07-06","Audience player quality and latency UI","ABR fallback, error states and live-delay notice tested","Not started"
"MM-07-09","G07","Codex GPT-6.1 Sol","M","MM-07-04","Raise-hand/viewer-to-speaker authorization","Promotion/demotion secure and no echo on transitions","Not started"
"MM-07-10","G07","Codex GPT-6.1 Sol","S","MM-07-09","Speaker moderation dashboard","Host can invite, approve, revoke and remove speakers","Not started"
"MM-07-11","G07","Codex GPT-6.1 Sol","S","MM-07-03","Audience Q&A/polls/chat event integration","Permissions and moderated fanout tested","Not started"
"MM-07-12","G07","Codex GPT-6.1 Sol","S","MM-07-03","Audience identity and signed playback tokens","No cross-event stream/session leakage","Not started"
"MM-07-13","G07","Codex GPT-6.1 Sol","S","MM-07-08","Webinar analytics and audience counters","Distinct actual watchers from registrations and sockets","Not started"
"MM-07-14","G07","Codex GPT-6.1 Sol","S","MM-07-07","Streaming failure/fallback states","Stage/egress/CDN outage alerts and recovery UI","Not started"
"MM-07-15","G07","Chat GPT-6","S","MM-07-10","Runbook for event organizers and moderators","Step-by-step preflight, backup and emergency actions","Not started"
"MM-07-16","G07","Codex/Work GPT-6 Astra","S","MM-07-14","Validate stage/broadcast/control-plane architecture","Failure-mode review before load testing","Not started"
"MM-08-01","G08","Chat GPT-6","S","G07","Specify real viewer performance methodology","Distinguishes synthetic sockets from actual media playback","Not started"
"MM-08-02","G08","Codex GPT-6.1 Sol","M","MM-08-01","Build scalable playback load-test harness","Reproducible simulator reports actual decoding/viewer state","Not started"
"MM-08-03","G08","Codex GPT-6.1 Sol","S","MM-08-02","API/auth join storm load tests","Rate, p95/p99, error counts and rate-limiting report","Not started"
"MM-08-04","G08","Codex GPT-6.1 Sol","S","MM-08-02","Realtime message flood/sharding benchmarks","Moderation queue, hot-key, backpressure evidence","Not started"
"MM-08-05","G08","Codex GPT-6.1 Sol","S","MM-08-02","Broadcast adaptive bitrate and CDN instrumentation","Rebuffers, bitrate, startup time and region tracked","Not started"
"MM-08-06","G08","Codex GPT-6.1 Sol","M","MM-08-02","10K viewer staging validation","Real audience playback, cost and provider quotas documented","Not started"
"MM-08-07","G08","Codex/Work GPT-6 Astra","M","MM-08-06","Review 50K/100K multi-region design before paid runs","Quantified bottlenecks, failovers, quota and budget approval","Not started"
"MM-08-08","G08","Codex GPT-6.1 Sol","M","MM-08-06","Failure drills and reconnect-storm harness","SFU/egress/origin/CDN failure traces and recovery tests","Not started"
"MM-08-09","G08","Codex GPT-6.1 Sol","M","MM-08-07","50K real-viewer controlled test","Reproducible quality, logs and approved spend","Not started"
"MM-08-10","G08","Codex GPT-6.1 Sol","M","MM-08-09","100K real-viewer controlled test","Verified concurrent stream playback with independent evidence","Not started"
"MM-08-11","G08","Chat GPT-6","S","MM-08-10","Publish tested capacity and limitations report","Clearly distinguishes maximum observed and safe offered capacity","Not started"
"MM-08-12","G08","Codex/Work GPT-6 Astra","S","MM-08-10","Production scaling readiness assessment","Independent go/no-go on capacity, failover and economics","Not started"
"MM-09-01","G09","Chat GPT-6","S","G03","Define organization plans and enterprise workflows","SCIM/SSO/admin/retention prioritized by pilot customers","Not started"
"MM-09-02","G09","Codex GPT-6.1 Sol","M","MM-09-01","Organization admin console and member lifecycle","Role policy and audit tests for org create/invite/remove","Not started"
"MM-09-03","G09","Codex GPT-6.1 Sol","M","MM-09-02","SSO OIDC/SAML integration and domain verification","Secure flow tested against test identity provider","Not started"
"MM-09-04","G09","Codex GPT-6.1 Sol","M","MM-09-03","SCIM provisioning/deprovisioning adapter","Idempotency, rate limiting and revoked access verified","Not started"
"MM-09-05","G09","Codex GPT-6.1 Sol","S","MM-09-02","Admin policies and default meeting restrictions","Meeting rules inherited with authorized overrides only","Not started"
"MM-09-06","G09","Codex GPT-6.1 Sol","S","MM-09-02","Tenant-aware audit log and export","Immutable or tamper-evident records, scoped export tested","Not started"
"MM-09-07","G09","Codex GPT-6.1 Sol","S","MM-09-06","Data retention policy and export/delete workflow","Policy applied to chats, recordings and transcripts","Not started"
"MM-09-08","G09","Codex/Work GPT-6 Astra","S","MM-09-07","Enterprise tenancy and compliance architecture review","Trust boundaries, regional and incident risks documented","Not started"
"MM-09-09","G09","Codex GPT-6.1 Sol","M","MM-09-01","Calendar provider OAuth and invitation integration","Minimum scopes, token safety and update sync tested","Not started"
"MM-09-10","G09","Codex GPT-6.1 Sol","S","MM-09-05","Public API keys, quotas and webhook signatures","Revocation, idempotency and verification tests","Not started"
"MM-09-11","G09","Codex GPT-6.1 Sol","S","MM-09-10","Webhook retries and delivery audit","Backoff, deduplication and dead-letter behavior visible","Not started"
"MM-09-12","G09","Chat GPT-6","S","MM-09-08","Enterprise onboarding, security questionnaire package","Evidence-based security answers; no unearned certification","Not started"
"MM-10-01","G10","Chat GPT-6","S","G04","Mobile/desktop research and feature parity scope","Prioritized workflows and supported-device matrix","Not started"
"MM-10-02","G10","Codex GPT-6.1 Sol","M","MM-10-01","React Native shared auth and contracts setup","App builds with known versions and no embedded secrets","Not started"
"MM-10-03","G10","Codex GPT-6.1 Sol","M","MM-10-02","LiveKit React Native AV meeting integration","Android/iOS real join, publish, subscribe verified","Not started"
"MM-10-04","G10","Codex GPT-6.1 Sol","S","MM-10-03","Mobile camera/microphone/permission UX","Denials, route changes, Bluetooth and lifecycle tested","Not started"
"MM-10-05","G10","Codex GPT-6.1 Sol","M","MM-10-03","Mobile screen share and background restrictions","OS-specific capabilities documented and tested","Not started"
"MM-10-06","G10","Codex GPT-6.1 Sol","S","MM-10-03","Mobile chat, hand raise and meeting controls","Contract compatible with web and reconnect tested","Not started"
"MM-10-07","G10","Codex GPT-6.1 Sol","S","MM-10-02","Deep links and push notifications","Join invitations secure and expired links rejected","Not started"
"MM-10-08","G10","Codex GPT-6.1 Sol","S","MM-10-03","Mobile release signing, CI and crash reporting","Test build pipeline with private signing credentials","Not started"
"MM-10-09","G10","Chat GPT-6","S","MM-10-01","Desktop packaging decision review","Web/PWA versus native utility value and cost documented","Not started"
"MM-10-10","G10","Codex GPT-6.1 Sol","M","MM-10-09","Optional desktop app/PWA launch flow","Only if approved; desktop join/device/screen share pass","Not started"
"MM-11-01","G11","Chat GPT-6","S","G07","Design pricing hypotheses and fair-use policies","Tier grid lists limits, viewer-minutes and overages","Not started"
"MM-11-02","G11","Chat GPT-6","S","MM-11-01","Billing provider versus open-source engine decision","Compare payment compliance, complexity and recurring fees","Not started"
"MM-11-03","G11","Codex GPT-6.1 Sol","S","MM-11-02","Usage metering event schema","Counts room time, speaker usage, viewer-minutes and AI spend","Not started"
"MM-11-04","G11","Codex GPT-6.1 Sol","M","MM-11-03","Plan entitlement and quota enforcement","Limits enforced on backend with denial explanations","Not started"
"MM-11-05","G11","Codex GPT-6.1 Sol","M","MM-11-04","Billing checkout and webhook state reconciliation","Verified signatures, idempotent events and retries","Not started"
"MM-11-06","G11","Codex GPT-6.1 Sol","S","MM-11-05","Customer invoices, tax data flow and payment portal","Customer sees correct invoices without card handling in app","Not started"
"MM-11-07","G11","Codex GPT-6.1 Sol","S","MM-11-05","Cancel, downgrade, grace period and refunds states","Documented state transitions and automated tests","Not started"
"MM-11-08","G11","Codex GPT-6.1 Sol","S","MM-11-03","Product analytics and consent configuration","Privacy policy and opt-out behavior tested","Not started"
"MM-11-09","G11","Codex GPT-6.1 Sol","S","MM-11-05","Email notifications and transaction templates","Retries, unsubscribe where required, no token leaks","Not started"
"MM-11-10","G11","Codex GPT-6.1 Sol","S","MM-11-04","Usage dashboard, budget alerts and abuse limits","Metrics match metering ledger and alert triggers","Not started"
"MM-11-11","G11","Chat GPT-6","S","MM-11-01","Support/help center and status-page content","User troubleshooting, escalation and incident template","Not started"
"MM-11-12","G11","Codex GPT-6.1 Sol","S","MM-11-03","Integration API docs and sample client","Versioned examples work on a nonprod sandbox","Not started"
"MM-11-13","G11","Codex/Work GPT-6 Astra","S","MM-11-07","Review billing and tenancy fraud scenarios","Payment/replay/overage and privilege risks dispositioned","Not started"
"MM-12-01","G12","Chat GPT-6","S","G07","Define SLOs, error budgets and launch service tiers","Measurable AV join and event quality targets","Not started"
"MM-12-02","G12","Codex GPT-6.1 Sol","M","MM-12-01","Production Infrastructure-as-Code plan","Reproducible environments, no hardcoded secrets","Not started"
"MM-12-03","G12","Codex GPT-6.1 Sol","M","MM-12-02","Staging and production CI/CD with approvals","Rollback, protected environments and image signing tested","Not started"
"MM-12-04","G12","Codex GPT-6.1 Sol","S","MM-12-02","Central metrics, tracing and log redaction","Dashboards and traces cover core end-to-end flow","Not started"
"MM-12-05","G12","Codex GPT-6.1 Sol","S","MM-12-04","Alerting for media, API, broadcasts, storage and spend","Alerts tested; defined responders and severities","Not started"
"MM-12-06","G12","Codex GPT-6.1 Sol","S","MM-12-02","Backup and point-in-time restore tests","Documented restoration time and verified consistency","Not started"
"MM-12-07","G12","Codex GPT-6.1 Sol","M","MM-12-03","Tenant isolation and security regression suite","Automated negative authorization tests across services","Not started"
"MM-12-08","G12","Codex GPT-6.1 Sol","S","MM-12-03","Dependency, container and secret scanning","CI blocks critical findings and produces SBOM","Not started"
"MM-12-09","G12","Codex/Work GPT-6 Astra","M","MM-12-07","Independent threat-model review of implemented code","Prioritized findings with verified remediation evidence","Not started"
"MM-12-10","G12","Codex GPT-6.1 Sol","S","MM-12-07","Rate limit, DDoS, CAPTCHA and abuse protections","Join storm and spam simulations meet targets","Not started"
"MM-12-11","G12","Codex GPT-6.1 Sol","M","MM-12-03","Browser/mobile end-to-end test automation","Core joining, device, screen share, moderator flows run","Not started"
"MM-12-12","G12","Chat GPT-6","S","MM-12-11","Accessibility manual audit and acceptance matrix","Screen reader and keyboard issues documented and triaged","Not started"
"MM-12-13","G12","Codex GPT-6.1 Sol","S","MM-12-11","Performance budget and web bundle optimization","Measured startup, CPU/network and device memory","Not started"
"MM-12-14","G12","Codex GPT-6.1 Sol","S","MM-12-07","Data privacy/consent/retention integration tests","Delete/export/recording permissions tested","Not started"
"MM-12-15","G12","Chat GPT-6","S","MM-12-05","Incident response, on-call and runbook drafts","Severity matrix and rollback exercise schedule","Not started"
"MM-12-16","G12","Codex GPT-6.1 Sol","M","MM-12-06","Disaster-recovery and failover game day","Recovery/availability evidence and known limitations","Not started"
"MM-12-17","G12","Codex/Work GPT-6 Astra","S","MM-12-09","Release candidate architecture readiness review","Open risks and go/no-go signed off by responsible human","Not started"
"MM-12-18","G12","Chat GPT-6","S","MM-12-14","Legal and compliance evidence checklist","No unsupported SOC2/HIPAA/GDPR claims; counsel review plan","Not started"
"MM-13-01","G13","Chat GPT-6","S","G12","Write beta recruitment, support and feedback plan","Defined pilot cohort and measurable success criteria","Not started"
"MM-13-02","G13","Codex GPT-6.1 Sol","S","MM-13-01","Feature flags, rollout rings and kill switches","Safe staging-to-beta-to-production promotion","Not started"
"MM-13-03","G13","Chat GPT-6","S","MM-13-01","Prepare product onboarding and FAQ","Users can create/join first meeting without developer help","Not started"
"MM-13-04","G13","Chat GPT-6","S","MM-13-01","Document transparent product limits and comparisons","Only tested features and capacity claimed","Not started"
"MM-13-05","G13","Codex GPT-6.1 Sol","S","MM-13-02","Release observability and usage funnel dashboards","Signup, join, quality and conversion measurable","Not started"
"MM-13-06","G13","Chat GPT-6","S","MM-13-01","Beta feedback triage and roadmap revision","Categorized failures with severity and ownership","Not started"
"MM-13-07","G13","Codex GPT-6.1 Sol","M","MM-13-06","Fix pilot defects and meet release acceptance tests","High severity problems resolved or launch blocked","Not started"
"MM-13-08","G13","Chat GPT-6","S","MM-13-04","Pricing page, terms/privacy and support contacts","Owner/legal-approved wording and payment disclosures","Not started"
"MM-13-09","G13","Codex/Work GPT-6 Astra","S","MM-13-07","Final multi-service risk and go/no-go review","Security, data, load, cost and operational risks assessed","Not started"
"MM-13-10","G13","Chat GPT-6","S","MM-13-09","Publish post-launch reliability and product iteration plan","Quarterly improvement, feedback cadence, ownership","Not started"

~~~~

---

## docs/FOUNDATION_AUDIT_2026-11-15.md — audit/livekit-foundations-2026-11-15

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/audit/livekit-foundations-2026-11-15/docs/FOUNDATION_AUDIT_2026-11-15.md  
Git blob SHA: 7bce8e810a9d152f1c88eee0c9dd27088577bc23  
Review state at snapshot: UNMERGED DRAFT; not approved.

~~~~markdown
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

~~~~

---

## docs/DECISIONS/0003-livekit-foundations.md — audit/livekit-foundations-2026-11-15

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/audit/livekit-foundations-2026-11-15/docs/DECISIONS/0003-livekit-foundations.md  
Git blob SHA: 062215dfb053d20fb230a2955ac3a603061d60a2  
Review state at snapshot: UNMERGED DRAFT; not approved.

~~~~markdown
# ADR-0003: LiveKit Meet reference + LiveKit Server as the two primary foundations

**Status: Proposed — requires owner/engineering acceptance**

**Date:** 2026-11-15

**Related backlog:** MM-01-02, MM-01-03, MM-01-12

**Related issues:** #1, #2, #3

## Context

MegaMeet needs a commercial-grade interactive meeting foundation without reimplementing WebRTC, an SFU or an entire conferencing platform. The study catalog contains 30 repositories, including complete conferencing products (Jitsi Meet and BigBlueButton), LiveKit application examples and media infrastructure, broadcast origins, collaboration libraries and operational tools.

The project also wants an original product experience and control plane. Combining multiple complete conferencing engines would increase operational complexity, duplicate media/signaling responsibilities and make authorization boundaries harder to reason about.

The repository's original-code license and contributor policy remain unresolved. This ADR therefore selects architectural foundations but does not authorize importing upstream source into MegaMeet.

## Decision

Select **exactly two primary foundational repositories**:

### Primary foundation 1 — LiveKit Meet

Repository: https://github.com/livekit-examples/meet

Reviewed commit: c3a16bdc7be03e201615779e8f2f6ee61d41ec91

License: Apache-2.0 repository license.

Role:

- frontend/reference foundation,
- meeting interaction patterns,
- device/prejoin/media-control examples,
- LiveKit Components integration patterns.

MegaMeet will not treat its demo backend as a production authorization service.

The reviewed app/api/connection-details route accepts caller-supplied room/name/metadata and issues a five-minute token with join, publish, data-publish and subscribe rights without application authentication or tenant/meeting authorization. The reviewed recording routes also explicitly warn that they are unauthenticated.

MegaMeet must replace these boundaries with original server-side admission, RBAC, tenant isolation, rate limiting, consent and audit logic.

The reviewed package also includes @livekit/krisp-noise-filter 0.4.6, whose npm license metadata points to separate LiveKit terms of service. MegaMeet should omit this dependency until its terms are separately approved.

### Primary foundation 2 — LiveKit Server

Repository: https://github.com/livekit/livekit

Pinned release: v1.13.11

Pinned commit: 385aa40f9292fe1db8caad87301e4b285b7c198a

License: Apache-2.0 with root LICENSE and NOTICE.

Role:

- WebRTC SFU,
- room/media transport,
- signaling/media routing,
- adaptive media delivery,
- TURN support/fallback,
- room/media APIs,
- integration point for Egress/Ingress.

MegaMeet should consume LiveKit Server as an external service/API/SDK dependency rather than maintaining a custom SFU fork.

## Why not Jitsi Meet

Jitsi Meet is mature, Apache-2.0 and actively maintained. It is a strong reference system and a viable choice for a product whose strategy is to operate/customize Jitsi.

It is not selected for MegaMeet because the application and deployment model are more tightly coupled to the Jitsi ecosystem (Jitsi Videobridge, Jicofo, Prosody/XMPP, Jibri and related components). Its client repository also spans web/mobile/native packaging and a large dependency surface.

Adopting Jitsi next to LiveKit would duplicate conferencing/media engines. Replacing LiveKit entirely with Jitsi would pull MegaMeet toward a complete Jitsi product architecture rather than the proposed original Next.js/control-plane design.

## Why not BigBlueButton

BigBlueButton is a rich, actively maintained virtual-classroom platform and an excellent source of product lessons for moderation, polling, whiteboards, shared notes, recordings and breakout-room workflows.

It is not selected as a primary MegaMeet foundation because:

- it is a large multi-service application,
- its domain is education/classrooms,
- repository licensing is LGPL-3.0 and requires more distribution diligence,
- operations/security surface is materially larger,
- adopting it beside LiveKit would duplicate product/media responsibilities.

Use it as a reference, not as a second conferencing engine.

## Consequences

### Positive

- avoids building a custom SFU/WebRTC stack,
- keeps MegaMeet's product/domain authorization original,
- aligns with the existing modular-monorepo ADR,
- keeps the initial frontend stack close to Next.js/React/TypeScript,
- provides a path to self-hosted or managed media,
- supports recording/broadcast export later through LiveKit Egress,
- reduces the number of major media technologies the team must operate.

### Negative / risks

- MegaMeet still depends on LiveKit APIs/protocol behavior and release cadence.
- Self-hosted LiveKit requires real networking/TURN/Redis/observability expertise at scale.
- A self-hosted room currently fits on one node; 100K audience delivery must not be modeled as one giant interactive room.
- LiveKit Meet demo authorization cannot be trusted as production policy.
- Some optional ecosystem packages have separate terms and must be audited individually.
- LiveKit Server's GitHub repository currently shows no published advisories but also no SECURITY.md; absence of advisories is not evidence of zero vulnerability risk.

## Large-event consequence

Interactive meetings and the presenter stage use LiveKit.

Large audience playback uses a separate broadcast provider/origin/CDN path:

LiveKit stage -> Egress -> managed broadcast ingest/origin -> audience playback.

Chat, Q&A, polls, viewer authentication and stage-request state remain MegaMeet concerns.

Do not claim 100K production capacity until real playback tests, provider quota approval and budget approval exist.

## Required legal/operational handling

- Preserve required Apache-2.0 license/attribution obligations for any redistributed upstream code/binaries.
- Preserve LiveKit Server NOTICE material where required.
- Track exact tags/SHAs in a dependency inventory/SBOM.
- Do not use LiveKit trademarks or branding as MegaMeet branding.
- Do not copy upstream source until issue #1 establishes MegaMeet's original-code/contribution policy.
- Re-run dependency/advisory checks at adoption and on upgrades.

## Validation

Accept this ADR only after:

1. issue #1 is resolved,
2. MM-01-02/03 evidence is reviewed,
3. the token/admission threat model is reviewed,
4. the team accepts LiveKit operational/network requirements,
5. the large-event provider decision remains independently gated by MM-01-09.

## Rollback / migration

MegaMeet should isolate provider-specific media calls behind a narrow media adapter and keep meeting identities, roles, permissions and recordings metadata in MegaMeet's own domain model.

If LiveKit later fails cost, reliability, licensing or product requirements, a different media provider can be evaluated without changing the canonical meeting/tenant authorization model. A migration would still be substantial and must be tested; this ADR does not claim media-engine replacement is trivial.

~~~~

---

## docs/CONTINUATION.md — audit/livekit-foundations-2026-11-15

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/audit/livekit-foundations-2026-11-15/docs/CONTINUATION.md  
Git blob SHA: 023445d7a3697e55259206c87bf6e79f3d6918e6  
Review state at snapshot: UNMERGED DRAFT; not approved.

~~~~markdown
# MegaMeet continuation handoff

**Updated:** 2026-11-15

This file is intentionally short. Read it before redoing repository research.

## Current repository state

- Main remains documentation/governance only.
- There is no runnable MegaMeet application, package.json, lockfile, test suite or GitHub Actions workflow.
- There were no pull requests before the current audit branch.
- Issues #1-#20 are the active planning/epic set.
- The authoritative delivery plan remains docs/TASK_BACKLOG.md with 178 work orders.

## Current blocker

**Issue #1 / MM-00-07:** the owner has not selected the license and contributor policy for original MegaMeet code.

AGENTS.md, CONTRIBUTING.md and docs/LICENSING.md say substantive product-code/source import should not begin before that decision.

Do not silently bypass this gate.

## Foundation research result

Proposed exact two main repositories:

1. LiveKit Meet
   - https://github.com/livekit-examples/meet
   - reviewed commit c3a16bdc7be03e201615779e8f2f6ee61d41ec91
   - Apache-2.0 repository license
   - use as UI/reference foundation only
   - replace demo token/recording authorization

2. LiveKit Server
   - https://github.com/livekit/livekit
   - v1.13.11
   - commit 385aa40f9292fe1db8caad87301e4b285b7c198a
   - Apache-2.0 with LICENSE + NOTICE
   - use as external SFU/media infrastructure

Serious alternatives reviewed: Jitsi Meet and BigBlueButton. Keep them as reference systems; do not stack their conferencing engines with LiveKit.

Full evidence: docs/FOUNDATION_AUDIT_2026-11-15.md

Decision proposal: docs/DECISIONS/0003-livekit-foundations.md

## Security finding to preserve

Do not reuse LiveKit Meet's app/api/connection-details route unchanged.

The reviewed route authenticates nobody and grants every caller room join + publish + data publish + subscribe based on caller-provided room/name/metadata.

MegaMeet needs a server-owned meeting-grant endpoint with tenant checks, invitation/admission checks, server-derived role/capabilities, short TTL, rate limits, audit events and negative authorization tests.

The upstream recording start/stop routes are also explicitly unauthenticated demonstration code.

## Dependency caveat

The reviewed LiveKit Meet package uses @livekit/krisp-noise-filter 0.4.6. npm marks its license as “SEE LICENSE IN https://livekit.io/legal/terms-of-service”.

Do not add it to MegaMeet until separately reviewed/approved.

## Architecture direction

- Keep the modular monorepo.
- Start with apps/web plus only real shared packages.
- Do not scaffold empty microservices.
- Keep product identity/roles/meetings canonical in MegaMeet.
- Use short-lived server-issued LiveKit grants.
- Interactive meetings: LiveKit SFU.
- Large event: bounded LiveKit presenter stage -> Egress -> managed broadcast/CDN.
- Audience interaction plane remains separate from video playback.
- Do not claim 100K until real playback/load and budget/quota gates pass.

## Next task

First: resolve **MM-00-07 / issue #1** with a written owner decision.

After G00/G01 approval, the first product-code task is **MM-02-01**: create the minimal Next.js/TypeScript monorepo and reproducible build, without copied LiveKit Meet source or unapproved optional dependencies.

~~~~

---

## docs/LICENSING_DECISION_WORKSHEET.md — docs/mm-00-07-license-decision-worksheet-2026-11-16

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/docs/mm-00-07-license-decision-worksheet-2026-11-16/docs/LICENSING_DECISION_WORKSHEET.md  
Git blob SHA: fec2c9701e355cce30ceafa4ceec93a1c629ea7f  
Review state at snapshot: UNMERGED DRAFT; not approved.

~~~~markdown
# MM-00-07 — MegaMeet original-code licensing decision worksheet

**Status: OWNER DECISION REQUIRED — NOT APPROVED**  
**Prepared:** 2026-11-16  
**Linked:** [Issue #1](https://github.com/arunabanarjee32-bit/google-meet/issues/1) · [Backlog MM-00-07](TASK_BACKLOG.md) · [Licensing guidance](LICENSING.md)

## Scope and boundary

MegaMeet is an independently branded commercial meeting product, currently documented but not implemented on the default branch. This worksheet describes choices for **MegaMeet's original code and contributions**. It does not change the copyright or license of LiveKit, Jitsi, BigBlueButton, any existing package, or their logos/assets. A public GitHub repository without a LICENSE file is **not** an unrestricted open-source grant; it is also **not** a confidentiality mechanism.

**No choice below has been made on the owner's behalf. Do not add LICENSE, copy upstream source, or begin substantive product-code contributions until the owner records the choice and required review approves it.**

## Choices to resolve

| Model | What the owner can do | Important tradeoff | Initial suitability |
| --- | --- | --- | --- |
| **Proprietary original code** | Keep MegaMeet application/control-plane code under commercial terms; sell hosting, services and proprietary features | For confidentiality, keep source in a private repo; the current public repo can remain a separate open documentation project. Vet inbound contributions and third-party redistribution. | Strong option if ownership/control and commercial differentiation dominate |
| **Apache-2.0 original code** | Release original MegaMeet source with permissive reuse, modifications and commercial distribution; includes express patent terms | Other parties may legally build competing distributions, while keeping license/notice obligations | Strong option if open community adoption and self-hosting are strategic |
| **MIT original code** | Release original MegaMeet source with simple permissive reuse, including commercial redistribution | Similar competitive redistribution risk; no express patent license in MIT text | Good simple open-source option |
| **AGPL-3.0 original code** | Require reciprocal source-access obligations for covered network-served modifications, subject to exact license terms | Higher legal/compliance burden, contributor friction and ecosystem compatibility diligence | Only if strong reciprocal open-source obligations are intentional |
| **Dual licensing** | Offer the same copyright-controlled original code under different terms where ownership and contributor grants permit | Adds legal, contributor, support and license-compliance complexity | Defer unless there is a specific commercial reason and legal support |

This is a product/legal tradeoff table, **not legal advice**. An attorney should review the final choice, patents, jurisdictions and commercial contracts.

## Contributor policy — choose separately

1. **No external code contributions initially.** Accept issues/docs feedback; only authorized maintainers write product code. Simplest for a proprietary early product.
2. **DCO / sign-off model.** Contributors certify their right to submit code under the project license. Does **not** automatically assign their copyright to the owner.
3. **CLA or copyright assignment.** May support additional licensing models but creates legal/process friction; have counsel prepare and validate terms.

A permissive upstream dependency does not grant exclusive ownership of upstream technology. Keep dependency versions, notices, trademarks and third-party assets in a documented inventory.

## Technical reuse policy, independent of owner-code license

- **LiveKit Meet:** examined at `c3a16bdc7be03e201615779e8f2f6ee61d41ec91`, repository Apache-2.0. Treat as a frontend *reference*, not a production login/admission/recording backend.
- **LiveKit Server:** examined at `v1.13.11` / `385aa40f9292fe1db8caad87301e4b285b7c198a`, repository Apache-2.0; use as service/SDK integration rather than copying an SFU.
- **Optional @livekit/krisp-noise-filter:** reviewed package has separate terms; do not include without a specific legal decision.
- For any redistribution, preserve license/NOTICE as applicable and review package-level dependencies, brand marks, fonts, media, SDK/model terms and SBOM.

Research evidence: [the open foundation audit PR](https://github.com/arunabanarjee32-bit/google-meet/pull/21). Its proposed ADR-0003 is **not** owner approval.

## Owner decision record — complete in issue #1

- **Copyright owner/legal entity:** [owner to complete]
- **Original-code strategy:** [proprietary / Apache-2.0 / MIT / AGPL-3.0 / dual / other]
- **Will product source remain publicly accessible?** [yes / no; repository plan]
- **Outside contributions allowed initially?** [no / DCO / CLA / other]
- **Who can approve and merge code?** [maintainers and required review]
- **Initial trademark and brand rules:** [owner to complete; MegaMeet is still a working name]
- **Third-party NOTICE/license inventory owner:** [owner to assign]
- **Written legal review/approval reference:** [issue comment / document / reviewer]
- **Decision date and sign-off:** [owner to record]

## Acceptance checklist for MM-00-07 / issue #1

- [ ] Owner explicitly chooses a model and contributor terms in issue #1.
- [ ] Legal/commercial review recorded when appropriate.
- [ ] Appropriate LICENSE and/or proprietary notices prepared **after** the decision.
- [ ] CONTRIBUTING.md, docs/LICENSING.md and source-reuse policy updated consistently.
- [ ] Copyright/attribution/third-party notice requirements assigned.
- [ ] G00/G01 reviewers acknowledge which coding work is permitted.

**Next code task only after G00/G01 acceptance:** MM-02-01 — minimal Next.js/TypeScript web skeleton, dependency lockfile, build, tests, environment validation and CI. Do not start with an unauthenticated LiveKit Meet demo token route.

~~~~

---

