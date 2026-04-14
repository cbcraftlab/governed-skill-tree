# Evaluation Notes

This document explains why the governed skill tree is structured the way it is, and what kinds of failure modes it is designed to avoid.

It is not a benchmark report.
It is an evaluation note about system behavior, maintainability, and collaboration quality.

---

## What This System Is Trying To Improve

Most skill collections eventually drift toward one or more of these problems:

- too many responsibilities collapsed into one fuzzy layer
- weak distinction between planning, phase control, tool choice, and execution
- no explicit place for verification
- handoff and memory treated as afterthoughts
- skill growth happening reactively instead of deliberately

The governed skill tree is intended to reduce those problems by making the working path explicit.

---

## Core Hypothesis

The main hypothesis behind this repository is simple:

> Long-horizon human-AI collaboration becomes more stable when routing, phase control, tool choice, execution, verification, and continuity are treated as separate responsibilities.

This does not guarantee perfect outcomes.
But it improves the system's ability to stay understandable, governable, and extensible over time.

---

## Comparison: Flat Skill Pile vs Governed Skill Tree

### Flat Skill Pile

Typical characteristics:

- many skills exist at the same apparent layer
- trigger boundaries are weak or implicit
- routing, control, execution, and review are often blended together
- new skills are added because a problem appeared once
- handoff behavior depends too much on ad hoc prompting

Typical failure modes:

- the wrong skill activates too early
- the system answers before correctly framing the task
- tool choice is treated like phase control
- verification is skipped or vaguely implied
- continuity is lost between runs
- the skill inventory grows, but clarity does not

### Governed Skill Tree

Typical characteristics:

- responsibilities are intentionally separated
- the intake path is explicit
- phase control is distinct from routing
- tool choice is distinct from risk interception
- verification has its own place in the workflow
- compression, handoff, and storage are continuity outputs, not leftovers
- system growth is governed instead of purely reactive

Expected advantages:

- clearer reasoning about why a skill exists
- fewer silent overlaps between control surfaces
- safer domain execution
- better continuity across long-running work
- easier maintenance as the tree expands

---

## Why Separation Matters

This repository deliberately separates:

- **Capability Routing**
- **Phase Control**
- **Tool Routing**
- **Domain Skill Execution**
- **Verification**
- **Compression / Handoff / Storage**

The point is not theoretical purity.

The point is that when these layers collapse into each other, the system becomes harder to understand and harder to trust.

Examples:

- If routing and phase control blur together, the system may classify a task correctly but still respond in the wrong phase.
- If tool choice and approval logic blur together, the system may select a valid tool but apply it without proper risk review.
- If execution and verification blur together, the system may treat completion as success without checking outcomes.
- If continuity is not explicit, long-horizon work becomes fragile across windows, threads, or sessions.

---

## Governance-Specific Benefits

### 1. Better Authority Boundaries

A governed tree makes it easier to define:

- who decides what kind of task this is
- who controls the current work phase
- who selects tools
- who can block risky work
- who handles continuity outputs

This matters because many system failures are not caused by weak skills.
They are caused by overlapping authority.

### 2. Better Maintenance

A new skill is easier to judge when you can ask:

- which layer does it belong to
- what problem does it solve
- why is an existing skill not enough
- what trigger should activate it
- what boundary must it not cross

Without that structure, skill growth becomes clutter.

### 3. Better Collaboration

In long-horizon human-AI work, the user is not only asking for execution.
The user also needs:

- predictable routing
- stable phase behavior
- continuity across conversations
- understandable summaries and handoffs

Governance improves collaboration because it reduces surprise.

---

## What This Repository Does Not Claim

This repository does not claim:

- that every project needs organ-style layering
- that flat collections are always bad
- that governance replaces good prompts, tools, or models
- that this design is complete

Instead, it claims something narrower:

> If a skill system is expected to grow, cross phases, support domain execution, and preserve continuity over time, governance becomes increasingly valuable.

---

## Evaluation Criteria To Expand Later

Future evaluation notes may include:

- before/after comparisons of skill routing quality
- examples of phase confusion in flatter systems
- examples of safer execution through explicit verification
- examples of better continuation through structured handoff
- examples of governed skill growth vs reactive skill accumulation

---

## Current Status

This repository currently provides:

- the governed core concept
- the intake path structure
- governance notes
- metadata rules
- migration logic
- example slices
- one domain-oriented showcase

It does not yet provide a full benchmark suite.

That is intentional for the current public slice.

---

## Practical Conclusion

The governed skill tree is not mainly about having more skills.

It is about making skill systems easier to reason about, easier to extend, and harder to destabilize as collaboration becomes longer, messier, and more real.
