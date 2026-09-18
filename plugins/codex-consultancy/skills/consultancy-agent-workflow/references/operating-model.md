# Operating model

## Staffing and capacity

Choose the smallest complete team. Each added role must remove material uncertainty, shorten a critical-path decision, or supply independent review. Do not create roles for status reporting alone or to fill capacity.

| Work shape | Typical ownership |
|---|---|
| Small reversible change | Manager or delivery owner implements; focused independent reviewer where feasible |
| Substantial implementation | Delivery Lead integrates; contributors own separable components; independent acceptance owner |
| Research or investigation | Distinct evidence/hypothesis owners where useful; one synthesis owner and independent evidence review |
| High-risk cross-system work | Delivery Lead, specialists for actual risk boundaries, and independent acceptance |

These are examples, not fixed teams. The Manager can own integration when a separate lead adds no value. Name acceptance ownership before implementation, but launch acceptance work only when there is useful evidence or an artifact to inspect. A Manager who implemented the change cannot also claim independent acceptance of it.

Inspect live capacity, whether the Manager counts toward it, and whether completed or idle agents retain slots. Do not assume waves release capacity. Reserve capacity for acceptance; reuse compatible agents when possible, preserving their actual model/effort and avoiding review of their own implementation. If retained slots prevent independent acceptance, disclose the limitation and use the strongest feasible direct checks. Do not invent a minimum delivery headcount or silently drop critical review. Configuration changes may require a new task or app reload; do not change global capacity without authorization.

## Briefs and coordination

Use the persona and result contracts in [specialist-routing.md](specialist-routing.md) when defining roles. Every brief needs a concrete perspective, bounded mission, owned artifact or decision, inputs, authority/read-write scope, reporting line, dependencies, completion evidence, and stop/escalation condition. Include relevant project instructions and require loading any applicable project skill. State whether nested delegation is allowed; allow it only for designated leads with reserved capacity and the same allocation rules.

Give the first-pass context needed for the assignment. Let specialists expand their search when evidence warrants it, reporting why; this does not require a new user approval. Use artifact paths rather than repeated transcripts.

Before a parallel wave, identify its critical path, independent work, disjoint write scopes, required wait points, integration owner, and fallback for partial or contradictory results. Do not delegate an immediate local blocker merely to manufacture parallelism. Use concise messages for decisions and shared files for large artifacts; wait for milestones instead of polling.

Keep a compact roster:

```text
Agent ID | Current role | Reports to | Model/effort/fork actually requested | Observed settings if exposed | Owned artifacts | Status
```

On reassignment, identify the output moving, tell the prior owner to stop, hand off, or review, and issue a fresh brief with current decisions and adopted audit guidance. A follow-up does not change an agent's runtime configuration.

## Evidence, integration, and recovery

Accept each result against its brief before reuse. Confirm scope, artifact, evidence, assumptions, unresolved questions, and respected boundaries. Resolve conflicting findings against evidence and acceptance criteria rather than averaging conclusions. Preserve verified partial outputs and assign the smallest missing check or repair; do not restart good work unnecessarily.

After two unsuccessful attempts using substantially the same approach, change hypothesis, narrow scope, or escalate with the failed approach and evidence. Interrupt obsolete, duplicate, or out-of-scope work. Recover autonomously when possible; ask the user only when an actual decision or authorization is missing.

Contributors run focused checks. The integration owner validates combined behavior; the independent acceptance owner inspects the artifact and evidence and exercises relevant normal, failure, and integration paths. Coordinate suite ownership to avoid redundant full runs: one existing full run may supply shared evidence, with independent targeted checks rather than another identical full run. Rerun affected checks after meaningful changes. Separate-agent review alone does not prove independent evidence, and completion messages are not proof of correctness.

## Audits and reuse

Run staffing and final handoff controls using [usage-audit.md](usage-audit.md). Adjacent checks can share a snapshot when no meaningful execution intervened. Add an intermediate audit only for material changes, repeated failures, an expensive wave, blocking verification defects, usage pressure, or a user-requested review. Delegate an Auditor only when independent assessment adds value; a focused reviewer may also audit if the two scopes remain clear. Reuse appropriately configured control agents when useful.

Before spawning a Skill Maker, the Manager checks:

- repeated successful use or unusually strong evidence of generalization;
- stable, non-obvious guidance and a concrete future invocation;
- relevant installed skills, preferring a narrow extension over duplication;
- ability to exclude secrets and transient project state.

A successful one-off alone is insufficient. If an existing skill already covers the need, reuse it. If the check fails, retain a candidate and the missing evidence only when useful; do not block delivery. For a mature candidate within authorized scope, the Skill Maker loads the available skill-creator guidance, creates or updates the smallest useful skill, validates it, and reports its path. Serialize skill writes through the Manager. Defer installation or broader changes when authority is missing.

## Durable state

Use `.codex/consultancy/operating-log.md` in writable projects; for intentionally read-only tasks, keep equivalent state in task context and provide a concise handoff. Maintain:

```text
Current outcome and acceptance criteria:
Decisions, assumptions, and unresolved choices:
Roster, ownership, dependencies, and checkpoints:
Adopted efficiency guidance and reasons:
Workflow candidates: evidence; observe | draft | validated | installed
Durable lessons and exceptions:
```

Update existing entries; do not accumulate stale status. Persist only compact aggregate telemetry needed for comparisons, never credentials, account identifiers, private chain-of-thought, full transcripts, or raw usage payloads. Every resumed specialist receives the current relevant state. At closeout report outcome, verification, caveats, material ownership/audit changes, telemetry limitations, and any skill produced; omit empty administrative sections.
