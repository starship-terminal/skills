---
name: pareto-analysis
version: 1.0.0
description: |
  Use when resources are limited and you must prioritize cause categories.
  Pareto says 20% of causes produce 80% of effects — find the vital few,
  deprioritize the trivial many. Output: a Pareto chart (bars + cumulative
  line) and a clear "vital few" cut.
triggers:
  - "where should I focus"
  - "what gives the most impact"
  - "limited resources, must prioritize"
  - "what's the 80/20"
tools: []
mutating: false
family: rca
---

# Pareto Analysis (80/20)

A small number of causes typically produces most of the effect. Find the vital few, deprioritize the trivial many.

## Contract

- The skill takes a list of items with measurable impact (counts, cost, hours).
- The skill sorts descending by impact and computes cumulative percentage.
- The skill identifies the items whose cumulative share crosses ~80% — the vital few.
- The skill recommends action on the vital few and deprioritization of the rest.

## Phases

1. **List the items** with their measurable impact. If the user gives qualitative data, prompt for measurement before proceeding.
2. **Sort descending by impact.**
3. **Compute the cumulative percentage.**
4. **Identify the 80% cut.** The smallest set of items whose cumulative share crosses ~80% — the vital few.
5. **Draw the Pareto chart.** Bars for per-item %, line for cumulative %, priority stars.
6. **Recommend.** Action on the vital few; revisit the rest only after.

## Output Format

```
Item                       %      Cumulative %   Priority
─────────────────────────────────────────────────────────
<item 1>                  <p1>%        <c1>%          star-star-star
<item 2>                  <p2>%        <c2>%          star-star-star
<item 3>                  <p3>%        <c3>%          star-star
<item 4>                  <p4>%        <c4>%          star
<item 5>                  <p5>%        <c5>%          (low priority)
...
```

Vital few: <items whose cumulative % crosses 80%>
Trivial many: <the rest>

## Worked example (car repair complaints)

```
Item                       %      Cumulative %   Priority
─────────────────────────────────────────────────────────
Scratches                 48%        48%          ★★★
Misalignment              24%        72%          ★★★
Faulty wiring             14%        86%          ★★
Paint issues               8%        94%          ★
Other                      6%        100%          ·
```

Vital few: Scratches, Misalignment (cumulative 72%, just under but close to 80%)
Trivial many: Faulty wiring, Paint issues, Other

Recommendation: focus defect-reduction effort on scratches + misalignment. The 5 other categories together make up only 28% of complaints — revisit only after the top two are addressed.

## Anti-Patterns

- Chasing the trivial many. They will mostly vanish once the vital few are fixed. Don't allocate effort proportional to count.
- Skipping the cumulative %. Without it, the 80% cut is invisible.
- Treating "80%" as exact. It's a guideline — 70% or 85% may be the right cut for the user's data.
- "Cost down" as the goal. Goal is the best cost/benefit pairing, which may mean increasing one cost to unlock larger benefit elsewhere.

## Tools Used

(none — pure reasoning skill)
