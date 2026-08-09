# Handoff

## Last updated
2026-08-09 20:57 UTC

## Current state
This repo is a public collection of authored opencode skills. Two authored skills live under the `continuity` category: `session-handoff` (canonical at `skills/continuity/session-handoff/`, installed copy kept in sync at `.agents/skills/session-handoff/`) and `decision-log` (at `skills/continuity/decision-log/`), which captures why a decision was made in `docs/DECISIONS.md` and owns that responsibility; session-handoff delegates decision capture to it. The repo tracks only authored skills: `.agents/` and `skills-lock.json` are gitignored, an MIT `LICENSE` is present, and a root `README.md` documents both skills, the category layout, and install + maintenance sections. `AGENTS.md` records the repo conventions (skill layout, dual-copy sync gotcha, prose rules, SVG verification, session workflow). README visuals are complete: `hero.svg` (centered title-only composition with a visible yellow OPEN AGENT SKILLS eyebrow, 1200x320), `workflow.svg` (session-handoff lifecycle), and `decision-flow.svg` + `decision-record.svg` (decision-log). All prose and alt text pass `anti-ai-slop-writing` (no em dashes, no banned words). Remote `origin` (`git@github.com:pkhamre/skills.git`) is configured and `main` is in sync with `origin/main` at `0f2b042` (with new commits `9824ec4` etc. on top, awaiting push).

## Next actions
1. Visually preview the README SVGs (`hero.svg`, `workflow.svg`, `decision-flow.svg`, `decision-record.svg`) at GitHub width; no rasterizer was available in this environment, so they were only verified via XML well-formedness and `audit_readme.py`.
2. Confirm the `npx skills add pkhamre/skills --skill <name>` install path resolves skills nested under `skills/continuity/`.
3. Decide whether to add more authored skills under `skills/` over time.

## Blockers
None.
