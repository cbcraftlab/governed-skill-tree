# Task Intake Pipeline

Use this as the default entry protocol.

The first job of intake is not to find a tool.

The first job is to decide whether the input can safely be inherited as a known request.

## Default Flow

1. input classification
   Classify the input as observed fact, user claim, question, action request, ambiguous signal, potential induction, topic switch, or continuity signal.
2. cognitive safety gate
   Stop when the referent is missing, context-inferred, or carried by authority pressure.
3. decision gate
   When the answer may shape action, separate confirmed facts, inferences, unknowns, assumptions, error cost, and the smallest useful validation.
4. `brain-workspace-bootstrap`
   Use when the repository or workspace shape is not yet understood.
5. `brain-skill-orchestrator`
   Choose the lead organ and the smallest useful skill chain.
6. `controller-work-state-controller`
   Determine the current phase and the next safe transition.
7. `brain-tool-routing`
   Choose the safest execution surface for the current step.
8. domain skill execution
   Run the specialized skill for the actual task.
9. `leg-verification-runner` or domain-specific validation
   Validate in proportion to the risk of the step.
10. collaboration, compression, handoff, or storage
   Turn the result into a human-facing artifact when needed.

## Allowed Short-Circuits

Short-circuits are allowed only when they do not steal authority from another layer.

Examples:

- memory-only requests may enter through `memory-memory-router`
- already-understood tool questions may enter through `brain-tool-routing`
- high-risk work may enter through `balance-*` before execution

Short-circuits must still respect the input-side gates.

If the target object is missing, a shortcut cannot become tool use.

## Anti-Patterns

Avoid these common collapses:

- accepting a user claim as confirmed fact without marking it as a claim
- binding "this" or "that" to the nearest old topic when the next action could mutate project state
- treating "experts confirmed it" or "no need to ask" as approval
- using tool routing as if it were top-level planning
- letting implementation begin before phase safety is checked
- treating vague "be careful" language as a substitute for balance-layer review
- adding a new skill before checking whether the real issue is overlap or invocation discipline
