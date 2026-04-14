---
name: balance-unity-codex-guard
description: Use this skill before Unity file edits when a task may modify project code, scenes, prefabs, assets, or configuration, so the change is bounded, risk-classified, and explicitly approved before editing begins.
---

# Unity Codex Guard

## Role Contract

- `Primary Role`: pre-edit risk interception
- `Secondary Role`: approval gating
- `Can Block`: yes
- `Can Escalate`: yes, by redirecting toward diagnosis, scene audit, contract review, or safe implementation after approval
- `Depends On`: a proposed Unity edit or any request that may touch project files, scenes, prefabs, assets, or configuration
- `Specialization`: Unity-specific

## Overview

Use this skill only in the pre-edit approval stage.

Read [references/pre-edit-risk-matrix.md](references/pre-edit-risk-matrix.md) when you need risk classes, stop conditions, or approval checklist wording.

## Core Goal

Turn an edit request into a safe, bounded, approval-ready change proposal.

## Authority Boundary

This skill owns:

- risk classification before editing
- smallest-safe-scope proposal
- approval gating before file modification

This skill does not own:

- diagnosis-first investigation when the root problem is still unclear
- implementation after approval
- phase authority for the whole task

## Primary Constraint Source

Read this file first when it exists:

`Assets/_Project/Docs/Merged_Simplified_Codex_Constraints_With_Git.md`

## Trigger

Use this skill when the task may:

- modify Unity code
- modify scenes or prefabs
- modify serialized assets
- modify config or project settings
- introduce new files into risk-sensitive areas

## Input

Expect:

- the requested change
- relevant project constraints
- affected files or likely change envelope

## Output Structure

Before editing, state:

- `约束摘要`
- `目标改动`
- `风险分类`
- `影响文件`
- `新增文件目标目录`
- `回滚方式`
- `是否需要重新确认`

## Risk Classes

Classify the requested edit before approval:

- `code-only`
- `scene-or-prefab`
- `serialization-sensitive`
- `config-or-project`
- `hot-update-or-lifecycle`
- `mixed-risk`

## Rules

- do not edit files, even if the user says "直接改", until the summarized scope is explicitly approved
- classify risk before discussing implementation details
- stop when the change envelope expands materially after inspection
- preserve the smallest safe approved scope

## Stop Conditions

Stop and realign before editing when:

- the best location for a new file is unclear
- the requested scope drifts after the summary is presented
- user changes conflict with the proposed plan
- the risk class expands materially after inspection
- the task should really be diagnosed first with another skill

## Handoffs

- hand off to `eye-unity-log-debug` if diagnosis is still unresolved
- hand off to `eye-unity-scene-audit` when the real uncertainty is scene wiring
- hand off to `balance-unity-contract-review` when the real uncertainty is protocol correctness
- hand off to `leg-unity-safe-implement` only after approval exists
