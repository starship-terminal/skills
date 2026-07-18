---
name: constraint-elimination
version: 1.0.0
description: |
  Use when the user is stuck on "we can't" and the source of the can't is
  unclear. Surface every apparent constraint, classify each as hard (physics,
  law, logic) vs soft (convention, policy, "we've always..."), remove the
  soft ones before solving. The looser problem often solves itself.
triggers:
  - "we can't because"
  - "blocked by"
  - "what if we removed this constraint"
  - "why do we have to do it this way"
  - "stuck on the can't"
tools: []
mutating: false
family: first-principles
---

# Constraint Elimination

Surface every apparent constraint on a problem. Classify each as hard (physics, law, logic) or soft (convention, policy, custom). Remove the soft ones before solving.

## Contract

- The skill lists ALL constraints the user can articulate, not just the obvious one.
- The skill tags each constraint: HARD (physics / law / logic) or SOFT (convention / policy / "we've always...").
- The skill asks for each SOFT constraint: "If this were not true, what would we do?"
- The skill removes SOFT constraints and solves the looser problem.
- The skill reconciles the looser solution against the HARD ones only.
- The skill does NOT remove HARD constraints by hopeful thinking. Compute, physics, regulation, and contract are real.

## Phases

1. **State the problem.**
2. **List ALL constraints.** Budget, time, tooling, policy, regulation, custom, "we don't have the people," "the customer needs..."
3. **Tag each constraint: HARD or SOFT.**
   - HARD: physics, law, regulation, binding contract, irreducible logic.
   - SOFT: convention, policy (changeable), "we've always done it this way," untested assumption masquerading as a rule.
4. **For each SOFT constraint: ask "If this were not true, what would we do?"** Record the answer.
5. **Remove the SOFT constraints. Solve the looser problem.**
6. **Reconcile the looser solution against the HARD ones only.** If it still works, you have your answer.

## Output Format

```
PROBLEM: <one line>

CONSTRAINTS TABLE:
| Constraint                              | Type   | Action if removed                         |
|-----------------------------------------|--------|-------------------------------------------|
| <constraint 1>                          | SOFT   | <what we would do if it weren't true>     |
| <constraint 2>                          | HARD   | Keep — must reconcile against             |
| ...                                     | ...    | ...                                       |

REMOVED (soft):
  - <constraint, action if removed>

KEPT (hard):
  - <constraint, why it's hard>

LOOSER PROBLEM SOLUTION:
  <the solution with soft constraints removed>

RECONCILED AGAINST HARD:
  <does the looser solution respect the hard constraints? If yes, this is the answer.>
```

## Worked example (problem: cannot ship the feature this quarter)

```
PROBLEM: Cannot ship the analytics dashboard this quarter

CONSTRAINTS TABLE:
| Constraint                              | Type   | Action if removed                                   |
|-----------------------------------------|--------|-----------------------------------------------------|
| No budget this quarter                   | SOFT   | Phase delivery differently — ship MVP now, full later|
| Must fit in current platform            | SOFT   | Build the new module separately                     |
| Cannot break backward compat            | HARD   | Keep the legacy API intact                          |
| Data model immutable                     | HARD   | Use additive schema only                            |
| Team goes on vacation in August         | HARD   | Calendar reality                                    |
| Customer needs the full feature set     | SOFT   | Customer needs the outcome; subset may deliver it   |

REMOVED (soft):
  - No budget this quarter -> phase the delivery
  - Must fit in current platform -> build the new module separately
  - Customer needs the full feature set -> confirm subset delivers the outcome

KEPT (hard):
  - Cannot break backward compat — keep legacy API
  - Data model immutable — additive schema only
  - Team vacation in August — calendar reality

LOOSER PROBLEM SOLUTION:
  Ship a 3-screen MVP this quarter built as a separate module. MVP
  covers 80% of the analytics the customer actually uses (verified
  against their top 5 reports). Additive schema only; legacy API stays.

RECONCILED AGAINST HARD:
  Respects backward compat (separate module), respects data model
  (additive), respects calendar (MVP scope fits before August). YES.
```

## Anti-patterns

- Collapsing HARD into SOFT because the constraint is inconvenient. Compute, physics, regulation, and contract are real. They don't bend because you want them to.
- Removing only one constraint and calling it done. The skill removes ALL softs; the looser problem is the union of all removals.
- Skipping the reconciliation step. The looser solution is not the answer if it violates a hard constraint — adjust it.
- Tagging a "customer need" as HARD. Most customer needs are SOFT — the customer needs an outcome, not a feature list. Verify.

## Tools Used

(none — pure reasoning skill)
