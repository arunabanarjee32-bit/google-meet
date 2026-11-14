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
