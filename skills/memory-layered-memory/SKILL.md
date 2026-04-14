---
name: memory-layered-memory
description: Use this skill to store and recall context across short-term work state, long-term preferences, and project knowledge without polluting one layer with another.
---

# Layered Memory

## Role Contract

- `Primary Role`: memory storage and recall governance
- `Secondary Role`: continuity support
- `Can Block`: yes, when the requested write targets the wrong layer or when confirmation is required
- `Can Escalate`: yes, by redirecting toward handoff, decision journal, or a different memory layer
- `Depends On`: a real memory operation request or a routed handoff from `memory-memory-router`
- `Specialization`: generic

## Overview

Use this skill to keep memory useful by separating temporary work state from durable facts.

Read [references/memory-layers.md](references/memory-layers.md) when it is unclear which layer a fact belongs to or whether it should be stored at all.

## Core Goal

Put the right memory into the right layer so future recall is clean, relevant, and low-noise.

## Authority Boundary

This skill owns:

- layer selection
- memory save, recall, update, or delete guidance
- boundary warnings about wrong-layer writes

This skill does not own:

- immediate cross-window handoff generation
- same-thread human-facing status compression
- decision-record authoring

## Trigger

Use this skill when the user wants to:

- save temporary work state
- save or recall durable preferences
- save or recall project-stable knowledge
- update or delete an existing memory item

## Input

Expect:

- a concrete memory operation
- content to classify
- current recall target or write target

## Output

When this skill is active, produce:

1. `Operation`
2. `Chosen Layer`
3. `Why This Layer`
4. `Boundary Warning`
5. `Memory Payload or Recall Result`
6. `Next Action`

## Memory Layers

Use these layers:

- `short-term`
  active progress, latest results, blockers, current status, next step
- `long-term`
  user preferences, collaboration habits, durable reusable lessons
- `project-knowledge`
  stable project structure, baselines, architecture facts, fixed constraints

## Layer Rules

### Short-term

Use for current work state that may expire soon.

### Long-term

Use for preferences or reusable habits that should survive many future sessions.

### Project knowledge

Use for stable project facts that should not depend on the current debugging round.

## Rules

- keep temporary progress out of durable memory
- keep preferences out of project knowledge
- keep project facts out of long-term personal memory
- if a memory is mixed, say which part belongs where
- if confirmation is required, stop before writing
- if nothing should be stored, say so directly

## Boundaries

- do not use this skill for immediate cross-window handoff
- do not confuse a decision record with a general memory item
- do not save noisy conversation residue just because it exists
- do not treat every summary as memory-worthy
