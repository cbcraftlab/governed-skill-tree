---
name: memory-memory-router
description: Use this skill to route memory-related requests to the right memory operation and specialized memory skill. Trigger it when Codex must decide whether the user needs layered memory storage, recall, handoff, status compression, or a decision record.
---

# Memory Router

## Role Contract

- `Primary Role`: memory control and routing
- `Secondary Role`: none
- `Can Block`: no
- `Can Escalate`: yes, by redirecting to the correct memory or collaboration skill and by stopping accidental persistence
- `Depends On`: a request that plausibly involves save, recall, compress, handoff, or decision capture
- `Specialization`: generic

## Overview

Use this skill as the control layer above memory-related skills.

It chooses the correct memory path before anything is stored, recalled, compressed, or handed off.

Read [references/routing-rules.md](references/routing-rules.md) when a request could plausibly be memory, handoff, compression, or decision capture.

## Core Goal

Choose the correct memory action before anything is stored, recalled, or compressed.

## Authority Boundary

This skill owns:

- memory-intent classification
- memory-path selection
- explaining why nearby memory paths are worse fits

This skill does not own:

- durable storage itself
- handoff generation itself
- same-thread status compression itself
- decision-record authoring itself

If the request is not truly about memory behavior, say so and stop routing.

## Trigger

Use this skill when the user asks to:

- save something for later
- recall previous context
- prepare a handoff
- compress state for continuity
- preserve the rationale behind a decision

## Input

Expect:

- a memory-flavored user request
- current thread context
- any recalled evidence already available

## Output

When this skill is active, produce:

1. `Memory Intent`
2. `Chosen Route`
3. `Why This Route`
4. `Not This`
5. `Next Action`

## Main Routes

Route to one of these:

- `memory-layered-memory`
- `memory-codex-handoff`
- `collab-status-compressor`
- `memory-decision-journal`
- no memory action

## Routing Rules

### Use `memory-layered-memory`

When the user wants storage, recall, update, or delete in a real memory layer.

### Use `memory-codex-handoff`

When the user wants the current work state carried into another session or another window soon.

### Use `collab-status-compressor`

When the user wants a concise status now, not durable storage.

### Use `memory-decision-journal`

When the user wants the why behind a decision preserved.

### Use no memory action

When the request is just normal same-thread progress and no persistence or continuity artifact is actually needed.

## Rules

- route before writing
- do not store things just because the user said "remember" loosely
- separate immediate continuity from durable memory
- separate decision rationale from generic status
- if the request does not need memory behavior, say so directly

## Boundaries

- do not replace the specialized skill you route to
- do not turn every long conversation into a memory event
- do not use this skill for generic planning or implementation routing
