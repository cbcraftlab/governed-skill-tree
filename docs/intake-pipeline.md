# Task Intake Pipeline

Use this as the default entry protocol.

## Default Flow

1. `brain-workspace-bootstrap`
   Use when the repository or workspace shape is not yet understood.
2. `brain-skill-orchestrator`
   Choose the lead organ and the smallest useful skill chain.
3. `controller-work-state-controller`
   Determine the current phase and the next safe transition.
4. `brain-tool-routing`
   Choose the safest execution surface for the current step.
5. domain skill execution
   Run the specialized skill for the actual task.
6. `leg-verification-runner` or domain-specific validation
   Validate in proportion to the risk of the step.
7. collaboration, compression, handoff, or storage
   Turn the result into a human-facing artifact when needed.

## Allowed Short-Circuits

Short-circuits are allowed only when they do not steal authority from another layer.

Examples:

- memory-only requests may enter through `memory-memory-router`
- already-understood tool questions may enter through `brain-tool-routing`
- high-risk work may enter through `balance-*` before execution

## Anti-Patterns

Avoid these common collapses:

- using tool routing as if it were top-level planning
- letting implementation begin before phase safety is checked
- treating vague "be careful" language as a substitute for balance-layer review
- adding a new skill before checking whether the real issue is overlap or invocation discipline
