# Debug Triage

## Goal

Use this checklist to classify Unity failures quickly and decide whether to stay in debug mode or hand off.

## Failure Matrix

| Class | Typical signs | First checks | Common handoff |
| --- | --- | --- | --- |
| compile | CS errors, assembly failures, missing namespaces | compiler output, changed files, asmdef or package references | `leg-unity-safe-implement` after approval |
| runtime | exceptions, initialization failures, null refs | latest runtime logs, reproduction step, startup order | `leg-unity-safe-implement` after approval |
| scene-side | object not found, missing references, inactive gate | hierarchy, components, serialized refs, active state | `eye-unity-scene-audit` |
| contract-side | wrong IDs, payload drift, protocol lifecycle mismatch | docs, payload logs, field types, ownership | `balance-unity-contract-review` |
| test-side | isolated test failure, fixture/setup break | failing test output, setup path, deterministic reproduction | stay here or hand off after cause is clear |

## Root-Cause Rules

- Prefer the first actionable blocker over the loudest log.
- Treat repeated downstream exceptions as noise until the upstream fault is explained.
- If one compile error can explain many later errors, stop there first.
- If runtime failures happen only after a scene enters a path, check whether the scene-side gate is broken before editing logic.
- If the failure depends on external payload shape, verify the contract before changing Unity parsing.

## Reporting Standard

Always separate:

- confirmed evidence
- inferred cause
- proposed fix
- remaining uncertainty
