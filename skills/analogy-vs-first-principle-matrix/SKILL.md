---
name: analogy-vs-first-principle-matrix
version: 1.0.0
description: |
  Use as a meta-skill before applying any first-principles framework. A 2x2
  matrix that decides whether the problem should be reasoned by analogy
  (copy/improve a similar solution — faster, safer when an analogous problem
  has a proven solution) or by first principles (derive from fundamentals —
  slower, optimal when the analogous solution is itself failing). Axes:
  stakes (low/high) and novelty (analogy-available / not).
triggers:
  - "should we just do what X did"
  - "is analogy enough here"
  - "analogy vs first principles"
  - "copy or rebuild"
  - "incremental or fundamental"
tools: []
mutating: false
family: decision
---

# Analogy vs First Principle Matrix

A 2x2 to decide (and label) whether a problem should be reasoned by analogy (copy/improve a similar solution) or by first principles (derive from fundamentals).

## Contract

- The skill assesses two axes: stakes (low / high) and novelty (analogy can supply a proven answer / not).
- The skill picks the quadrant and the default within it.
- The skill routes to the corresponding mode: copy-and-improve, or one of the first-principles skills in this pack.
- The skill is a META skill — it picks the mode, it doesn't apply the framework itself.

## Phases

1. **State the problem.**
2. **Assess stakes: low or high?** Cost of being wrong.
3. **Assess novelty: can analogy supply a proven answer (yes/no)?** Has a similar problem already been solved, and is the solution proven in conditions like ours?
4. **Locate in the 2x2 matrix.**
5. **Pick the default mode** based on the quadrant.
6. **Route** to copy-and-improve (analogy mode) or to a first-principles skill in this pack.

## Output Format

```
PROBLEM: <one line>
STAKES: <low / high> — <why>
NOVELTY: <yes / no> — <why the analogy does / doesn't fit>

                       Analogy available?
                       Yes              No
              ┌─────────────────┬─────────────────┐
   High       │ <your cell>     │ <your cell>     │
   stakes     │ Copy & improve  │ First-principles│
              │ existing proven │ from fundamentals│
              │ — fast, reliable│ — slow, optimal │
              ├─────────────────┼─────────────────┤
   Low        │ <your cell>     │ <your cell>     │
   stakes     │ Just copy it    │ Use analogy as  │
              │ — ship          │ scaffold only   │
              └─────────────────┴─────────────────┘

ROUTING: <copy-and-improve OR first-principles skill in this pack>
```

## Decision rules

| Quadrant | Default | Reasoning |
|----------|---------|-----------|
| High stakes, analogy available | Copy & improve existing proven | Fast and reliable — the analogous solution already carries the risk |
| High stakes, analogy not available | First principles from fundamentals | Slow and optimal — analogy doesn't fit, you must derive |
| Low stakes, analogy available | Just copy it — ship | Cost of being wrong is small; speed wins |
| Low stakes, analogy not available | Use analogy as scaffold only | Borrow the shape, derive the specifics |

The matrix chooses the *starting* mode. Specialists often zig-zag across it as clarity improves — start analogy, hit a wall, switch to first-principles on the part that doesn't fit.

## Worked example (problem: build a payment reconciliation system)

```
PROBLEM: Build a payment reconciliation system for a fintech
STAKES: high — money; reconciliation bugs cost real dollars and trust
NOVELTY: yes — Stripe, Plaid, and many fintechs have solved this; the
  pattern is proven

                       Analogy available?
                       Yes              No
              ┌─────────────────┬─────────────────┐
   High       │  YOU ARE HERE   │                 │
   stakes     │ Copy & improve  │ First-principles│
              │ existing proven │ from fundamentals│
              ├─────────────────┼─────────────────┤
   Low        │                 │                 │
   stakes     │ Just copy it    │ Use analogy as  │
              │                 │ scaffold only   │
              └─────────────────┴─────────────────┘

ROUTING: Copy-and-improve. Start from the Stripe/Plaid pattern. Modify
  only where your specific ledger model differs. Don't reinvent the
  reconciliation loop — it's been solved and the bugs are expensive.
```

## Worked example (problem: design battery cost-down that beats existing chemistry)

```
PROBLEM: Design a battery cost-down that beats existing chemistries
STAKES: high — company-defining bet
NOVELTY: no — existing chemistries define the cost wall; analogy copies the wall

ROUTING: First principles. The analogous solution (existing chemistry) is
  what's failing. Use `constraint-elimination` to surface the
  chemistry-physics constraints (HARD) vs the manufacturing-process
  constraints (often SOFT), then `blank-slate-design` to rebuild the
  cost structure from the physics up.
```

## When to use

- Whenever someone proposes "let's just do what X did" without checking whether the analogy fits.
- To make a deliberate choice between incremental and fundamental reasoning up front — before the team has implicitly chosen by happening to read the analogous solution first.
- As the entry point to the `reasoning-and-analyses` pack when the agent is unsure which child framework to load.

## Anti-Patterns

- Using analogy when the analogous solution is itself the failure. Analogy copies the wall you're trying to break.
- Using first-principles when an analogous solution exists and the stakes are low. You're spending weeks to derive what someone already shipped.
- Treating the matrix as committed. The matrix picks the START; if the chosen mode hits a wall, switch.

## Tools Used

(none — pure routing skill)
