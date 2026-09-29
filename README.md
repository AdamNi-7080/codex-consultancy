# Consultancy Agent Workflow

An installable Codex skill for adaptive, manager-led specialist delivery. The repository, marketplace, and plugin identifier remain `codex-consultancy`.

## How it works

- Maps the smallest complete team before work starts, with explicit delivery, integration, and independent acceptance ownership.
- Uses discovery for unresolved material choices and continues already-authorized work without repeated sign-off.
- Assigns Junior, Mid, Senior, or Principal job levels and applies their GPT-6 model and effort baselines at spawn time.
- Checks staffing and final handoff, adding independent or intermediate audits when useful.
- Requires a separate acceptance owner for every engagement, with proportionate checks and explicit uncertainty.
- Preserves verified partial results and changes approach after repeated failure.
- Creates reusable skills only when evidence and a concrete future use justify them.
- Uses real telemetry when available and clearly labeled proxies otherwise.

The Manager coordinates and signs off; specialists deliver the work. Each distinct assignment uses a fresh subagent, while follow-ups may finish or correct the original assignment. Required work waits when capacity prevents a hire. Persistent Goals require explicit requests. The workflow does not expand authorization for publication, external messages, spending, or destructive actions.

## Install

Your Codex account needs GitHub access to this repository.

```sh
codex plugin marketplace add AdamNi-7080/codex-consultancy
codex plugin add codex-consultancy@codex-consultancy
```

Start a new Codex task and invoke `$consultancy-agent-workflow`, or ask for a managed consultancy engagement.

## Update and compatibility

Version 0.1.1 unifies the skill name as `consultancy-agent-workflow`. The previous `$consultancy` invocation is replaced by `$consultancy-agent-workflow`; no duplicate alias skill is shipped. Repository, marketplace, and plugin installation identifiers are unchanged.

Refresh your marketplace and update the plugin through your installed Codex plugin management flow, then start a new task to load the revised instructions. This repository update does not itself reinstall plugins or change global configuration.

The workflow instructions can be checked structurally and reviewed against scenarios; improved delivery quality and reduced overhead still need evidence from real engagements.
