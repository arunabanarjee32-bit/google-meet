# MegaMeet source-document snapshot — Part 4 of 5

Captured 2026-11-16; source: main branch (tree dd2284f26f7822c086bef5070839364e42c01d8f). This preserves development, quality, cost and original architecture decision records, as reference-only content.

## docs/COST_MODEL.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/COST_MODEL.md  
Blob SHA: 5105b12cd083053ffd82f59b723f2e986e61230d

~~~~markdown
# Early operating-cost model: assumptions, not price quotes

**No infrastructure bill has been measured for this repository.** Avoid promising cheap 100K meetings without explicit video-distribution pricing and capacity commitments. Reassess published vendor prices/limits before procurement.

## Cost drivers to track

| Driver | Unit | Questions |
| --- | --- | --- |
| Interactive stage | speaker-hour, SFU CPU/network | Concurrent publishers, simulcast, regional routing, TURN relay |
| Broadcast delivery | viewer-minute, delivered GB | Bitrate/ABR ladder, concurrent viewers, regional egress |
| Transcoding | input hour, rendition minute | Composite stage, resolution, replay encoding |
| Real-time interaction | connections, messages/sec | Join spikes, broadcasts, Redis, broker traffic |
| Database and storage | provisioned/used GB, IOPS | Presence data boundaries, logs, meeting records |
| Recording | stored GB-month, egress | Consent, retention, export and playback |
| AI | audio minute / token / GPU-hour | Captions, translation, summaries |
| Reliability | environments, regions, support | Observability, failover, DDoS mitigation, on-call |
| Engineering | development & maintenance effort | Dependency upgrades, security review, incident response |

## Bandwidth illustrations

At 100K viewers averaging 1 Mbps for one hour, network delivery is approximately 45 decimal TB. At 2 Mbps, about 90 TB. This is **not** the origin bandwidth if a CDN distributes it, and it is **not** a complete provider bill.

For estimation:

- Total viewer-minutes = concurrent viewers × average watched minutes (adjust for churn).
- Delivery GB (decimal) ≈ viewer count × average watched seconds × mean Mbps / 8,000.
- Billing amount = actual vendor price sheet for relevant delivery unit, region, quality and service tier × measured usage, plus fixed/other variable charges.
- Add cost sensitivity for 25%, 50%, 100% of attendees and for high/low-resolution variants.

Do not infer that a single flat-rate VPS can directly deliver 100 Gbps. Avoid quoting a vendor price unless the date, SKU and contractual source are recorded.

## Cost review checklist for each milestone

1. Baseline spending during two-person test.
2. 100/1K viewer cost per viewer-hour and operational complexity.
3. 10K trial with actual media replay/playback, billed egress and monitoring.
4. 100K forecast and reserve fund before test; provider quota approval.
5. Alerts and kill switches for out-of-control traffic and AI inference bills.
6. Unit economics for free, paid and enterprise plans based on realistic usage.

A useful experiment compares managed broadcast to a self-hosted origin + contracted CDN with total engineering, reliability and support costs included. A lower per-GB estimate alone is not sufficient.

~~~~

---

## docs/DEVELOPMENT.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/DEVELOPMENT.md  
Blob SHA: 84f3cfef8167b0cf5303be0c6b10a3b000151560

~~~~markdown
# Developer quickstart (project currently documentation-only)

There is **no runnable MegaMeet application yet**. Do not run commands from tutorials that assume an `apps/web` folder exists. Start from [README](../README.md), then review [Contributing](../CONTRIBUTING.md) and [Roadmap](ROADMAP.md).

## Prerequisites for the future Phase 1 prototype

- Node.js LTS and a single documented package manager/version.
- Git and a code editor.
- A test LiveKit development environment with **no production secrets**.
- Docker or documented locally hosted dependencies only if required by the first vertical slice.
- A compatible browser, webcam and microphone or test devices.

The approved Phase 1 pull request must add exact versioned setup commands, scripts, a redacted `.env.example`, and a small smoke-test guide. Until it exists, these are requirements, not instructions.

## Expected developer flow once code exists

1. Check out a branch corresponding to a scoped issue.
2. Install using the lockfile and documented tooling.
3. Copy `.env.example` to a local untracked environment file and provide development-only credentials.
4. Start minimal dependencies and the web app; join from two real browsers.
5. Run lint, type checks, unit/integration tests and security scans.
6. Submit the PR template with actual command output and dependency changes.

## Proposed first tests

- Secure meeting-create and join endpoint contracts.
- Expired/invalid/token-for-other-room rejection.
- Roles: viewer cannot publish or promote self; host controls explicitly authorized.
- Browser device permission denied, successful A/V and screen share.
- Rejoin after network drop without granting stronger privileges.
- No cross-tenant record, chat or recording access.

## Architecture decision notes

Use [AGENTS.md](../AGENTS.md) for AI coding instructions and [Codex work orders](CODEX_TASKS.md) for small tasks. Do not create an elaborate mobile/backend microservice forest before a working meeting prototype. All infrastructure environments must have a tested teardown procedure to avoid runaway cost.

~~~~

---

## docs/DEFINITION_OF_DONE.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/DEFINITION_OF_DONE.md  
Blob SHA: fda30a97ba73a54ba12b6174d75745fcfd2269fd

~~~~markdown
# Definition of done and release gates

A feature is **not** complete because an AI coding agent wrote files or a demo screenshot looks good.

## Every implementation PR

- Linked issue and scope/acceptance criteria.
- Reuse and license review for new dependencies; pinned versions, notices where required.
- Compiles/builds using documented local steps and contains no secrets.
- Automated tests added/updated where appropriate and **actually executed**; failures reported.
- Authorization and tenant/room isolation considered and tested for sensitive paths.
- UI accessibility/keyboard and responsive behavior checked for impacted flows.
- Error handling, reconnection/fallback and observability included for real-time features.
- Documentation, config examples and deployment implications updated.
- Reviewer understands rollback/data migration and operational costs.

## Media feature gates

- Actual multi-device A/V and screen-share tests, not mocked interfaces alone.
- Join/rejoin, permission denied, device switch, degraded network and browser compatibility.
- Permissions tested for host, presenter, attendee and viewer.
- Recording consent and notification verified when applicable.

## Scale and service gates

- Define concurrency, geographic coverage, workload and quality targets *before* test.
- Record real media client metrics distinct from simulated API/chat connections.
- Report buffering, rejoin, mean/p95/p99 latency, failed joins, bill estimates and resource saturation.
- Test failure scenarios and reconnect storms; instrument dashboards and alerts.
- Security/privacy and provider quota reviews sign off on the claimed scale.

## No unsupported claims

Mark untested features **planned**, **prototype**, **tested in staging**, or **production-verified** with links to evidence. Never label "supports 100K" without a documented, reproducible, real-video test and approved operational budget.

## Documentation only contributions

Fixing docs counts as done when links are valid, guidance is coherent with the approved architecture, and reviewers have checked important technical/legal statements.

~~~~

---

## docs/DECISIONS/0001-modular-monorepo.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/DECISIONS/0001-modular-monorepo.md  
Blob SHA: 9963b94daba88057227a9f4941220ca7312dbcb0

~~~~markdown
# ADR-0001: Modular monorepo, external engines

**Status: Proposed — requires owner/engineering acceptance**  
**Context:** We want a distinct commercial product with collaboration, 100K audience events and cost-controlled development. There are public Zoom-like apps and multiple incompatible media stacks.

## Decision

Build and maintain original UI, APIs, domain models, administration, AI integration and orchestration in **one main monorepo**, with packages/services deployed independently as warranted. Integrate vetted media/identity/collaboration projects through public APIs and SDKs. Do not combine full competing conferencing apps (e.g. Jitsi + BigBlueButton + LiveKit) into one codebase.

## Alternatives

- Fork one complete app forever: fast demo, potential coupling to upstream structure and limits.
- Multiple independent application repos: deployment independence, more coordinated development/CI overhead.
- Invent all subsystems: maximum theoretical control, prohibitively high security/performance maintenance burden.

## Consequences

**Pros:** shared types, consistent UX, focused Codex tasks, easier issue onboarding and targeted upgrades.  
**Cons:** monorepo tooling and ownership boundaries need care; runtime systems still require production orchestration; third-party vendors remain dependencies.

## Validation

Revisit if deployment/release complexity demonstrably exceeds benefits, or if regulatory isolation requires repository boundaries. Keep contract versioning and smoke tests regardless of repository layout.

**Related:** [Architecture](../ARCHITECTURE.md), [Tech stack](../TECH_STACK.md).

~~~~

---

## docs/DECISIONS/0002-interactive-and-broadcast.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/DECISIONS/0002-interactive-and-broadcast.md  
Blob SHA: 1450e971b74112df6e860064c10f38e49125aa2d

~~~~markdown
# ADR-0002: Separate interactive meeting from large-event media delivery

**Status: Proposed — requires owner/engineering acceptance**

## Context

A product claiming 100,000 members in "one meeting" can mean 100K simultaneous publishers, or one event with limited speakers and many viewers. These are not interchangeable workloads.

## Decision

Use a LiveKit/WebRTC **interactive meeting path** for ordinary conferences and a **bounded speaker stage** for large events. Export the stage to a separately scalable broadcast/CDN distribution path for audience-only viewers. Chat/Q&A/polls/presence and admission are distinct from video delivery but share the event identity and moderation model.

## Alternatives

- A single gigantic WebRTC room for all attendees: simpler conceptual story, substantially harder and often impractical media fanout at 100K.
- Pure HLS broadcast without stage interactivity: simpler distribution but limited speaker promotion.
- Global WebRTC audience delivery: lower latency but likely higher cost/operational complexity; evaluate if user requirements justify it.

## Consequences and caveats

- Audience members will not all appear as video tiles; they interact through chat, polls and moderated speaker requests.
- Broadcast can lag the live speaker stage; promotion needs audio muting, countdowns and clock-aware UX.
- Egress and a media origin are not substitutes for CDN capacity, admission security or chat infrastructure.
- Test 100K **real video playback**, not 100K synthetic socket connections.

## Open choices

Provider and commercial agreement, maximum stage publishers, audience-latency goal, regions, CDN access control, recording/privacy policies, event limits, fallback path.

**Related:** [100K plan](../SCALABILITY_100K.md), [Cost model](../COST_MODEL.md).

~~~~

---

## docs/DECISIONS/README.md

Original: https://github.com/arunabanarjee32-bit/google-meet/blob/main/docs/DECISIONS/README.md  
Blob SHA: 75b5fd571702321b44d5ec8f581e076c25b2c63a

~~~~markdown
# Architecture decision records

ADRs capture choices rather than treating earlier chats or generated docs as binding engineering law.

| ADR | Decision | State |
| --- | --- | --- |
| [0001](0001-modular-monorepo.md) | Modular monorepo + external engines | Proposed |
| [0002](0002-interactive-and-broadcast.md) | Split interactive and massive-audience delivery | Proposed |

To add an ADR, explain **context, decision, alternatives, consequences, measurable validation, reversibility and approval status**. Mark superseded decisions and link successors, rather than silently editing history. Decisions that involve license choice, privacy or cost require project-owner approval.

~~~~

---

