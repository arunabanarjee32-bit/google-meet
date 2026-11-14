# Codex credit-saving operating policy

**Goal:** Spend Sol and Astra capacity only on high-value work that can be verified. Do not assume a fixed token or credit cost per message: cloud usage depends on model, scope, context and effort. Check ChatGPT **Settings → Usage** for remaining Work/Codex allowance and resets. Codex and Work share that allowance.

## Model routing rules

1. **Chat GPT-6 (C):** First write task spec, test cases, API contract, copy, docs, comparison, mock data or a small isolated code draft here. This is planning/output, not proof that code runs.
2. **Codex GPT-6.1 Sol (S):** Default repository engineer. Use for focused implementation, package integration, lint/tests, CI and conventional bugs. Begin at Standard speed + Low or Medium reasoning; increase only if needed.
3. **GPT-6 Astra (A):** Use for one difficult decision/failure at a time: distributed SFU/CDN architecture, role escalation attack surfaces, race conditions, multi-service outage or unresolvable Sol bug. Provide failing test/logs and a precise question. Ask for design review before broad code changes.
4. **Human approver:** Licenses, commercial contracts, money, compliance claims, production credentials and releases require explicit decision. Agents may prepare recommendations, not silently approve.

### Hard caps per coding work order

- **One issue, one deliverable, one branch/PR**. Typical target one focused user-visible vertical slice or one test suite.
- Prepare required file paths, behavior, acceptance tests and **out-of-scope** first.
- No 'build my complete Zoom competitor' prompts. Break large tasks into no more than a few adjacent files/services per PR where practical.
- Stop if unplanned work appears, there are missing secrets/accounts, deployment cost is unknown, or a maintainer decision is necessary.
- Avoid unnecessary whole-repository prompts: quote relevant files, short prior decisions and current acceptance criteria. Let Codex inspect the minimum tree it needs.
- Never run parallel agents touching the same files or schema migrations.
- Do not retry the identical failing request repeatedly. First collect failure evidence, then adjust requirements or escalate to Astra.
- No paid 10K/100K load testing or production operations without explicit owner approval and a safe shutdown/teardown plan.
- Record model used and approximate allowance/credit change **if available**. Do not invent an exact quote.

## Escalation ladder

1. Chat drafts spec + negative tests.
2. Sol implements, runs tests, reports diff.
3. If failure: Sol performs **one focused diagnosis** with stack trace and minimal repro.
4. If still blocked due to architecture/security/concurrency: Astra handles the **specific blocker**, not the whole project.
5. Sol integrates Astra's reviewed fix and tests; human approves risky changes.

## Suggested cut/paste prompt for Chat

> For task [ID] in docs/TASK_BACKLOG.md, create a concise implementation specification. Identify exact components to reuse, files/APIs to touch, security and license concerns, 5 positive and negative test cases, measurable acceptance conditions and explicit out-of-scope items. Return the smallest possible deliverable; don't claim execution.

## Suggested cut/paste prompt for Sol in Codex

> Read AGENTS.md and task [ID] in docs/TASK_BACKLOG.md. Inspect the current repository, not imagined files. Implement ONLY this task using the approved, licensed stack. First give a short scope and acceptance plan. Prefer mature dependencies; do not rewrite media engines. Keep changes to one reviewable PR. Add tests for both success and unauthorized/failure cases. Run available build, type, lint and tests; report actual output, changed files, dependencies/licenses and known gaps. Do not run paid infrastructure without approval. Stop on unresolved legal, credential or budget decisions.

## Suggested cut/paste prompt for Astra in Codex/Work

> Review task [ID] with these exact files, failing tests/logs and approved architecture decisions. You are a senior reviewer, not the primary feature implementer. Identify root cause, alternatives, security/latency/cost risks, and recommend the smallest safe change with a testable proof. Do not rewrite unrelated modules or claim load capacity without measured evidence. Produce an ADR/risk summary and a scoped follow-up task for Sol. Only implement a fix if the issue explicitly requires it.

## Budget dashboard to maintain in issues/PRs

| Field | Example |
| --- | --- |
| Task ID | MM-04-02 |
| Assigned lane | Sol |
| State | Ready / In progress / PR / Tested / Released |
| Intended verification | Token escalation rejected by server |
| Model / effort / speed | GPT-6.1 Sol / Medium / Standard |
| Spend signal | Manual before/after usage (if available) |
| Result | PR URL, test logs, remaining blocker |
| Escalation needed? | No / Astra on specific failure |

If Chat/Work/Codex model access changes, use the nearest available equivalent with the same **role**, but never assume this project document grants account entitlements.
