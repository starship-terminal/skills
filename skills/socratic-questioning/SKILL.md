---
name: socratic-questioning
version: 1.0.0
description: |
  Use when the user's problem is fuzzy, restated differently each time, contains
  unexamined absolutes ("always", "never", "must"), or has hidden assumptions
  clouding the answer. Drives a six-category Socratic questioning pass —
  clarity, assumptions, evidence, viewpoints, implications, meta — to surface
  what's really being asked before proposing any answer.
triggers:
  - "what are we taking for granted"
  - "surface the assumptions"
  - "the problem uses absolutes like always or never"
  - "fuzzy problem, can't pin it down"
tools: []
mutating: false
family: first-principles
---

# Socratic Questioning

From the Greek philosopher Socrates. Ask a series of thought-provoking questions to explore different ideas, think logically and critically. The point is not right answers but better questions and clarified thinking.

## Contract

- The skill runs all six categories, in order.
- The skill never supplies an answer before the categories are done.
- Every assertion the user or the skill makes is treated as a hypothesis; the skill requests its evidence.
- The skill ends with a tightened restatement of the problem.

## Phases

1. **Restate the problem in one line.** If the user gave more than a sentence, paraphrase down.
2. **Clarity.** Ask: "What exactly do we mean by <core concept>?" Re-state in operational terms. The goal is a definition the user and the agent both agree on.
3. **Assumptions.** Ask: "What are we taking for granted? Are we assuming all <X> have the same impact?" Surface and qualify every assumption. Mark each as held / qualified / discarded.
4. **Evidence.** Ask: "What examples, data, or counter-examples exist?" Distinguish lived experience from assertion. Note where the evidence is thin.
5. **Viewpoints.** Ask: "How would a utilitarian / engineer / affected user / skeptic frame this?" Force at least three perspectives. Don't pick one — list what each sees.
6. **Implications.** Ask: "What happens if everyone did this / no one did this? What are the first- and second-order effects?"
7. **Meta.** Ask: "Why does this question matter? What norms or values are we protecting by asking it?"
8. **Restate.** Tighten the problem based on what shifted. Hand off to a child skill or to the user's decision.

## Output Format

After each Phase, a short block:

```
PHASE N — <category>
Question: <the Socratic question>
Findings:
  - <finding 1>
  - <finding 2>
Shift: <what changed in the problem understanding, in one line>

PROBLEM RESTATE: <tightened one-line problem>
```

At the end, the full restated problem in a single blockquote.

## Worked example (problem: "Is lying always wrong?")

```
PHASE 2 — Clarity
Question: What do we mean by lying?
Findings:
  - Lying = act of deliberately making false statements or conveying misleading information
  - Often to manipulate, avoid consequences, or achieve personal gains
Shift: The term covers deliberate false statements, not honest mistakes

PHASE 3 — Assumptions
Question: Are we assuming all lies have the same impact?
Findings:
  - No: white lies, lies of omission, half-truths, nefarious lies all differ
  - Context really matters — the same statement can be a lie or kindness depending on the situation
Shift: "Lying" is not one category; the moral question decomposes by kind of lie

PHASE 4 — Evidence
Question: Has lying actually helped someone?
Findings:
  - A doctor might lie to a terminally ill patient to provide comfort in final days
  - White lies protect feelings daily; some lies are meant to protect people
Shift: Lie-as-harm is not universal; lie-as-protection exists and is common

PHASE 5 — Viewpoints
Question: What would a utilitarian say?
Findings:
  - Utilitarian: lying is permissible as long as it maximizes overall happiness or minimizes harm
  - Deontologist: lying is wrong regardless of outcome (Kant)
  - Affected party: depends on whether the lie was discovered
Shift: Different ethical frameworks reach different verdicts on the same lie

PHASE 6 — Implications
Question: What if no one lied?
Findings:
  - Positives: trust and transparency increase; accountability improves
  - Negatives: emotional harm could rise; social friction; loss of privacy
Shift: Truth-at-all-costs has its own cost — the choice is between two imperfect worlds

PHASE 7 — Meta
Question: Why is it important to ask about the morality of lying?
Findings:
  - Impacts well-being, trust, and social bonds between cultures
  - Personal and cultural norms determine what counts as a "lie" worth judging
Shift: The question itself encodes a commitment to the value of trust

> PROBLEM RESTATE: "Under what conditions, if any, is a deliberate false
> statement justified, and what moral framework should decide?"
```

## Anti-Patterns

- Skipping a category because the answer seems obvious. The category that seems obvious is usually where the hidden assumption lives.
- Letting the user supply an answer in Phase 2 and running the rest against it. Run each Phase fresh.
- Stopping at one viewpoint in Phase 5. Three is the minimum — the skill forces perspective, not consensus.
- Treating the meta question as optional. It's the one that reveals why the problem matters to the user at all.

## Tools Used

(none — pure reasoning skill)
