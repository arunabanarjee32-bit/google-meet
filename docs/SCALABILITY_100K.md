# 100,000+ audience system: engineering and validation plan

**This is a target, not an existing capability.** One logical event with 100K viewers means most are audience-only; a smaller bounded stage publishes audio/video in real time. It is not technically or economically equivalent to 100K people publishing 100K cameras to each other.

## Media delivery model

1. Host and approved presenters publish to a LiveKit SFU stage using WebRTC.
2. A controlled composite or selected program feed is exported via egress.
3. A managed broadcast service or verified origin/CDN fans the encoded stream out across regions.
4. Viewers subscribe to the broadcast (adaptive variants and signed access).
5. A separately scaled event-control plane handles join auth, moderation, polls, Q&A, chat and hand-raise.
6. A viewer who becomes a speaker switches to a short-lived authorized stage session; remove broadcast audio when appropriate to avoid echo and rebroadcast delay.

The actual product must specify whether viewer latency is seconds (e.g. LL-HLS) or low-latency WebRTC and handle stage/broadcast clock differences. Do not promise sub-second delivery without evidence.

## Capacity calculations (planning illustrations)

At 100,000 concurrent viewers watching an average **1 Mbps** encoded stream:

- Aggregate distribution: **100 Gbps**.
- 60-minute event transfer: about **45 TB** (decimal), *before overhead and variant/quality effects*.
- At 2 Mbps average: about **200 Gbps** and **90 TB** per hour.
- 100K authenticated joined viewers also create identity, WebSocket, presence, heartbeat and API load unrelated to video bytes.

These are bandwidth/data quantities, **not dollar quotes**. A CDN/media provider must explicitly support the regional concurrency, ingest/egress and billing. Evaluate peak join rate, not just total viewers.

## Reliability and protective design

- Admission control and queueing for burst joins; short-lived signed event/video tokens.
- Regional edge distribution, health checks, origin protection and provider quotas.
- CDN/video fallback strategy; test recoverability when broadcast fails.
- Rate limits, per-event moderation thresholds, slow mode, spam protection, queue caps.
- Aggregate and sample presence counters rather than broadcasting every join to everyone.
- Separate chat partitions/shards from video infrastructure; protect databases from hot-key write storms.
- Backpressure, bounded queues, retry policies and late-join idempotency for Q&A/polls.
- Telemetry: successful viewers, active speakers, join latency, start failures, buffering, media bitrate, error rates, server saturation, moderated events.
- Consent, privacy, anti-abuse and retention policies must scale too.

## Test ladder

| Gate | Test | Evidence required |
| --- | --- | --- |
| A | 2–25 interactive participants | Functional AV/host-control tests |
| B | 100–1,000 audience viewers | Real playback + join/leave, moderated chat tests |
| C | 10,000 audience viewers | Verified media delivery and multi-service soak test |
| D | 50,000 audience viewers | Regional load/failure, burst and cost evidence |
| E | 100,000+ audience viewers | Concurrent *actual playback*, audited metrics, quota and cost validation |

At every gate: report deployment version, locations, device/network profile, measured concurrency, duration, RTT/latency, failure percentage, rebuffers, p95/p99 join time, bills and infrastructure diagrams. Synthetic fake clients may load API/chat but **do not prove media viewing capacity**.

## Failure drills

- SFU stage loss while a CDN stream is in progress.
- Egress interruption, broadcast origin outage and viewer reconnect storm.
- A sudden 100K join surge, a malicious chat flood, Q&A moderation backlog.
- Promotion race: two moderators approve the same viewer simultaneously.
- Multi-region network partition, stale role tokens, billing limit and provider throttling.
- Recording/storage failure with visible and correct client state.

## Go/no-go

Do **not** advertise a 100K guarantee until an accepted Gate E run exists for the advertised delivery mode, with legal/financial approval, operational runbooks, abuse response and support staffing. Keep a smaller published limit until then.

See [Architecture](ARCHITECTURE.md), [Costs](COST_MODEL.md), [Security](SECURITY_PRIVACY.md), and [Roadmap](ROADMAP.md).
