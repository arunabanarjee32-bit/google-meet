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
