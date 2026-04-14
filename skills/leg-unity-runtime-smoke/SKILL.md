---
name: leg-unity-runtime-smoke
description: Use this skill for Unity runtime smoke validation after changes. It verifies whether a requested path can actually run in Play Mode, classifies the validation scope, separates compile success from runtime success, reports pass/fail/blocked clearly, and routes failures toward debugging, scene audit, or contract review when the smoke check breaks.
---

# Unity Runtime Smoke

## Role Contract

- `Primary Role`: runtime smoke validation
- `Secondary Role`: failure handoff routing
- `Can Block`: yes, when runtime proof is requested but the path cannot yet be entered or observed cleanly
- `Can Escalate`: yes, by redirecting to log debug, scene audit, contract review, or explicit validation debt
- `Depends On`: a concrete runtime path and an expected success condition
- `Specialization`: Unity-specific

Use this skill when the goal is runtime confidence, not root-cause diagnosis.

Read [references/runtime-smoke-checklist.md](references/runtime-smoke-checklist.md) when you need validation scope definitions, result criteria, or failure handoff guidance.

## Trigger

Use this skill when the user asks to:

- 做运行冒烟
- 验证主链
- 验证交互路径
- 看改动后还能不能跑通

## Input

Expect:

- the runtime path to validate
- the expected success condition
- any current environment constraints

## Core Goal

Validate the smallest meaningful runtime path and say clearly whether it passed, failed, or was blocked.

## Validation Scope

Classify the requested smoke check before running it:

- `entry-smoke`: can the app or scene enter the requested start point
- `main-path-smoke`: can the main user flow reach its expected end state
- `interaction-smoke`: does one key interaction work at a basic usable level
- `regression-smoke`: does a previously working path still run after a change

## Strong Trigger Prefixes

If the user starts with any of these, trigger this skill first:

- `冒烟验证：`
- `运行验证：`
- `主链验证：`
- `流程验证：`

Treat the content after `：` as the runtime path or validation scope.

## Workflow

1. define the smallest meaningful runtime path
2. identify the expected success condition
3. prepare a clean observation surface when needed
4. run only the minimum validation steps
5. inspect the critical runtime logs and visible state
6. classify the outcome as `通过`, `失败`, or `受阻`
7. recommend the next step

## Output Structure

Prefer this structure:

- `验证类型`：entry-smoke / main-path-smoke / interaction-smoke / regression-smoke
- `验证路径`：what was checked
- `结果`：`通过` / `失败` / `受阻`
- `关键观察`：what happened
- `日志结论`：blocking log or clear log surface
- `未覆盖范围`：what was not validated
- `下一步建议`：what to do next

## Boundary Rules

- do not present smoke validation as full QA
- do not turn this into deep diagnosis when a smoke run fails
- hand off to `eye-unity-log-debug` when runtime or compile analysis is required
- hand off to `eye-unity-scene-audit` when the path looks scene-side blocked
- hand off to `balance-unity-contract-review` when external payload correctness is the real blocker
- do not edit files as part of smoke validation unless a separate approved implementation step exists
