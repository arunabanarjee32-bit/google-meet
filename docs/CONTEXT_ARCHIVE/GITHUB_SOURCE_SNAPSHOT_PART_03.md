# MegaMeet source-document snapshot — Part 3 of 5

Captured 2026-11-16; source: main branch (tree dd2284f26f7822c086bef5070839364e42c01d8f). This preserves master plan, complete 178-task Markdown backlog, model/credit instructions, scoped Codex tasks, first sprint and issue index. Canonical documents remain at their original paths.

## docs/DELIVERY_MASTER_PLAN.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/DELIVERY_MASTER_PLAN.md  
Blob SHA: 6a9c42506e20c2b6a2a799524abdfcd3bc07e67b

~~~~markdown
# MegaMeet end-to-end execution plan — 14 gated phases

**Last planned: 2026-11-14. Project status: documentation only.** For the full **178-task backlog**, see [TASK_BACKLOG.md](TASK_BACKLOG.md) and its [CSV export](TASK_BACKLOG.csv). Tasks are proposed until actual PR/test evidence exists.

## Goal and delivery strategy

Build an original commercially operated video meeting and collaboration product, benchmarked against Zoom, Teams and Meet, with an independently validated **100,000+ concurrent audience-viewer** event mode. The design is **not** 100K simultaneous live publishers. The product must be safe, maintainable, accessible and cost-aware; becoming market #1 is an ambition, not something an engineering plan can guarantee.

### Who does what

| Lane | Responsibility | Typical deliverable | Do NOT spend this lane on |
| --- | --- | --- | --- |
| **C: GPT-6 in Chat** | Requirements, competitor analysis, code/test drafts, ADRs, developer guides, acceptance cases, release language | Short ready-to-implement spec or patch + tests | Claiming unexecuted code works or inventing legal conclusions |
| **S: GPT-6.1 Sol in Codex** | Default code implementer, focused refactors, dependencies, CI, unit/integration tests, builds, staging deployment with approval | Small branch/PR, logs and test output | Rewriting proven engines, huge vague tasks, unauthorized paid cloud runs |
| **A: Astra in Codex/Work** | Escalation for difficult architecture, distributed state, security-critical invariants, bottleneck/root-cause and prelaunch risk review | Decision / narrow complex fix / proof of risk remediation | Formatting, CRUD scaffolding, routine UI and docs |
| **H: Owner and qualified humans** | Legal licensing/branding, budgets and accounts, production keys, security approvals, real device tests, compliance and launch authorization | Recorded decision/approval and real-world evidence | Unsupervised delegation to any AI |

The user's requested “GPT-6 Sol in regular Chat” is represented by **GPT-6 in Chat**. GPT-6.1 Sol is a separate Codex/Work model; regular Chat model selection may differ. Check the model picker and current usage dashboard before work.

### Allocation of tasks (counts, NOT guaranteed percent of credits)

- Chat GPT-6: **46** work orders.
- Codex GPT-6.1 Sol: **115** work orders.
- Astra: **17** work orders, kept intentionally rare.
- Human approvals are additional cross-cutting gates.

**These counts are not money or token estimates.** Some distributed-systems or security tasks can dominate cost. Start with Standard speed, Low/Medium effort; measure actual usage and escalate only when evidence supports it.

## Dependency-aware roadmap

| Phase | Work packages | Exit evidence | Primary delivery mode |
| --- | --- | --- | --- |
| G00 | Product, ownership and governance (10 tasks) | Owner approves licensing, target user, branding, and no external code import before approval. | 0 Sol, 9 Chat, 1 Astra |
| G01 | Architecture, reuse and interface contracts (12 tasks) | Approved architecture decision records, verified dependency plan, threat model and operational baseline. | 0 Sol, 8 Chat, 4 Astra |
| G02 | Monorepo, CI and local developer experience (12 tasks) | Clone, configure, build, run and test the minimal app reproducibly in a clean environment. | 11 Sol, 1 Chat, 0 Astra |
| G03 | Accounts, organizations, scheduling and core APIs (12 tasks) | Authenticated users can create, schedule, securely join and end a meeting; access isolation tests pass. | 10 Sol, 1 Chat, 1 Astra |
| G04 | Reliable real-time video meetings (16 tasks) | Two browsers and a small group complete real A/V and screen share tests under role controls and network disruption. | 14 Sol, 1 Chat, 1 Astra |
| G05 | Collaboration, moderation and accessible workflows (13 tasks) | Chats, Q&A, polls, notes and whiteboard operate with persistence, authorization and usable accessibility. | 11 Sol, 2 Chat, 0 Astra |
| G06 | Recording, playback, captions and optional AI (12 tasks) | Recordings and transcripts follow explicit consent, access, retention and deletion policies. | 8 Sol, 3 Chat, 1 Astra |
| G07 | Webinar and 100K-event product architecture (16 tasks) | Small real event works end-to-end: live stage -> broadcast -> audience plus separate moderation. | 12 Sol, 2 Chat, 2 Astra |
| G08 | 100K load, security and resiliency validation (12 tasks) | Real playback capacity proven at successive tiers before any 100K customer claim. | 8 Sol, 2 Chat, 2 Astra |
| G09 | Enterprise security, administration and integrations (12 tasks) | Multi-tenant enterprise pilot passes SSO, admin policies, retention, audit and integration tests. | 9 Sol, 2 Chat, 1 Astra |
| G10 | Mobile applications and desktop strategy (10 tasks) | Supported mobile platforms reliably join and use core meeting flows; desktop only if justified. | 8 Sol, 2 Chat, 0 Astra |
| G11 | Monetization, product analytics and customer integrations (13 tasks) | A trial organization can subscribe, receive invoices, view usage and access allowed features reliably. | 9 Sol, 3 Chat, 1 Astra |
| G12 | Production security, quality, SRE and operations (18 tasks) | Security review, deploy/recovery, observability, quality and accessibility signed off for production. | 12 Sol, 4 Chat, 2 Astra |
| G13 | Beta pilots, commercial launch and ongoing improvement (10 tasks) | Approved public release has real customers, support, rollout controls and evidence-backed capacity claims. | 3 Sol, 6 Chat, 1 Astra |

### Suggested release slices and sequencing

1. **Commitment gate:** G00 → G01. Choose project license, technical stack, deployment constraints and initial user segment. No expensive implementation yet.
2. **First live product:** G02 → G03 → G04. Demonstrate actual two-browser interactive meeting, secure roles and screen share.
3. **Customer value:** G05 and G06 in parallel once G04 works (chat, moderation, recording and consent); release a private beta for the small-meeting mode.
4. **Differentiating event capability:** G07 then G08. Build a reliable stage-to-broadcast experience, with progressively tested concurrency. **Do not wait for 100K to release small-meeting features.**
5. **Commercial expansion:** G09, G10 and G11 as demand warrants, not as blocking prerequisites for initial beta.
6. **Operational readiness:** G12 is continuous from the first deployed environment, with its gate before general availability.
7. **Launch:** G13 is a staged beta → production rollout. For *advertising 100K* require successful G08 Gate E evidence in addition to G12.

## Scope guardrails

- Build one original monorepo; use LiveKit and other vetted technologies as licensed dependencies/services, not copies of entire competing apps.
- Reuse-first component audit for every feature. Do not add Keycloak, Centrifugo, SRS, Novu, Kill Bill, React Native, and all other candidates at once; justify when each is necessary.
- Free-tier or managed vendor services are not inherently cheaper than self-hosting at 100K; evaluate **cost per verified viewer-hour**, latency and required staff.
- Treat SDK/media, access control, chat/fanout, event admission, stream delivery and analytics as separate scalable concerns.
- Avoid using Astra just because an issue has many lines; split it and try Sol first when risks are moderate.
- Avoid speculative compliance claims. Public repository does not equal a license for proprietary code redistribution.

## Releases: explicit definition of completion

- **Prototype** = real two-browser A/V with local reproducible tests; not production.
- **Private beta** = tested access/roles, basic meeting UX, explicit privacy notices, monitored deployments.
- **Commercial small-meeting GA** = release approval after security, operational, accessibility and support readiness, independently of 100K.
- **Webinar beta** = real stage-to-CDN playback and live moderation with measured small audience.
- **100K-capable tier** = verified actual concurrent video playback under agreed quality/regions, provider quota/budget approval, failure recovery and signed-off operational readiness.

## Next actions in order

1. Owner reviews [GitHub issue #1](https://github.com/arunabanarjee32-bit/google-meet/issues/1) on original-code license and contributor policy.
2. Assign **Chat** tasks G00 and G01 for requirements, licenses and cost comparisons before coding.
3. Ask **Astra** only for G01-04/G01-05 after initial Chat architecture pack is ready (short targeted review).
4. Send **Sol** one small Phase G02 skeleton task after the gate; provide acceptance tests and ask for one PR, not an entire application.
5. Review usage and actual test evidence; continue one task/PR at a time.

## References

- [Detailed work orders](TASK_BACKLOG.md)
- [Credit policy and delegation prompts](CODEX_CREDIT_POLICY.md)
- [First sprint](FIRST_SPRINT.md)
- [Codex agent rules](../AGENTS.md)
- [100K media validation](SCALABILITY_100K.md)
- [Definition of done](DEFINITION_OF_DONE.md)

~~~~

---

## docs/TASK_BACKLOG.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/TASK_BACKLOG.md  
Blob SHA: e5fcfcaf2f4f2088873bab5f8c16637ec7719f79

~~~~markdown
# MegaMeet: full end-to-end task backlog

> **Planning baseline: 2026-11-14.** All tasks are **NOT STARTED** unless verified independently against actual code and tests. MegaMeet's source-code license is still undecided. This is a delivery plan, not a statement that the product already exists. Task numbers are stable references; do not mark complete merely because a code generator wrote files.

This contains **178 discrete work orders across 14 phases**. It serves as the executable breakdown of [Project vision](PROJECT_VISION.md), [Requirements](PRODUCT_REQUIREMENTS.md), and the [Delivery plan](DELIVERY_MASTER_PLAN.md). Some phases can proceed in parallel after gates are satisfied; production and paid tests still require human approvals.

## Assignment codes

- **C / Chat GPT-6:** specs, design docs, code drafts, test cases, content, reference implementations, review plans. This assistant can help write files/patches, but no completion claim without real execution/tests.
- **S / Codex GPT-6.1 Sol:** the default implementation engineer; scoped changes in the actual repository, integration tests, CI and build verifications.
- **A / GPT-6 Astra in Codex/Work:** targeted escalation: especially hard architecture, distributed-systems challenges, permission/security audits and incident analysis. Give Astra a narrow question and files, not an entire unfinished product.
- **H / human decision-maker (gate, not an AI worker):** owner signs off on licenses, third-party payments, data policies, security releases, business and production claims.

**Sizes** are approximate *work unit sizes*, not hours or credits: S = one narrow PR/review; M = may need 2–3 separate PRs and a milestone check. Dependencies are task IDs or phase gate Gxx. If a task gets too big, split it into smaller child issues before coding.

## Phase table

| Phase | Focus | Chat (C) | Sol (S) | Astra (A) | Total |
| --- | --- | ---: | ---: | ---: | ---: |
| G00 | Product, ownership and governance | 9 | 0 | 1 | 10 |
| G01 | Architecture, reuse and interface contracts | 8 | 0 | 4 | 12 |
| G02 | Monorepo, CI and local developer experience | 1 | 11 | 0 | 12 |
| G03 | Accounts, organizations, scheduling and core APIs | 1 | 10 | 1 | 12 |
| G04 | Reliable real-time video meetings | 1 | 14 | 1 | 16 |
| G05 | Collaboration, moderation and accessible workflows | 2 | 11 | 0 | 13 |
| G06 | Recording, playback, captions and optional AI | 3 | 8 | 1 | 12 |
| G07 | Webinar and 100K-event product architecture | 2 | 12 | 2 | 16 |
| G08 | 100K load, security and resiliency validation | 2 | 8 | 2 | 12 |
| G09 | Enterprise security, administration and integrations | 2 | 9 | 1 | 12 |
| G10 | Mobile applications and desktop strategy | 2 | 8 | 0 | 10 |
| G11 | Monetization, product analytics and customer integrations | 3 | 9 | 1 | 13 |
| G12 | Production security, quality, SRE and operations | 4 | 12 | 2 | 18 |
| G13 | Beta pilots, commercial launch and ongoing improvement | 6 | 3 | 1 | 10 |
| **Total** | | **46** | **115** | **17** | **178** |

## G00 — Product, ownership and governance

**Prerequisite:** None  
**Gate to proceed:** Owner approves licensing, target user, branding, and no external code import before approval.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-00-01 | C | S | Interview plan and customer personas | Interview script and 3 prioritized buyer personas | none |
| MM-00-02 | C | S | Competitive capability matrix | Dated, sourced matrix of Zoom, Meet, Teams and webinar features | none |
| MM-00-03 | C | S | Define launch positioning and differentiators | One-sentence value proposition and measurable hypotheses | none |
| MM-00-04 | C | S | Define first customer segment and MVP constraints | Named segment, must-have workflows and exclusions | none |
| MM-00-05 | C | S | Write user journeys for host, guest, moderator, viewer | Each journey has success, failure and accessibility paths | none |
| MM-00-06 | C | S | Draft privacy and data-retention policy decisions | Decision sheet identifies unresolved legal questions | none |
| MM-00-07 | C | S | Draft original-code license options | Tradeoffs for proprietary/open-source, upstream notices and CLA/DCO | none |
| MM-00-08 | A | S | Review commercial licensing architecture | Identify risky source imports and commercialization blockers | MM-00-07 |
| MM-00-09 | C | S | Define project naming and trademark check plan | Brand-selection checklist; no affiliation implied | none |
| MM-00-10 | C | S | Define price/customer research experiments | Research hypotheses and testable pricing assumptions | MM-00-04 |

## G01 — Architecture, reuse and interface contracts

**Prerequisite:** G00  
**Gate to proceed:** Approved architecture decision records, verified dependency plan, threat model and operational baseline.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-01-01 | C | S | Inventory current repository and planned features | Diff between actual files and desired capabilities; no invented code | G00 |
| MM-01-02 | C | S | Upstream version, license and security spreadsheet | Exact tags, license/NOTICE, dependencies and maintenance evidence | MM-01-01 |
| MM-01-03 | C | S | Reuse/build/defer decision for each feature | Approved decision table cites mature libraries and reasons | MM-01-02 |
| MM-01-04 | A | M | Interactive media versus broadcast architecture ADR | Signed-off stage, audience, egress, latency and failure model | MM-01-03 |
| MM-01-05 | A | M | Control-plane and realtime state boundaries | Event/domain graph prevents cross-room permissions and hot keys | MM-01-04 |
| MM-01-06 | C | S | API and event naming/specification | Versioned OpenAPI draft and event schemas without code | MM-01-05 |
| MM-01-07 | C | S | Domain data model and tenant boundaries | ERD for users, orgs, rooms, events, tickets and assets | MM-01-05 |
| MM-01-08 | A | S | Threat model and trust boundary review | Abuse cases for tokens, admin, viewers, recordings and AI | MM-01-05 |
| MM-01-09 | C | S | Managed broadcast/CDN versus SRS comparison | Latency, quality, quotas, ops and monthly cost assumptions | MM-01-04 |
| MM-01-10 | C | S | Browser and mobile support matrix | Versions, capabilities, accessibility and test devices listed | MM-01-03 |
| MM-01-11 | A | S | Architecture cost/reliability red-team review | Written risks, fallbacks and decision owners | MM-01-08 |
| MM-01-12 | C | S | Approve implementation architecture and gates | Decision records reviewed by human maintainer | MM-01-04 |

## G02 — Monorepo, CI and local developer experience

**Prerequisite:** G01  
**Gate to proceed:** Clone, configure, build, run and test the minimal app reproducibly in a clean environment.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-02-01 | S | M | Initialize Next.js TypeScript monorepo | Minimal running app and lockfile; no placeholder microservices | G01 |
| MM-02-02 | S | S | Package manager and workspace tooling | Version pinned and clean install documented | MM-02-01 |
| MM-02-03 | S | S | Environment schema and redacted sample | Missing/invalid values fail fast; no secrets committed | MM-02-01 |
| MM-02-04 | S | S | ESLint formatting and typecheck scripts | Checks run locally and in CI with recorded output | MM-02-01 |
| MM-02-05 | S | S | Unit and integration test harness | Sample meaningful tests run in CI | MM-02-01 |
| MM-02-06 | S | S | GitHub Actions build/test workflow | PR checks run with least-privilege permissions | MM-02-04 |
| MM-02-07 | S | S | Docker development configuration | Minimum required services start with documented teardown | MM-02-03 |
| MM-02-08 | S | S | Typed API contract package | Client/server contract compiles with schema validation | MM-01-06 |
| MM-02-09 | S | S | Structured error and log helpers | Correlation IDs and sensitive fields redacted | MM-02-01 |
| MM-02-10 | C | S | Write exact local setup and troubleshooting | New developer guide tested against fresh clone | MM-02-07 |
| MM-02-11 | S | S | Dependabot/security scanning and lockfile audit | Version pinning and actionable dependency alerts | MM-02-06 |
| MM-02-12 | S | S | Preview deployment and branch protections proposal | Nonproduction preview with safe secrets and rollback notes | MM-02-06 |

## G03 — Accounts, organizations, scheduling and core APIs

**Prerequisite:** G02  
**Gate to proceed:** Authenticated users can create, schedule, securely join and end a meeting; access isolation tests pass.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-03-01 | S | M | Integrate chosen identity provider/OIDC | Signup/login/logout/guest flow verified | G02 |
| MM-03-02 | S | S | Session lifecycle and CSRF protections | Expiry, logout, refresh and anti-CSRF tests pass | MM-03-01 |
| MM-03-03 | S | S | User profile and preferences persistence | Users update valid profile fields without tenant leakage | MM-03-01 |
| MM-03-04 | S | M | Organization/workspace entities | Create/join/invite with strict membership checks | MM-03-01 |
| MM-03-05 | A | S | Review tenant RBAC and resource authorization | Adversarial permission matrix with denied escalation tests | MM-03-04 |
| MM-03-06 | S | M | Meeting create, edit, cancel and list APIs | Idempotent APIs, ownership checks and validation | MM-03-04 |
| MM-03-07 | S | S | Secure meeting links and invitation tickets | Unpredictable ID, expiry and revoked ticket denial | MM-03-06 |
| MM-03-08 | S | S | Meeting schedule with timezone/DST handling | Cross-timezone test cases and valid recurrence approach | MM-03-06 |
| MM-03-09 | S | S | Calendar UI with selected licensed library | Calendar CRUD + keyboard support | MM-03-08 |
| MM-03-10 | C | S | Invitation email text, policy and templates | Localized, accessible and unambiguous join copy | MM-03-07 |
| MM-03-11 | S | M | Meeting dashboard, history and search | Only authorized meetings show; pagination tested | MM-03-06 |
| MM-03-12 | S | S | Audit events for meeting control actions | Structured create/join/revoke/end evidence persisted | MM-03-06 |

## G04 — Reliable real-time video meetings

**Prerequisite:** G03  
**Gate to proceed:** Two browsers and a small group complete real A/V and screen share tests under role controls and network disruption.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-04-01 | S | M | Integrate LiveKit meeting SDK/Components | Real bidirectional audio/video between two browsers | G03 |
| MM-04-02 | S | S | Server-generated short-lived LiveKit grants | Client cannot forge speaker/host roles | MM-04-01 |
| MM-04-03 | S | S | Device preview and permissions handling | Camera/mic denied, changed and unplugged cases handled | MM-04-01 |
| MM-04-04 | S | M | Join/leave/lobby/deny workflow | Host admission and guest join policies enforced server-side | MM-04-02 |
| MM-04-05 | S | S | Media mute, camera toggle and device switching | UI reflects actual track state on both peers | MM-04-01 |
| MM-04-06 | S | M | Share entire screen/window/tab | Presenter-only share permission and browser fallback tested | MM-04-02 |
| MM-04-07 | S | S | Grid, active speaker and spotlight layouts | Responsive with keyboard/screen-reader affordances | MM-04-01 |
| MM-04-08 | S | S | Participant roster and speaking indicators | Role/state correct under reconnect and departure | MM-04-01 |
| MM-04-09 | S | S | Host kick, mute request, lock and co-host grants | Unauthorized attempts fail and events are audited | MM-04-02 |
| MM-04-10 | S | S | Reactions and raise hand in small meetings | Events not lost across short reconnect | MM-04-08 |
| MM-04-11 | S | M | Reconnect and unstable network UX | Recovery, offline, retry and track reset behavior tested | MM-04-05 |
| MM-04-12 | S | S | Bandwidth adaptation and low-data mode | Measured under throttled network and weak CPU | MM-04-01 |
| MM-04-13 | S | S | Share-link guest browser interoperability test | Chromium, Firefox, Safari differences documented | MM-04-04 |
| MM-04-14 | S | S | SIP/TURN decision and NAT traversal smoke | Known network restrictions and TURN costs documented | MM-04-01 |
| MM-04-15 | A | S | Media permission and failure review | Host privilege, revoked token, SFU failure cases assessed | MM-04-09 |
| MM-04-16 | C | S | Meeting UX acceptance script and bug matrix | Human QA can reproduce every critical scenario | MM-04-12 |

## G05 — Collaboration, moderation and accessible workflows

**Prerequisite:** G04  
**Gate to proceed:** Chats, Q&A, polls, notes and whiteboard operate with persistence, authorization and usable accessibility.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-05-01 | C | S | Define chat/Q&A/polls privacy and UX rules | User stories cover history, retention, spam and moderation | G04 |
| MM-05-02 | S | M | Select and integrate realtime transport | Authorized channels, reconnect and fanout metrics work | MM-05-01 |
| MM-05-03 | S | M | Persist meeting chat with pagination | Ordered history, retention and room access tests | MM-05-02 |
| MM-05-04 | S | S | Chat moderation, spam limits and abuse reports | Rate limits and deletion/ban actions tested | MM-05-03 |
| MM-05-05 | S | S | Meeting reactions and pinned messages | Consistent updates and screen-reader announcements | MM-05-03 |
| MM-05-06 | S | M | Polling create/vote/close/results | One eligible vote per poll setting; role checks | MM-05-02 |
| MM-05-07 | S | M | Moderated Q&A submit, vote, answer and archive | Host moderation, per-event limits and persistence | MM-05-02 |
| MM-05-08 | S | S | Hand-raise queue and speaker requests | Deterministic queue order and moderator controls | MM-05-07 |
| MM-05-09 | S | M | Whiteboard integration and permissions | Board edits isolated per meeting; export works | MM-05-01 |
| MM-05-10 | S | S | Collaborative notes with Yjs or vetted alternative | Concurrent edits converge; permissions validated | MM-05-09 |
| MM-05-11 | C | S | Accessibility audit and text alternatives | WCAG-oriented keyboard/contrast/screen-reader checklist | MM-05-06 |
| MM-05-12 | S | S | File/link sharing metadata and safety policy | Access checks, upload limits and safe previews | MM-05-03 |
| MM-05-13 | S | S | Chat/Q&A flood and reconnect tests | Backpressure, ordering and data integrity verified | MM-05-04 |

## G06 — Recording, playback, captions and optional AI

**Prerequisite:** G04  
**Gate to proceed:** Recordings and transcripts follow explicit consent, access, retention and deletion policies.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-06-01 | C | S | Recording consent and data lifecycle policy | Owner-approved retention, disclosure and permissions rules | G04 |
| MM-06-02 | S | M | Integrate LiveKit Egress recording jobs | Start/stop/state, errors and artifacts tracked | MM-06-01 |
| MM-06-03 | S | S | Recording consent and visible indicator UX | Every participant sees enabled status and policy | MM-06-02 |
| MM-06-04 | S | M | Secure recording storage and signed playback | Tenant isolation, expiry and access tests | MM-06-02 |
| MM-06-05 | S | S | Recording search, share, delete and retention job | Allowed actions and deletion verified end-to-end | MM-06-04 |
| MM-06-06 | S | S | Caption UI and transcript format ingestion | Timing, speaker labeling and accessibility tested | MM-06-03 |
| MM-06-07 | C | S | Evaluate transcription engines and costs | Benchmarks of languages, quality, privacy and expense | MM-06-06 |
| MM-06-08 | S | M | Consent-gated transcription pipeline | Secrets, retries, opt-in and deletion handled | MM-06-07 |
| MM-06-09 | S | M | Summary, action item and transcript search | Grounded output with source timestamps and edit option | MM-06-08 |
| MM-06-10 | C | S | AI translation quality and policy benchmark | Languages/latency/cost and consent requirements documented | MM-06-08 |
| MM-06-11 | A | S | Review AI data exposure and recording threat model | Negative access tests, misuse and third-party data flow risks | MM-06-08 |
| MM-06-12 | S | S | Recording and AI quota/cost kill switches | Usage limits and shutdown tested in staging | MM-06-08 |

## G07 — Webinar and 100K-event product architecture

**Prerequisite:** G04+G01  
**Gate to proceed:** Small real event works end-to-end: live stage -> broadcast -> audience plus separate moderation.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-07-01 | C | S | Define webinar tiers, latency and attendee UX | Document viewer/speaker differences and transition states | G04 |
| MM-07-02 | S | M | Event domain entities and participant roles | Event != SFU room; tickets and role policy tested | MM-07-01 |
| MM-07-03 | S | S | Large-event creation and registration API | Capacity, invite/approval and signed admission tested | MM-07-02 |
| MM-07-04 | A | M | Review speaker promotion transaction design | Race/replay/echo/rollback rules and security tests | MM-07-02 |
| MM-07-05 | S | M | Bounded LiveKit speaker-stage workflow | Only authorized presenters can publish | MM-07-02 |
| MM-07-06 | S | M | Egress program feed to chosen broadcast provider | Real stage playback on at least two viewer devices | MM-07-05 |
| MM-07-07 | S | S | Broadcast provider adapter and health states | Start/stop/retry, status and normalized errors verified | MM-07-06 |
| MM-07-08 | S | S | Audience player quality and latency UI | ABR fallback, error states and live-delay notice tested | MM-07-06 |
| MM-07-09 | S | M | Raise-hand/viewer-to-speaker authorization | Promotion/demotion secure and no echo on transitions | MM-07-04 |
| MM-07-10 | S | S | Speaker moderation dashboard | Host can invite, approve, revoke and remove speakers | MM-07-09 |
| MM-07-11 | S | S | Audience Q&A/polls/chat event integration | Permissions and moderated fanout tested | MM-07-03 |
| MM-07-12 | S | S | Audience identity and signed playback tokens | No cross-event stream/session leakage | MM-07-03 |
| MM-07-13 | S | S | Webinar analytics and audience counters | Distinct actual watchers from registrations and sockets | MM-07-08 |
| MM-07-14 | S | S | Streaming failure/fallback states | Stage/egress/CDN outage alerts and recovery UI | MM-07-07 |
| MM-07-15 | C | S | Runbook for event organizers and moderators | Step-by-step preflight, backup and emergency actions | MM-07-10 |
| MM-07-16 | A | S | Validate stage/broadcast/control-plane architecture | Failure-mode review before load testing | MM-07-14 |

## G08 — 100K load, security and resiliency validation

**Prerequisite:** G07  
**Gate to proceed:** Real playback capacity proven at successive tiers before any 100K customer claim.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-08-01 | C | S | Specify real viewer performance methodology | Distinguishes synthetic sockets from actual media playback | G07 |
| MM-08-02 | S | M | Build scalable playback load-test harness | Reproducible simulator reports actual decoding/viewer state | MM-08-01 |
| MM-08-03 | S | S | API/auth join storm load tests | Rate, p95/p99, error counts and rate-limiting report | MM-08-02 |
| MM-08-04 | S | S | Realtime message flood/sharding benchmarks | Moderation queue, hot-key, backpressure evidence | MM-08-02 |
| MM-08-05 | S | S | Broadcast adaptive bitrate and CDN instrumentation | Rebuffers, bitrate, startup time and region tracked | MM-08-02 |
| MM-08-06 | S | M | 10K viewer staging validation | Real audience playback, cost and provider quotas documented | MM-08-02 |
| MM-08-07 | A | M | Review 50K/100K multi-region design before paid runs | Quantified bottlenecks, failovers, quota and budget approval | MM-08-06 |
| MM-08-08 | S | M | Failure drills and reconnect-storm harness | SFU/egress/origin/CDN failure traces and recovery tests | MM-08-06 |
| MM-08-09 | S | M | 50K real-viewer controlled test | Reproducible quality, logs and approved spend | MM-08-07 |
| MM-08-10 | S | M | 100K real-viewer controlled test | Verified concurrent stream playback with independent evidence | MM-08-09 |
| MM-08-11 | C | S | Publish tested capacity and limitations report | Clearly distinguishes maximum observed and safe offered capacity | MM-08-10 |
| MM-08-12 | A | S | Production scaling readiness assessment | Independent go/no-go on capacity, failover and economics | MM-08-10 |

## G09 — Enterprise security, administration and integrations

**Prerequisite:** G03+G06  
**Gate to proceed:** Multi-tenant enterprise pilot passes SSO, admin policies, retention, audit and integration tests.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-09-01 | C | S | Define organization plans and enterprise workflows | SCIM/SSO/admin/retention prioritized by pilot customers | G03 |
| MM-09-02 | S | M | Organization admin console and member lifecycle | Role policy and audit tests for org create/invite/remove | MM-09-01 |
| MM-09-03 | S | M | SSO OIDC/SAML integration and domain verification | Secure flow tested against test identity provider | MM-09-02 |
| MM-09-04 | S | M | SCIM provisioning/deprovisioning adapter | Idempotency, rate limiting and revoked access verified | MM-09-03 |
| MM-09-05 | S | S | Admin policies and default meeting restrictions | Meeting rules inherited with authorized overrides only | MM-09-02 |
| MM-09-06 | S | S | Tenant-aware audit log and export | Immutable or tamper-evident records, scoped export tested | MM-09-02 |
| MM-09-07 | S | S | Data retention policy and export/delete workflow | Policy applied to chats, recordings and transcripts | MM-09-06 |
| MM-09-08 | A | S | Enterprise tenancy and compliance architecture review | Trust boundaries, regional and incident risks documented | MM-09-07 |
| MM-09-09 | S | M | Calendar provider OAuth and invitation integration | Minimum scopes, token safety and update sync tested | MM-09-01 |
| MM-09-10 | S | S | Public API keys, quotas and webhook signatures | Revocation, idempotency and verification tests | MM-09-05 |
| MM-09-11 | S | S | Webhook retries and delivery audit | Backoff, deduplication and dead-letter behavior visible | MM-09-10 |
| MM-09-12 | C | S | Enterprise onboarding, security questionnaire package | Evidence-based security answers; no unearned certification | MM-09-08 |

## G10 — Mobile applications and desktop strategy

**Prerequisite:** G04  
**Gate to proceed:** Supported mobile platforms reliably join and use core meeting flows; desktop only if justified.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-10-01 | C | S | Mobile/desktop research and feature parity scope | Prioritized workflows and supported-device matrix | G04 |
| MM-10-02 | S | M | React Native shared auth and contracts setup | App builds with known versions and no embedded secrets | MM-10-01 |
| MM-10-03 | S | M | LiveKit React Native AV meeting integration | Android/iOS real join, publish, subscribe verified | MM-10-02 |
| MM-10-04 | S | S | Mobile camera/microphone/permission UX | Denials, route changes, Bluetooth and lifecycle tested | MM-10-03 |
| MM-10-05 | S | M | Mobile screen share and background restrictions | OS-specific capabilities documented and tested | MM-10-03 |
| MM-10-06 | S | S | Mobile chat, hand raise and meeting controls | Contract compatible with web and reconnect tested | MM-10-03 |
| MM-10-07 | S | S | Deep links and push notifications | Join invitations secure and expired links rejected | MM-10-02 |
| MM-10-08 | S | S | Mobile release signing, CI and crash reporting | Test build pipeline with private signing credentials | MM-10-03 |
| MM-10-09 | C | S | Desktop packaging decision review | Web/PWA versus native utility value and cost documented | MM-10-01 |
| MM-10-10 | S | M | Optional desktop app/PWA launch flow | Only if approved; desktop join/device/screen share pass | MM-10-09 |

## G11 — Monetization, product analytics and customer integrations

**Prerequisite:** G03+G07  
**Gate to proceed:** A trial organization can subscribe, receive invoices, view usage and access allowed features reliably.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-11-01 | C | S | Design pricing hypotheses and fair-use policies | Tier grid lists limits, viewer-minutes and overages | G07 |
| MM-11-02 | C | S | Billing provider versus open-source engine decision | Compare payment compliance, complexity and recurring fees | MM-11-01 |
| MM-11-03 | S | S | Usage metering event schema | Counts room time, speaker usage, viewer-minutes and AI spend | MM-11-02 |
| MM-11-04 | S | M | Plan entitlement and quota enforcement | Limits enforced on backend with denial explanations | MM-11-03 |
| MM-11-05 | S | M | Billing checkout and webhook state reconciliation | Verified signatures, idempotent events and retries | MM-11-04 |
| MM-11-06 | S | S | Customer invoices, tax data flow and payment portal | Customer sees correct invoices without card handling in app | MM-11-05 |
| MM-11-07 | S | S | Cancel, downgrade, grace period and refunds states | Documented state transitions and automated tests | MM-11-05 |
| MM-11-08 | S | S | Product analytics and consent configuration | Privacy policy and opt-out behavior tested | MM-11-03 |
| MM-11-09 | S | S | Email notifications and transaction templates | Retries, unsubscribe where required, no token leaks | MM-11-05 |
| MM-11-10 | S | S | Usage dashboard, budget alerts and abuse limits | Metrics match metering ledger and alert triggers | MM-11-04 |
| MM-11-11 | C | S | Support/help center and status-page content | User troubleshooting, escalation and incident template | MM-11-01 |
| MM-11-12 | S | S | Integration API docs and sample client | Versioned examples work on a nonprod sandbox | MM-11-03 |
| MM-11-13 | A | S | Review billing and tenancy fraud scenarios | Payment/replay/overage and privilege risks dispositioned | MM-11-07 |

## G12 — Production security, quality, SRE and operations

**Prerequisite:** G04+G07  
**Gate to proceed:** Security review, deploy/recovery, observability, quality and accessibility signed off for production.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-12-01 | C | S | Define SLOs, error budgets and launch service tiers | Measurable AV join and event quality targets | G07 |
| MM-12-02 | S | M | Production Infrastructure-as-Code plan | Reproducible environments, no hardcoded secrets | MM-12-01 |
| MM-12-03 | S | M | Staging and production CI/CD with approvals | Rollback, protected environments and image signing tested | MM-12-02 |
| MM-12-04 | S | S | Central metrics, tracing and log redaction | Dashboards and traces cover core end-to-end flow | MM-12-02 |
| MM-12-05 | S | S | Alerting for media, API, broadcasts, storage and spend | Alerts tested; defined responders and severities | MM-12-04 |
| MM-12-06 | S | S | Backup and point-in-time restore tests | Documented restoration time and verified consistency | MM-12-02 |
| MM-12-07 | S | M | Tenant isolation and security regression suite | Automated negative authorization tests across services | MM-12-03 |
| MM-12-08 | S | S | Dependency, container and secret scanning | CI blocks critical findings and produces SBOM | MM-12-03 |
| MM-12-09 | A | M | Independent threat-model review of implemented code | Prioritized findings with verified remediation evidence | MM-12-07 |
| MM-12-10 | S | S | Rate limit, DDoS, CAPTCHA and abuse protections | Join storm and spam simulations meet targets | MM-12-07 |
| MM-12-11 | S | M | Browser/mobile end-to-end test automation | Core joining, device, screen share, moderator flows run | MM-12-03 |
| MM-12-12 | C | S | Accessibility manual audit and acceptance matrix | Screen reader and keyboard issues documented and triaged | MM-12-11 |
| MM-12-13 | S | S | Performance budget and web bundle optimization | Measured startup, CPU/network and device memory | MM-12-11 |
| MM-12-14 | S | S | Data privacy/consent/retention integration tests | Delete/export/recording permissions tested | MM-12-07 |
| MM-12-15 | C | S | Incident response, on-call and runbook drafts | Severity matrix and rollback exercise schedule | MM-12-05 |
| MM-12-16 | S | M | Disaster-recovery and failover game day | Recovery/availability evidence and known limitations | MM-12-06 |
| MM-12-17 | A | S | Release candidate architecture readiness review | Open risks and go/no-go signed off by responsible human | MM-12-09 |
| MM-12-18 | C | S | Legal and compliance evidence checklist | No unsupported SOC2/HIPAA/GDPR claims; counsel review plan | MM-12-14 |

## G13 — Beta pilots, commercial launch and ongoing improvement

**Prerequisite:** G12 (and G08 for 100K promise)  
**Gate to proceed:** Approved public release has real customers, support, rollout controls and evidence-backed capacity claims.

| ID | Lead | Size | Work order | Acceptance evidence | Depends on |
| --- | --- | --- | --- | --- | --- |
| MM-13-01 | C | S | Write beta recruitment, support and feedback plan | Defined pilot cohort and measurable success criteria | G12 |
| MM-13-02 | S | S | Feature flags, rollout rings and kill switches | Safe staging-to-beta-to-production promotion | MM-13-01 |
| MM-13-03 | C | S | Prepare product onboarding and FAQ | Users can create/join first meeting without developer help | MM-13-01 |
| MM-13-04 | C | S | Document transparent product limits and comparisons | Only tested features and capacity claimed | MM-13-01 |
| MM-13-05 | S | S | Release observability and usage funnel dashboards | Signup, join, quality and conversion measurable | MM-13-02 |
| MM-13-06 | C | S | Beta feedback triage and roadmap revision | Categorized failures with severity and ownership | MM-13-01 |
| MM-13-07 | S | M | Fix pilot defects and meet release acceptance tests | High severity problems resolved or launch blocked | MM-13-06 |
| MM-13-08 | C | S | Pricing page, terms/privacy and support contacts | Owner/legal-approved wording and payment disclosures | MM-13-04 |
| MM-13-09 | A | S | Final multi-service risk and go/no-go review | Security, data, load, cost and operational risks assessed | MM-13-07 |
| MM-13-10 | C | S | Publish post-launch reliability and product iteration plan | Quarterly improvement, feedback cadence, ownership | MM-13-09 |

## Maintaining this backlog

- Keep one source of truth: change this file in a reviewed PR. Create individual GitHub issues for **the next sprint only**; avoid opening 178 unprioritized issues at once. Phase epics can link to this inventory.
- Update task state in tracked issues with code/test evidence; do not silently alter completed tasks. Avoid two agents editing the same files simultaneously.
- Use [Credit policy](CODEX_CREDIT_POLICY.md), [AGENTS.md](../AGENTS.md), [Definition of done](DEFINITION_OF_DONE.md) and [Security](SECURITY_PRIVACY.md).
- An external service/SDK can be evaluated without copying its entire source; honor every license and notice.
- 100K viewer performance is a **load-test gate**, not a mere feature flag.

~~~~

---

## docs/CODEX_CREDIT_POLICY.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/CODEX_CREDIT_POLICY.md  
Blob SHA: ef93839bf4354d1ac82065394cc4c672fbfaaead

~~~~markdown
# Codex credit-saving operating policy

**Goal:** Spend Sol and Astra capacity only on high-value work that can be verified. Do not assume a fixed token or credit cost per message: cloud usage depends on model, scope, context and effort. Check ChatGPT **Settings → Usage** for remaining Work/Codex allowance and resets. Codex and Work share that allowance.

## Model routing rules

1. **Chat GPT-6 (C):** First write task spec, test cases, API contract, copy, docs, comparison, mock data or a small isolated code draft here. This is planning/output, not proof that code runs.
2. **Codex GPT-6.1 Sol (S):** Default repository engineer. Use for focused implementation, package integration, lint/tests, CI and conventional bugs. Begin at Standard speed + Low or Medium reasoning; increase only if needed.
3. **GPT-6 Astra (A):** Use for one difficult decision/failure at a time: distributed SFU/CDN architecture, role escalation attack surfaces, race conditions, multi-service outage or unresolvable Sol bug. Provide failing test/logs and a precise question. Ask for design review before broad code changes.
4. **Human approver:** Licenses, commercial contracts, money, compliance claims, production credentials and releases require explicit decision. Agents may prepare recommendations, not silently approve.

### Hard caps per coding work order

- **One issue, one deliverable, one branch/PR**. Typical target one focused user-visible vertical slice or one test suite.
- Prepare required file paths, behavior, acceptance tests and **out-of-scope** first.
- No 'build my complete Zoom competitor' prompts. Break large tasks into no more than a few adjacent files/services per PR where practical.
- Stop if unplanned work appears, there are missing secrets/accounts, deployment cost is unknown, or a maintainer decision is necessary.
- Avoid unnecessary whole-repository prompts: quote relevant files, short prior decisions and current acceptance criteria. Let Codex inspect the minimum tree it needs.
- Never run parallel agents touching the same files or schema migrations.
- Do not retry the identical failing request repeatedly. First collect failure evidence, then adjust requirements or escalate to Astra.
- No paid 10K/100K load testing or production operations without explicit owner approval and a safe shutdown/teardown plan.
- Record model used and approximate allowance/credit change **if available**. Do not invent an exact quote.

## Escalation ladder

1. Chat drafts spec + negative tests.
2. Sol implements, runs tests, reports diff.
3. If failure: Sol performs **one focused diagnosis** with stack trace and minimal repro.
4. If still blocked due to architecture/security/concurrency: Astra handles the **specific blocker**, not the whole project.
5. Sol integrates Astra's reviewed fix and tests; human approves risky changes.

## Suggested cut/paste prompt for Chat

> For task [ID] in docs/TASK_BACKLOG.md, create a concise implementation specification. Identify exact components to reuse, files/APIs to touch, security and license concerns, 5 positive and negative test cases, measurable acceptance conditions and explicit out-of-scope items. Return the smallest possible deliverable; don't claim execution.

## Suggested cut/paste prompt for Sol in Codex

> Read AGENTS.md and task [ID] in docs/TASK_BACKLOG.md. Inspect the current repository, not imagined files. Implement ONLY this task using the approved, licensed stack. First give a short scope and acceptance plan. Prefer mature dependencies; do not rewrite media engines. Keep changes to one reviewable PR. Add tests for both success and unauthorized/failure cases. Run available build, type, lint and tests; report actual output, changed files, dependencies/licenses and known gaps. Do not run paid infrastructure without approval. Stop on unresolved legal, credential or budget decisions.

## Suggested cut/paste prompt for Astra in Codex/Work

> Review task [ID] with these exact files, failing tests/logs and approved architecture decisions. You are a senior reviewer, not the primary feature implementer. Identify root cause, alternatives, security/latency/cost risks, and recommend the smallest safe change with a testable proof. Do not rewrite unrelated modules or claim load capacity without measured evidence. Produce an ADR/risk summary and a scoped follow-up task for Sol. Only implement a fix if the issue explicitly requires it.

## Budget dashboard to maintain in issues/PRs

| Field | Example |
| --- | --- |
| Task ID | MM-04-02 |
| Assigned lane | Sol |
| State | Ready / In progress / PR / Tested / Released |
| Intended verification | Token escalation rejected by server |
| Model / effort / speed | GPT-6.1 Sol / Medium / Standard |
| Spend signal | Manual before/after usage (if available) |
| Result | PR URL, test logs, remaining blocker |
| Escalation needed? | No / Astra on specific failure |

If Chat/Work/Codex model access changes, use the nearest available equivalent with the same **role**, but never assume this project document grants account entitlements.

## Using Chat for actual code generation

Chat can produce complete **small, isolated files** such as TypeScript types, Zod schemas, pure validation helpers, mock fixtures, unit tests, UI components, starter templates, SQL migrations and sample SDK clients. Ask for specific inputs/outputs and tests, then have Sol integrate and **execute** those tests. This often reduces Sol's exploratory work. Chat should not assert that a generated module compiles, is secure, or integrates with the current repository unless it has actually inspected and validated it. If Chat has permission to commit a patch via the connected GitHub integration, still require normal review/CI before considering it done.

~~~~

---

## docs/CODEX_TASKS.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/CODEX_TASKS.md  
Blob SHA: a879040a3b51b68939e923c28aebf6ac3dbd47c0

~~~~markdown
# Codex work orders — predictable, credit-conscious development

**Always read [AGENTS.md](../AGENTS.md).** These work orders explicitly prevent broad, expensive prompts like “build Zoom completely”. Do not run all tasks in parallel without reviewing dependency gates.

## Work order A: audit only (do this first)

> Inspect the repository. Do not modify files or install packages. Report current implemented vs planned features. Verify upstream repo versions/licenses and their exact package terms. Compare livekit-examples/meet, LiveKit Server/Components/Egress, Keycloak, Centrifugo, Excalidraw, Yjs, FullCalendar and broadcast options. Classify each requirement as ALREADY IMPLEMENTED, REUSE, CUSTOM BUILD or DEFER. Propose an ADR, minimal MVP dependency list, test plan, cost assumptions and specific files for the next PR. Record all unknowns. Stop and request maintainer approval for licensing/provider decisions.

**Acceptance:** evidence-backed, no code changes, no false status claims.

## Work order B: first skeleton (only after owner chooses code license)

> Implement only the smallest testable Next.js/TypeScript monorepo skeleton for a two-person meeting. Follow approved architecture, avoid duplicating LiveKit components, pin dependencies, add .env.example without secrets, lint/type-check/test scripts, a real local-development README section, and CI. Do not create apps/mobile, AI, billing, large events or empty microservices yet. Run install/build/test and report outputs.

**Acceptance:** new developer follows exact local setup, sees a working page and test output.

## Work order C: secure join flow

> Add secure meeting create/join for two browser users and server-minted, short-lived LiveKit grants. Include host/guest roles with deny-by-default role elevation, AV controls, device permission handling, screen share, and basic reconnection tests. Do not add large-event broadcast mode. Write authorization tests and a minimal threat model update.

**Acceptance:** live two-browser smoke test; unauthorized self-promotion rejected.

## Work order D: collaboration without reinvention

> Evaluate and integrate only approved chat transport and UI controls, preserving persistent storage, authorization, moderation, rate limiting and deterministic message ordering. Reuse approved packages, avoid wholesale merging of another chat application. Add tests and document load assumptions. Implement one vertical slice only.

**Acceptance:** no cross-room leakage, bounded fanout, reproducible tests.

## Work order E: large-event proof of concept

> Build a bounded LiveKit speaker stage and an isolated broadcast adapter for one approved CDN/broadcast provider. Add streaming state and audience join flow using signed access. Keep Q&A/raise-hand control separate. Document latency difference, provider quotas, output costs, consent and known limitations. Test at small scale; don't market 100K.

**Acceptance:** real stage-to-viewer playback and failure/recovery trace, recorded billing assumptions.

## Work order F: scale validation

> Design a staged load-test plan 1K -> 10K -> 50K -> 100K real concurrent viewers, distinguish API/WebSocket synthetic load from actual media playback, quantify join bursts, chat rate, buffering, errors, region mix and costs. Prepare an execution budget and ask before any paid load run.

**Acceptance:** test harness, metrics schema and budget approval; no fabricated results.

## Standard report after each task

1. Intent and scope completed.
2. Files changed and upstream licenses.
3. Tests run with pass/fail and evidence.
4. New env vars, costs, secrets or provider steps.
5. Risks, known missing parts, next single work order.

## Stop conditions

Stop rather than guess when owner licensing is undecided, destructive data migrations are needed, a paid cloud API needs approval, or performance claims lack measurements. Never run unbounded paid load or AI processing from an unspecified budget.

~~~~

---

## docs/FIRST_SPRINT.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/FIRST_SPRINT.md  
Blob SHA: 68cf59d2a38761ba5fdd2336eb4fa330c6c6659c

~~~~markdown
# First sprint: low-cost sequence (no product code exists yet)

## Sprint objective

Make project decisions explicit and prepare a single, runnable Phase 1 prototype without burning Astra credits on ordinary implementation. The **repo currently has docs only**; beginning code requires owner agreement on original-code licensing/contribution terms.

| Order | Backlog task | Lead | Output | Stop condition |
| --- | --- | --- | --- | --- |
| 1 | MM-00-04 + MM-00-07 | Chat | One-page launch segment/MVP and license options | Owner must choose license terms |
| 2 | MM-01-01 + MM-01-02 + MM-01-03 | Chat | Current repo inventory and exact upstream reuse/NOTICE table | License/version unknown |
| 3 | MM-01-06 + MM-01-07 | Chat | First OpenAPI/event contract and domain model | Unresolved identity/tenant model |
| 4 | MM-01-04 + MM-01-05 | Astra | Narrow review of stage/broadcast and control-plane architecture | Human must approve cost/architecture |
| 5 | MM-02-01 | Sol | Small Next.js/TS skeleton PR; clean build | No license approval, cannot use external code |
| 6 | MM-02-03 + MM-02-04 + MM-02-05 | Sol | Validated env schema, lint and tests | Missing provider secrets; use safe mock/test setup |
| 7 | MM-02-10 | Chat | Updated developer guide tested against actual scripts | PR missing runnable commands |
| 8 | MM-03-01 then MM-04-01 + MM-04-02 | Sol | Actual safe login/token issue and two-browser meeting | Unauthorized media grant / nonpassing tests |

**Do not start all eight orders together.** Limit to one active code PR, plus an independent documentation/research task if needed. Only assign Astra in order 4 if the design genuinely contains unresolved risks; otherwise keep it as a later optional review.

## Owner's immediate decisions

- Original project license/contributor policy, final product name and copyright owner.
- Available development budget and whether any paid managed video provider is authorized.
- First target customer segment, region and acceptable event latency.
- Whether launch first focuses on normal meetings or a livestream-led product.

## Next milestone proof

A new contributor clones the repo and follows exact setup instructions; two separate browsers can create/join a meeting with real A/V and screen share, role restrictions and tests. Anything less remains a prototype in progress.

For all later work orders see [the full backlog](TASK_BACKLOG.md) and [credit policy](CODEX_CREDIT_POLICY.md).

~~~~

---

## docs/ISSUE_INDEX.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/ISSUE_INDEX.md  
Blob SHA: ac7bcb037ec912e223d5aa9894cae9908c6bb741

~~~~markdown
# GitHub phase-issue index

**178 planned work orders in 14 phase epics.** Each phase issue contains a full checkbox inventory, leads (C/S/A), dependencies and acceptance criteria. These checklist entries are not yet implemented. Developers should create individual implementation issues only when a near-term task is ready; link the corresponding epic and task ID.

| Gate | Work package | Items | GitHub epic |
| --- | --- | ---: | --- |
| G00 | Product, ownership and governance | 10 | [Issue #7](https://github.com/arunabanarjee32-bit/google-meet/issues/7) |
| G01 | Architecture, reuse and interface contracts | 12 | [Issue #8](https://github.com/arunabanarjee32-bit/google-meet/issues/8) |
| G02 | Monorepo, CI and local developer experience | 12 | [Issue #9](https://github.com/arunabanarjee32-bit/google-meet/issues/9) |
| G03 | Accounts, organizations, scheduling and core APIs | 12 | [Issue #10](https://github.com/arunabanarjee32-bit/google-meet/issues/10) |
| G04 | Reliable real-time video meetings | 16 | [Issue #11](https://github.com/arunabanarjee32-bit/google-meet/issues/11) |
| G05 | Collaboration, moderation and accessible workflows | 13 | [Issue #12](https://github.com/arunabanarjee32-bit/google-meet/issues/12) |
| G06 | Recording, playback, captions and optional AI | 12 | [Issue #13](https://github.com/arunabanarjee32-bit/google-meet/issues/13) |
| G07 | Webinar and 100K-event product architecture | 16 | [Issue #14](https://github.com/arunabanarjee32-bit/google-meet/issues/14) |
| G08 | 100K load, security and resiliency validation | 12 | [Issue #15](https://github.com/arunabanarjee32-bit/google-meet/issues/15) |
| G09 | Enterprise security, administration and integrations | 12 | [Issue #16](https://github.com/arunabanarjee32-bit/google-meet/issues/16) |
| G10 | Mobile applications and desktop strategy | 10 | [Issue #17](https://github.com/arunabanarjee32-bit/google-meet/issues/17) |
| G11 | Monetization, product analytics and customer integrations | 13 | [Issue #18](https://github.com/arunabanarjee32-bit/google-meet/issues/18) |
| G12 | Production security, quality, SRE and operations | 18 | [Issue #19](https://github.com/arunabanarjee32-bit/google-meet/issues/19) |
| G13 | Beta pilots, commercial launch and ongoing improvement | 10 | [Issue #20](https://github.com/arunabanarjee32-bit/google-meet/issues/20) |
| **Total** | | **178** | |

## Existing kickoff issues

- [#1 Licensing and contributor policy](https://github.com/arunabanarjee32-bit/google-meet/issues/1) — blocks upstream code import and substantive source contributions.
- [#2 Upstream license/technology audit](https://github.com/arunabanarjee32-bit/google-meet/issues/2) — reuse-first decision.
- [#3 Interactive vs large-event architecture](https://github.com/arunabanarjee32-bit/google-meet/issues/3) — control plane, media strategy.
- [#4 Working two-browser meeting MVP](https://github.com/arunabanarjee32-bit/google-meet/issues/4) — only after foundation approvals.
- [#5 Real 100K capacity and test-cost plan](https://github.com/arunabanarjee32-bit/google-meet/issues/5) — no unsanctioned paid load tests.
- [#6 Security and privacy threat model](https://github.com/arunabanarjee32-bit/google-meet/issues/6) — recurring security work.

## Guidelines

1. The [detailed task inventory](TASK_BACKLOG.md) is the source of truth for IDs and assignment, not chat history.
2. **Chat GPT-6** handles specs, documentation, test cases and self-contained source-code drafts/components when requested. **Codex GPT-6.1 Sol** integrates and verifies code in the actual repo. **Astra** focuses on exceptionally hard design/debugging and security/scalability reviews. All three may participate in a task, but there is only one assigned lead for spending control.
3. Keep a PR reviewable; avoid coding against guessed requirements or creating fake tests/performance results.
4. Legal, privacy, budgets, production credentials, acceptance and release need human sign-off.
5. Use [Credit policy](CODEX_CREDIT_POLICY.md) and [First sprint](FIRST_SPRINT.md) to plan the next task.

~~~~

---

