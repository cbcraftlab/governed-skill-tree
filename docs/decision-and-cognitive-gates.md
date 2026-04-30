# Decision And Cognitive Gates

This note describes the public input-side safety layer for the governed skill tree.

The goal is simple:

before a request becomes routing, tool use, file inspection, implementation, memory writing, or documentation changes, the system should understand what kind of input it has received and whether the target is actually known.

## Cognitive Gate

The cognitive gate classifies incoming input before accepting its premise.

Useful input classes include:

- observed fact
- user claim
- question
- action request
- ambiguous signal
- potential induction
- topic switch
- relation or continuity signal

The gate is especially important when a request uses phrases such as:

- "this"
- "that"
- "the previous conclusion"
- "you promised"
- "experts confirmed it"
- "no need to ask"
- "just continue"
- "proceed directly"

These phrases may be valid in context, but they are not proof that the referenced object, approval, or authority is known.

## Missing Referent Stop

If the action target is missing, ambiguous, or only inferred from old context, the system should not silently bind it to the previous topic.

Until the referent is known, do not:

- call tools
- inspect project files
- modify code or docs
- write memory
- enter project execution
- treat authority pressure as approval

The correct move is to name the missing object or ask for the referent.

## Decision Gate

The decision gate applies when an answer may shape action.

Examples:

- choosing a route
- changing architecture
- deciding whether to continue or stop a line of work
- changing files, docs, memory, or framework rules
- making a model-training or evaluation judgment
- recommending a high-cost implementation direction

Before giving a firm conclusion, separate:

- confirmed facts
- working inferences
- unknowns
- key assumptions
- error cost
- smallest useful validation

If evidence is weak, the output should present candidates and validation paths rather than a final plan disguised as certainty.

## How This Fits The Tree

These gates do not replace existing organs.

- `brain-skill-orchestrator` still owns capability-family routing.
- `controller-work-state-controller` still owns phase transitions.
- `brain-tool-routing` still owns current-step execution-surface choice.
- `balance-*` still owns risk interception and veto.

The gates sit before those layers when the input itself is not safe to inherit.

## Public Boundary

This document is a public boundary note, not a full private runtime policy.

It intentionally avoids project-specific context, personal continuity rules, private handoff formats, and internal evaluation logs.
