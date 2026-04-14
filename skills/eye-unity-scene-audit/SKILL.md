---
name: eye-unity-scene-audit
description: Use this skill to inspect Unity scenes, prefabs, hierarchy wiring, serialized references, active-state gates, and runtime entry object setup when the main uncertainty is scene-side.
---

# Unity Scene Audit

## Role Contract

- `Primary Role`: scene-side inspection
- `Secondary Role`: diagnosis boundary classification
- `Can Block`: yes, when scene evidence is missing or the target is too unclear to audit safely
- `Can Escalate`: yes, by handing off to log debug, contract review, or safe implementation
- `Depends On`: a scene, prefab, hierarchy, reference, or runtime-entry setup question
- `Specialization`: Unity-specific

## Overview

Use this skill when the main question is whether a scene, prefab, hierarchy, or runtime entry setup is wired correctly.

Read [references/scene-audit-checklist.md](references/scene-audit-checklist.md) when you need a scene-side checklist or a boundary heuristic between scene problems and code problems.

## Core Goal

Answer one focused question: is the failure scene-side, code-side, or still unclear?

## Authority Boundary

This skill owns:

- scene-side inspection
- hierarchy and serialized-reference verification
- scene-vs-code boundary judgment based on concrete evidence

This skill does not own:

- generalized runtime log diagnosis
- contract correctness review
- scene modification without a separate approved implementation step

## Trigger

Use this skill when the user asks to:

- inspect scene wiring or prefab setup
- verify hierarchy paths or object presence
- check missing references or component attachments
- audit UI, camera, bootstrap, or manager setup
- judge whether an issue is caused by scene-side configuration

## Input

Expect:

- a scene target, prefab target, hierarchy path, or flow under inspection
- expected success condition when known

## Output Structure

Prefer this structure:

- `检查目标`
- `结果`
- `关键发现`
- `影响范围`
- `边界判断`
- `下一步建议`

## Rules

- do not claim a scene problem without a concrete mismatch
- do not invent a scene-side explanation when the scene looks correct
- do not broaden the audit into general runtime debugging
- do not modify scenes, prefabs, or serialized data unless a separate approved implementation step exists

## Handoffs

- hand off to `eye-unity-log-debug` when runtime evidence, not scene structure, is driving the diagnosis
- hand off to `leg-unity-safe-implement` only after a specific scene or code fix is approved
- hand off to `balance-unity-contract-review` when the path depends on external payload assumptions rather than local scene wiring
