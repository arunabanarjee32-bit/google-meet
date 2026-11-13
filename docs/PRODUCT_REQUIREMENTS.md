# Product requirements and feature inventory

**Status:** target capabilities, not implemented functionality. Priorities are proposed and must be adjusted after user research. **P0** = first working product, **P1** = competitive core, **P2** = enterprise/advanced, **P3** = later. "Reuse" means integrate a dependency; it does not mean the feature works automatically.

## Roles and permissions

- **Platform operator:** account/platform health, safety, abuse and incident management.
- **Organization administrator:** members, SSO, policies, audit logs and billing.
- **Meeting organizer / host:** schedule, admit, remove, mute, recording/streaming and stage controls.
- **Co-host/moderator:** configured subset of host actions.
- **Speaker/presenter:** publish media and share screen with authorization.
- **Attendee:** join a standard conference with host-controlled media privileges.
- **Broadcast viewer:** watch live content, ask approved questions, chat/poll according to policy; no media publish by default.

Enforce authorization on the server even if a UI button is hidden.

## Feature matrix

| Area | Feature | Priority | Build vs reuse |
| --- | --- | --- | --- |
| Identity | Signup/login, accounts, session management | P0 | Integrate vetted identity provider; custom UX |
| Meetings | Create/join by secure link, lobby, role tokens | P0 | LiveKit SDK + own control API |
| AV | Microphone, camera, device selection, adaptive video | P0 | LiveKit + browser/mobile SDK |
| Meetings | Screen sharing, layouts, participant roster | P0 | LiveKit Components + custom UX |
| Controls | Admit/mute/kick/lock, role-based permissions | P0 | Own policy layer over LiveKit |
| Collaboration | Persistent meeting chat with moderation | P1 | Messaging transport + own storage/moderation |
| Scheduling | Calendar, invites, timezone support | P1 | Reuse calendar UI, integrate provider APIs later |
| Recording | Explicit start/stop consent, storage, playback | P1 | LiveKit Egress + access policy |
| Accessibility | Keyboard/screen reader/captions baseline | P1 | UI/a11y practices and vetted caption service |
| Collaboration | Polls, hand raise, moderated Q&A | P1 | Own domain workflows and realtime events |
| Collaboration | Whiteboard and shared notes | P1 | Excalidraw + Yjs integration |
| Large events | Organizer registration and viewer admission | P1 | Own control plane |
| Large events | Speaker stage + audience broadcast | P1 | LiveKit + Egress + broadcast/CDN |
| Large events | Raise hand -> request -> moderated stage promotion | P1 | Own orchestrator, LiveKit permissions |
| Mobile | Android and iOS application | P2 | React Native LiveKit SDK + custom app |
| Enterprise | Organizations, SSO, policy, audit export | P2 | Keycloak/OIDC + own management layer |
| Enterprise | Retention, legal hold options, region control | P2 | Own data governance + hosting capabilities |
| AI | Consent-based transcript, summary, translation | P2 | Model/agent integrations; human-readable disclosures |
| Business | Payments, plans, usage metering, invoices | P2 | Payment/billing integration |
| Developer | Webhooks, API docs, SDK and integrations | P2 | Own API contracts |
| Advanced | Breakouts, PSTN, SIP, live interpretation | P3 | Evaluate dedicated media integrations |
| Advanced | Virtual backgrounds, intelligent noise removal | P3 | Client SDK/optional model integration |

## User flows to implement

**Small meeting:** sign in (or configured guest join) -> schedule/create -> secure share link -> permissions/device preview -> join -> AV + screen share -> optional recording with visible notice -> end -> access permitted artifacts.

**Large event:** organizer configures capacity and region -> moderator manages limited speaker stage -> viewers join same logical event through independent broadcast delivery -> chat/Q&A/polls traverse scalable interaction plane -> moderator approves viewer request to stage (re-auth + device checks + elevated short-lived permissions) -> viewer returns to audience safely. Broadcast latency may be higher than live speakers; indicate the mode and manage synchronization.

**Enterprise:** organization creates workspace -> SSO setup -> role policies -> meeting defaults -> retention and audit settings -> exported events as authorized.

## Critical acceptance criteria (before claiming MVP)

1. Two users can join a real browser meeting with camera/microphone permission handling.
2. Host tokens are server-issued; unauthorized clients cannot self-promote or access another meeting.
3. Screen sharing, reconnection and device switching work in supported browsers.
4. A repeatable test suite covers permissions, basic API contracts and join flow.
5. Documentation includes environment variables, local setup and known limitations.
6. Recording is off by default and explicitly indicated when enabled.

## Acceptance criteria for 100K events

- The design shows one logical event, bounded stage size and independently scaling distribution.
- Join storms, stream failure, region failover, chat flood, Q&A moderation and promotion are tested.
- Capacity and latency are measured at several tiers with provider quota confirmation.
- Cost, data-transfer assumptions, privacy and anti-abuse measures are reviewed.
- The product never labels a load test of fake websocket connections as proof of successful 100K live-video viewers.

## Feature parity: benchmark, not a claim

Track Zoom, Teams, and Meet user workflows for joining, moderation, scheduling, screen share, recording, captioning, enterprise administration, collaboration, mobile experience and large webinars. Avoid copying proprietary UI or claims that a specific competitor is universally #1. Record verified competitor feature evidence only when making a launch comparison.

See [Definition of done](DEFINITION_OF_DONE.md) and [Roadmap](ROADMAP.md).
