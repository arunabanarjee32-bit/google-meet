# Open-source reuse and technology decision matrix

**Last surveyed: 2026-11-14.** These are shortlisted components, not installed dependencies or commitments. Licenses below reflect GitHub's repository metadata as checked on that date and **must be independently verified against the exact version, subpackages, NOTICE files and commercial use context**.

## Guiding choice: one product, not a pile of applications

Use **one main application monorepo**. Integrate mature packages and deployable services at defined interfaces. Do not merge the Jitsi, BigBlueButton, LiveKit and other complete conferencing applications into one overlapping codebase. Build differentiated orchestration and UX instead of a new SFU.

| Function | Shortlist / repo | Reported license | Proposed use |
| --- | --- | --- | --- |
| Meeting UI starter | [livekit-examples/meet](https://github.com/livekit-examples/meet) | Apache-2.0 | Reference/front-end starter; customize after audit |
| Real-time media | [livekit/livekit](https://github.com/livekit/livekit) | Apache-2.0 | SFU / room infrastructure |
| UI components | [livekit/components-js](https://github.com/livekit/components-js) | Apache-2.0 | Device, room and media controls |
| Recording/export | [livekit/egress](https://github.com/livekit/egress) | Apache-2.0 | Egress/recording; not a CDN |
| RTMP/WHIP ingestion | [livekit/ingress](https://github.com/livekit/ingress) | Apache-2.0 | Optional encoder/OBS ingestion |
| Authentication / SSO | [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 | Evaluate for organizations/OIDC |
| Real-time messaging | [centrifugal/centrifugo](https://github.com/centrifugal/centrifugo) | Apache-2.0 | WebSocket fanout; persist/moderate separately |
| Whiteboard | [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) | MIT | Whiteboard integration subject to package audit |
| Collaborative state | [yjs/yjs](https://github.com/yjs/yjs) | GitHub: NOASSERTION | Audit actual source/package license before adopting |
| Calendar UI | [fullcalendar/fullcalendar](https://github.com/fullcalendar/fullcalendar) | MIT (repo) | Standard/calendar UI; premium separately licensed |
| Cache | [valkey-io/valkey](https://github.com/valkey-io/valkey) | BSD-3-Clause | Redis-compatible cache and ephemeral state |
| Self-hosted media origin option | [ossrs/srs](https://github.com/ossrs/srs) | MIT | Evaluate for origin; CDN capacity is separate |
| Mobile media SDK | [livekit/client-sdk-react-native](https://github.com/livekit/client-sdk-react-native) | Apache-2.0 | Later mobile support |
| Agent framework | [livekit/agents](https://github.com/livekit/agents) | Apache-2.0 | Optional AI pipeline |
| Speech transcription | [openai/whisper](https://github.com/openai/whisper) | MIT | Optional speech-to-text evaluation |
| Product analytics | [umami-software/umami](https://github.com/umami-software/umami) | MIT | Optional metrics; respect consent/privacy |
| Subscription billing | [killbill/killbill](https://github.com/killbill/killbill) | Apache-2.0 | Evaluate at paid launch; may be too heavy initially |
| Load testing | [locustio/locust](https://github.com/locustio/locust) | MIT | API/WebSocket load, not proof of video playback |

## Broadcast: choose explicitly, don't blindly stack everything

- **Managed first candidate:** AWS IVS or Cloudflare Stream for edge delivery at 100K+ audience ambitions; evaluate actual quotas, available protocols, latency, access control, privacy, cost and product limits.
- **Self-hosted evaluation:** SRS as origin plus distribution/CDN; requires operations expertise, testing and support. An origin is not a magically scalable global network.
- **LiveKit Egress** may export the speaker feed, but a broadcast provider/CDN must handle audience distribution.
- **Do not choose both managed broadcast vendors in the first milestone** unless failover requirements justify complexity.

## Alternatives requiring elevated license diligence

- [OvenMediaEngine](https://github.com/AirenSoft/OvenMediaEngine) has AGPL-3.0 licensing in the reviewed public ecosystem; don't silently embed it in proprietary code.
- [tldraw](https://github.com/tldraw/tldraw): licensing is not a blanket permissive MIT grant for production commercial embedding.
- [Cal.com](https://github.com/calcom/cal.com): AGPL/commercial module distinctions.
- [Novu](https://github.com/novuhq/novu): edition and module licenses need verification.
- [Coturn](https://github.com/coturn/coturn): useful TURN option; verify exact licenses/deployment.
- Entire app alternatives (Jitsi Meet, BigBlueButton, Owncast) may be studied for product patterns, but do not merge their core media engines without architecture and legal review.

## Selection checklist for every dependency

- Exact git tag, package name, version, SPDX/license text, notices and dependencies.
- Compatibility with intended proprietary or public distribution model.
- Maintenance, security posture, release cadence, API stability, support needs.
- Expected engineering hours for integration/upgrade, monthly hosting and vendor costs.
- Replaceability, observability and rollback.
- Unit/integration/security/load-test plan.

Store decisions in ADRs; keep a machine-readable software bill of materials once code exists. See [Licensing](LICENSING.md).
