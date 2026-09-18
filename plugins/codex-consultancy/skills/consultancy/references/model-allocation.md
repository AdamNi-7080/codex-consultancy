# Model and reasoning allocation

Last researched: 2026-09-17. This policy interprets current official OpenAI model positioning for consultancy subagents. Re-check current documentation if the exposed model lineup or descriptions change.

Official positioning:

- [GPT-5.6 Luna](https://developers.openai.com/api/docs/models/gpt-5.6-luna) is optimized for cost-sensitive, high-volume workloads.
- [GPT-5.6 Terra](https://developers.openai.com/api/docs/models/gpt-5.6-terra) balances intelligence and cost.
- [GPT-5.6 Sol](https://developers.openai.com/api/docs/models/gpt-5.6-sol) is the flagship tier for complex professional work.
- [OpenAI model guidance](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-5.5) describes `low` as efficient reasoning, `medium` as the balanced quality/latency/cost point, `high` for hard complex agentic work where latency matters less, and `xhigh` for the hardest asynchronous work or capability-boundary evaluations. It warns that higher effort can increase unnecessary searching or overthinking and should be raised only when it measurably helps.

These are API descriptions, not proof of performance on a particular repository or the Codex app's actual billing. Use them as allocation priors, then adjust from observed task results. Only choose models and efforts that the current `spawn_agent` tool exposes.

## Default ladder

Choose the lowest rung likely to meet the quality bar:

| Rung | Use when | Typical work |
|---|---|---|
| Luna `low` | Instructions are explicit, scope is bounded, and correctness is cheaply checkable | Inventory, file mapping, search-result collection, formatting, summarization, documentation from settled facts, running prescribed tests, routine audit, Skill Maker pre-check |
| Luna `medium` | The work is bounded but needs modest synthesis or several deterministic tool steps | Comparing a few known artifacts, drafting tests from explicit acceptance criteria, structured documentation, simple reproducible investigation |
| Terra `low` | Some professional judgment is needed but the path and acceptance criteria are clear | Jira/BA refinement, focused code review, small reversible implementation, targeted QA design, evidence reconciliation |
| Terra `medium` | Normal engineering or analytical work needs multi-step reasoning and tools | Standard feature implementation, non-trivial debugging, integration, test design, domain analysis, independent acceptance |
| Terra `high` | A genuinely difficult bounded problem remains after decomposition | Cross-module diagnosis, conflicting evidence, complex integration, risky migration planning |
| Sol `low` or `medium` | The task needs flagship capability because ambiguity, breadth, novelty, or consequence is unusually high, but prolonged deep reasoning is not yet justified | Difficult architecture synthesis, high-stakes review, resolving several interacting systems or contracts |
| Sol `high` | Hard reasoning is both critical and resistant to decomposition or Terra-level attempts | Severe cross-system ambiguity, consequential security/protocol reasoning, critical integration after a documented lower-tier failure |
| Sol `xhigh`/`max` | Exceptional asynchronous work or explicit capability-boundary evaluation | Use only with user direction or concrete evaluation evidence; never as a routine delivery default |

`none`, if exposed, is for latency-critical classification, extraction, or reformatting with no meaningful planning or tool chain. Prefer `low` whenever the role must search, plan, use several tools, or make a multi-step decision.

## Role starting points

Role titles do not determine capability needs. These are starting points, not entitlements:

| Role/work item | Start with |
|---|---|
| Auditor using proxies, status summarizer, technical writer with settled content | Luna `low` |
| Evidence collector, test runner, bounded documentation synthesis | Luna `low` or `medium` |
| BA refining a clear ticket, focused reviewer, small-change developer | Terra `low` |
| Standard developer, QA/SET designing acceptance, Delivery Lead integrating a normal feature | Terra `medium` |
| Investigator facing conflicting evidence or a Delivery Lead integrating multiple systems | Terra `high` |
| Architect or adversarial reviewer for novel, high-consequence, cross-system work | Sol `medium`; raise only if the gate passes |

A senior persona does not automatically receive Sol. A junior or mechanical role does not automatically receive Luna if it owns a genuinely hard decision.

## Sol and high-effort escalation gate

Before assigning Sol or any `high`-and-above effort, record:

1. at least one capability trigger: novel or conflicting evidence, cross-system coupling, adversarial reasoning, high consequence, or a documented lower-tier failure;
2. why splitting the task into narrower roles would not remove the hard reasoning;
3. the cheaper model/effort considered;
4. the observable condition for returning to a cheaper tier.

For Sol `high`, require at least two capability triggers, or one trigger plus a failed Terra `medium`/`high` attempt. Normally allow only one Sol `high` critical-path role per wave. The Auditor must return `adjust` when this evidence is absent.

Allocation is enforced by the `spawn_agent` arguments, not by the written plan. Every spawn must explicitly carry the approved model and effort with `fork_turns="none"` or a bounded positive count. An omitted or full-history fork is an allocation failure when it inherits a different parent configuration.

## Escalate and de-escalate

Escalate one dimension at a time:

1. tighten the brief and reduce context;
2. increase effort on the current model if deeper reasoning is the missing factor;
3. move up a model tier if capability or reliability is the missing factor;
4. use Sol `high+` only after the gate passes.

De-escalate after the ambiguous decision is resolved. A Sol architect can hand a settled plan to Terra implementers; Terra can hand deterministic checks and reporting to Luna. Do not keep downstream roles on an expensive configuration merely because an upstream role needed it.

## Staffing audit questions

The staffing Auditor checks:

- Is most routine work on Luna and most ordinary judgment-bearing work on Terra?
- Does every Sol or `high+` allocation contain the required evidence?
- Could task decomposition replace a model upgrade?
- Is the chosen effort justified independently of the model?
- Is there a defined de-escalation point?
- Do the actual `spawn_agent` arguments match the approved model, effort, and bounded fork for every role?
- Was any agent reused with `followup_task` despite the new role requiring a different configuration?

Do not approve the staffing plan until unsupported Sol/high allocations are downgraded or justified and the exact spawn manifest is compliant.
