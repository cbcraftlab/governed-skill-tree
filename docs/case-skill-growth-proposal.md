# Case: Skill Growth Proposal

This case shows why a governed skill system should not grow by reflex.

When a workflow issue appears, the default response should not be:

> add another skill

The better response is:

> diagnose the problem, then decide whether growth is actually justified

This is how a governed system avoids turning useful capability into unmanaged sprawl.

---

## Why this case exists

Many AI workflows become harder to maintain for a simple reason:

they treat every repeated inconvenience as evidence that a new skill is needed.

At first, this feels productive.

A new edge case appears.
A new instruction is added.

A recurring failure appears.
A new skill is added.

A special handoff need appears.
Another helper is added.

The system grows, but the growth is reactive.

Over time, this creates a familiar pattern:
- more pieces
- more overlap
- more hidden conflicts
- less confidence about what should happen next

The problem is not growth itself.

The problem is unguided growth.

---

## Scenario

A human and an AI are working together over time on a structured workflow.

The collaboration is generally useful, but one friction point keeps appearing:

the assistant sometimes handles mid-stream requests inconsistently.

In some sessions, it jumps too early into execution.
In others, it stays too long in clarification.
In handoff moments, some context is preserved well and some is lost.

The team notices the friction and asks:

**Should we add a new skill?**

This case examines how that decision changes under two different system models.

---

## Reflex model: grow on every pain

In the reflex model, repeated friction is treated as direct evidence that the system needs another skill.

The logic is simple:

- something failed
- the current setup was not enough
- therefore a new skill should be added

This model feels fast because it produces immediate action.

But it often skips the most important question:

**What kind of problem is this, actually?**

### Common reflex responses

When friction appears, teams often do one of the following:

- add a new skill for the failing case
- add another instruction to an existing skill
- create a narrow helper for one repeated scenario
- patch the symptom without changing routing logic
- duplicate behavior that already partially exists elsewhere

This reduces local pain, but it often increases global confusion.

---

## Why this fails

### 1. One-off noise gets treated as structural need

Not every recurring annoyance deserves system growth.

Some issues are:
- user-specific variance
- temporary instability
- wording sensitivity
- normal operating noise

If the system grows around every irritation, it starts overfitting to fragments.

### 2. Routing failures get misdiagnosed as missing capability

A request may fail not because the system lacks a skill, but because:
- the wrong stage was activated
- the handoff boundary was weak
- existing skills overlapped without clear routing
- the assistant switched modes too early

Adding a new skill does not fix diagnosis errors.
It often hides them.

### 3. Local fixes create global complexity

Each additional skill may be reasonable on its own.

But the system is not experienced one skill at a time.
It is experienced as a whole.

As more skills accumulate:
- discovery gets harder
- overlap grows
- behavior becomes less legible
- maintenance cost rises faster than capability

### 4. Growth becomes easier than governance

Once a system gets used to reactive expansion, adding new parts starts to feel easier than improving structure.

That is the trap.

The system becomes good at expanding, but weak at regulating expansion.

---

## Governed model: proposal before growth

In a governed system, repeated friction does not automatically trigger new capability.

It triggers evaluation.

The key shift is this:

**growth is a proposal, not a reflex**

That means the system first asks:
- Is this a true repeated pattern?
- Is the problem capability, routing, stage control, or continuity?
- Would a new skill reduce complexity, or add to it?
- Is revision better than expansion?

Only after that does it decide whether growth is warranted.

---

## The governed decision flow

### Step 1: Detect repeated friction

The first threshold is repetition.

The system should not grow because of one awkward interaction.
It should only enter growth evaluation when a pattern appears across multiple uses.

The signal is not:
- one bad run

The signal is more like:
- repeated failure under similar conditions
- recurring ambiguity in the same workflow segment
- stable pain that survives normal phrasing differences

### Step 2: Diagnose the source of failure

Before proposing growth, the system should determine what kind of issue it is dealing with.

Possible causes include:
- missing capability
- weak routing
- poor stage separation
- overlapping skills
- weak handoff structure
- unclear entry conditions
- bad naming or discoverability

This step matters because different failures require different fixes.

### Step 3: Evaluate response options

A governed system should consider several possible responses:

- add a new skill
- revise an existing skill
- improve routing rules
- tighten stage boundaries
- merge overlapping skills
- document a usage pattern without changing the system
- reject the change entirely

Adding a skill should be only one option among several.

### Step 4: Write a growth proposal

If growth still looks justified, the change should be proposed explicitly.

That proposal should explain:
- what problem is being solved
- why existing structure is insufficient
- why the issue is not better solved by governance changes
- what new complexity the addition may create
- how the new skill will be routed and constrained

This turns growth into a design decision instead of an impulse.

### Step 5: Decide deliberately

The final decision should be made at the system level, not just the symptom level.

The question is not:

> would this new skill be useful?

The better question is:

> would this make the whole system more governable?

That is a much higher bar, and it is the right one.

---

## Example growth proposal template

A lightweight proposal can be as simple as this:

### Proposed change
Add, revise, merge, or reject a skill-level change.

### Repeated friction
What pattern has appeared more than once?

### Current failure mode
What is going wrong in the current workflow?

### Root cause hypothesis
Is this mainly a capability gap, routing problem, stage problem, continuity problem, or overlap issue?

### Alternatives considered
What other fixes were considered besides adding a new skill?

### Decision
What should change now?

### Governance impact
How will this affect routing, overlap, maintenance, and future growth?

This keeps the system from growing in the dark.

---

## Example decision outcomes

A governed review does not always end in expansion.

### Outcome A: Add a new skill

This is appropriate when:
- the task is clearly distinct
- repeated demand is real
- current skills cannot absorb it cleanly
- routing can remain clear after addition

### Outcome B: Revise an existing skill

This is appropriate when:
- the capability already exists in rough form
- the real issue is weak definition or coverage
- adding a new skill would create overlap

### Outcome C: Improve routing

This is appropriate when:
- multiple skills already exist
- the wrong one is being activated
- the issue is flow control, not missing function

### Outcome D: Tighten stage boundaries

This is appropriate when:
- the assistant shifts modes too early
- planning and execution bleed into each other
- handoff and active work are not clearly separated

### Outcome E: Reject growth

This is appropriate when:
- the issue is too narrow
- the pattern is not stable yet
- the cost of growth is higher than the value of growth

A healthy system must be able to say no.

---

## What changed structurally

The difference between the two models is not speed.

It is discipline.

### Reflex model
- friction leads directly to expansion
- local relief is prioritized
- system shape changes opportunistically

### Governed model
- friction leads first to diagnosis
- multiple responses are evaluated
- expansion must justify itself structurally

This is how a system stays coherent as it becomes more capable.

---

## Side-by-side comparison

| Dimension | Reflex Growth | Governed Growth Proposal |
|---|---|---|
| Default response to friction | Add something | Diagnose first |
| View of repeated pain | Immediate evidence of missing skill | Signal for evaluation |
| Alternatives considered | Often few | Explicitly compared |
| Root cause analysis | Weak or skipped | Required |
| Risk of overlap | High | Lower |
| Maintainability | Degrades over time | Better protected |
| Structural coherence | Incidental | Deliberate |
| Ability to reject growth | Weak | Strong |

---

## Why this matters

Skill systems often fail slowly.

Not because they stop being useful.
Because they stop being governable.

Each new addition may help in isolation while making the whole harder to reason about.

That is why growth must be governed.

A good system does not just become larger.
It becomes more intentional.

---

## Takeaway

A governed skill tree should not grow every time it feels friction.

It should grow when repeated evidence, diagnosis, and structural judgment all point in the same direction.

That is the difference between capability expansion and system design.

Good systems do not just grow.

They govern growth.

---

## Next case

- [Case: Handoff and Continuity](./case-handoff-continuity.md)
