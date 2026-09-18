# Consultancy Agent Workflow

An installable Codex skill for adaptive, manager-led specialist delivery. The repository, marketplace, and plugin identifier remain `codex-consultancy`.

## How it works

- Selects the smallest complete team, with explicit ownership and bounded assignments.
- Uses discovery for unresolved material choices and continues already-authorized work without repeated sign-off.
- Applies model and effort choices at spawn time, based on difficulty and consequence.
- Checks staffing and final handoff, adding independent or intermediate audits when useful.
- Verifies artifacts and evidence independently where feasible, with proportionate tests and explicit uncertainty.
- Preserves verified partial results and changes approach after repeated failure.
- Creates reusable skills only when evidence and a concrete future use justify them.
- Uses real telemetry when available and clearly labeled proxies otherwise.

The Manager can work directly. Constrained or unavailable delegation is disclosed, with serial execution where feasible. Persistent Goals require explicit requests. The workflow does not expand authorization for publication, external messages, spending, or destructive actions.

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
