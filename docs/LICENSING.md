# Licensing, branding and third-party compliance

**The owner has not selected a license for MegaMeet's original code.** This is a governance blocker before substantive source-code contribution or external redistribution. A public GitHub repository with no LICENSE file should not be interpreted as unrestricted open-source permission.

## Immediate decisions needed from the project owner

1. Decide between open-source, source-available and proprietary distribution, with legal review.
2. Choose a compatible license (if open-sourcing), contribution agreement/DCO approach, copyright policy and any trademark policy.
3. Decide who can accept contributions and how third-party notices are preserved.
4. Confirm the final product name and run trademark clearance. The repository path contains `google-meet`, but this project must not claim association with Google or use confusing Google Meet marks.

Until those decisions, contributors should begin with **issues, documentation corrections and architectural proposals**; maintainers should pause substantial source-code reuse submissions requiring a license grant.

## Upstream components vs your original product

Running or modifying third-party projects does not transfer their copyrights. A new brand, deployment, custom APIs and original application code may be under your control while integrated upstream packages remain under their own licenses. AI-assisted output may have special contractual/legal nuances; don't guarantee copyright or exclusivity without review.

## Verification procedure

For each imported dependency, record: upstream URL; exact version/commit/package; full LICENSE and NOTICE; source/modification notices; transitive dependencies; commercial use terms; whether server/network-access obligations apply; and whether trademark or patent grants matter.

- Prefer permissive, well-maintained components when technically appropriate.
- Apache-2.0 requires license/notice compliance and may include patent terms.
- MIT and BSD variants require preservation of appropriate notices.
- AGPL and other copyleft licenses require careful evaluation for a hosted commercial service; do not assume they cannot be used, nor assume there are no obligations.
- Multi-license and open-core projects may license premium components separately.
- Re-evaluate on version upgrades and include a dependency license report in CI once code exists.

## Initial candidate inventory

See [Technology matrix](TECH_STACK.md), where licenses are explicitly labelled as *GitHub repository metadata* checked on 2026-11-14, not final legal approval. Particularly verify Yjs's packaged license (GitHub reports NOASSERTION), and any licenses for diagrams, fonts, media assets, translations, transcription models, and mobile SDK transitive packages.

## Contributor guidance

Do not copy code from Zoom, Teams, Meet, proprietary designs, or random public GitHub repositories. Link to a reusable project's license and use package/service integrations when possible. Never put secrets, credentials, recorded meetings, personal data, or third-party assets without rights in this public repo.

**This is project-planning guidance, not legal advice.** License choice is a maintainer decision requiring competent review.
