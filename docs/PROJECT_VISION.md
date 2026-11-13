# Project vision and operating principles

**Status: proposal, not a shipped product.** **MegaMeet** is the *working* name for a commercial-quality, independent video-meeting and collaboration platform. The aim is to become a credible competitor to Zoom Workplace, Google Meet, and Microsoft Teams, not to copy their branding or assert market leadership.

## Mission

Make high-quality, secure, accessible meetings and collaborative events available from one coherent product, from a two-person call to an event with **100,000+ concurrent viewers**. People should use one link and one identity while media delivery adapts to audience size.

## Users and jobs-to-be-done

1. **Individuals and teams:** create a meeting quickly, join in a browser, share a screen, chat, record with consent, and follow up.
2. **Hosts and moderators:** admit/mute/remove people, manage speakers, run polls and Q&A, prevent abuse, review attendance and recordings.
3. **Organizations:** central administration, SSO, policy and data controls, reliable scheduling, compliance support, integrations.
4. **Event organizers:** register large audiences, offer a responsive live stage, audience-wide captions, moderated interactions and analytics.
5. **Developers and partners:** stable APIs, documented deployments, webhooks and extension interfaces.

## Product differentiation hypotheses (to validate with customers)

- **Meeting-to-event continuity:** start a normal call and expand to a controlled broadcast without forcing participants onto a different product.
- **Cost and operational transparency:** clear quality/latency/capacity modes and predictable usage-based streaming costs.
- **Accessibility and multilingual participation:** real-time captions and translation, with transparent consent and graceful low-bandwidth operation.
- **Developer-friendly and self-hostable options** where feasible, without implying the full system is currently self-hosted or production-ready.
- **Trust by design:** secure defaults, host moderation, explicit recording disclosures, admin controls.

These are hypotheses, not achieved differentiators. Interview potential customers and validate before building everything.

## Non-negotiable engineering principles

- **Reuse before build:** audit mature, maintained libraries and licenses before asking Codex to invent an engine.
- **One product, modular architecture:** main monorepo for original application code; external components used as packages/services.
- **Measure instead of promise:** availability, quality, latency, load, privacy and security must be demonstrated.
- **Stage and audience are different:** the 100K audience primarily watches; only a smaller controlled speaker group publishes.
- **Avoid irreversible lock-in:** define interfaces for authentication, broadcast providers and persistence.
- **Privacy/security/accessibility from the start:** do not bolt them on at launch.
- **Contributors need evidence:** document changes, tests, costs and trade-offs.

## Non-goals for initial delivery

- A new custom WebRTC SFU or a replacement for the entire browser media stack.
- A 100,000-person fully meshed audio/video room with every camera/mic live.
- Every enterprise compliance certification at first release.
- Guaranteed sub-second latency for everyone across all world regions.
- A feature-by-feature clone of proprietary competitor implementations.

## North-star outcomes and measurable quality gates

The roadmap prioritizes reliable user outcomes. Proposed benchmarks for eventual release (subject to discovery and cost evaluation):

| Dimension | What to measure |
| --- | --- |
| Join UX | Time from clicking a link to usable audio/video; browser and mobile success rate |
| Quality | Media connection success, rebuffer ratio, packet loss, adaptation, screen-share readability |
| Reliability | Availability SLO, call drop/recovery rate, graceful degradation under load |
| Security | AuthZ coverage, abuse handling, incident response, dependency and penetration-test findings |
| Accessibility | WCAG-oriented keyboard, screen reader, captions and high-contrast QA |
| Scale | Evidence at 100, 1K, 10K, then 100K concurrent **audience** connections |
| Cost | Actual cost per viewer-hour, meeting-hour, and active speaker-hour |
| Product | Retention, host success rate, user satisfaction, willingness to pay |

## Open decisions

Ownership/legal structure; final product name and trademark clearance; initial customer segment; repository license; hosting regions; provider selection; latency target; retention periods; pricing; launch scope. Decisions belong in documented ADRs and should not be assumed by AI agents.

See [Requirements](PRODUCT_REQUIREMENTS.md), [Architecture](ARCHITECTURE.md), and [Roadmap](ROADMAP.md).
