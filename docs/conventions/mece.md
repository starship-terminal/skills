# MECE Triggers

Triggers across skills in the same skillpack must be **Mutually Exclusive and Collectively Exhaustive**. This is the rule that makes a pack dispatcher actually dispatch instead of guess.

## Mutually Exclusive

No two skills in the same pack should fire on the same user intent. If they do, the resolver doesn't know which to pick, and the user sees inconsistent behavior.

### Test

For every pair of skills A and B in a pack, read A's triggers and B's triggers. Is there any user message that could reasonably match both? If yes, do one of:

1. Narrow the triggers so they don't overlap.
2. Merge the skills (if they really are the same job).
3. Split the triggering context into a third skill that routes between them.

### Example (good)

In `reasoning-and-analyses`:

- `five-whys` triggers on "single symptom chain, root cause unknown".
- `fishbone-diagram` triggers on "many cause categories, problem has multiple contributing causes".

These are MECE: a problem with one symptom chain goes to five-whys, a problem with many cause categories goes to fishbone. A problem that's both is the user's call — and the resolver says so explicitly.

### Example (bad)

If both `five-whys` and `fault-tree-analysis` listed "find the root cause" as a trigger, the resolver would have to guess. `fault-tree-analysis` is specifically for parallel/cascading failure paths with logic gates; `five-whys` is for a single linear chain. The triggers say so.

## Collectively Exhaustive

For every problem in the pack's domain, at least one skill should fire. If there's a category of problem the pack claims to cover but no skill handles, the pack has a gap.

### Test

List the problem archetypes the pack covers in its `SKILL.md` (or `RESOLVER.md`). For each, walk through the resolver table — does at least one row match? If no, either add a skill or narrow the pack's claim.

## Resolver's role

`RESOLVER.md` is where MECE becomes operational. It's a table: trigger phrase -> skill. If the resolver has a row that matches two skills, that's a MECE violation and a bug. If a real problem matches no row, that's also a bug — add a row or a skill.

## When MECE is too strict

Some frameworks legitimately overlap. In `reasoning-and-analyses`, several skills are different lenses on the same root-cause question. The resolver handles this with a "When the problem is X, choose between Y and Z based on W" row — making the user's context the disambiguator, not chance. This is acceptable; silent overlap is not.

## Action when a violation is found

1. Pick which skill owns the trigger.
2. Remove the trigger from the other skill's frontmatter.
3. Update `RESOLVER.md` so the row points to one skill only.
4. Update `manifest.json` descriptions if they now overlap.
5. Note the fix in `CHANGELOG.md`.
