# Skillpack Anatomy

A skillpack is an authoring and catalog concept. Installable skills remain flat
under `skills/`; their pack metadata lives under `packs/`. This separation lets
the `skills` CLI discover each skill independently while preserving pack-level
routing and shared conventions.

## Required files

```text
packs/<pack>/
├── RESOLVER.md           # Required routing metadata
├── manifest.json         # Required machine-readable index
└── references/           # Required when shared references exist
    ├── <reference1>.md
    └── <reference2>.md

skills/
├── <pack-router>/        # Optional installable dispatcher
│   └── SKILL.md
└── <skill>/
    └── SKILL.md
```

### Pack router skill

Some packs benefit from an installable dispatcher that picks the right child.
When present, it lives at `skills/<pack-name>/SKILL.md`. It must remain useful
when installed alone and must not assume every sibling skill is installed.

### `RESOLVER.md`

The dispatcher metadata: a table mapping user intent to skills in the pack. It
is designed for maintainers and pack tooling. See
`packs/reasoning-and-analyses/RESOLVER.md` for the worked reference.

### `manifest.json`

The machine-readable index of every skill in the pack:

```json
{
  "name": "<pack-name>",
  "version": "1.0.0",
  "description": "<one-line pack description>",
  "skills": [
    {
      "name": "<skill-name>",
      "path": "../../skills/<skill-name>/SKILL.md",
      "description": "<one-line skill description>",
      "family": "<family-name>"
    }
  ]
}
```

### `references/`

Cross-cutting references used by multiple skills in the pack. They are not
installable skills. Examples include a shared overview, output rules, glossary,
or example dataset.

### `skills/<skill>/SKILL.md`

Every discoverable skill lives directly beneath `skills/`. See
`docs/skill-authoring.md`.

## Adding a new skillpack

```bash
mkdir -p packs/<pack>/references
touch packs/<pack>/RESOLVER.md
touch packs/<pack>/manifest.json
# optionally: mkdir -p skills/<pack> && touch skills/<pack>/SKILL.md
# add the pack to README.md and CHANGELOG.md
```

## Adding a skill to an existing pack

```bash
mkdir -p skills/<skill>
touch skills/<skill>/SKILL.md
# add a row to packs/<pack>/manifest.json
# add a row to packs/<pack>/RESOLVER.md
```

## What a pack does not contain

- Tests: keep them in a root `evals/` or `tests/` folder.
- Tooling scripts: keep them in a root `scripts/` folder.
- Build artifacts.
- End-user documentation: keep it under root `docs/`.
