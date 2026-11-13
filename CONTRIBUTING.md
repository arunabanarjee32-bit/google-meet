# Contributing to MegaMeet

Welcome! **MegaMeet is a planned product with architecture documentation, not a finished meeting system.** You should be able to understand the mission without access to any past chats.

## Read before starting

1. [README.md](README.md) — status and high-level overview.
2. [Project vision](docs/PROJECT_VISION.md) — why this product should exist.
3. [Requirements](docs/PRODUCT_REQUIREMENTS.md) — what users should be able to do.
4. [Architecture](docs/ARCHITECTURE.md) — how normal meetings differ from 100K events.
5. [Roadmap](docs/ROADMAP.md) — prioritize milestones.
6. [Tech stack](docs/TECH_STACK.md), [Licensing](docs/LICENSING.md), and [Definition of done](docs/DEFINITION_OF_DONE.md).

## Important: licensing decision is open

The repository owner **has not yet chosen a license for original MegaMeet code**. Please begin with issue discussions, small documentation corrections and architecture/license proposals. Do **not** submit substantive source-code copies or licensed upstream code until the owner sets the contribution/license policy. Public repository access does not imply an open-source license.

## How to propose work

- Search [issues](https://github.com/arunabanarjee32-bit/google-meet/issues) for duplication.
- Create a feature, audit or bug issue that includes **user impact, milestone, reuse candidates, scope, acceptance tests, legal/security considerations, and proposed cost impact**.
- For an architectural choice, write an ADR proposal listing alternatives, consequences, migration/fallback, and tradeoffs.
- Get maintainer alignment on high-risk dependency, public license, privacy, vendor or architecture decisions before coding.

## Pull request process (once source contributions are authorized)

1. Create a focused branch from the current default branch.
2. Keep a PR small and scoped to one issue or vertical slice; don't independently scaffold the whole company.
3. Link the issue; note which tested behavior changed and what did **not** change.
4. Run available lint, type, unit, integration and security checks. If not available yet, say so. Never manufacture green CI results.
5. Include docs updates, architecture decision and changelog note as needed.
6. Preserve upstream notices, lockfiles and exact versions; do not copy unlicensed snippets or secrets.
7. Have a human reviewer approve changes that affect authentication, permissions, recording, data deletion, payments, security or infrastructure costs.

## Code and design principles

- Prefer well-maintained libraries/services for media, identity, realtime messaging and drawing rather than inventing replacements.
- Start with one TypeScript/Next.js app and add services only for proven needs.
- Enforce permissions server-side; keep media provider secrets and API keys off clients.
- Build for accessibility (keyboard and screen readers), localization and poor networks.
- Keep low-latency stage and higher-latency audience state distinct; test transitions and echo handling.
- Use feature flags and migration plans to avoid breaking existing flows.
- Document unsupported browsers, limits and consent requirements.
- Evaluate software supply-chain security and third-party licenses.

## PR template and review

GitHub will populate the checklist in [.github/PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md). Use our [Definition of Done](docs/DEFINITION_OF_DONE.md).

## Communication

Be constructive and specific. Report security problems privately (see [SECURITY.md](SECURITY.md)), never in a public issue with exploit details. No maintainers, support channels, response-time guarantees, or release dates are implied by these documents.
