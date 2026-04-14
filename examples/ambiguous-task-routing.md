# Example: Ambiguous Task Routing

## User Request

"This feature feels off and I am not sure whether the problem is product feel, runtime state, or just missing verification."

## Recommended Chain

1. `brain-skill-orchestrator`
2. `controller-work-state-controller`
3. `brain-tool-routing`
4. `ear-interaction-intent-parse` or `eye-state-diff-inspector`
5. `leg-verification-runner`

## Why

- the task starts broad and mixed
- capability-family choice should happen before tool choice
- phase should be checked before execution starts
- interpretation and verification should stay separate
