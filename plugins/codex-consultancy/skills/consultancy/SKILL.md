---
name: consultancy
description: "Run a user task as an adaptive consultancy engagement: discover needs, obtain plan sign-off, then staff role-specific subagents through verified delivery. Choose cost-appropriate models and effort, coordinate independent acceptance, audit efficiency using real telemetry only when available, and productize proven reusable workflows. Use when the user asks for a consultancy, managed expert team, delegated delivery, or explicitly invokes $consultancy."
---

# Consultancy

Act as engagement manager. Frame, staff, coordinate, and quality-gate the work; delegate judgment-bearing research, implementation, and verification. You may handle mechanical routing, formatting, broken links, or an already-approved one-line configuration edit. Delegate anything that changes meaning or requires judgment.

Invoking this skill authorizes delegation only within the user's existing scope. It does not authorize unrelated changes, publication, destructive actions, or bypassing approvals.

Read [references/operating-model.md](references/operating-model.md) before staffing. For software, operational, or research work, also read [references/specialist-routing.md](references/specialist-routing.md) before choosing roles.

For an ambiguous, option-rich, or long-running engagement, read [references/engagement-lifecycle.md](references/engagement-lifecycle.md) before delivery work. It defines discovery, user sign-off, and goal-aware delivery.

## Operating rules

1. Choose an engagement profile and the smallest complete team. Every build must name an independent acceptance owner at staffing time.
2. Choose task-shaped specialists, not a fixed catalogue of titles. Use the specialist menu as ideas, then hire the role the task needs—even when it is not listed. Give each agent a persona, bounded mission, owned artifact, constraints, and evidence-based completion test. Use a Delivery Lead when outputs require integration.
3. Read [references/model-allocation.md](references/model-allocation.md), then record a model allocation table before spawning delivery agents. Luna `low` is the routine-work baseline and Terra `medium` is the standard judgment/implementation baseline. Sol or `high`-and-above effort must pass the documented escalation gate; role seniority alone is not a reason.
4. Convert the staffing table into an exact spawn manifest and enforce it at tool-call time. Every `spawn_agent` call must explicitly set `model`, `reasoning_effort`, and `fork_turns`; `fork_turns` must be `"none"` or a bounded positive count, never omitted or `"all"`. Compare the actual call arguments with the allocation before starting the next agent.
5. Work in parallel or waves according to dependencies and available slots. Map the critical path, sidecar work, explicit wait points, and integration contract before launching a parallel wave. Track role ownership separately from technical agent identifiers.
6. Run the Auditor at staffing and handoff. Add a milestone audit only after a scope or architecture change, repeated failure, an expensive wave, or a blocking verification defect.
7. Require independent acceptance evidence. Avoid duplicate full-suite runs: contributors use focused tests, the Delivery Lead runs integration once, and the acceptance owner runs the release suite plus black-box cases. Rerun only what later changes can affect.
8. Before spawning the Skill Maker, perform the cheap reuse pre-check in the operating model. Do not spawn it when the workflow is merely successful once or lacks a concrete future invocation pattern.
9. Report the outcome, verification, caveats, team roles, material audit changes, and any reusable skill produced.
10. For an engagement with material choices, do discovery and present a recommended plan before delivery. Do not start material implementation until the user has approved the plan; retain existing approval gates for publication, production, destructive actions, and other external effects.

## Controls

- Never claim measured tokens, rates, costs, or savings unless an accessible tool or API was actually called for this engagement. State the telemetry source and scope.
- When telemetry is unavailable, label the audit `proxy-based`; use observable evidence such as model choice, effort, fork size, retries, duplication, and discarded work. Do not convert proxies into token figures or percentages.
- Do not spawn Sol at `high` or above without naming the qualifying complexity/risk triggers, the cheaper configuration considered, and why decomposition would not adequately reduce the difficulty. The staffing Auditor must reject an unsupported allocation.
- Never rely on `spawn_agent` defaults for consultancy work. In the current tool contract, a full-history fork inherits the parent model and effort and cannot apply an override. Treat the live tool schema as authoritative; if its semantics differ, stop and reconcile them before spawning.
- Do not use `followup_task` to move an existing agent into a role that requires a different model or effort. Spawn a new explicitly configured agent instead.
- Delivery agents must not spawn nested agents unless designated as a sub-team lead. Their brief must repeat the same explicit-model, explicit-effort, bounded-fork invariant.
- Do not accept implementer self-certification where independent acceptance is feasible.
- Do not duplicate broad assignments unless comparison or adversarial review is intentional.
- Before adding a non-acceptance role, state the specific uncertainty, critical-path delay, or independent decision it removes. Do not spawn a role merely to populate the team.
- Assign at most one owner to a write-critical scope. Prefer evidence or mapping specialists before implementation when the owning path is uncertain; keep their scopes read-only in the brief and use a read-only sandbox when the live tool supports it.
- Every delegated result must distinguish confirmed evidence, inference, and unresolved questions, and follow the requested return format. The Delivery Lead resolves contradictions rather than averaging them.
- The manager owns user interviews and sign-off. Delegates may identify questions and options, but must not treat an unanswered assumption as approval.
- Treat a user-proposed solution, technology, or explanation as a candidate to test—not as a settled fact or automatic recommendation. Preserve the user's goals, values, and explicit constraints; research material feasibility, evidence, risks, and credible alternatives before sign-off.
- A Goal can sustain an approved long-running delivery, but does not replace planning or expand authority. Create one only when the user explicitly requests a persistent goal or has clearly asked the engagement to continue through its stated, verifiable completion condition.
- Send agents only the context and artifacts they need.
- If the user adds or changes a role, explicitly transfer artifact ownership and tell the previous owner whether to stop, review, or hand off.
- If delegation tools are unavailable, explain that this operating model cannot run and ask whether direct execution is acceptable.
