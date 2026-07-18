---
name: fault-tree-analysis
version: 1.0.0
description: |
  Use when a failure event has multiple parallel or cascading contributors
  connected by AND/OR logic — the failure path is not linear. A top-down
  deductive failure analysis: define the top event, decompose into basic
  events, connect with logic gates. Pairs with five-whys on the most likely
  basic event.
triggers:
  - "parallel failure paths"
  - "cascading failures"
  - "AND/OR logic between causes"
  - "model how this failed"
tools: []
mutating: false
family: rca
---

# Fault Tree Analysis (FTA)

A top-down deductive failure analysis using Boolean logic gates to combine contributing basic events into a top undesired event.

## Contract

- The skill defines one top event and decomposes it into basic events.
- The skill uses only two gate types: AND (all inputs must occur) and OR (any one input causes the output).
- Every branch ends at a basic event — an atomic cause that won't be decomposed further in this tree.
- The skill ends with a reading: which paths are weak (OR chains), which are resilient (AND chains), and which basic event to drill further.

## Phases

1. **Define the top event.** The undesired event you're analyzing, in one line.
2. **Identify its direct causes.** Decompose one level down.
3. **Connect each set of causes with a gate.**
   - OR gate: any one input causes the output (one-of-many).
   - AND gate: all inputs must occur for the output (parallel defenses).
4. **Repeat down each branch** until you reach basic events (atomic causes).
5. **Draw the tree in ASCII.** Below.
6. **Read the tree.** Identify the weak paths (OR gates — single points of failure) and the resilient paths (AND gates — defense in depth). Recommend which basic event to drill (usually via `five-whys`).

## Output Format

```
                    <TOP EVENT>
                /       |       \
             (gate)   (gate)   (gate)
              / \      / \      / \
           <e1> <e2> <e3> <e4> <e5> <e6>
                     (gate)
                      / \
                   <e7> <e8>
```

Logic-gate semantics:

| Gate | Failure occurs when... | Reading |
|------|------------------------|---------|
| OR   | any one input fails    | weakest link — single point of failure |
| AND  | all inputs fail         | defense in depth — resilient path |

## Worked example (top event: data center power loss)

```
                Data Center Power Loss
                  /            \
               (OR)            (OR)
               /   \           /   \
        Utility   Generator  Battery  Starter Motor
        Failure    Failure   Failure    Failure
                    (AND)        |
                     |           |
                                v
                            Fuel Depletion
```

Meaning:
- Power is lost if **utility** fails **OR** generator fails (OR gate at top).
- Generator fails only if (**battery** fails **AND** starter motor fails) **OR** fuel depletes.

Reading:
- Top OR is the weak link — either path fails the data center.
- Generator's AND gate is defense in depth — battery and starter must both fail before the generator dies on that path. Resilient.
- Fuel depletion is a separate OR input to generator failure — single-point.
- Most likely drill candidate: fuel depletion (single OR input, easy to mitigate with monitoring).

## Anti-Patterns

- Using a single gate type everywhere. Real failures have both AND and OR — using only one flattens the model and loses the reading.
- Ending a branch at a non-basic event. If you can decompose further, you should; basic events are atomic.
- Skipping the reading. A drawn tree nobody interprets is just a diagram.
- Confusing top-down (FTA, this) with bottom-up (FMEA). FTA starts at the failure and asks "what could cause this?" — that's our direction.

## Tools Used

(none — pure reasoning skill)
