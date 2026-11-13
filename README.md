<p align="center">
  <img src="brand/banners/banner-readme-1280x320.png" alt="skills" width="800">
</p>

# Agent Skills

Reusable skills for AI coding agents, organized for installation with the
open `skills` CLI.

## Install

List the available skills:

```bash
npx skills@latest add starship-terminal/skills --list
```

Install interactively:

```bash
npx skills@latest add starship-terminal/skills
```

Install a specific skill:

```bash
npx skills@latest add starship-terminal/skills --skill five-whys
```

## Catalog

| Pack | Purpose | Status |
|---|---|---|
| `reasoning-and-analyses` | First-principles reasoning and analysis frameworks for conversation-time problem solving | Active |

The pack currently contains a dispatcher and ten standalone skills:

- Socratic questioning
- Fishbone diagram
- Five whys
- Fault-tree analysis
- Pareto analysis
- Mind mapping
- Blank-slate design
- Cost-benefit disassembly
- Constraint elimination
- Analogy vs first-principles matrix

## Repository layout

```text
agent-skills/
├── skills/                    # Installable skills; one folder per skill
│   └── <skill>/
│       └── SKILL.md
├── packs/                     # Catalog metadata and shared pack references
│   └── <pack>/
│       ├── RESOLVER.md
│       ├── manifest.json
│       └── references/
├── docs/                      # Authoring conventions
├── CHANGELOG.md
└── VERSION
```

`skills/` stays flat so each skill is independently discoverable and
installable. `packs/` records relationships between skills without affecting
installer discovery.

## Authoring

1. Read `docs/skill-authoring.md` for the `SKILL.md` standard.
2. Read `docs/skillpack-anatomy.md` for pack organization.
3. Follow the conventions in `docs/conventions/`.
4. Use `packs/reasoning-and-analyses/` as the worked example.
