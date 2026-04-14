# Contributing

Thanks for helping improve the tree.

This project is not optimized for "add a new skill quickly at any cost."

It is optimized for adding skills without breaking routing clarity.

## Before You Add A Skill

Check these questions first:

1. is this a real capability gap, or just weak invocation discipline?
2. is the issue actually a boundary problem between existing skills?
3. can the problem be solved by sharpening one current skill?
4. is the new skill reusable enough to maintain over time?

If the answer is still "yes, a new skill is needed," use:

- `brain-capability-gap-detect`
- [SKILL_TEMPLATE.md](SKILL_TEMPLATE.md)

## Authoring Rules

Every public skill should declare:

- `Primary Role`
- `Secondary Role`
- `Can Block`
- `Can Escalate`
- `Depends On`
- `Specialization`

Every skill should also define:

- what it owns
- what it does not own
- when to hand off

## Boundary Rules

Do not submit a skill that:

- silently duplicates an existing skill
- steals phase authority from `controller-work-state-controller`
- steals routing authority from `brain-skill-orchestrator`
- steals tool-surface choice from `brain-tool-routing`
- bypasses a `balance-*` veto by wording alone

## Preferred Contribution Types

- clearer examples
- tighter boundary wording
- better metadata consistency
- domain packs that respect the governed core
- migration notes for compatibility layers

## Good First Contributions

- add a new example flow
- improve one skill's boundary clarity
- refine one governance note
- propose one carefully justified domain pack

## Scope Rule

Public contributions should strengthen the governed core first.

If a contribution adds a domain-specific pack, it should still make sense to readers who are not in that domain.
