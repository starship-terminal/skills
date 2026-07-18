# Output Rules — Reasoning & Analyses Pack

Pack-specific output conventions. Builds on
`../../../docs/conventions/output-rules.md`.

## Conversational cadence

This pack is designed for use inside a conversation. Each skill runs across multiple turns, not in one giant dump.

- After every Phase, pause for the user. Show what shifted. Let them confirm or redirect.
- If a Phase surfaces something that changes the problem, restate the problem before the next Phase.
- A skill can be interrupted at any Phase. The agent doesn't owe the user a complete run if they redirect.

## Visual artifacts

Several skills produce visual structures. Render them in ASCII, not prose:

| Skill | Artifact | ASCII shape |
|---|---|---|
| `fishbone-diagram` | Fishbone | Diagonal bones off a horizontal spine, problem to the right |
| `fault-tree-analysis` | Fault tree | Top event at top, branches with AND/OR gates, basic events at leaves |
| `pareto-analysis` | Pareto chart | Table with bars (%), line (cumulative %), priority stars |
| `mind-mapping` | Mind map | Central node with radiating branches, indent for depth |
| `analogy-vs-first-principle-matrix` | 2x2 matrix | Quadrant diagram with axes labeled |

When the artifact has a "reading" rule (e.g. AND gate vs OR gate in fault tree, the 80% cut in Pareto), state the reading in one line under the diagram, not above it.

## ASCII conventions

- Tables: pipe-delimited, header row, alignment row, data rows.
- Trees: indentation marks depth; arrows (`->`, `=>`, `|`) mark edges where it adds meaning.
- Matrices: 2x2 boxes drawn with `+`, `-`, `|` characters.
- Keep everything under 80 columns where possible.

## Tone

These are thinking tools, not authorities. The skill applies the framework; the user owns the conclusion. Don't editorialize about whether the framework is "powerful" or "elegant" — apply it and show the result.

## Length

A skill run should produce one screen of terminal output where possible. The visual artifacts are the load-bearing output — the surrounding text should just be the phase transitions and the reading.
