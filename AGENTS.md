# Instructions for Codex and other coding agents

This document is the repository-level operating manual for AI assistants. **Read README, docs/PROJECT_VISION.md, docs/PRODUCT_REQUIREMENTS.md, docs/ARCHITECTURE.md, docs/ROADMAP.md, docs/TECH_STACK.md, docs/LICENSING.md and CONTRIBUTING.md first.**

## Project facts that must not be invented

- MegaMeet is a **working name** for an independently branded meeting/collaboration product; the repo path does not create Google affiliation.
- This repo initially contains **planning documentation only**. Do not claim code, tests, deployments or 100K concurrency already exist unless you can point to verified artifacts.
- 100,000+ applies to **concurrent audience viewers for a single logical event with a bounded active-speaker stage**, not 100K simultaneously publishing video tracks.
- The owner's license for original code is **not yet selected**. Do not import or submit substantive third-party code until licensing/contribution authorization is clear.
- A GitHub public repo or a production-facing README is not evidence of implementation.

## Working method to minimize Codex credits

1. **Inventory first.** Inspect real files, check current implementation and constraints; avoid rewriting working functionality.
2. **Reuse audit.** For every major feature, list mature candidates, exact license/version, integration cost and risks. Prefer packages/services over copying whole applications.
3. **Scope first.** Propose a small milestone, measurable acceptance tests, file paths and a credit/time budget before starting a large feature.
4. **Implement vertically.** One working user flow at a time. No placeholder service forests, fake dashboards or fabricated tests.
5. **Verify visibly.** Run available local tests/linters/builds, report commands, outputs and remaining gaps.
6. **Stop on blockers.** Ask for owner decision on code license, provider credentials, paid vendor commitments, high-impact architecture changes and security/privacy policies.
7. **No secret handling in Git.** Use environment variables, sample .env files without credentials, and appropriate secrets managers in deployment.
8. **Explain the result.** Provide concise diff summary, third-party dependencies added, licensing notes, tests, costs and next discrete step.

## Default proposed stack (NOT pre-approved or installed)

- Primary web app: Next.js/React/TypeScript, building from Apache-2.0 LiveKit Meet where legally vetted.
- AV: LiveKit SDK/Components/Server; Egress for recording and stream output.
- Interactive broadcast: bounded WebRTC speaker stage + separate managed CDN broadcast distribution.
- Realtime interactions: backend event model + scalable transport; evaluate Centrifugo, Valkey and a broker as warranted.
- Identity: OIDC/Keycloak evaluation; PostgreSQL for canonical domain data.
- Whiteboard/state: Excalidraw/Yjs after their package-level license audit.
- Optional later: React Native, captions/Whisper/agents, scheduling, enterprise SSO, billing.

Do **not** silently replace this proposal with a completely different media engine or merge competing conferencing stacks.

## Requirements for any code PR

- Every feature linked to an issue, milestone and acceptance criteria.
- No accidental tenant/room data leakage or unsigned role elevation.
- Recording and AI transcription **opt-in/visible with consent logic**, per policy.
- Use dependency lockfiles, environment schema, tests, structured logging and documented rollback.
- Meet accessibility expectations; never rely on mouse-only controls.
- Include a tested upgrade path and deployment impact when adding stateful services.
- No 100K capability claim without measured actual viewers, quota checks and evidence described in docs/SCALABILITY_100K.md.

## First safe tasks

- Perform license/version audit and draft decisions (no source import).
- Propose minimal skeleton and CI after license decision.
- Implement two-browser secure meeting flow as Phase 1, with tests.
- Add large event mode only after the basic meeting path is reliable.

See [Codex work orders](docs/CODEX_TASKS.md) for copyable scoped assignments.

## Delivery work orders and model assignment

The authoritative **178-task, 14-phase** task breakdown is [docs/TASK_BACKLOG.md](docs/TASK_BACKLOG.md); the master rollout/gates are in [docs/DELIVERY_MASTER_PLAN.md](docs/DELIVERY_MASTER_PLAN.md). Work on one narrow task ID at a time using [docs/CODEX_CREDIT_POLICY.md](docs/CODEX_CREDIT_POLICY.md). **Codex GPT-6.1 Sol is the default implementation lane**; **Astra is an exception/escalation lane**; **GPT-6 in Chat drafts specs and small patches but does not substitute for passing actual tests**. Maintainer approval is mandatory at legal, paid infrastructure, high-risk security and release gates. Do not assign a task to multiple agents concurrently editing the same files.
