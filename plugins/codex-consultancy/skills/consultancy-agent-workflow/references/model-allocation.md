# Job level and model allocation

Assign the job level before choosing a model. Level describes the autonomy, ambiguity, and consequence of the owned assignment, not the person's title or the number of steps. Use the same test for implementers, leads, researchers, reviewers, and acceptance owners. These baselines use the currently exposed GPT-6 family and [official model guidance](https://developers.openai.com/api/docs/guides/model-selection); check the live spawn tool for availability and supported effort values.

| Job level | Assignment ownership | Minimum spawn configuration |
|---|---|---|
| Junior | Executes a prescribed, bounded task with little independent judgment and cheap verification | `gpt-6-luna` / `low` |
| Mid | Owns a component or focused review and makes routine decisions within clear boundaries | `gpt-6-sol` / `low` |
| Senior | Resolves meaningful ambiguity, integrates multiple outputs, or accepts material work independently | `gpt-6-sol` / `medium` |
| Principal | Owns consequential cross-domain decisions, architecture, or the hardest unresolved judgment | `gpt-6-astra` / `medium` |

An independent acceptance owner is at least Mid; use Senior or Principal when the risk and judgment require it. Do not assign a lower level because the check is short, or a higher one merely because a role title sounds senior. If an assignment requires more autonomy or consequence than its level allows, raise the job level and update the team map.

## Difficulty and escalation

The table is a floor, not a fixed ceiling. Raise effort above the level baseline for unusually difficult reasoning; raise model capability when breadth or reliability requires it. Record the concrete reason and the evidence that would allow simpler follow-through in a separate, freshly staffed assignment. Never lower effort or model below the job level floor to save usage. Reserve `xhigh`, `max`, and `ultra` for exceptional bottlenecks when the live tool supports them; Astra does not use `none`.

If the named model or an adequate equivalent is unavailable, do not silently hire below the level's capability. Check live model descriptions, choose an available configuration at or above the required capability when clear, and record the substitution. If no suitable configuration exists, queue the assignment and report the constraint.

## Apply at spawn time

For every distinct assignment, record the role, job level, model, effort, fork, owned output, and escalation condition. Spawn a fresh agent with explicit `model` and `reasoning_effort`. Default to `fork_turns="none"` and a self-contained bounded brief; use a supported positive partial fork only when specific recent turns are needed. Under the current collaboration contract, an omitted or `"all"` fork inherits the parent settings and cannot apply model or effort overrides.

Check the actual spawn arguments against the planned level and record the agent ID and observed settings when exposed. Do not infer configuration from the persona. A `followup_task` may finish or correct the same assignment, but cannot change the agent's model or effort and must never start a new assignment. A change of level or mission requires a new agent with a concise handoff.

If a mismatch is found, preserve valid evidence, assess its quality implications, and give remaining work to a fresh correctly configured agent. The staffing audit checks intended and actual levels and allocations; past usage cannot be undone.
