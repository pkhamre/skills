# Handoff

## Last updated
2026-08-10 10:11 UTC

## Current state
This repo is a public collection of authored opencode skills. Authored skills: `session-handoff` (canonical at `skills/continuity/session-handoff/`, installed copy kept in sync at `.agents/skills/session-handoff/`) and `decision-log` (at `skills/continuity/decision-log/`), both under the `continuity` category, plus the new `idea-developer` skill at `skills/creativity/idea-developer/` under a new `creativity` category. `idea-developer` turns a rough tech/product idea into a one-page plan via an adaptive probing interview, with the question bank in `references/questions.md` and a progressive-fill plan template (one-liner, problem, audience, solution, differentiators, MVP scope, risks, next actions). Its skill-creator eval (3 with-skill vs baseline cases) passed 10/10 template assertions with-skill vs 0/10 baseline; description optimization was skipped because the user is happy with the skill as-is. The repo tracks only authored skills: `.agents/` and `skills-lock.json` are gitignored, an MIT `LICENSE` is present, and a root `README.md` documents all three skills (Session Handoff, Decision Log, Idea Developer), the category layout, and install + maintenance sections. `AGENTS.md` records the repo conventions (skill layout, dual-copy sync gotcha, prose rules, SVG verification, session workflow). README visuals are complete: `hero.svg`, `workflow.svg`, `decision-flow.svg`, `decision-record.svg`. All prose and alt text pass `anti-ai-slop-writing`. Remote `origin` (`git@github.com:pkhamre/skills.git`) is configured; `main` is ahead of `origin/main` by unpushed commits.

## Next actions
1. Push `main` to `origin/main` once the current commit lands.
2. Visually preview the README SVGs at GitHub width; no rasterizer was available in this environment, so they were only verified via XML well-formedness and `audit_readme.py`.

## Blockers
None.
