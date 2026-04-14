---
name: ear-interaction-intent-parse
description: Use this skill to translate fuzzy user language, product language, or subjective feedback into concrete engineering intent when the user describes something as feeling wrong, strange, jumpy, not smooth, unlike another product, or unclear in non-technical terms. Trigger it when the user is describing experience, feel, expectation, or dissatisfaction rather than naming a technical subsystem.
---

# Interaction Intent Parse

## Role Contract

- `Primary Role`: subjective-intent translation
- `Secondary Role`: diagnostic routing preparation
- `Can Block`: yes, when the user's statement is too ambiguous to map safely to a concrete next check
- `Can Escalate`: yes, by redirecting to comparison, state diff, or another evidence-gathering skill
- `Depends On`: fuzzy user language, product language, or experience-level dissatisfaction
- `Specialization`: generic

## Overview

Use this skill as the "ears" layer that converts subjective feedback into actionable intent without losing the user's actual meaning.

Read [references/intent-patterns.md](references/intent-patterns.md) when you need examples of common feedback patterns and their likely engineering translations.

## Trigger

Use this skill when the user says things like:

- 感觉不对
- 不够顺
- 不像 GPT
- 很跳
- 我以为它会怎样

## Input

Expect:

- the user's original wording
- any comparison target or expectation they mention
- current known context if available

## Core Goal

Preserve the user's felt problem while translating it into:

- observed symptom
- expected behavior
- likely subsystem or layer
- best next diagnostic question or action

## Workflow

1. extract the literal user wording
2. identify whether the complaint is about:
   feel, timing, continuity, correctness, expectation mismatch, or workflow friction
3. restate the issue in plain engineering terms
4. name the most likely layer involved
5. suggest the smallest next check or comparison

## Output Shape

When this skill is active, produce:

1. `User Wording`
2. `Parsed Intent`
3. `Expected Experience`
4. `Likely Layer`
5. `Suggested Next Step`

## Typical Translations

- "This feels weird"
  probably a runtime comparison or state mismatch problem
- "It is not smooth"
  probably timing, batching, animation, or streaming continuity
- "It does not feel like GPT"
  probably comparison against a reference interaction model
- "I thought it would do X"
  expectation mismatch or rule mismatch
- "This is too jumpy"
  likely layout reflow, scroll timing, or batch updates

## Important Rules

- do not dismiss vague language as low-value
- do not over-translate into implementation detail too early
- preserve the user's target feeling, not just the nearest code module
- prefer one strongest interpretation over many weak guesses
- if the statement is too ambiguous, propose the smallest clarifying comparison or test

## Do Not Use This Skill For

- explicit technical bug reports that already name the subsystem
- memory storage or handoff
- direct implementation when the user has already given a concrete spec
