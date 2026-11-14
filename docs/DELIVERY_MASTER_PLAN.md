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
