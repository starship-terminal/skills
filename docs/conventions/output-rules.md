# Output Rules

Cross-cutting rules for what every skill in this repo produces as output. Applies to every skillpack.

## Style

- ASCII-friendly. Output renders in a monospace terminal and in markdown. No emojis unless the user explicitly asks.
- No preamble. Don't open with "Here is..." or "Based on..." — start with the artifact.
- No postamble. Don't close with "Hope this helps!" or "Let me know if..."
- Keep tables and ASCII diagrams under 80 columns where possible.

## Structure

- Every output starts with a one-line problem restatement, then the analysis.
- Walk through Phases in order. Show intermediate results, not just the final answer.
- When a skill produces a visual artifact (fishbone, fault tree, matrix), draw it in ASCII and explain the reading underneath, not above.

## Conversational mode

Skills in this repo are designed to be used in conversation. That means:

- Show your work step by step. The user should be able to interrupt at any phase and redirect.
- After every Phase, pause briefly (in writing) — let the user see what shifted before moving on.
- When a Phase discovers something that changes the problem, restate the problem before the next Phase.

## Citations and grounding

- If a skill's output depends on a fact from the user, label it: `[User: ...]`.
- If a skill's output depends on a general knowledge claim, and the user might reasonably disagree, label it: `[Assumption: ...]`.
- Pure reasoning frameworks (the entire `reasoning-and-analyses` pack) don't need external citations — they're structured thinking tools, not knowledge retrieval.

## Length

- A skill run should fit on one screen of terminal output when possible.
- If a skill legitimately produces a lot (e.g. a full fishbone with many cause categories), let it scroll — don't truncate the artifact for aesthetics.
- Don't pad. If a Phase has nothing to add, write `(no findings)` and move on.

## What NOT to do

- Don't hand the user a wall of prose. Use structure: tables, ASCII diagrams, numbered lists.
- Don't summarize the framework before applying it. The user can read the `SKILL.md` if they want the framework — the conversation output is the analysis.
- Don't substitute formatting for substance. A table with one row is just a sentence.
- Don't editorialize about the framework. Apply it; show the result.
