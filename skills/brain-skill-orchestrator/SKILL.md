---
name: brain-skill-orchestrator
description: Use this skill as the top-level brain when the task type is unclear, when multiple skill families may apply, or when Codex must choose the right capability family before any phase or tool decision is made.
---

# Skill Orchestrator

## Role Contract

- `Primary Role`: capability-family routing
- `Secondary Role`: task classification
- `Can Block`: yes, when the task family is still too ambiguous for safe downstream routing
- `Can Escalate`: yes, by redirecting toward `balance-*`, `controller-*`, or domain-first routes when capability routing alone is not enough
- `Depends On`: a broad, mixed, or unclear user task
- `Specialization`: generic

## Overview

Use this skill as the capability-family router above specialized skills.

Its job is to classify the task, identify the primary organ, and suggest the smallest useful skill chain.

It is not the owner of phase control, tool selection, or risk veto.

Read [references/organ-taxonomy.md](references/organ-taxonomy.md) when the primary organ is unclear.

## Core Goal

Turn a user request into a small routing decision:

- what kind of problem this is
- which organ family should lead
- which specialized skill should run next

## Authority Boundary

This skill owns:

- task classification
- primary organ selection
- capability-family selection
- suggested skill ordering

This skill does not own:

- phase determination
- phase transitions
- tool or surface choice
- implementation details
- risk veto or safety approval

If phase is unclear, hand off to `controller-work-state-controller`.

If the execution surface is unclear inside an already chosen step, hand off to `brain-tool-routing`.

If risk or safety concerns dominate the task, route toward the `balance-*` family instead of trying to resolve them here.

## Trigger

Use this skill when:

- the task type is broad or ambiguous
- multiple organ families could plausibly lead
- the user is speaking in goals rather than a concrete step

## Input

Expect:

- the user request
- current thread context
- any already-known task constraints

## Classification Pass

Before invoking anything else, classify the request by:

- primary organ:
  `brain`, `controller`, `eyes`, `ears`, `memory`, `hands`, `legs`, `balance`, or `collaboration`
- task type:
  exploration, implementation, validation, review, handoff, or memory-related continuity
- uncertainty level:
  low, medium, or high
- risk level:
  low, medium, or high

## Routing Rules

### Brain-first

Use when the request is broad, ambiguous, mixed, or asks for system design.

When the request is specifically about whether the skill tree is missing a reusable capability, route to `brain-capability-gap-detect`.

### Eyes-first

Use when the user gives captures, logs, screenshots, state comparisons, or asks what feels different.

### Ears-first

Use when the user describes subjective feel, product language, or vague dissatisfaction rather than naming a subsystem.

### Memory-first

Use when the user asks to save, recall, compress, or hand off context.

### Legs-first

Use only when the implementation direction is already clear and the main need is execution or validation.

### Balance-first

Use when the main need is risk control, approval boundaries, review, compatibility checks, assumption audit, or impact scanning.

## Output Shape

When this skill is active, produce:

1. `Task Classification`
2. `Primary Organ`
3. `Suggested Skill Order`
4. `Stop Conditions`

Keep it short. This skill should route work, not solve it.

## Rules

- route before deep execution
- choose the smallest useful skill chain
- prefer one lead organ unless the request is genuinely mixed
- respect explicitly named skills unless there is a clear mismatch
- do not reclassify repeatedly unless new evidence appears

## Boundaries

- do not determine the current work phase
- do not replace `controller-work-state-controller`
- do not replace `brain-tool-routing`
- do not choose tools when only capability routing is needed
- do not expand into implementation when routing is the main job

## Typical Examples

- "This effect feels off. Help me determine what is wrong."
  route to `ear-interaction-intent-parse` or `eye-runtime-capture-compare`
- "I am switching accounts. Prepare a continuation handoff."
  route to `memory-codex-handoff`
- "I am worried this change may cause regressions. Move carefully."
  route to `balance-*`, then `controller-*`, then `leg-*`
