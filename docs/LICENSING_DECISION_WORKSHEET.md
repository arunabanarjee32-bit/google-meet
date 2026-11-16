# MM-00-07 — MegaMeet original-code licensing decision worksheet

**Status: OWNER DECISION REQUIRED — NOT APPROVED**  
**Prepared:** 2026-11-16  
**Linked:** [Issue #1](https://github.com/arunabanarjee32-bit/google-meet/issues/1) · [Backlog MM-00-07](TASK_BACKLOG.md) · [Licensing guidance](LICENSING.md)

## Scope and boundary

MegaMeet is an independently branded commercial meeting product, currently documented but not implemented on the default branch. This worksheet describes choices for **MegaMeet's original code and contributions**. It does not change the copyright or license of LiveKit, Jitsi, BigBlueButton, any existing package, or their logos/assets. A public GitHub repository without a LICENSE file is **not** an unrestricted open-source grant; it is also **not** a confidentiality mechanism.

**No choice below has been made on the owner's behalf. Do not add LICENSE, copy upstream source, or begin substantive product-code contributions until the owner records the choice and required review approves it.**

## Choices to resolve

| Model | What the owner can do | Important tradeoff | Initial suitability |
| --- | --- | --- | --- |
| **Proprietary original code** | Keep MegaMeet application/control-plane code under commercial terms; sell hosting, services and proprietary features | For confidentiality, keep source in a private repo; the current public repo can remain a separate open documentation project. Vet inbound contributions and third-party redistribution. | Strong option if ownership/control and commercial differentiation dominate |
| **Apache-2.0 original code** | Release original MegaMeet source with permissive reuse, modifications and commercial distribution; includes express patent terms | Other parties may legally build competing distributions, while keeping license/notice obligations | Strong option if open community adoption and self-hosting are strategic |
| **MIT original code** | Release original MegaMeet source with simple permissive reuse, including commercial redistribution | Similar competitive redistribution risk; no express patent license in MIT text | Good simple open-source option |
| **AGPL-3.0 original code** | Require reciprocal source-access obligations for covered network-served modifications, subject to exact license terms | Higher legal/compliance burden, contributor friction and ecosystem compatibility diligence | Only if strong reciprocal open-source obligations are intentional |
| **Dual licensing** | Offer the same copyright-controlled original code under different terms where ownership and contributor grants permit | Adds legal, contributor, support and license-compliance complexity | Defer unless there is a specific commercial reason and legal support |

This is a product/legal tradeoff table, **not legal advice**. An attorney should review the final choice, patents, jurisdictions and commercial contracts.

## Contributor policy — choose separately

1. **No external code contributions initially.** Accept issues/docs feedback; only authorized maintainers write product code. Simplest for a proprietary early product.
2. **DCO / sign-off model.** Contributors certify their right to submit code under the project license. Does **not** automatically assign their copyright to the owner.
3. **CLA or copyright assignment.** May support additional licensing models but creates legal/process friction; have counsel prepare and validate terms.

A permissive upstream dependency does not grant exclusive ownership of upstream technology. Keep dependency versions, notices, trademarks and third-party assets in a documented inventory.

## Technical reuse policy, independent of owner-code license

- **LiveKit Meet:** examined at `c3a16bdc7be03e201615779e8f2f6ee61d41ec91`, repository Apache-2.0. Treat as a frontend *reference*, not a production login/admission/recording backend.
- **LiveKit Server:** examined at `v1.13.11` / `385aa40f9292fe1db8caad87301e4b285b7c198a`, repository Apache-2.0; use as service/SDK integration rather than copying an SFU.
- **Optional @livekit/krisp-noise-filter:** reviewed package has separate terms; do not include without a specific legal decision.
- For any redistribution, preserve license/NOTICE as applicable and review package-level dependencies, brand marks, fonts, media, SDK/model terms and SBOM.

Research evidence: [the open foundation audit PR](https://github.com/arunabanarjee32-bit/google-meet/pull/21). Its proposed ADR-0003 is **not** owner approval.

## Owner decision record — complete in issue #1

- **Copyright owner/legal entity:** [owner to complete]
- **Original-code strategy:** [proprietary / Apache-2.0 / MIT / AGPL-3.0 / dual / other]
- **Will product source remain publicly accessible?** [yes / no; repository plan]
- **Outside contributions allowed initially?** [no / DCO / CLA / other]
- **Who can approve and merge code?** [maintainers and required review]
- **Initial trademark and brand rules:** [owner to complete; MegaMeet is still a working name]
- **Third-party NOTICE/license inventory owner:** [owner to assign]
- **Written legal review/approval reference:** [issue comment / document / reviewer]
- **Decision date and sign-off:** [owner to record]

## Acceptance checklist for MM-00-07 / issue #1

- [ ] Owner explicitly chooses a model and contributor terms in issue #1.
- [ ] Legal/commercial review recorded when appropriate.
- [ ] Appropriate LICENSE and/or proprietary notices prepared **after** the decision.
- [ ] CONTRIBUTING.md, docs/LICENSING.md and source-reuse policy updated consistently.
- [ ] Copyright/attribution/third-party notice requirements assigned.
- [ ] G00/G01 reviewers acknowledge which coding work is permitted.

**Next code task only after G00/G01 acceptance:** MM-02-01 — minimal Next.js/TypeScript web skeleton, dependency lockfile, build, tests, environment validation and CI. Do not start with an unauthenticated LiveKit Meet demo token route.
