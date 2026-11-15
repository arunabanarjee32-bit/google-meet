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
