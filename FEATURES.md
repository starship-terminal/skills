# Features

Reusable first-principles reasoning skills for AI coding agents, packaged for installation with the open `skills` CLI.

## Install and routing

- **Install with the skills CLI**: lists, installs interactively, or installs one named skill from this repo. Status: stable. Surface: CLI. Entry point: `npx skills@latest add starship-terminal/skills` (README.md). Tests: none.
- **Pack dispatcher skill**: picks one of the ten child frameworks when the problem shape is unclear, or asks the user when two fit. It routes only and never applies a framework itself; the selected child skill must also be installed to continue. Status: stable. Surface: skill. Entry point: `skills/reasoning-and-analyses/SKILL.md`. Tests: none.

## Root-cause analysis

- **Fishbone diagram**: lays out cause categories side by side, with the problem at the head and causes on the bones. Status: stable. Surface: skill. Entry point: `skills/fishbone-diagram/SKILL.md`. Tests: none.
- **Five whys**: asks "why" repeatedly along one causal chain until it reaches an actionable root cause. Status: stable. Surface: skill. Entry point: `skills/five-whys/SKILL.md`. Tests: none.
- **Fault-tree analysis**: works backward from a failure through AND/OR gates to the basic events behind it. Status: stable. Surface: skill. Entry point: `skills/fault-tree-analysis/SKILL.md`. Tests: none.
- **Pareto analysis**: ranks cause categories by impact so you can focus on the vital few. Status: stable. Surface: skill. Entry point: `skills/pareto-analysis/SKILL.md`. Tests: none.

## First-principles reasoning

- **Socratic questioning**: runs a six-category question pass to surface assumptions, evidence, viewpoints, implications and purpose before any answer. Status: stable. Surface: skill. Entry point: `skills/socratic-questioning/SKILL.md`. Tests: none.
- **Blank-slate design**: drops inherited conventions and rebuilds a solution from the user's actual needs. Status: stable. Surface: skill. Entry point: `skills/blank-slate-design/SKILL.md`. Tests: none.
- **Cost-benefit disassembly**: splits a bundled solution into component costs and benefits, then reassembles only the justified pairs. Status: stable. Surface: skill. Entry point: `skills/cost-benefit-disassembly/SKILL.md`. Tests: none.
- **Constraint elimination**: sorts every "we can't" into hard or soft constraints and removes the soft ones before solving. Status: stable. Surface: skill. Entry point: `skills/constraint-elimination/SKILL.md`. Tests: none.

## Exploration and decisions

- **Mind mapping**: explores a topic non-linearly, with a central idea and branches of related parts. Status: stable. Surface: skill. Entry point: `skills/mind-mapping/SKILL.md`. Tests: none.
- **Analogy vs first-principles matrix**: uses a 2x2 of stakes and novelty to decide whether to copy a proven solution or derive one. Status: stable. Surface: skill. Entry point: `skills/analogy-vs-first-principle-matrix/SKILL.md`. Tests: none.

## Pack metadata

- **Pack manifest**: machine-readable index of the pack's ten skills with paths, descriptions and families. Status: stable. Surface: docs. Entry point: `packs/reasoning-and-analyses/manifest.json`. Tests: none.
- **Pack resolver**: routing table from user intent to skill, plus common chains (for example fishbone to five whys) and disambiguation rules. Status: stable. Surface: docs. Entry point: `packs/reasoning-and-analyses/RESOLVER.md`. Tests: none.
- **Shared references**: a first-principles overview and shared output rules used by the pack's skills. Status: stable. Surface: docs. Entry point: `packs/reasoning-and-analyses/references/first-principles-overview.md`, `packs/reasoning-and-analyses/references/output-rules.md`. Tests: none.

## Authoring docs

- **Skill authoring guide**: the `SKILL.md` standard for writing a new skill. Status: stable. Surface: docs. Entry point: `docs/skill-authoring.md`. Tests: none.
- **Skillpack anatomy**: describes the required pack files and how to add a pack or a skill to one. Status: stable. Surface: docs. Entry point: `docs/skillpack-anatomy.md`. Tests: none.
- **Conventions**: rules for frontmatter, MECE structure and output formatting. Status: stable. Surface: docs. Entry point: `docs/conventions/frontmatter.md`, `docs/conventions/mece.md`, `docs/conventions/output-rules.md`. Tests: none.

## Brand

- **Brand kit**: logos, lockups, banners, icons, fonts and a brand sheet for the repo. Status: stable. Surface: docs. Entry point: `brand/brand.md`. Tests: none.

No planned features: the repo has no roadmap, milestone or spec documents.
