# MegaMeet continuation handoff

**Updated:** 2026-11-15

This file is intentionally short. Read it before redoing repository research.

## Current repository state

- Main remains documentation/governance only.
- There is no runnable MegaMeet application, package.json, lockfile, test suite or GitHub Actions workflow.
- There were no pull requests before the current audit branch.
- Issues #1-#20 are the active planning/epic set.
- The authoritative delivery plan remains docs/TASK_BACKLOG.md with 178 work orders.

## Current blocker

**Issue #1 / MM-00-07:** the owner has not selected the license and contributor policy for original MegaMeet code.

AGENTS.md, CONTRIBUTING.md and docs/LICENSING.md say substantive product-code/source import should not begin before that decision.

Do not silently bypass this gate.

## Foundation research result

Proposed exact two main repositories:

1. LiveKit Meet
   - https://github.com/livekit-examples/meet
   - reviewed commit c3a16bdc7be03e201615779e8f2f6ee61d41ec91
   - Apache-2.0 repository license
   - use as UI/reference foundation only
   - replace demo token/recording authorization

2. LiveKit Server
   - https://github.com/livekit/livekit
   - v1.13.11
   - commit 385aa40f9292fe1db8caad87301e4b285b7c198a
   - Apache-2.0 with LICENSE + NOTICE
   - use as external SFU/media infrastructure

Serious alternatives reviewed: Jitsi Meet and BigBlueButton. Keep them as reference systems; do not stack their conferencing engines with LiveKit.

Full evidence: docs/FOUNDATION_AUDIT_2026-11-15.md

Decision proposal: docs/DECISIONS/0003-livekit-foundations.md

## Security finding to preserve

Do not reuse LiveKit Meet's app/api/connection-details route unchanged.

The reviewed route authenticates nobody and grants every caller room join + publish + data publish + subscribe based on caller-provided room/name/metadata.

MegaMeet needs a server-owned meeting-grant endpoint with tenant checks, invitation/admission checks, server-derived role/capabilities, short TTL, rate limits, audit events and negative authorization tests.

The upstream recording start/stop routes are also explicitly unauthenticated demonstration code.

## Dependency caveat

The reviewed LiveKit Meet package uses @livekit/krisp-noise-filter 0.4.6. npm marks its license as “SEE LICENSE IN https://livekit.io/legal/terms-of-service”.

Do not add it to MegaMeet until separately reviewed/approved.

## Architecture direction

- Keep the modular monorepo.
- Start with apps/web plus only real shared packages.
- Do not scaffold empty microservices.
- Keep product identity/roles/meetings canonical in MegaMeet.
- Use short-lived server-issued LiveKit grants.
- Interactive meetings: LiveKit SFU.
- Large event: bounded LiveKit presenter stage -> Egress -> managed broadcast/CDN.
- Audience interaction plane remains separate from video playback.
- Do not claim 100K until real playback/load and budget/quota gates pass.

## Next task

First: resolve **MM-00-07 / issue #1** with a written owner decision.

After G00/G01 approval, the first product-code task is **MM-02-01**: create the minimal Next.js/TypeScript monorepo and reproducible build, without copied LiveKit Meet source or unapproved optional dependencies.
