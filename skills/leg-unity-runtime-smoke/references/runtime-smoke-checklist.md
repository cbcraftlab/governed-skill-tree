# Runtime Smoke Checklist

## Validation Types

| Type | Best for | Minimum proof |
| --- | --- | --- |
| entry-smoke | scene or app entry | reaches intended start state without blocking errors |
| main-path-smoke | core user loop | reaches expected end state of the requested path |
| interaction-smoke | one key action | action can be performed and completes at basic usable level |
| regression-smoke | post-change confidence | previously working path still runs after the change |

## Result Rules

- `通过`: the requested path completed at smoke-test level and no blocking errors were observed
- `失败`: the path broke, emitted blocking errors, or could not reach the expected state
- `受阻`: tooling, environment, or missing prerequisites prevented full validation

## Failure Routing

- use `eye-unity-log-debug` when the first blocker is a runtime or compile failure
- use `eye-unity-scene-audit` when the path looks broken because of hierarchy, active state, or reference wiring
- use `balance-unity-contract-review` when the path depends on external protocol assumptions
