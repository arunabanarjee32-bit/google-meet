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
