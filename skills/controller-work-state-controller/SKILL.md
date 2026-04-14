---
name: controller-work-state-controller
description: Use this skill as the phase authority for the current task when Codex must determine the current work stage and the next safe transition.
---

# Work State Controller

## Role Contract

- `Primary Role`: phase authority
- `Secondary Role`: transition safety gating
- `Can Block`: yes, when the next phase lacks evidence, approval, or safety preconditions
- `Can Escalate`: yes, by redirecting to `balance-*`, `brain-skill-orchestrator`, or `brain-tool-routing` when the blocker is outside phase control
- `Depends On`: a task that needs phase judgment or safe next-step confirmation
- `Specialization`: generic

## Overview

Use this skill to keep work in the correct phase and avoid acting with the wrong toolset at the wrong time.

This is the phase authority for the skill system.

Read [references/state-model.md](references/state-model.md) when a boundary between phases is unclear.

## Core Goal

Classify the current work into a small, stable set of phases and recommend the next valid transition.

## Authority Boundary

This skill owns:

- current phase determination
- desired phase declaration
- transition safety judgment
- naming missing preconditions for the next transition

This skill does not own:

- top-level capability-family selection
- execution-surface choice
- implementation details
- risk approval or regression sign-off

If the task family is unclear, hand off to `brain-skill-orchestrator`.

If the current step is known but the tool surface is unclear, hand off to `brain-tool-routing`.

If the transition is blocked by unresolved risk, missing approval, or compatibility uncertainty, hand off to the relevant `balance-*` skill before allowing the phase change.

## Trigger

Use this skill when:

- the user asks what stage the work is in
- the team is moving from explore to implement or implement to validate
- the safe next transition is unclear

## Input

Expect:

- current task evidence
- desired next move, if one has been proposed
- known approvals, risks, and unresolved blockers

## Phase Set

Use these phases:

- `explore`
  gather context, inspect files, compare behavior, reduce ambiguity
- `decide`
  choose the implementation direction, classify risks, lock scope
- `implement`
  edit files or execute bounded changes
- `validate`
  compile, test, smoke, compare output, inspect regressions
- `handoff`
  compress status for the next window, later self, or another worker
- `archive`
  close out or stop when the work is complete enough to end

## Workflow

1. identify the current phase from evidence, not hope
2. identify the desired phase
3. check whether the transition is safe right now
4. if not safe, name the missing evidence, approval, or constraint
5. recommend the single best next transition

## Transition Rules

### Explore -> Decide

Allowed when the main uncertainty is reduced enough to choose a bounded path.

### Decide -> Implement

Allowed when scope, affected files, verification intent, and risk posture are understood, and any required approval exists.

### Implement -> Validate

Allowed as soon as there is a meaningful artifact to check.

### Validate -> Handoff

Use when the work is paused, context is long, or another window will continue.

### Validate -> Archive

Use when the requested goal is complete enough to stop.

## Output Shape

When this skill is active, produce:

1. `Current Phase`
2. `Desired Phase`
3. `Is Transition Safe`
4. `Missing Preconditions`
5. `Next Transition`

## Rules

- determine phase from evidence, not intent
- recommend one next transition, not multiple competing branches
- stop phase advancement when approval or risk gates are missing
- keep validation separate from implementation even when implementation feels complete

## Boundaries

- do not replace `brain-skill-orchestrator`
- do not replace `brain-tool-routing`
- do not expand into implementation when the job is phase control
- do not skip risk gates that belong to `balance-*`
