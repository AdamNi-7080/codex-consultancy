# Model and effort allocation

Use the models and effort labels exposed by the current spawning tool. These are task-routing defaults, not verified prices or benchmark claims. Runtime availability and descriptions take precedence; role seniority does not determine capability needs. The Manager retains the current task model.

| Task shape | Starting configuration when available |
|---|---|
| Bounded inventory, extraction, formatting, prescribed checks, telemetry collection | `gpt-5.6-luna` / `low` |
| Bounded synthesis or several explicit tool steps | `gpt-5.6-luna` / `medium` |
| Small reversible implementation or focused professional review | `gpt-5.6-terra` / `low` |
| Substantive implementation, analysis, integration, acceptance, or skill design | `gpt-5.6-terra` / `medium` |
| Difficult bounded diagnosis or integration | Terra / `high`, or Sol / `medium` if broader judgment is needed |
| Broad, novel, conflicting, or high-consequence professional judgment | `gpt-5.6-sol` / `medium` or `high` according to depth |
| Hardest cross-domain synthesis, architecture, or unresolved consequential problem | `gpt-6-astra` / `medium` or `high` |
| Compatible work when the preferred models are absent | Available alternatives such as `gpt-5.5`, selected from their exposed descriptions and observed results |

An Auditor collecting facts may use Luna; reconciling quality and cost tradeoffs may require Terra or stronger. Apply the same task test to leads, reviewers, and Skill Makers rather than assigning a model by title.

## Escalation and effort

Start with the least expensive configuration likely to meet the quality bar, accounting for verification and rework. Separate hard decisions from bounded follow-through. For Sol, Astra, or `high` and above, record a brief rationale: difficulty or consequence, cheaper/decomposed alternative considered, and when simpler work can be handed back. Do not require fixed trigger counts or a cheaper failure when risk already justifies capability.

`low` fits explicit, cheaply verifiable work; `medium` fits substantive work; `high` fits difficult reasoning. Reserve `xhigh` and `max` for an isolated exceptional bottleneck with a concrete reason. Use `ultra` only when exposed and explain why lower effort is inadequate. Use `none` only if accepted by the chosen model/tool and no meaningful reasoning is required.

Raise effort when deeper consideration is missing; raise model capability when breadth, reliability, or integration is missing. Narrow the brief when scope is the problem. Escalation handoffs include prior evidence and failed approaches. Downshift after uncertainty is resolved; do not retain an expensive configuration for mechanical follow-through.

## Apply allocations at spawn time

Record the role, task shape, model, effort, fork, rationale, and escalation condition. Where supported, each spawn explicitly supplies `model`, `reasoning_effort`, and `fork_turns="none"` with a self-contained brief, or a supported positive partial-fork count. Under the current collaboration contract, an omitted or `"all"` fork inherits the parent settings and cannot apply overrides.

Check actual call arguments against the allocation and record agent ID, reporting line, artifact ownership, and observed settings when exposed. Do not infer actual configuration from a persona or claim unobserved settings were confirmed. If the live schema differs or overrides are unavailable, use supported semantics, disclose the limitation, and adjust the assignment.

Reuse a configured agent only when its model and effort remain appropriate. `followup_task` does not change them. If a different configuration is needed, create a new agent when capacity permits or adapt the assignment and disclose the constraint. Nested leads must follow the same rules.

If a mismatch is found, inspect its quality and cost implications and preserve valid outputs. Correct future calls and reassign affected work where needed; do not blindly discard work or claim past usage can be undone. The staffing audit checks intended and actual allocations.
