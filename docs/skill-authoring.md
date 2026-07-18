# Skill Authoring

How to write a new `SKILL.md`. This is the conformance standard every skill in this repo must follow. It mirrors the GBrain skill-creator convention: frontmatter + Contract + Phases + Output Format + Anti-Patterns + Tools Used.

## Required file location

A discoverable skill lives at:

```
skills/<skill-name>/SKILL.md
```

No exceptions. One folder per skill, one `SKILL.md` per folder. The folder name is the skill's slug — lowercase, hyphenated, no numeric prefixes.

## Required frontmatter

```yaml
---
name: <skill-name>            # MUST match the folder name
version: 1.0.0
description: |
  <One paragraph. Start with "Use when..." so the agent knows the trigger.
   List the signals that make this skill the right pick.>
triggers:
  - "<phrase or pattern that should fire this skill>"
  - "<another trigger>"
tools:                          # MCP tools the skill calls, empty list if pure reasoning
  - <tool1>
mutating: <true|false>         # true if the skill writes files or external state
family: <family-name>          # logical grouping inside the pack (e.g. first-principles, rca)
---
```

## Required sections (in order)

1. `# {Title}` — matches the skill name, human-readable.
2. `## Contract` — 3-5 bullets, what this skill guarantees to do (or refuse to do).
3. `## Phases` — numbered workflow. Each phase is one numbered step with a bold title and a one-line description of the action.
4. `## Output Format` — what good output looks like. Include ASCII templates where the structure is visual (fishbone, fault tree, Pareto chart, mind map, matrix).
5. `## Anti-Patterns` — 3-5 bullets, what NOT to do.
6. `## Tools Used` — list the MCP tools the skill uses, with one-line descriptions. Write `(none — pure reasoning skill)` if the skill uses no tools.

## Writing rules

- One skill, one job. If you're describing two jobs, split the skill.
- Triggers must be MECE against every other skill in the same pack — see
  `docs/conventions/mece.md` and the pack metadata under `packs/`.
- Output must follow `docs/conventions/output-rules.md` — ASCII-friendly, no emojis, no preamble.
- Don't number skill folders. The loader discovers skills by name, not by order.
- Phases are a workflow, not a checklist. Each phase produces something the next phase uses.
- Anti-patterns are the load-bearing guardrails. Written from real failure modes, not generic good-intentions text.

## MECE check before creating a new skill

1. Open `packs/<pack>/manifest.json`.
2. Open `packs/<pack>/RESOLVER.md`.
3. Does any existing skill already cover your trigger? If yes, extend it instead of creating a new one.
4. Add the new skill to `manifest.json` and `RESOLVER.md` in the same PR / commit.
5. Verify the pack still loads — open the resolver and trace a sample trigger through it.

## Example

See `skills/socratic-questioning/SKILL.md` as a worked reference.
