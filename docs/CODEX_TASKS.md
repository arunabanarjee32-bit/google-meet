# Codex work orders — predictable, credit-conscious development

**Always read [AGENTS.md](../AGENTS.md).** These work orders explicitly prevent broad, expensive prompts like “build Zoom completely”. Do not run all tasks in parallel without reviewing dependency gates.

## Work order A: audit only (do this first)

> Inspect the repository. Do not modify files or install packages. Report current implemented vs planned features. Verify upstream repo versions/licenses and their exact package terms. Compare livekit-examples/meet, LiveKit Server/Components/Egress, Keycloak, Centrifugo, Excalidraw, Yjs, FullCalendar and broadcast options. Classify each requirement as ALREADY IMPLEMENTED, REUSE, CUSTOM BUILD or DEFER. Propose an ADR, minimal MVP dependency list, test plan, cost assumptions and specific files for the next PR. Record all unknowns. Stop and request maintainer approval for licensing/provider decisions.

**Acceptance:** evidence-backed, no code changes, no false status claims.

## Work order B: first skeleton (only after owner chooses code license)

> Implement only the smallest testable Next.js/TypeScript monorepo skeleton for a two-person meeting. Follow approved architecture, avoid duplicating LiveKit components, pin dependencies, add .env.example without secrets, lint/type-check/test scripts, a real local-development README section, and CI. Do not create apps/mobile, AI, billing, large events or empty microservices yet. Run install/build/test and report outputs.

**Acceptance:** new developer follows exact local setup, sees a working page and test output.

## Work order C: secure join flow

> Add secure meeting create/join for two browser users and server-minted, short-lived LiveKit grants. Include host/guest roles with deny-by-default role elevation, AV controls, device permission handling, screen share, and basic reconnection tests. Do not add large-event broadcast mode. Write authorization tests and a minimal threat model update.

**Acceptance:** live two-browser smoke test; unauthorized self-promotion rejected.

## Work order D: collaboration without reinvention

> Evaluate and integrate only approved chat transport and UI controls, preserving persistent storage, authorization, moderation, rate limiting and deterministic message ordering. Reuse approved packages, avoid wholesale merging of another chat application. Add tests and document load assumptions. Implement one vertical slice only.

**Acceptance:** no cross-room leakage, bounded fanout, reproducible tests.

## Work order E: large-event proof of concept

> Build a bounded LiveKit speaker stage and an isolated broadcast adapter for one approved CDN/broadcast provider. Add streaming state and audience join flow using signed access. Keep Q&A/raise-hand control separate. Document latency difference, provider quotas, output costs, consent and known limitations. Test at small scale; don't market 100K.

**Acceptance:** real stage-to-viewer playback and failure/recovery trace, recorded billing assumptions.

## Work order F: scale validation

> Design a staged load-test plan 1K -> 10K -> 50K -> 100K real concurrent viewers, distinguish API/WebSocket synthetic load from actual media playback, quantify join bursts, chat rate, buffering, errors, region mix and costs. Prepare an execution budget and ask before any paid load run.

**Acceptance:** test harness, metrics schema and budget approval; no fabricated results.

## Standard report after each task

1. Intent and scope completed.
2. Files changed and upstream licenses.
3. Tests run with pass/fail and evidence.
4. New env vars, costs, secrets or provider steps.
5. Risks, known missing parts, next single work order.

## Stop conditions

Stop rather than guess when owner licensing is undecided, destructive data migrations are needed, a paid cloud API needs approval, or performance claims lack measurements. Never run unbounded paid load or AI processing from an unspecified budget.
