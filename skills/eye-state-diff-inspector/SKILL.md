---
name: eye-state-diff-inspector
description: Use this skill to compare two states, outputs, runs, snapshots, configurations, or UI situations and isolate the meaningful differences when the user asks what changed or why one state behaves differently from another. Trigger it for before/after comparisons, current-vs-expected comparisons, state mismatch questions, config mismatch questions, or whenever the task depends on identifying deltas instead of reasoning from one snapshot alone.
---

# State Diff Inspector

## Role Contract

- `Primary Role`: delta inspection
- `Secondary Role`: explanatory-difference ranking
- `Can Block`: yes, when the comparison anchors are not clear enough to separate noise from meaningful deltas
- `Can Escalate`: yes, by redirecting to runtime comparison, scene audit, or log debug when the evidence type is better handled elsewhere
- `Depends On`: two comparable states, outputs, runs, configs, or snapshots
- `Specialization`: generic

## Overview

Use this skill to identify what changed, what matters, and what likely explains a behavior difference.

Read [references/diff-dimensions.md](references/diff-dimensions.md) when you need a checklist of comparison dimensions.

## Trigger

Use this skill when the user asks:

- what changed
- why one state behaves differently from another
- which delta actually matters

## Input

Expect:

- two comparison anchors
- the relevant state, output, config, or snapshot evidence

## Core Goal

Separate:

- cosmetic differences
- behavioral differences
- state machine differences
- config or data differences
- meaningful deltas from irrelevant noise

## Input Types

- before vs after run
- old config vs new config
- expected state vs actual state
- screenshot A vs screenshot B
- log set A vs log set B
- scene setup A vs scene setup B

## Workflow

1. define the two comparison anchors clearly
2. list raw differences
3. remove irrelevant or expected differences
4. group the remaining deltas by dimension
5. identify the smallest delta set that best explains the changed behavior

## Output Shape

When this skill is active, produce:

1. `Comparison Anchors`
2. `Raw Deltas`
3. `Meaningful Deltas`
4. `Most Likely Explaining Delta`
5. `Suggested Next Check`

## Rules

- compare only like with like
- call out irrelevant deltas as noise
- do not assume the biggest delta is the root cause
- prefer one best explaining delta set over a long unranked list
- distinguish state differences from user-perceived differences

## Do Not Use This Skill For

- single-snapshot diagnosis with no comparison anchor
- full code review
- durable memory storage
- handoff summary generation
