# Pre-Edit Risk Matrix

## Risk Classes

| Class | Typical examples | What to emphasize |
| --- | --- | --- |
| code-only | localized script change | scope, affected files, compile validation |
| scene-or-prefab | prefab wiring, scene object setup | reference safety, serialized impact |
| serialization-sensitive | inspector field changes | compatibility and migration risk |
| config-or-project | ProjectSettings, packages, build config | broad blast radius |
| hot-update-or-lifecycle | boot path, loading, initialization order | runtime and ordering risk |
| mixed-risk | multiple categories at once | require tighter approval summary |

## Approval Checklist

Before edits, summarize:

- what will change
- which files are likely affected
- where new files would live
- what the main risk is
- how to roll back

## Stop Conditions

Pause when the target directory is unclear, the scope expands, or the task should be diagnosed before implementation.
