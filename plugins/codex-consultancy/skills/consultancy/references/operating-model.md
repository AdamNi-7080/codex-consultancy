# Consultancy operating model

## 1. Select the engagement profile

Choose the lightest profile that covers the risk. Add roles only when they own distinct work.

### Delegation-worth-it check

Before adding a role other than required independent acceptance, write one sentence explaining which of these it does:

- removes material uncertainty;
- shortens a critical-path decision through parallel work; or
- supplies an independent challenge or acceptance decision.

If none apply, keep the work with the existing owner. A role that only repeats an existing inspection, produces generic status, or exists to make the engagement look staffed fails this check.

| Profile | Typical team and controls |
|---|---|
| Research or proposal | Research lead, distinct domain/technology specialists when useful, independent reviewer |
| Investigation | Delivery Lead from the start when findings need integration, investigator, reproducer or hypothesis challenger |
| Small reversible change | Delivery Lead who may implement, focused independent reviewer or tester |
| Medium implementation | Delivery Lead, contributor, independent SET/QA; writer when user-facing or operational docs matter |
| Large or high-risk platform work | Delivery Lead, specialists for risky boundaries and core slice, independent SET, relevant security/privacy reviewer, writer; staged waves and conditional milestone audit |

For software delivery, name acceptance ownership before implementation begins. The acceptance owner must be independent of the implementation being certified. When implementation is conditional, name the acceptance owner at staffing but do not launch it until a change is approved and exists. For research, use an independent evidence reviewer; for data pipelines, use a test or data-quality engineer.

The team design is a default, not a fixed org chart. Combine roles for small work where independence is preserved; separate them when risk, breadth, or ownership warrants it.

## 2. Brief and track roles

Use [specialist-routing.md](specialist-routing.md) to select functional roles from the task rather than treating role names as a fixed organisation chart. A named role is a brief, not a claim of authority or entitlement to a model tier.

Every assignment includes:

```text
Role label and persona: <identity, priorities, decision style>
Mission: <one bounded objective>
Why this role: <why this expertise/perspective fits now>
Owned output: <artifact or decision>
Inputs: <minimum context and files>
Context budget: <first-pass inputs and condition for widening>
Boundaries: <what not to change or assume>
Quality bar: <completion test and evidence>
Dependencies: <upstream and downstream roles>
Return format: <concise structure>
Stop/escalate: <when to hand back rather than continue>
```

Maintain a lightweight role-history table:

```text
Agent ID | Current role label | Wave | Owned artifacts | Previous roles | Status
```

Technical identifiers may be reused, but reporting must always use the current role label. On reassignment, record the old role, issue a fresh brief, and state whether prior ownership is transferred, retained for review, or closed.

For every parallel wave, add a compact coordination map:

```text
Critical path: <roles and ordered decisions>
Sidecars: <independent roles>
Write scopes: <one owner each, or none>
Wait point: <result required before the next wave>
Integration contract: <inputs, decision owner, output>
Fallback: <what happens if a result is partial or conflicts>
```

Do not delegate an immediate, local blocker merely to make the team look busy. Start read-heavy mapping or evidence work before a writer when the owner, behaviour, or change boundary is unknown. State `read-only` in those briefs; apply an actual read-only sandbox too only when the live tool exposes it.

Limit the context budget in each brief to the paths, sources, decisions, and environment facts needed for its first pass. An agent may broaden the search only after reporting why that bounded set cannot answer its mission. This prevents parallel roles from repeating full-repository archaeology.

When the user introduces a role or changes ownership:

1. name the artifact or decision moving;
2. identify the new owner;
3. tell the previous owner to stop editing, hand off, or become reviewer;
4. pass only the necessary state;
5. update the role-history table.

## 3. Select model and effort economically

Read [model-allocation.md](model-allocation.md) before spawning agents. Use only models and efforts exposed by `spawn_agent` in the current session.

Create this staffing record:

```text
Role | Task shape | Model | Effort | Fork | Why this clears the bar | Escalation trigger
```

Start at Luna `low` for routine bounded work and Terra `medium` for ordinary judgment-bearing delivery. Decompose an overly broad assignment before upgrading it. Any Sol allocation or `high`-and-above effort must satisfy the escalation gate and name the cheaper option rejected.

### Enforce the allocation at spawn time

The staffing table is not evidence that the allocation happened. Before each wave, build and check the exact spawn manifest:

```text
Role | task_name | model argument | reasoning_effort argument | fork_turns argument | context source
```

For every `spawn_agent` call:

- explicitly pass the allocated `model` and `reasoning_effort`, even when they match the parent;
- explicitly set `fork_turns="none"` for a self-contained brief or a bounded positive turn count when recent context is essential;
- never omit `fork_turns` and never set it to `"all"`—under the current collaboration-tool contract, either produces a full-history fork that inherits the parent model and effort rather than the declared override;
- prefer `fork_turns="none"` plus the minimum files, decisions, and acceptance criteria needed by the role;
- after the call, record the actual arguments used. Do not infer the effective allocation from the role name or staffing plan.

Immediately before calling the tool, assert:

```text
fork_turns is present and is not "all"
model == approved model
reasoning_effort == approved effort
```

For example, an approved Terra-medium role must be spawned with explicit arguments equivalent to:

```text
fork_turns="none", model="gpt-5.6-terra", reasoning_effort="medium"
```

Do not replace those arguments with a full-history fork for convenience; put required context into the role brief or use a bounded positive turn count.

The staffing Auditor must inspect the intended manifest and the actual spawn-call arguments. It returns `stop/replan` for any mismatch before delivery work continues.

If a spawned agent needs another model or effort, do not repurpose it with `followup_task`; spawn a new agent with explicit arguments. Reuse an agent only when its existing configuration remains appropriate and retained context is beneficial.

Delivery-agent briefs must say whether nested delegation is allowed. If allowed, include this same invariant; otherwise prohibit further spawning.

If a mismatch is discovered after spawning, interrupt affected active agents, inspect workspace changes without discarding unrelated or valid work, record which outputs may have used the wrong allocation, and restart only the necessary roles with correct arguments. Do not claim the earlier usage can be undone.

## 4. Schedule and integrate

Use waves when roles exceed available concurrency:

1. evidence and requirements;
2. implementation or artifact creation;
3. Delivery Lead integration;
4. independent acceptance;
5. handoff audit and optional workflow productization.

Wait for milestones rather than polling. Route concise findings downstream. Interrupt work that is obsolete, duplicative, or outside scope.

For verification:

- contributors run focused tests for the code they change;
- the Delivery Lead runs one complete integration check after substantive integration;
- the independent acceptance owner runs one release-level check plus adversarial or black-box cases;
- repeat affected tests after code or configuration changes, but do not rerun full suites after documentation-only edits unless documentation is part of the tested artifact.

The Delivery Lead integrates specialist outputs and resolves conflicts. In incidents or investigations with a user-facing conclusion, assign the Delivery Lead from the first wave as decision and communications owner. The manager checks ownership and acceptance coverage; judgment-bearing gaps go back to a delivery role. The manager may apply only mechanical, semantically neutral corrections or an exact change already approved by the responsible role.

At each wait point, reconcile rather than concatenate results: mark facts as confirmed only when supported by cited evidence, record incompatible findings and the decision owner, and turn unresolved questions into the smallest next check. Do not let an implementer proceed on a speculative map without explicitly accepting that risk.

### Accept delegated output before reuse

The manager accepts an output before treating it as downstream input. Check:

- its stated scope matches the brief;
- the owned artifact or decision is present;
- evidence meets the stated quality bar;
- evidence, inference, and unknowns remain separate;
- stop/escalation conditions were respected; and
- any conflict, missing proof, or residual risk is routed to a named next owner.

Return incomplete work for a bounded repair, adjust the plan, or close the role with its limitation recorded. Do not promote a plausible narrative to an implementation decision without accepting its evidence.

### Lightweight wave recipes

Use these only when they fit; adapt or skip steps for a smaller engagement.

| Shape | Typical flow |
|---|---|
| Defect | Mapper and/or Reproducer -> Implementer -> independent QA/SET |
| Feature | BA or Mapper -> Implementer -> independent SET; add Writer only for durable user/operator/API material |
| Investigation | Evidence researcher plus hypothesis challenger -> Delivery Lead conclusion -> independent evidence review |

Each flow still needs the delegation-worth-it check, disjoint write ownership, and acceptance of each result.

## 5. Audit adaptively

Run the Auditor control at staffing and final handoff. It may be a manager-run manifest/handoff check; delegate it only when an independent assessment adds value. A small engagement may combine an independent Auditor with its focused independent reviewer. Add an intermediate Auditor turn only when:

- scope, architecture, or ownership materially changed;
- an agent failed or retried repeatedly;
- an expensive implementation wave is about to begin;
- independent verification found a blocking defect;
- the user requests a cost or utilization review.

### Establish the data basis first

Before making token claims, inspect the tools actually exposed in the current session.

- If a compatible session/turn usage tool is accessible, call it and record its name, covered agents/turns, and whether usage is complete or best effort. API documentation alone is not evidence that the current local sessions are queryable.
- If required session IDs, turn IDs, credentials, or a compatible tool are unavailable, do not attempt to infer exact usage. Use proxy mode.

Auditor output:

```text
Data basis: telemetry | proxies
Telemetry source and scope: <tool/API and covered turns, or unavailable>
Verdict: efficient | adjust | stop/replan
Evidence: <measured usage or observable proxies>
Waste risks: <overpowered model, excess effort, context, overlap, retries>
Actions: <up to five concrete changes>
Expected effect: <directional quality, latency, and cost impact>
```

Telemetry mode may use reported input, cached-input, output, reasoning, and total-token fields, while acknowledging any best-effort limitation. Proxy mode may use model/effort choice, number of turns, fork size, output length, tool calls, retries, duplicated inspections, blocked time, and discarded work. It must not present exact token counts, utilization rates, prices, or savings.

The Auditor advises; it does not invent hard token conditions without measurements or redo the domain task.

## 6. Productize only plausible reuse

The manager performs this cheap pre-check before spawning a Skill Maker:

- Has the workflow succeeded more than once, or is there unusually strong evidence it generalizes?
- Is it stable and non-obvious?
- Can the manager name at least one concrete future invocation pattern?
- Does an existing skill not already cover it?
- Can it be encoded without secrets or transient project state?

Spawn the Skill Maker only when all answers are plausibly yes. Otherwise report `Skill Maker not started` and the failed criterion.

When started, the Skill Maker reviews the verified workflow, loads the available `skill-creator` skill, creates or narrowly updates the best-matching skill, validates it, and reports the path and result. A successful one-off engagement alone is insufficient.

## 7. Final handoff

Report concisely:

- delivered outcome and verification;
- unresolved caveats;
- roles and ownership changes;
- material model/effort or staffing changes from the audit;
- telemetry source, or that efficiency findings were proxy-based;
- any skill created, or why the Skill Maker was not started.

Do not claim the manager personally performed delegated judgment-bearing work.
