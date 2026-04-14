---
name: balance-dependency-impact-scan
description: Use this skill before a change to scan what code paths, assets, contracts, scenes, tools, tests, or workflows are likely to be affected by the target modification.
---

# Dependency Impact Scan

## Role Contract

- `Primary Role`: pre-change impact scanning
- `Secondary Role`: validation-scope sizing
- `Can Block`: yes, when the blast radius is still too unclear for safe implementation
- `Can Escalate`: yes, by redirecting to architecture review, safer scoping, or stronger verification planning
- `Depends On`: a known change target with uncertain dependency or regression scope
- `Specialization`: generic

## Overview

Use this skill before implementation when the change target is known but the blast radius is not.

This is a balance-layer skill because its primary purpose is to bound change risk before edits begin.

## Trigger

Use this skill when:

- you know what you want to change
- but you do not yet know what else it will affect

## Input

Expect:

- the intended change target
- relevant dependents or surrounding structure
- the current verification expectation if known

## Core Goal

Map the likely impact envelope of a planned change so implementation and verification stay proportional to real risk.

## When To Use

Use this skill when:

- a script, component, config, contract, or shared utility is about to change
- the main fear is "what else will this touch"
- the change spans dependencies that are easy to miss in a local edit
- verification scope is unclear because impact scope is unclear

## Workflow

1. identify the intended change target
2. scan direct dependents and closely coupled surfaces
3. identify indirect risks, runtime paths, or compatibility edges
4. propose the smallest safe change envelope
5. recommend the verification scope implied by that impact

## Output Shape

When this skill is active, produce:

1. `Change Target`
2. `Direct Dependents`
3. `Indirect Risks`
4. `Safe Change Envelope`
5. `Verification Impact`
6. `Next Safe Action`

## Rules

- focus on impact, not full architecture redesign
- separate confirmed dependents from suspected ones
- highlight shared utilities and protocol boundaries early
- let impact size influence validation size

## Boundaries

- do not replace implementation planning once the impact envelope is already clear
- do not perform the implementation itself
- do not replace `brain-tool-routing` for tool choice
- do not replace `balance-assumption-audit` when the main issue is evidence quality rather than dependency scope
