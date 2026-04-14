---
name: brain-tool-routing
description: Use this skill to choose the execution surface for the current step after the capability family and work phase are already understood.
---

# Tool Routing

## Role Contract

- `Primary Role`: current-step tool-surface routing
- `Secondary Role`: execution fallback planning
- `Can Block`: yes, when permissions, environment limits, or surface mismatch make the step unsafe to execute
- `Can Escalate`: yes, by redirecting to `brain-skill-orchestrator`, `controller-work-state-controller`, or a safer fallback surface
- `Depends On`: a known immediate job and a known or intentionally fixed phase
- `Specialization`: generic

## Overview

Use this skill to bridge a known step into the safest concrete execution surface without guessing.

This skill chooses how to perform the current step, not what the overall task is and not which phase the work is in.

Read [references/routing-matrix.md](references/routing-matrix.md) when more than one tool family could plausibly handle the same step.

## Core Goal

Choose the safest and most direct tool surface that can complete the current step with minimal overhead.

## Authority Boundary

This skill owns:

- execution-surface choice for the current step
- permission and environment awareness for that step
- fallback surface selection when the preferred surface is blocked

This skill does not own:

- task-family classification
- phase determination or phase transitions
- implementation scope control
- safety approval or regression review

If the task family is still unclear, hand off to `brain-skill-orchestrator`.

If the current phase is unclear, hand off to `controller-work-state-controller`.

If the step is blocked mainly by risk or uncertainty rather than tooling, hand off to the relevant `balance-*` or domain skill.

## Trigger

Use this skill when:

- the current step is known
- the remaining question is which tool surface should execute it
- shell, MCP, local inspection, web, or manual action are all plausible options

## Input

Expect:

- the immediate job
- known phase and task-family context
- environment and permission constraints

## Preconditions

Use this skill only when:

- the immediate job is already known
- the current phase is already known or intentionally fixed
- the remaining question is which surface should execute the step

## Main Tool Surfaces

Route work among these surfaces:

- local file inspection
- shell command execution
- MCP or app tools
- web lookup
- skill-first guidance
- user-side manual step when environment limits block direct execution

## Workflow

1. identify the immediate job, not the whole project
2. identify which surface can answer that job most directly
3. check safety, permissions, and environment limits
4. prefer one primary surface unless parallel work is clearly beneficial
5. name the fallback if the preferred surface is blocked

## Routing Priorities

### Prefer local inspection first

Use local files, code search, and existing workspace context before web lookup when the answer should already exist in the repo.

### Prefer MCP for environment-aware actions

Use MCP or app-native tools when the task depends on editor state, workspace state, automations, screenshots, or structured environment APIs.

### Prefer shell for direct system operations

Use shell when the task is a command-line action, file discovery, git inspection, build step, or script execution that does not need browser or editor semantics.

### Prefer web only when time-sensitive or externally sourced

Use web lookup when the user asks for current information, official documentation, external quotes, or anything likely to have changed.

### Prefer skill-first when the main risk is procedural

Use a specialized skill first when the task depends more on workflow discipline than on raw tool access.

## Output Shape

When this skill is active, produce:

1. `Immediate Job`
2. `Primary Surface`
3. `Why This Surface`
4. `Blocked By`
5. `Fallback Surface`
6. `Next Action`

## Rules

- route the current step, not the entire roadmap
- prefer the lowest-overhead surface that still preserves correctness
- separate "can run" from "should run"
- say explicitly when permissions or sandbox limits matter
- respect user-named tools unless they are clearly mismatched

## Boundaries

- do not replace top-level task classification
- do not replace `controller-work-state-controller`
- do not choose the next phase
- do not browse the web when local context is sufficient
- do not hide permission needs or environment blockers
