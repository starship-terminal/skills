---
name: fishbone-diagram
version: 1.0.0
description: |
  Use when a problem has many contributing cause categories and you want them
  visible side-by-side before drilling deeper. Visual root-cause tool: problem
  at the fish head, major cause categories on the bones, specific causes on
  the sub-bones. Pairs well with five-whys — pick the most likely bone and
  drill down it.
triggers:
  - "many cause categories"
  - "what's contributing to this problem"
  - "see causes side by side"
  - "categorize the possible causes"
tools: []
mutating: false
family: rca
---

# Fishbone (Ishikawa) Diagram

A structured root-cause analysis tool. The problem is the fish head; the major cause categories are the bones; the specific causes are the sub-bones.

## Contract

- The skill produces one fishbone, with the problem at the head and 4-6 cause category bones.
- Every bone has at least one specific cause on a sub-bone.
- The skill ends with: which bone is most likely, and a recommendation to drill further (usually via `five-whys`).
- The skill does NOT identify the root cause — it identifies the candidate bones to drill into.

## Phases

1. **State the problem in one line.** Place it at the head of the fish (right side).
2. **Pick 4-6 cause categories.** Common starters: People, Process, Technology, Environment, Materials, Methods, Measurement, Management. Use whatever fits the domain.
3. **For each category, list specific causes.** Each goes on a sub-bone. If a category has no causes, drop the bone.
4. **Draw the fishbone in ASCII.** Below.
5. **Read the fish.** Identify the 1-2 bones most likely to hold the root cause.
6. **Recommend.** Hand off to `five-whys` on the most likely bone, or to `fault-tree-analysis` if the bones have AND/OR logic.

## Output Format

```
              <Cat1>                  <Cat2>                  <Cat3>
                |                        |                       |
   -------------|----------+-------------|----------+------------|-------
                |          |             |          |            |
                v          v             v          v            v
              (sub)      (sub)         (sub)      (sub)        (sub)
                |          |             |          |            |
                +----------+-------------+----------+------------+
                                       |
                                       v
                            [ PROBLEM STATEMENT ]
```

Reading:
- Each bone is a major cause category.
- Each sub-bone is a specific cause within that category.
- The most likely bone is the one to drill further (using `five-whys`).

## Worked example (problem: declining student test scores)

```
            Staffing            Environment          Technology
              |                      |                   |
   -----------|---------+------------|---------+---------|-------
              |         |             |         |         |
              v         v             v         v         v
         high        shortage       noisy      poor      outdated
        teacher      of subs        classrooms ventilation tablets
        turnover                                  |
                                                v
                                            slow internet
              +---------+------------+---------+---------+
              |         |            |                   |
              v         v            v                   v
                          [ Declining student test scores ]
```

Cause category assessment:
- **Staffing** — most likely. High teacher turnover directly affects instruction quality.
- **Environment** — possible contributor but secondary.
- **Technology** — likely but indirect.

Recommendation: hand off to `five-whys` on the Staffing bone.

## Anti-Patterns

- Treating every bone as equal. The fishbone is a triage tool — pick the bone to drill.
- Putting solutions on the bones. The bones are causes, not fixes. Solutions come after the root cause is found.
- Forcing six bones when four fit. A bone with no specific causes is dead weight; drop it.
- Skipping the reading. A drawn fish nobody interprets is a drawing exercise.

## Tools Used

(none — pure reasoning skill)
