# Security, privacy and abuse-prevention baseline

**Status: requirements and threat model; not an implemented security program.** Security reviews must be conducted on actual code and production deployments.

## Core threats

- Unauthorized entry via guessed/leaked meeting IDs, stolen media tokens and weak guest links.
- Cross-organization data leaks, insecure direct-object reference, role escalation.
- Rogue attendees publishing media, hijacking screen shares or triggering recording.
- Leaked recordings, retention violations, transcript/model data disclosures.
- Join storms, credential abuse, bot swarms, chat spam, message amplification and DDoS.
- WebSocket replay, untrusted webhook payloads, malicious file uploads, XSS/CSRF/SSRF.
- Supply-chain compromise and leaked vendor credentials in CI or commit history.
- Unclear consent for recording, transcript, AI use and third-party processors.

## Required controls

| Area | Required behavior |
| --- | --- |
| Identity | OIDC, secure sessions, optional MFA/SSO, verified tenant boundaries |
| Admission | Unpredictable identifiers, waiting rooms and policies, expiring guest tokens |
| Authorization | Server-side RBAC/ABAC, least privilege, audited promotion and revocation |
| Media | Short-lived scoped LiveKit tokens, TLS/SRTP transport, configured TURN where needed |
| Recording | Off by default; visible consent/notice, scoped storage and playback, expiry |
| Data | Encryption in transit/at rest, retention/delete/export workflow, minimal collection |
| Realtime | Message size/rate limits, authorization for subscriptions, moderator controls |
| APIs | Input validation, parameter authorization, throttles, idempotency, structured audit |
| Secrets | Secrets manager, environment validation, rotation, no tokens in source/console logs |
| Infrastructure | Least-privilege IAM, patching, dependency scans, backups, restoration drills |
| AI | Explicit opt-in, disclosed processors/regions, transcript controls and access logging |
| Clients | Secure headers, CSP as appropriate, safe URL handling and mobile permission UX |

**Do not claim end-to-end encryption.** WebRTC transport encryption and a server-side media SFU/egress can protect transport while still allowing server-side processing; true E2EE requires a separately designed and tested key model and may conflict with server recording/AI.

## Large-event specifics

- Gate viewer access with signed tickets; never let audience tokens publish to the stage.
- Prevent accidental echo when a viewer is promoted from delayed broadcast to real-time speaker.
- Distinguish public attendee count from private user presence records; minimize exported PII.
- Use moderation queues, anti-spam and per-event quota guards for 100K fanout.
- Set hard limits on AI processing, stream transcoding and recordings to control abuse/cost.

## Privacy/product decisions the owner must make

Data-controller obligations and jurisdiction, hosting geography, cookie/analytics policy, guest retention, meeting retention, public-recording discoverability, minors, request fulfillment and organizational legal holds. No regulatory compliance claim should be made without validation.

## Security release gate

Complete code review, SAST/dependency scan, authZ/tenant isolation tests, secrets scan, incident-response playbook, backup/restore test, DDoS risk assessment, independent penetration test and privacy impact review appropriate to deployment.

Report security issues using [SECURITY.md](../SECURITY.md); never put exploits, passwords or personal recordings in public GitHub issues.
