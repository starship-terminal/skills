# Reasoning & Analyses Skill Resolver

This is the dispatcher metadata for the `reasoning-and-analyses` pack.
Installable implementations live under `skills/`. **Read the selected
`SKILL.md` before acting.** If two skills could match, read both—most are
designed to chain (for example, fishbone to identify a category, then five
whys along that category).

## When to load the pack

Load this pack whenever the user has a problem to think through, diagnose, restructure, or reason about from first principles. Don't load it for backend-only work, prose editing, or non-problem-solving conversation.

## Routing table

| Trigger / shape | Skill |
|---|---|
| "What are we taking for granted", "surface the assumptions", problem uses absolutes ("always", "never", "must") | `socratic-questioning/SKILL.md` |
| Many cause categories, want them visible side-by-side | `fishbone-diagram/SKILL.md` |
| One symptom, need to find the root cause, single chain | `five-whys/SKILL.md` |
| Parallel or cascading failures, AND/OR logic between causes | `fault-tree-analysis/SKILL.md` |
| "Where should I focus", "what gives me the most impact", limited resources | `pareto-analysis/SKILL.md` |
| "Brainstorm", "explore this topic", "what are the parts of", non-linear study | `mind-mapping/SKILL.md` |
| "We've always done it this way", "let's start from scratch", empty-state design | `blank-slate-design/SKILL.md` |
| Trade-offs to decompose, "is this worth it", cost-benefit bundle to restructure | `cost-benefit-disassembly/SKILL.md` |
| "We can't because", "blocked by", "what if we removed this constraint" | `constraint-elimination/SKILL.md` |
| "Should we just do what X did", "is analogy enough here", analogy vs first-principles decision | `analogy-vs-first-principle-matrix/SKILL.md` |
| Fuzzy problem, can't pick a child | load `SKILL.md` at the pack root and follow its routing |

## Common chains

| Start with | Then chain to | Why |
|---|---|---|
| `fishbone-diagram` | `five-whys` | Identify the most likely bone, then five-whys along that bone to the root cause |
| `pareto-analysis` | `five-whys` | Pick the vital few, then five-whys on the top item |
| `fault-tree-analysis` | `five-whys` | Identify the most likely basic event, then five-whys on it |
| `socratic-questioning` | any | Socratic surfaces assumptions; the chosen child then works against the cleaned-up problem |
| `constraint-elimination` | `blank-slate-design` | Remove the soft constraints, then redesign from the looser problem |

## Disambiguation rules

- If `five-whys` vs `fault-tree-analysis` both seem to fit, the test is: is the failure path linear (five-whys) or parallel/cascading with gates (fault-tree)?
- If `fishbone-diagram` vs `fault-tree-analysis` both seem to fit, the test is: are you categorizing causes that all contribute to one problem (fishbone) or are you modeling the chain of events that produced a specific failure (fault-tree)?
- If `socratic-questioning` vs `constraint-elimination` both seem to fit, the test is: are you surfacing assumptions to clarify the problem (Socratic) or are you actively removing soft constraints to widen the solution space (constraint-elimination)?

## When the user asks for "first principles"

Read `references/first-principles-overview.md` first. The three-step core
(identify assumptions, break down to first principles, rebuild) is the
upstream pattern every skill in this pack supports.
