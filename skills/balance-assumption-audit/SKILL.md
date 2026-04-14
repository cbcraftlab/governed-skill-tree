---
name: balance-assumption-audit
description: Use this skill to separate confirmed facts, working inferences, unknowns, and required validation before a decision or implementation step proceeds on shaky premises.
---

# Assumption Audit

## Role Contract

- `Primary Role`: assumption-risk interception
- `Secondary Role`: validation-scope clarification
- `Can Block`: yes, when critical next steps depend on unverified assumptions
- `Can Escalate`: yes, by redirecting to validation, diagnosis, or phase control before unsafe progress continues
- `Depends On`: a plan or decision path with mixed evidence quality
- `Specialization`: generic

## Overview

Use this skill when the current plan may be relying on unstated assumptions, inferred behavior, or half-verified premises.

This is a balance-layer skill because its primary purpose is to prevent false certainty from driving the next step.

## Trigger

Use this skill when:

- facts and inferences are mixed together
- the next step rests on guessed behavior
- the team needs to separate knowns from unknowns

## Input

Expect:

- the current plan or claim set
- available evidence
- the next decision or action being considered

## Core Goal

Reduce avoidable mistakes by classifying the current reasoning into:

- confirmed facts
- plausible inferences
- unresolved unknowns
- validation still required

## When To Use

Use this skill when:

- the path forward depends on guessed behavior
- multiple explanations still fit the evidence
- the user wants Codex to think more like an engineer and less like a guesser
- a decision appears ready, but the evidence quality is uneven

## Workflow

1. collect the claims currently driving the plan
2. classify each claim as fact, inference, or unknown
3. identify which unknowns materially change the next decision
4. decide whether the current plan can proceed safely
5. recommend the smallest validation step needed

## Output Shape

When this skill is active, produce:

1. `Confirmed Facts`
2. `Working Inferences`
3. `Open Unknowns`
4. `Validation Needed`
5. `Can Proceed`
6. `Next Safe Action`

## Rules

- prefer explicit uncertainty over fake confidence
- distinguish missing evidence from negative evidence
- block progression when a critical assumption could invalidate the plan
- keep the validation ask as small as possible

## Boundaries

- do not replace full diagnosis or investigation
- do not choose tools unless the validation path is blocked by tooling ambiguity
- do not replace `controller-work-state-controller` for phase control
- do not expand into implementation when the audit itself is the job
