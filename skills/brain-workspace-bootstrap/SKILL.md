---
name: brain-workspace-bootstrap
description: Use this skill to quickly understand a new repository, worktree, or unfamiliar project before making changes, so later routing and implementation decisions start from real workspace evidence.
---

# Workspace Bootstrap

## Role Contract

- `Primary Role`: workspace orientation
- `Secondary Role`: capability-routing preparation
- `Can Block`: yes, when the workspace is still too unclear for safe next-step routing
- `Can Escalate`: yes, by handing off to `brain-skill-orchestrator`, `controller-work-state-controller`, or deeper domain skills once the workspace is understandable enough
- `Depends On`: an unfamiliar workspace, a new repo, or a request that clearly needs orientation first
- `Specialization`: generic

## Overview

Use this skill to build a minimal working map of a workspace before implementation starts.

Read [references/bootstrap-checklist.md](references/bootstrap-checklist.md) when the repo shape is unfamiliar or there are multiple plausible entry points.

## Core Goal

Reach "ready to work" understanding with the smallest possible inspection pass.

## Authority Boundary

This skill owns:

- shallow workspace orientation
- likely entry-point identification
- initial risk and unknown capture

This skill does not own:

- deep architectural review
- phase authority
- tool routing for every later step
- implementation

## Trigger

Use this skill when Codex needs to:

- understand a new repo first
- identify likely entry points
- discover build or runtime surfaces
- find the most relevant directories before further routing

## Input

Expect:

- the workspace itself
- the user's immediate goal, if known
- repo state and top-level structure

## Output

When this skill is active, produce:

1. `Workspace Type`
2. `Likely Entry Points`
3. `Important Areas`
4. `Relevant Tools or Commands`
5. `Known Risks or Unknowns`
6. `Best Starting Point`

## Workflow

1. inspect the top-level workspace shape
2. identify the stack, framework, or runtime family
3. find the likely execution or entry surfaces
4. locate the files or folders most relevant to the user request
5. stop once the workspace is understandable enough to act

## Rules

- keep the first pass shallow and high-signal
- prefer repo evidence over assumptions
- do not over-read unrelated files
- stop when there is enough context to move into the next phase
- if the user request is specific, orient around that request instead of mapping the whole repo

## Boundaries

- do not replace deeper research for new feature design
- do not browse the web when the repo itself can answer the bootstrap questions
- do not drift into implementation during orientation
- do not turn bootstrap into a full architecture review
