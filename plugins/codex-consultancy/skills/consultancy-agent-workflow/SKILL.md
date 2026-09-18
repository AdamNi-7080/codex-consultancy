---
name: consultancy-agent-workflow
description: Coordinate a manager-led team of specialized subagents for complex, multi-discipline work. Use when the user asks for subagents, parallel agent work, a consultancy-style team, dynamic expert staffing, or coordinated delivery across multiple roles; do not use for ordinary tasks that can be completed directly without delegation.
---

# Consultancy Agent Workflow

The primary agent is the Manager: it owns scope, staffing, integration, decisions, and final acceptance. Specialists own bounded workstreams. Choose the smallest complete team; Auditor and Skill Maker are controls to apply when useful, not mandatory standing agents. The Manager may perform substantive work directly when that is efficient.

Read [references/operating-model.md](references/operating-model.md) before staffing and [references/model-allocation.md](references/model-allocation.md) before spawning. Use [references/specialist-routing.md](references/specialist-routing.md) when selecting unfamiliar roles or defining specialist briefs. For unresolved material choices, use [references/engagement-lifecycle.md](references/engagement-lifecycle.md). Read [references/usage-audit.md](references/usage-audit.md) for staffing and handoff audits, and when usage pressure or execution failures warrant another audit.

## Essential workflow

1. Establish outcomes, constraints, existing authorization, acceptance evidence, and available tools, skills, models, and capacity. Inspect existing engagement state before resuming.
2. Staff only roles that remove uncertainty, shorten the critical path, or provide useful independent judgment. Name an acceptance owner before implementation; preserve independence where feasible and disclose limitations.
3. Give each specialist a task-shaped persona, bounded objective, owned artifact, minimal inputs, authority, dependencies, completion test, and stop/escalation condition. Record actual model, effort, and fork settings using the allocation reference.
4. Execute independent work in parallel and dependent work through explicit handoffs. Keep one owner per write scope. Accept evidence before using a result downstream; separate confirmed facts, inference, and unknowns.
5. Audit staffing and final handoff. Add intermediate checks for material scope or architecture changes, repeated failure, an expensive wave, verification defects, or usage pressure. The Manager may perform these checks; delegate an Auditor when independent assessment adds value.
6. Integrate and verify the deliverable. Preserve verified partial work and request the smallest repair for missing evidence. Agent completion and implementer claims alone are not acceptance evidence.
7. Run the reuse pre-check before spawning a Skill Maker. Capture only stable, demonstrated knowledge with a concrete future use, following the installed skill-creator guidance.
8. Deliver one coherent result with verification, remaining uncertainty, material staffing/audit decisions, and reusable knowledge produced. Keep operating state compact and current.

## Boundaries and recovery

- Delegation does not broaden authorization for mutations, external messages, publication, spending, or destructive actions. Existing explicit authorization remains valid; do not invent another approval gate.
- Preserve user goals, values, and explicit constraints. Test material factual assumptions and proposed solutions fairly without reopening settled preferences. Ask only for unresolved decisions that materially affect the work.
- Create a persistent Goal only when the user explicitly requests one; ordinary instructions to finish a task are not a request for a Goal. Follow the live Goal tool's status and completion rules.
- After two unsuccessful attempts using substantially the same approach, change the hypothesis, narrow the assignment, or escalate capability. Preserve evidence and valid work; pursue available autonomous recovery before asking the user to intervene.
- Independent acceptance requires inspecting the artifact and evidence, not repeating the implementer's report. Reproduce behavior or use external checks when appropriate; a different agent is not automatically an independent evidence source.
- If delegation is unavailable, proceed serially where feasible and disclose reduced independence. Runtime capacity and tool schemas are authoritative; do not change global configuration to make the workflow fit.
- Never invent token counts, costs, limits, or savings. Call available read-only telemetry tools; where relevant telemetry is unavailable, label efficiency conclusions proxy-based and state the gap.
