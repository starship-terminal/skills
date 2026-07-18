---
name: five-whys
version: 1.0.0
description: |
  Use when the symptom is clear but the root cause is unknown, and the failure
  path is a single linear chain. Repeatedly ask why (typically ~5 times) along
  the causal chain until you reach a process / system gap, not a symptom.
  Stop when the answer is actionable; don't force exactly five whys.
triggers:
  - "single symptom chain"
  - "find the root cause"
  - "why did this happen"
  - "keep asking why"
tools: []
mutating: false
family: rca
---

# Five Whys

Repeatedly ask "why" along a single causal chain to dig deeper into causes. The goal at the end of questioning is to reach the root cause.

## Contract

- The skill follows ONE causal chain. If the chain branches, this is the wrong skill — use `fault-tree-analysis`.
- The skill stops when the answer is a process/system fix, not a symptom. Not necessarily at 5.
- The skill ends with a one-line root cause and a one-line action against it.
- The skill never stops at a human-blame answer ("someone forgot"). Push to the system that allowed the forgetting.

## Phases

1. **State the observed problem.**
2. **Ask: "Why did this happen?" Answer.** Treat the answer as the next problem.
3. **Repeat 4-6 times.** Each "why" drills one level deeper. State the chain explicitly.
4. **Stop when the answer is a system/process gap** — something you can fix with a process change, a calendar entry, a checklist, an automation. Not "the person was careless."
5. **State the root cause in one line.**
6. **Propose an action plan against the root cause.** One line. Actionable.

## Output Format

```
PROBLEM: <one-line symptom>

1. Why? -> <answer 1>
2. Why? -> <answer 2>
3. Why? -> <answer 3>
4. Why? -> <answer 4>
5. Why? -> <answer 5>

ROOT CAUSE: <one line>
ACTION: <one line, actionable>
```

## Worked example (problem: server went down)

```
PROBLEM: Server went down last night

1. Why? -> Server overheated
2. Why? -> Cooling system failed
3. Why? -> Maintenance schedule was skipped
4. Why? -> Task was not in the team's work tracking system
5. Why? -> Maintenance was never properly documented and scheduled

ROOT CAUSE: Maintenance process is undocumented — no SOP, no calendar entry, no tracking
ACTION: Standardize maintenance SOPs in the work tracker with calendar alerts and an owner
```

## Stop criteria

- The "why" chain leaves the original domain (e.g. from server into corporate HR) → stop one step earlier.
- You reach a single, actionable system/process fix → stop.
- The answer becomes "human error" or "someone forgot" → push one more why to the system that allowed it.
- Don't force exactly 5. Sometimes 3 is enough; sometimes 7 is right.

## Anti-Patterns

- Stopping at a human-blame answer. "Someone forgot" is a symptom, not a root cause.
- Branching into multiple chains without finishing one. If the answer splits into two, pick the more likely one and finish it; revisit the other if the first chain doesn't yield an actionable root.
- Forcing exactly five. The number is a guideline; the stop criterion is what matters.
- Stopping at "the tool failed." Why did the tool fail? Why was it not caught? Push to the system.

## Tools Used

(none — pure reasoning skill)
