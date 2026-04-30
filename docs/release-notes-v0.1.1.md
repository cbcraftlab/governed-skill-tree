# Release Notes v0.1.1

This is a small public boundary patch.

It does not expand the repository into the full internal system.

## Added

- `docs/decision-and-cognitive-gates.md`
  - public note for input classification, missing-referent stops, authority-pressure handling, and action-shaping decision gates
- `cases/missing-referent-execution-stop.md`
  - case showing why ambiguous "this/that" requests should not trigger tool use or project execution

## Updated

- `README.md`
  - expands the public framing from skill-tree governance to task-intake and runtime-judgment governance
  - updates system flow and default intake flow
  - links the new gate note and missing-referent case
- `SKILL_TREE.md`
  - adds input-side safety gates to the governance summary and default intake pipeline
- `docs/intake-pipeline.md`
  - adds input classification, cognitive safety, and decision gating before execution routing
- `skills/brain-tool-routing/SKILL.md`
  - clarifies that missing or context-inferred referents block tool-surface selection
- `skills/controller-work-state-controller/SKILL.md`
  - clarifies that missing targets and unverified approval block advancement into execution phases

## Still Out Of Scope

- private identity or relationship continuity rules
- private handoff templates
- project-specific engineering state
- full internal skill inventory
- local evaluation logs or private test transcripts
