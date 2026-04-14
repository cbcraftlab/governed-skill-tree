---
name: brain-capability-gap-detect
description: Use this skill to detect recurring capability gaps in the current skill system and propose whether a new skill, boundary adjustment, or layer placement change is warranted. Trigger it when repeated tasks, repeated mistakes, or repeated ad-hoc reasoning suggest the existing skill tree is missing a reusable capability.
---

# Capability Gap Detect

## Role Contract

- `Primary Role`: capability-gap detection
- `Secondary Role`: skill-growth proposal framing
- `Can Block`: yes, when the team is about to add a new skill but the gap has not yet been distinguished from simple overlap or naming noise
- `Can Escalate`: yes, by redirecting to "no new skill", "refine an existing skill", "add a new skill", or "adjust boundaries only"
- `Depends On`: repeated workflow friction, recurring mistakes, recurring ad-hoc reasoning, or an explicit request to assess whether a new skill should exist
- `Specialization`: generic

## Overview

Use this skill to judge whether the current skill tree is actually missing a reusable capability.

It helps the system grow deliberately instead of reacting to every friction point with another skill name.

## Core Goal

Produce one disciplined answer:

- no new skill needed
- an existing skill should be sharpened
- a new skill should be added
- a boundary between skills should be adjusted

## Authority Boundary

This skill owns:

- identifying repeated capability gaps
- deciding whether the right answer is a new skill, a refinement, or no change
- proposing the safest layer placement and boundary definition

This skill does not own:

- creating or modifying skills without approval
- silently expanding the skill tree
- replacing the actual authoring step once a new skill is approved

If the task is really about implementing a newly approved skill, hand off to `.system/skill-creator` and the standard `SKILL_TEMPLATE.md` workflow instead of keeping this skill in control.

## Trigger

Use this skill when:

- the same task pattern keeps reappearing
- the same class of mistake keeps reappearing
- current work depends too much on temporary judgment rather than a stable workflow
- the user asks whether a new organ skill or helper skill should be added

## Typical Trigger Examples

- "这类任务这两周已经重复出现三次了，感觉现在总靠临时判断在做，要不要沉淀成 skill？"
- "我们最近总在同一种边界问题上来回补丁，现有 skill 是不是少了一个中间层？"
- "先别急着加 skill，帮我判断这到底是缺能力，还是现有 skill 边界没写清。"

## Input

Expect:

- examples of repeated friction, mistakes, or repeated task patterns
- the current nearby skills and their boundaries
- the desired outcome if a new capability were added

## Output

When this skill is active, produce:

1. `Observed Repetition`
2. `Gap Judgment`
3. `Recommended Action`
4. `Proposed Layer And Name`
5. `Boundary With Existing Skills`
6. `Why This Is Worth Maintaining`

## Workflow

1. identify the repeated task, repeated mistake, or repeated reasoning burden
2. check whether an existing skill already covers it in principle
3. decide whether the issue is missing capability, weak boundary, weak naming, or simple discipline drift
4. if a new skill is justified, propose the smallest safe skill concept
5. define the recommended organ layer, name, and boundaries
6. stop for approval before any skill is added or changed

## Rules

- do not propose a new skill just because one task felt annoying once
- prefer sharpening an existing boundary before creating a new skill
- distinguish "missing capability" from "poor invocation discipline"
- prefer the smallest reusable capability that solves the repeated problem
- say explicitly when no new skill should be added

## Boundaries

- do not auto-create or auto-modify skills
- do not invent new organs casually
- do not confuse a one-off convenience with a real capability gap
- do not override governance rules just because a proposal sounds elegant

## Handoffs

- hand off to `brain-skill-orchestrator` when the real issue is task routing rather than skill-tree growth
- hand off to `balance-assumption-audit` when the supposed gap is really weak evidence or unverified assumptions
- hand off to `.system/skill-creator` and `SKILL_TEMPLATE.md` only after the user approves the proposed new skill or boundary change
