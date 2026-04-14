# Validation Matrix

Use this reference when the right validation depth is unclear.

## Choose By Change Type

### Code path change

- start with compile
- add targeted test if the code already has tests
- add runtime smoke if behavior depends on scene wiring, input, timing, or async flow

### Scene or prefab wiring

- compile is necessary but not sufficient
- prefer runtime smoke
- add hierarchy or scene inspection if the failure may be wiring related

### Config or contract change

- validate shape first
- confirm runtime consumption if the data drives behavior
- compare expected and actual payloads when possible

### UX or visual change

- compile proves little
- prefer runtime smoke plus capture comparison

## Good Output Examples

### Fast narrow validation

- `Validation Goal`: confirm the edited scripts still compile
- `Chosen Validation`: compile only
- `Why This Level`: no scene or runtime behavior changed
- `Result`: pass
- `Residual Risk`: runtime path not exercised
- `Next Step`: stop unless the user wants runtime confidence

### Runtime-first validation

- `Validation Goal`: confirm the new chat flow behaves correctly in play mode
- `Chosen Validation`: compile plus runtime smoke
- `Why This Level`: compile cannot prove scroll behavior or entry ordering
- `Result`: blocked
- `Residual Risk`: runtime state still unknown
- `Next Step`: run the relevant smoke path

## Escalation Rule

If a stronger validation is blocked by environment limits, name the blocked step and keep the lighter evidence separate.
