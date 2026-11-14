# First sprint: low-cost sequence (no product code exists yet)

## Sprint objective

Make project decisions explicit and prepare a single, runnable Phase 1 prototype without burning Astra credits on ordinary implementation. The **repo currently has docs only**; beginning code requires owner agreement on original-code licensing/contribution terms.

| Order | Backlog task | Lead | Output | Stop condition |
| --- | --- | --- | --- | --- |
| 1 | MM-00-04 + MM-00-07 | Chat | One-page launch segment/MVP and license options | Owner must choose license terms |
| 2 | MM-01-01 + MM-01-02 + MM-01-03 | Chat | Current repo inventory and exact upstream reuse/NOTICE table | License/version unknown |
| 3 | MM-01-06 + MM-01-07 | Chat | First OpenAPI/event contract and domain model | Unresolved identity/tenant model |
| 4 | MM-01-04 + MM-01-05 | Astra | Narrow review of stage/broadcast and control-plane architecture | Human must approve cost/architecture |
| 5 | MM-02-01 | Sol | Small Next.js/TS skeleton PR; clean build | No license approval, cannot use external code |
| 6 | MM-02-03 + MM-02-04 + MM-02-05 | Sol | Validated env schema, lint and tests | Missing provider secrets; use safe mock/test setup |
| 7 | MM-02-10 | Chat | Updated developer guide tested against actual scripts | PR missing runnable commands |
| 8 | MM-03-01 then MM-04-01 + MM-04-02 | Sol | Actual safe login/token issue and two-browser meeting | Unauthorized media grant / nonpassing tests |

**Do not start all eight orders together.** Limit to one active code PR, plus an independent documentation/research task if needed. Only assign Astra in order 4 if the design genuinely contains unresolved risks; otherwise keep it as a later optional review.

## Owner's immediate decisions

- Original project license/contributor policy, final product name and copyright owner.
- Available development budget and whether any paid managed video provider is authorized.
- First target customer segment, region and acceptable event latency.
- Whether launch first focuses on normal meetings or a livestream-led product.

## Next milestone proof

A new contributor clones the repo and follows exact setup instructions; two separate browsers can create/join a meeting with real A/V and screen share, role restrictions and tests. Anything less remains a prototype in progress.

For all later work orders see [the full backlog](TASK_BACKLOG.md) and [credit policy](CODEX_CREDIT_POLICY.md).
