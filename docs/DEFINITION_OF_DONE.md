# Definition of done and release gates

A feature is **not** complete because an AI coding agent wrote files or a demo screenshot looks good.

## Every implementation PR

- Linked issue and scope/acceptance criteria.
- Reuse and license review for new dependencies; pinned versions, notices where required.
- Compiles/builds using documented local steps and contains no secrets.
- Automated tests added/updated where appropriate and **actually executed**; failures reported.
- Authorization and tenant/room isolation considered and tested for sensitive paths.
- UI accessibility/keyboard and responsive behavior checked for impacted flows.
- Error handling, reconnection/fallback and observability included for real-time features.
- Documentation, config examples and deployment implications updated.
- Reviewer understands rollback/data migration and operational costs.

## Media feature gates

- Actual multi-device A/V and screen-share tests, not mocked interfaces alone.
- Join/rejoin, permission denied, device switch, degraded network and browser compatibility.
- Permissions tested for host, presenter, attendee and viewer.
- Recording consent and notification verified when applicable.

## Scale and service gates

- Define concurrency, geographic coverage, workload and quality targets *before* test.
- Record real media client metrics distinct from simulated API/chat connections.
- Report buffering, rejoin, mean/p95/p99 latency, failed joins, bill estimates and resource saturation.
- Test failure scenarios and reconnect storms; instrument dashboards and alerts.
- Security/privacy and provider quota reviews sign off on the claimed scale.

## No unsupported claims

Mark untested features **planned**, **prototype**, **tested in staging**, or **production-verified** with links to evidence. Never label "supports 100K" without a documented, reproducible, real-video test and approved operational budget.

## Documentation only contributions

Fixing docs counts as done when links are valid, guidance is coherent with the approved architecture, and reviewers have checked important technical/legal statements.
