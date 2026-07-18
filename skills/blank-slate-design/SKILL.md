---
name: blank-slate-design
version: 1.0.0
description: |
  Use when legacy or conventional thinking is biasing the solution. Start
  with zero assumptions and rebuild from the user's actual needs. The
  blank-slate question: "If we could start from scratch, what would we build
  and why?" Originated in UI empty-state design, generalizes to any domain.
triggers:
  - "we've always done it this way"
  - "let's start from scratch"
  - "what would we build if nothing existed"
  - "empty state design"
  - "legacy is clouding the answer"
tools: []
mutating: false
family: first-principles
---

# Blank Slate Design

Start with zero assumptions. Don't rely on similarities, legacy systems, or conventional wisdom. Ask: "If we could start from scratch, what would we build and why?"

## Contract

- The skill surfaces every assumption embedded in the current solution.
- For each assumption, the skill asks: true/necessary, or merely inherited?
- The skill discards the merely-inherited assumptions.
- The skill rebuilds the design from the truths that remain.
- The skill never collapses a true constraint into a soft one. Hard constraints stay.

## Phases

1. **State what you're designing as if nothing exists yet.** No reference to current implementation.
2. **List every assumption currently embedded in the existing solution.** From the user, from the code, from the docs.
3. **For each assumption, ask: true/necessary, or merely inherited?** Mark each.
4. **Discard the merely-inherited ones.** Keep the true/necessary.
5. **Rebuild the design from the truths that remain.**
6. **Compare to the current approach** using the dimensions table below.

## Output Format

The dimensions table, comparing blank-slate to the inherited approach:

| Dimension       | Inherited                | Blank slate                |
|-----------------|--------------------------|----------------------------|
| <dim 1>         | <current>                | <rebuilt>                  |
| <dim 2>         | <current>                | <rebuilt>                  |
| ...             |                          |                            |

Then the rebuilt design description in prose.

## Differences from a traditional approach (UI example)

| Dimension       | Traditional                | Blank slate                |
|-----------------|----------------------------|----------------------------|
| Empty state     | Show nothing               | Give something active      |
| Guidance        | Implicit                   | Immediately clear          |
| Visual / tone   | Neutral                    | Friendly, inviting         |
| Onboarding      | External docs              | Built-in                   |
| Example content | None                       | Pre-seeded                 |
| Assumptions     | Carried forward            | Continuously questioned    |
| Best for        | Expert users               | Onboarding new users       |

## Worked example (task management app — empty state)

Inherited design: when a new user logs in with no tasks, show an empty list. Add a tooltip "Click + to add a task."

Assumptions in the inherited design:
- Empty states are passive — ASSUMPTION (just convention)
- Users read tooltips — ASSUMPTION (they don't)
- Users will figure out the + button — ASSUMPTION (experts only)
- The product's job is task management — TRUE
- The user has at least one task in mind — ASSUMPTION (often they don't)

Discarded: all of the above except "the product's job is task management."

Rebuilt:
- Welcome the user with a headline.
- Give them a button to add their first task immediately.
- Show an example task as pre-seeded content.
- Offer a 30-second tour built into the page (not external docs).

This applies the blank-slate principles directly: active (give something), clear guidance, friendly tone, engagement-first, built-in onboarding, example context.

## Worked example (non-UI: community workshop)

Inherited design: mail out a printed agenda the day before; assume students will arrive prepared.

Assumptions:
- Mail is the right channel — ASSUMPTION (everyone checks email, but they ignore mass mail)
- Students prepare in advance — ASSUMPTION (they don't)
- The agenda is enough — ASSUMPTION (no welcome, no context)

Rebuilt: hand them a welcome booklet on arrival with the agenda embedded, plus interactive prompts. Don't rely on pre-preparation.

## Anti-Patterns

- Treating "blank slate" as "throw away domain knowledge." Keep the *true* constraints; only discard the inherited ones.
- Rebuilding without listing assumptions first. You'll just reproduce them under a new name.
- Skipping the compare table. The table is what proves the rebuild is meaningfully different.

## Tools Used

(none — pure reasoning skill)
