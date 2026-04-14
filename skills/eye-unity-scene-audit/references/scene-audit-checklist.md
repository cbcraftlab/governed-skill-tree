# Scene Audit Checklist

## Core Checks

Use the smallest useful checklist for the target:

- object exists where the flow expects it
- required components are attached
- serialized references are populated
- active-state gates do not block the path unexpectedly
- duplicate managers or conflicting instances are not present
- hierarchy path matches lookup assumptions

## Boundary Heuristics

Prefer scene-side classification when:

- the object is missing or inactive
- a serialized reference is empty
- the hierarchy path is wrong
- the required component is absent
- the expected manager exists twice

Prefer code-side classification when:

- the scene looks correct but runtime logic still fails
- the object is found but behavior is wrong inside code
- the failure depends on external payload timing or shape

## Reporting Rule

Name the exact object, component, or reference mismatch. Do not stop at a vague statement such as "scene may be wrong".
