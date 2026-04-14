---
name: <skill-name>
description: "<one-sentence description of what this skill does, when it should be used, and what boundary it respects>"
---

# <Skill Title>

## Role Contract

- `Primary Role`: <main system role>
- `Secondary Role`: <optional supporting role or `none`>
- `Can Block`: <yes/no and why>
- `Can Escalate`: <yes/no and how this skill escalates or hands off>
- `Depends On`: <upstream context, phase, approval, evidence, or user intent required>
- `Specialization`: <generic / Unity-specific / tooling-family / system / compatibility>

## Overview

Use this skill to <plain-language summary of the job>.

Read [references/<reference-file>.md](references/<reference-file>.md) when <the boundary or deeper checklist needs clarification>.

## Core Goal

State the smallest useful success condition for this skill.

Example:

- classify the task correctly
- produce one actionable diagnosis
- generate one continuity artifact
- choose one safe validation path

## Authority Boundary

This skill owns:

- <decision or artifact this skill is allowed to produce>
- <second owned responsibility>

This skill does not own:

- <neighboring responsibility that belongs to another layer>
- <another thing it must not silently take over>

If the task is really about <neighboring concern>, hand off to `<other-skill>`.

## Trigger

Use this skill when:

- <trigger pattern 1>
- <trigger pattern 2>
- <trigger pattern 3>

## Input

Expect:

- <input evidence or request shape 1>
- <input evidence or request shape 2>
- <input evidence or request shape 3>

## Output

When this skill is active, produce:

1. `<output field 1>`
2. `<output field 2>`
3. `<output field 3>`
4. `<output field 4>`
5. `<output field 5>`

Keep the shape stable so nearby skills and future maintenance stay predictable.

## Workflow

1. <first step>
2. <second step>
3. <third step>
4. <fourth step>
5. <final step>

## Rules

- <rule about staying narrow>
- <rule about evidence quality>
- <rule about not over-claiming>
- <rule about honesty, approval, or residual risk>

## Boundaries

- do not <common overreach 1>
- do not <common overreach 2>
- do not replace `<neighbor-skill>` when the task is really about that layer

## Handoffs

- hand off to `<skill-a>` when <condition>
- hand off to `<skill-b>` when <condition>
- hand off to `<skill-c>` when <condition>

## Optional Sections

Add these only when they materially help the skill:

- `Phase Set`
- `Validation Ladder`
- `Risk Classes`
- `Layer Model`
- `Trigger Prefixes`
- `Output Structure`
- `Examples`
- `Stop Conditions`
- `Compatibility Notes`

## Authoring Notes

Use this template as the default for all new skills.

Practical guidance:

- keep `Role Contract` concise and operational
- define `Authority Boundary` before adding more workflow detail
- keep `Trigger`, `Input`, and `Output` specific enough to disambiguate neighboring skills
- if a skill overlaps with another skill, clarify `Primary Role` instead of inventing vague wording
- if the skill is a compatibility bridge, say so explicitly in `Specialization` or `Compatibility Notes`
- if the skill is tool-family only, make clear that it acquires or operates rather than interprets
