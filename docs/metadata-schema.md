# Metadata Schema

Every governed skill should publish the same core contract.

This keeps routing, maintenance, and migration legible.

## Required Fields

### `Primary Role`

The main responsibility this skill owns.

Examples:

- capability-family routing
- phase control
- risk interception
- runtime diagnosis
- tone modulation

### `Secondary Role`

An optional supporting responsibility.

Use `none` when the skill is intentionally narrow.

### `Can Block`

Whether the skill is allowed to stop progress temporarily.

If yes, say why.

### `Can Escalate`

Whether the skill can hand off upward or sideways when its own boundary is not enough.

If yes, say how.

### `Depends On`

What must already be true for this skill to be valid.

Examples:

- a broad user task
- a repeated failure pattern
- phase clarity
- explicit approval
- runtime evidence

### `Specialization`

Use one of:

- `generic`
- `Unity-specific`
- `tooling-family`
- `system`
- `compatibility`

## Why This Matters

Without a shared metadata contract:

- nearby skills become harder to distinguish
- routing becomes noisier
- migration decisions become hand-wavy
- maintenance falls back to name guessing

## Authoring Standard

Use [SKILL_TEMPLATE.md](../SKILL_TEMPLATE.md) for new public skills and major rewrites.
