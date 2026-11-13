# Early operating-cost model: assumptions, not price quotes

**No infrastructure bill has been measured for this repository.** Avoid promising cheap 100K meetings without explicit video-distribution pricing and capacity commitments. Reassess published vendor prices/limits before procurement.

## Cost drivers to track

| Driver | Unit | Questions |
| --- | --- | --- |
| Interactive stage | speaker-hour, SFU CPU/network | Concurrent publishers, simulcast, regional routing, TURN relay |
| Broadcast delivery | viewer-minute, delivered GB | Bitrate/ABR ladder, concurrent viewers, regional egress |
| Transcoding | input hour, rendition minute | Composite stage, resolution, replay encoding |
| Real-time interaction | connections, messages/sec | Join spikes, broadcasts, Redis, broker traffic |
| Database and storage | provisioned/used GB, IOPS | Presence data boundaries, logs, meeting records |
| Recording | stored GB-month, egress | Consent, retention, export and playback |
| AI | audio minute / token / GPU-hour | Captions, translation, summaries |
| Reliability | environments, regions, support | Observability, failover, DDoS mitigation, on-call |
| Engineering | development & maintenance effort | Dependency upgrades, security review, incident response |

## Bandwidth illustrations

At 100K viewers averaging 1 Mbps for one hour, network delivery is approximately 45 decimal TB. At 2 Mbps, about 90 TB. This is **not** the origin bandwidth if a CDN distributes it, and it is **not** a complete provider bill.

For estimation:

- Total viewer-minutes = concurrent viewers × average watched minutes (adjust for churn).
- Delivery GB (decimal) ≈ viewer count × average watched seconds × mean Mbps / 8,000.
- Billing amount = actual vendor price sheet for relevant delivery unit, region, quality and service tier × measured usage, plus fixed/other variable charges.
- Add cost sensitivity for 25%, 50%, 100% of attendees and for high/low-resolution variants.

Do not infer that a single flat-rate VPS can directly deliver 100 Gbps. Avoid quoting a vendor price unless the date, SKU and contractual source are recorded.

## Cost review checklist for each milestone

1. Baseline spending during two-person test.
2. 100/1K viewer cost per viewer-hour and operational complexity.
3. 10K trial with actual media replay/playback, billed egress and monitoring.
4. 100K forecast and reserve fund before test; provider quota approval.
5. Alerts and kill switches for out-of-control traffic and AI inference bills.
6. Unit economics for free, paid and enterprise plans based on realistic usage.

A useful experiment compares managed broadcast to a self-hosted origin + contracted CDN with total engineering, reliability and support costs included. A lower per-GB estimate alone is not sufficient.
