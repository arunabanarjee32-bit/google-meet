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
| MM-02-08 | S | S | Typed API contract package | Client/server contract compiles with schema validation | M01-06 |
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
