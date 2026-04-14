---
name: leg-verification-runner
description: Use this skill to choose and execute the smallest useful validation path after exploration or implementation, so confidence is proportional to the actual risk of the change.
---

# Verification Runner

## Role Contract

- `Primary Role`: validation planning and execution routing
- `Secondary Role`: delivery confidence reporting
- `Can Block`: yes, when the current proof level is too weak for the claimed confidence
- `Can Escalate`: yes, by handing off to runtime smoke, behavioral comparison, tests, or explicit validation debt
- `Depends On`: a changed artifact, a requested confidence level, or an explicit validation question
- `Specialization`: generic

## Overview

Use this skill to connect implementation work to the right level of proof.

Read [references/validation-matrix.md](references/validation-matrix.md) when the correct validation depth or evidence type is unclear.

## Core Goal

Pick the lightest validation step that can still prove or disprove the requested change.

## Authority Boundary

This skill owns:

- choosing the validation level
- deciding whether compile, test, smoke, comparison, or debt is the right answer
- reporting residual risk honestly

This skill does not own:

- implementation itself
- broad review findings
- pretending compile success equals runtime success

## Trigger

Use this skill when the user asks:

- how to validate a change
- what should be run next
- whether compile is enough
- whether the current proof is strong enough

## Input

Expect:

- what changed
- the failure mode or regression fear that matters
- available validation surfaces

## Output

When this skill is active, produce:

1. `Validation Goal`
2. `Chosen Validation`
3. `Why This Level`
4. `Result`
5. `Residual Risk`
6. `Next Step`

## Validation Ladder

Use this ladder from cheapest to strongest:

1. static check
2. compile or build
3. targeted test
4. runtime smoke
5. behavioral comparison
6. handoff with explicit validation debt

Do not jump to the top unless the change actually needs it.

## Rules

- prefer the smallest meaningful proof
- separate compile success from runtime success
- separate runtime success from UX success
- if validation is blocked, say what blocked it
- if confidence is low, state why
- if one validation step fails, do not over-claim based on earlier lighter checks

## Boundaries

- do not replace the specialized skill that performs the actual compile, test, smoke, or comparison
- do not recommend broad test sweeps when a targeted check can answer the question
- do not say "validated" when only compilation passed and runtime risk remains
- do not hide residual risk just because the user wants speed
