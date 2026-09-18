# Codex Consultancy

An installable Codex plugin that runs work as an evidence-led consultancy engagement rather than a generic multi-agent task.

## What it does

- Clarifies outcomes, constraints, and unanswered decisions before delivery.
- Treats suggested solutions, technologies, and explanations as candidates to test—not assumptions to adopt automatically.
- Uses task-shaped specialists for focused research, implementation, review, and acceptance work.
- Presents a research-backed recommendation, scope, risks, milestones, and verification plan for user sign-off.
- Delivers the approved scope with explicit ownership, bounded context, independent acceptance, and a concise handoff.
- Supports Codex Plan mode for structured choices and Goals for explicitly requested, long-running work with verifiable completion criteria.

## How an engagement works

1. **Discover** — the manager asks only material questions and dispatches targeted research into viable ideas and alternatives.
2. **Propose** — it separates confirmed evidence from assumptions and recommends a plan.
3. **Sign off** — you approve, revise, or reject the proposed scope before material implementation begins.
4. **Deliver** — specialist roles execute the approved work in dependency-aware waves.
5. **Accept and hand over** — independent review/QA verifies the outcome; the manager reports residual risks and completion evidence.

The skill is deliberately flexible: its role menu is a source of ideas, not a fixed organisation chart. It creates a task-specific role when needed, or researches the appropriate role first. It does not bypass approval boundaries, publish externally, or claim evidence it has not obtained.

## Install

Your Codex account needs GitHub access to this repository.

```sh
codex plugin marketplace add AdamNi-7080/codex-consultancy
codex plugin add codex-consultancy@codex-consultancy
```

Start a new Codex task, then invoke `$consultancy` or ask for a managed consultancy engagement.

## Update

Refresh the marketplace and reinstall the plugin after a new release. Start a new Codex task after reinstalling so it loads the updated skill instructions.
