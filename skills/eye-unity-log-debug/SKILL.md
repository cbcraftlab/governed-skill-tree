---
name: eye-unity-log-debug
description: Use this skill for Unity debugging tasks such as compile failures, runtime exceptions, test failures, console noise triage, and unclear failures that must be diagnosed before any fix.
---

# Unity Log Debug

## Role Contract

- `Primary Role`: evidence-driven diagnosis
- `Secondary Role`: implementation gating
- `Can Block`: yes, when diagnosis is still unresolved or evidence quality is too low
- `Can Escalate`: yes, by handing off to scene audit, contract review, assumption audit, or safe implementation
- `Depends On`: logs, compiler output, runtime evidence, or a failure that still needs diagnosis
- `Specialization`: Unity-specific

## Overview

Use this skill only when the current task is diagnosis first and implementation second.

Read [references/debug-triage.md](references/debug-triage.md) when you need the failure classification matrix or handoff heuristics.

## Core Goal

Turn noisy Unity failures into one actionable diagnosis.

## Authority Boundary

This skill owns:

- failure classification
- root-cause-first diagnosis
- smallest next diagnostic or corrective step recommendation

This skill does not own:

- broad implementation
- scene-side inspection when structure is the real question
- contract review when payload correctness is the real question

## Trigger

Use this skill when the user asks about:

- compile errors
- runtime exceptions
- test failures
- play mode failures
- unexplained Console noise
- a broken path that still needs diagnosis

## Input

Expect:

- compiler output, logs, test failures, runtime reproduction evidence, or relevant code context

## Output Structure

When reporting, prefer this order:

- `失败现象`
- `问题分类`
- `根因判断`
- `影响范围`
- `最小修法`
- `风险`
- `是否需要改文件批准`

## Failure Classification

Classify the issue before suggesting edits. Prefer these buckets:

- `compile`
- `runtime`
- `scene-side`
- `contract-side`
- `test-side`
- `unclear`

If the evidence points mainly to scene or contract boundaries, explicitly hand off to `eye-unity-scene-audit` or `balance-unity-contract-review` instead of forcing a pure code-debug answer.

## Rules

- prefer fresh, local evidence over memory
- do not chase every log line equally
- do not confuse downstream noise with root cause
- do not claim certainty without evidence
- do not jump into edits just because a likely fix seems obvious

## Boundaries

- diagnosis does not grant edit approval
- do not refactor while debugging unless explicitly requested
- do not act like a scene audit when the structure must be inspected directly
