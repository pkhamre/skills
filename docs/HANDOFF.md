# Handoff

## Last updated
2026-08-09 20:10 UTC

## Current state
This repo is being prepared for public release as a collection of authored opencode skills. The canonical source for `session-handoff` lives at `skills/continuity/session-handoff/` (an installed copy remains at `.agents/skills/session-handoff/` for local use). The repo tracks only authored skills: `.gitignore` ignores `.agents/` and `skills-lock.json`, an MIT `LICENSE` is present, and a root `README.md` documents `session-handoff` plus install and maintenance sections. This session redesigned the README: added `assets/readme/hero.svg` and `assets/readme/workflow.svg` (monochrome technical palette, session-lifecycle motif) via the `beautify-github-readme` skill, restructured the README around value -> proof -> mechanism -> install -> maintain, then passed it through `anti-ai-slop-writing` (removed all 6 em dashes; no banned words, exclamations, ellipses, or passive voice). Changes are committed locally (`617baa5`, `50f6c08`). No remote is configured and nothing has been pushed yet.

## Next actions
1. Visually preview `assets/readme/hero.svg` and `assets/readme/workflow.svg` at GitHub width (no rasterizer was available in this environment, so they were only verified via XML well-formedness and the bundled `audit_readme.py`).
2. Create the public GitHub repo and push (no remote is configured yet).
3. Decide whether to add more authored skills under `skills/` over time, using the README's maintenance section.

## Blockers
None.
