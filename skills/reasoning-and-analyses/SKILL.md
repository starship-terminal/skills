---
name: reasoning-and-analyses
version: 1.0.0
description: |
  Use when the user has a problem to think through, diagnose, restructure, or
  reason about from first principles. Dispatches to a child framework inside
  the pack: Socratic questioning, root cause analysis (fishbone, five whys,
  fault tree, Pareto), mind mapping, blank slate design, cost-benefit
  disassembly, constraint elimination, or the analogy vs first principle
  matrix. Load this skill when the user's problem shape is unclear; it picks
  the right child. Load a specific child directly when the shape is obvious.
triggers:
  - "problem to think through"
  - "diagnose this"
  - "restructure this"
  - "reason from first principles"
  - "what framework should I use"
tools: []
mutating: false
family: dispatcher
---

# Reasoning & Analyses

This is the dispatcher for the `reasoning-and-analyses` skillpack. It picks the right child framework for a problem and points the agent at the child `SKILL.md`.

## Contract

- The dispatcher picks exactly one child framework, or names the ambiguity and asks the user.
- The dispatcher never applies a framework itself — it routes to a child.
- Every child framework in the pack is covered by at least one row in the dispatcher table.

## Phases

1. **Restate the problem.** In one line, back to the user.
2. **Assess the shape.** Fuzzy? Multi-cause? Single symptom chain? Parallel failures? Need to prioritize? Need to explore? Stuck on convention? Trade-offs to decompose? Blocked by "we can't"? Choosing analogy vs first-principles?
3. **Route.** Look up the shape in the table below. Resolve to one child skill.
4. **Hand off.** Open the child `SKILL.md` and follow its Phases. Don't re-apply this dispatcher.

## Routing table

| If the problem is… | Use |
|---|---|
| Fuzzy, loaded with assumptions, or contains unexamined absolutes ("always", "never", "must") | `socratic-questioning` |
| Many contributing cause categories, want them side by side | `fishbone-diagram` |
| Single symptom chain, root cause unknown | `five-whys` |
| Parallel or cascading failure paths with AND/OR logic | `fault-tree-analysis` |
| Limited resources, must prioritize cause categories | `pareto-analysis` |
| Topic to explore non-linearly, brainstorming, study | `mind-mapping` |
| Legacy or conventional thinking biasing the answer | `blank-slate-design` |
| Bundle of costs and benefits to restructure optimally | `cost-benefit-disassembly` |
| Stuck on "we can't" — apparent constraints blocking a better solution | `constraint-elimination` |
| Choosing between analogy and first-principles reasoning up front | `analogy-vs-first-principle-matrix` |

## When the shape is ambiguous

If two rows match, name the two candidates and ask the user which fits. Don't guess. The child skills produce very different output and the wrong pick wastes a Phase.

## Anti-Patterns

- Applying a framework from here. This skill routes only — it doesn't analyze.
- Stacking frameworks the user didn't ask for. Some frameworks chain (fishbone then five-whys on a bone), but ask first.
- Skipping the restatement. If the agent mis-routed, the user finds out at Phase 4, not Phase 1.

## Tools Used

(none — pure dispatcher skill)
