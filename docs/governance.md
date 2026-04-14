# Governance Rules

This system is meant to stay governable as it grows.

That requires hard boundaries, not just naming conventions.

## 1. Authority Boundaries

### `brain-skill-orchestrator`

Owns:

- task classification
- lead organ selection
- capability-family selection
- suggested skill order

Does not own:

- work-phase control
- tool choice
- implementation execution
- risk approval

### `controller-work-state-controller`

Owns:

- current phase judgment
- safe next transition
- missing preconditions before advancing

Does not own:

- top-level task-family choice
- tool selection
- implementation scope
- risk approval

### `brain-tool-routing`

Owns:

- current-step tool choice
- execution-surface fallback
- permission-aware routing for the step in front of it

Does not own:

- overall task-family selection
- work-phase authority
- approval or veto power

### `balance-*`

Owns:

- risk interception
- assumption pressure checks
- impact-scope caution
- veto power when evidence is not good enough

Does not own:

- normal task-family routing
- phase transitions
- implementation itself

### `leg-*`

Owns:

- implementation execution
- verification execution
- delivery motion

Does not own:

- capability-family routing
- phase authority
- risk sign-off

## 2. Conflict Resolution

When multiple skills seem plausible, use this order:

1. `balance-*`
2. `controller-work-state-controller`
3. `brain-skill-orchestrator`
4. `brain-tool-routing`
5. domain skills

## 3. Interruption Policy

When the task changes mid-run:

- stop mentally before continuing
- preserve confirmed state
- re-run capability routing only if the task family really changed
- re-run phase control if the next safe transition is unclear
- re-run tool routing if the step or environment changed

## 4. Escalation Policy

Escalate when:

- approval is needed before a risky move
- assumptions are carrying too much of the plan
- impact scope is unknown
- permissions block the action

Escalation is not a substitute for ordinary routing.
