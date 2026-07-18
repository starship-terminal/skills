# Frontmatter

Required frontmatter for every `SKILL.md` in this repo. Apply it to every
installable folder under `skills/`, including an optional pack router.

## Required fields

```yaml
---
name: <slug>
version: <semver>
description: |
  <One paragraph. Start with "Use when..." List the signals that make this skill the right pick.>
triggers:
  - "<trigger phrase>"
tools:
  - <tool>           # empty list if pure reasoning
mutating: <true|false>
family: <family>
---
```

## Field rules

### `name`
- Lowercase, hyphenated.
- Matches the folder name exactly.
- No numeric prefixes (`01-...` forbidden).
- Globally unique across the repo (not just within the pack).

### `version`
- Semver, 3 segments (`1.0.0`).
- Bump on every behavior change — even small ones.

### `description`
- One paragraph, multi-line YAML block scalar.
- Start with "Use when...".
- List 2-4 signals that make this skill the right pick.
- The agent reads this to decide whether to load the skill — make it a good trigger phrase, not marketing copy.

### `triggers`
- List of phrases or patterns.
- MECE against every other skill in the pack (see `mece.md`).
- Phrases are examples, not regexes. The resolver matches on intent, not literal string equality.

### `tools`
- MCP tools the skill calls, by name.
- Empty list (`[]`) for pure reasoning skills.
- Don't list tools the skill *might* use — list the ones it *must* use.

### `mutating`
- `true` if the skill writes files, modifies external state, or makes calls with side effects.
- `false` if the skill only reads or only reasons.
- Drives trust-boundary decisions in agent platforms that gate writes.

### `family`
- Logical grouping inside the pack.
- For `reasoning-and-analyses`: `first-principles`, `rca`, `exploration`, `decision`.
- Skills in the same family often share pack-level `references/`.

## Forbidden fields

- `priority` — the resolver decides priority, not the skill.
- `experimental` — ship it or don't; no half-states.
- `author` — credit lives in `CHANGELOG.md` and git history.
- `created_at` — same.

## Optional fields (allowed)

- `examples:` — list of worked example inputs, useful for eval harnesses.
- `references:` — list of source URLs or docs the skill is derived from.
- `seealso:` — list of slugs of related skills in any pack.
