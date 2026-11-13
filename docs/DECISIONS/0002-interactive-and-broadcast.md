# ADR-0002: Separate interactive meeting from large-event media delivery

**Status: Proposed — requires owner/engineering acceptance**

## Context

A product claiming 100,000 members in "one meeting" can mean 100K simultaneous publishers, or one event with limited speakers and many viewers. These are not interchangeable workloads.

## Decision

Use a LiveKit/WebRTC **interactive meeting path** for ordinary conferences and a **bounded speaker stage** for large events. Export the stage to a separately scalable broadcast/CDN distribution path for audience-only viewers. Chat/Q&A/polls/presence and admission are distinct from video delivery but share the event identity and moderation model.

## Alternatives

- A single gigantic WebRTC room for all attendees: simpler conceptual story, substantially harder and often impractical media fanout at 100K.
- Pure HLS broadcast without stage interactivity: simpler distribution but limited speaker promotion.
- Global WebRTC audience delivery: lower latency but likely higher cost/operational complexity; evaluate if user requirements justify it.

## Consequences and caveats

- Audience members will not all appear as video tiles; they interact through chat, polls and moderated speaker requests.
- Broadcast can lag the live speaker stage; promotion needs audio muting, countdowns and clock-aware UX.
- Egress and a media origin are not substitutes for CDN capacity, admission security or chat infrastructure.
- Test 100K **real video playback**, not 100K synthetic socket connections.

## Open choices

Provider and commercial agreement, maximum stage publishers, audience-latency goal, regions, CDN access control, recording/privacy policies, event limits, fallback path.

**Related:** [100K plan](../SCALABILITY_100K.md), [Cost model](../COST_MODEL.md).
