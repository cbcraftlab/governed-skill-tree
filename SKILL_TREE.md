# Governed Skill Tree

This file is the public governed index for the first release batch.

It preserves the same design invariants used by the larger internal system:

- organ-based logical layering
- flat physical storage for compatibility
- governance before uncontrolled growth
- gradual migration instead of violent replacement

## Design Invariants

- logical organization is organ-based
- physical storage stays flat inside `skills/`
- generic skills are the cross-project layer
- domain packs are allowed when they remain clearly specialized
- compatibility and migration should be explicit

## Naming Families

Governed organ families:

- `brain-`
- `controller-`
- `eye-`
- `ear-`
- `memory-`
- `collab-`
- `leg-`
- `balance-`

Additional supported families:

- `.system/*`
- tooling-family skills such as `uloop-*`
- compatibility skills kept temporarily for migration

## System Governance Summary

### Authority Boundaries

- `brain-skill-orchestrator`
  owns task classification and capability-family selection
- `controller-work-state-controller`
  owns current phase judgment and phase transitions
- `brain-tool-routing`
  owns current-step execution-surface choice
- `balance-*`
  owns risk interception and veto authority
- `leg-*`
  owns implementation and verification execution

These layers must not silently replace one another.

### Conflict Resolution

Use this precedence when multiple skills could lead:

1. `balance-*`
2. `controller-work-state-controller`
3. `brain-skill-orchestrator`
4. `brain-tool-routing`
5. domain skills

### Escalation Rule

Escalate when:

- a risky step lacks approval
- assumptions are carrying too much of the plan
- impact scope is still unclear
- permissions or execution environment block the step

## Default Intake Pipeline

1. workspace bootstrap if context is still weak
2. capability-family routing
3. phase determination
4. current-step tool routing
5. domain skill execution
6. proportional verification
7. human-facing output, compression, or handoff

Permitted short-circuits are allowed only when they do not steal authority from another layer.

## Public Inventory

### Brain

- `brain-workspace-bootstrap`
- `brain-skill-orchestrator`
- `brain-tool-routing`
- `brain-capability-gap-detect`

### Controller

- `controller-work-state-controller`

### Eyes

- `eye-state-diff-inspector`
- `eye-unity-log-debug`
- `eye-unity-scene-audit`

### Ears

- `ear-interaction-intent-parse`

### Memory Control

- `memory-memory-router`
- `memory-layered-memory`

### Collaboration

- `collab-tone-regulator`

### Legs

- `leg-verification-runner`
- `leg-unity-runtime-smoke`

### Balance

- `balance-assumption-audit`
- `balance-dependency-impact-scan`
- `balance-unity-codex-guard`

## Metadata Rule

Every skill in this repository should declare:

- `Primary Role`
- `Secondary Role`
- `Can Block`
- `Can Escalate`
- `Depends On`
- `Specialization`

Read [docs/metadata-schema.md](docs/metadata-schema.md) and [SKILL_TEMPLATE.md](SKILL_TEMPLATE.md) before adding or revising skills.

## Public Release Note

This repository is intentionally smaller than the full internal tree.

It is meant to communicate the system design clearly before expanding the public surface.
