# Governed Skill Tree

> A governed skill system for long-horizon human-AI collaboration.

Governed Skill Tree is an organ-based skill system for human-AI collaboration.

It separates routing, phase control, tool choice, risk interception, verification, memory, and communication into explicit governed layers so a skill tree can grow without turning into prompt soup.

This first public batch focuses on the minimum set needed to show the design clearly.

## 中文简介

这是一个面向人机协作的“受治理技能树”实验。

它不是简单堆一堆 prompt 或 skill，而是把一套长期会增长的 AI 能力系统，拆成更清楚的职责层：

- `brain` 负责任务归类和能力路由
- `controller` 负责阶段判断和阶段切换
- `brain-tool-routing` 负责当前步骤的工具选择
- `balance` 负责风险拦截、假设审计和影响范围约束
- `leg` 负责实现与验证
- `memory` / `collab` 负责记忆、交接和对人表达

当前公开版先放通用核心，再放一个 `Unity showcase pack` 作为成熟案例。

也就是说，`Unity 不是这套系统的全部，而是目前最完整的链路。`

## Where to Start

If you're new to this repo, use this reading order:

1. **This README**
   - Understand the core idea, system flow, and public scope.

2. **`docs/governance.md`**
   - Read this to understand authority boundaries, conflict handling, and why the system is governed instead of flattened.

3. **`docs/intake-pipeline.md`**
   - Read this to see how work moves through the system:
     bootstrap → routing → phase control → tool choice → execution → verification → handoff.

4. **`docs/evaluation-notes.md`**
   - Read this if you want the rationale behind the separation model and the failure modes this system is designed to reduce.

5. **`SKILL_TREE.md`**
   - Use this as the logical map of the current skill structure, migration status, and layering strategy.

6. **Examples**
   - Start with the example closest to your use case:
     - **Ambiguous Task Routing** → best entry point for request classification
     - **Pre-Change Risk And Dependency Scan** → best entry point for safe execution
     - **Unity Debug To Runtime Smoke** → best entry point for domain workflow
     - **Skill Growth Proposal** → best entry point for governed evolution

If you only read one thing after this README, read **`docs/governance.md`** first.

## Release Notes

- **[`docs/release-notes-v0.1.0.md`](docs/release-notes-v0.1.0.md)**  
  First public slice of the repository.

- **[`docs/release-scope.md`](docs/release-scope.md)**  
  What is intentionally included in the public slice, and what is intentionally left out.

- **[`docs/release-checklist.md`](docs/release-checklist.md)**  
  Release readiness checklist for this repository.

## Who This Is For

This repo is for people who are trying to move beyond:

- flat skill folders
- giant prompt piles
- loosely coupled agent behaviors
- unclear routing between planning, execution, verification, and handoff

It is especially relevant if you care about:

- long-horizon human-AI collaboration
- governed task routing
- explicit phase control
- safer domain execution
- deliberate skill growth over time

## Why It Feels Different

Most skill collections collapse several responsibilities into one fuzzy layer.

This project pushes them apart on purpose:

- routing is not phase control
- phase control is not tool choice
- tool choice is not risk approval
- growth is not "just add another skill"
- domain packs are not the same thing as the generic core

That separation is the main idea.

## At A Glance

- explicit routing authority
- phase control
- tool-surface boundaries
- risk interception
- proportional verification
- memory and collaboration rules
- a unified skill authoring template

## Why This Exists

Most agent skill sets become harder to maintain as they grow:

- boundaries start overlapping
- routing becomes fuzzy
- "just use the right tool" is not enough
- migration gets messy
- the same judgment keeps getting re-invented

This project treats the skill layer as a governed operating surface, not just a registry.

## Core Ideas

- `organ-based logical layering`
  Skills are grouped by what kind of responsibility they own.
- `flat physical storage`
  Live skills still sit in a flat `skills/` directory for runtime compatibility.
- `hard authority boundaries`
  Routing, phase control, tool choice, risk interception, execution, and human-facing output do not silently collapse into one layer.
- `task intake pipeline`
  A task should enter the system in a predictable order.
- `gradual evolution`
  The system should be able to grow without becoming a naming graveyard.

## First Public Batch

This release focuses on the smallest set that shows the system's shape clearly.

### Core Generic Skills

- `brain-workspace-bootstrap`
- `brain-skill-orchestrator`
- `controller-work-state-controller`
- `brain-tool-routing`
- `balance-assumption-audit`
- `balance-dependency-impact-scan`
- `brain-capability-gap-detect`
- `ear-interaction-intent-parse`
- `eye-state-diff-inspector`
- `collab-tone-regulator`
- `memory-memory-router`
- `memory-layered-memory`
- `leg-verification-runner`

### Unity Showcase Pack

- `balance-unity-codex-guard`
- `eye-unity-log-debug`
- `eye-unity-scene-audit`
- `leg-unity-runtime-smoke`

The Unity pack is included as a flagship domain example, not as the whole identity of the system.


## System Flow

The system stays governable by separating the main path of work into distinct layers:

```mermaid
flowchart LR
    A[Workspace Bootstrap] --> B[Capability Routing]
    B --> C[Phase Control]
    C --> D[Tool Routing]
    D --> E[Domain Skill Execution]
    E --> F[Verification]
    F --> G[Compression / Handoff / Storage]
```

## What Makes This Different

- `routing is not phase control`
  `brain-skill-orchestrator` chooses the capability family, but not the work phase.
- `phase control is not tool choice`
  `controller-work-state-controller` owns phase transitions, but not which execution surface to use.
- `tool choice is not risk approval`
  `brain-tool-routing` can choose the current tool surface, but cannot approve risky work.
- `governance is explicit`
  `balance-*` skills can intercept unsafe moves instead of relying on vague "be careful" wording.
- `growth is governed`
  `brain-capability-gap-detect` helps decide whether a new skill is actually needed before the tree expands.

## What This Is Not

This repository is intentionally not:

- a giant prompt dump
- a replacement for every agent framework
- a Unity-only toolkit
- a claim that one naming scheme solves coordination by itself

The goal is more practical:

build a skill system that can keep growing without losing routing clarity, safety boundaries, or maintainability.

## How It Works

Default intake flow:

1. bootstrap the workspace if needed
2. classify the task and choose the lead organ
3. determine the current work phase
4. choose the current execution surface
5. run the domain skill
6. verify proportionally
7. compress, hand off, or store the result

Read:

- [SKILL_TREE.md](SKILL_TREE.md)
- [docs/governance.md](docs/governance.md)
- [docs/intake-pipeline.md](docs/intake-pipeline.md)
- [docs/metadata-schema.md](docs/metadata-schema.md)
- [docs/release-scope.md](docs/release-scope.md)
- [docs/what-this-is-not.md](docs/what-this-is-not.md)

## Repository Layout

```text
.
├─ README.md
├─ SKILL_TREE.md
├─ SKILL_TEMPLATE.md
├─ docs/
├─ examples/
└─ skills/
```

The `skills/` directory is intentionally flat.

That is part of the runtime compatibility model, not an accident.

## Quick Start

If you want to try the structure in a Codex-compatible environment:

1. copy the skill folders from `skills/` into your `$CODEX_HOME/skills`
2. keep the physical layout flat
3. use [SKILL_TREE.md](SKILL_TREE.md) as the governed index
4. use [SKILL_TEMPLATE.md](SKILL_TEMPLATE.md) for new skill authoring

## Examples

- [Ambiguous Task Routing](examples/ambiguous-task-routing.md)
- [Pre-Change Risk And Dependency Scan](examples/pre-change-risk-and-dependency-scan.md)
- [Unity Debug To Runtime Smoke](examples/unity-debug-to-runtime-smoke.md)
- [Skill Growth Proposal](examples/skill-growth-proposal.md)

## Contributing

If you want to extend the tree, start here:

- [CONTRIBUTING.md](CONTRIBUTING.md)
- [SKILL_TEMPLATE.md](SKILL_TEMPLATE.md)

New public skills should strengthen the governance model, not bypass it.

## Roadmap

Near-term priorities:

- refine more public examples
- add clearer domain-pack boundaries
- publish evaluation and comparison notes
- expand beyond the first showcase pack carefully

## Release Prep Note

Before creating the public repository or first tag, use:

- [docs/release-checklist.md](docs/release-checklist.md)

## License

This repository is licensed under [Apache-2.0](LICENSE).

## Current Release Boundary

This repository is a deliberate first slice, not the entire internal system.

It prioritizes:

- the governed core
- the metadata model
- the intake pipeline
- one mature domain showcase

It intentionally does not try to publish every internal skill on day one.
