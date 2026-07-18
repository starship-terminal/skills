---
name: mind-mapping
version: 1.0.0
description: |
  Use when you need to explore a topic non-linearly — brainstorming, study,
  planning anything where structure unfolds as you think. A central idea
  radiates outward into branches; each branch holds related subtopics,
  details, or tasks. Mirrors how the brain holds related concepts.
triggers:
  - "brainstorm"
  - "explore this topic"
  - "what are the parts of"
  - "map this out"
  - "non-linear study"
tools: []
mutating: false
family: exploration
---

# Mind Mapping

A tool to break complex problems into smaller components. Organize information, ideas, or concepts in a hierarchical yet non-linear way. The structure mimics how the brain processes information.

## Contract

- The skill produces one mind map, with one central idea at the center.
- The skill grows 3-5 main branches from the center; each branch can grow sub-branches freely.
- The skill ends with: read the map, identify what's missing — gaps in the tree are themselves information.
- The map is a TOOL for thinking, not the answer.

## Phases

1. **State the central idea/topic.** One phrase at the center.
2. **Identify 3-5 main branches.** The largest sub-questions of the central idea.
3. **Grow each branch.** Sub-branches for related details, examples, or tasks. Let branches split freely; don't force symmetry.
4. **Draw the map in ASCII.** Below.
5. **Read the map.** What's well-developed? What's thin or missing? The gaps are signal.
6. **Recommend.** Identify which branch is most worth pursuing, or which branch is a gap to fill.

## Output Format

```
                       <Branch 1>
                       /         \
              <sub 1a>          <sub 1b>
                     \           /
                      \         /
                       <CENTRAL IDEA>
                      /         \
                     /           \
                <Branch 2>     <Branch 3>
                /     \         /     \
          <sub 2a> <sub 2b> <sub 3a> <sub 3b>
```

Reading:
- Each main branch is a major subtopic of the central idea.
- Each sub-branch is a related detail, example, or task.
- Gaps (branches with no sub-branches, or asymmetries) reveal what's not yet understood.

## Worked example (central idea: First Principles Thinking)

```
                       Core Concepts
                       /            \
              reason from        break down to
              fundamentals       basic truths
                     \            /
                      \          /
                       First Principles Thinking
                      /          \
                    /              \
              Steps to Apply   Applications
              | identify assumptions   | engineering
              | break to first         | design
                principles             | business strategy
              | rebuild from scratch   | learning
```

Reading:
- Core Concepts and Steps to Apply are well-developed.
- Applications is shallow — only four items and no sub-branches.
- Gap: the "Applications" branch could grow sub-branches for each domain (engineering, design, etc.) to show concrete examples.

Recommendation: grow the Applications branch. The framework is understood; the next value is in concrete examples per domain.

## Anti-Patterns

- Forcing symmetry. A lopsided map is honest — it shows where you've thought and where you haven't.
- Stopping at one level of sub-branches. The point is depth where it matters, not breadth everywhere.
- Treating the map as the answer. The map organizes; the answer comes after.
- Numbering branches. The order is spatial, not ranked.

## Tools Used

(none — pure reasoning skill)
