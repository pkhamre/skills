# Handoff

## Last updated
2026-08-09 20:45 UTC

## Current state
This repo is being prepared for public release as a collection of authored opencode skills. Two authored skills now live under the `continuity` category: `session-handoff` (canonical at `skills/continuity/session-handoff/`, installed copy remains at `.agents/skills/session-handoff/`) and `decision-log` (at `skills/continuity/decision-log/`), which captures why a decision was made in `docs/DECISIONS.md` and replaces session-handoff's DECISIONS responsibility. The repo tracks only authored skills: `.gitignore` ignores `.agents/` and `skills-lock.json`, an MIT `LICENSE` is present, and a root `README.md` documents both skills, the category layout, and install + maintenance sections. The README was passed through `anti-ai-slop-writing` again (no em dashes, no banned words). Changes are committed locally (`f1fef0f`, plus the README update). No remote is configured and nothing has been pushed yet.

## Next actions
1. Visually preview `assets/readme/hero.svg` and `assets/readme/workflow.svg` at GitHub width (no rasterizer was available in this environment, so they were only verified via XML well-formedness and the bundled `audit_readme.py`). Decide whether the visuals should also depict decision-log.
2. Create the public GitHub repo and push (no remote is configured yet).
3. Confirm the `npx skills add pkhamre/skills --skill <name>` install path works with skills nested under `skills/continuity/`.

## Blockers
None.
