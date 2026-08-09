# AGENTS.md

## What this repo is

A public collection of authored opencode skills for GitHub (`pkhamre/skills`). There is no application code, no build, and no test or lint tooling. There is nothing to compile or run in CI; the deliverable is the markdown under `skills/` plus the root `README.md`.

## Where things live

- `skills/<category>/<name>/` — canonical, tracked authored skills. Each has `SKILL.md` (frontmatter `name` + `description`; the description drives triggering) and optionally `references/`, `scripts/`, or `assets/`.
- `.agents/skills/` and `skills-lock.json` — installed upstream skills and the opencode install manifest. Both are gitignored. Do not commit them.
- `assets/readme/` — hand-authored SVG images embedded in the README.
- `docs/` — session docs (HANDOFF, SESSION_LOG, DECISIONS, RUNBOOK), maintained via the session-handoff skill.

## Gotcha: two copies of session-handoff, not synced

`skills/continuity/session-handoff/` is the tracked canonical source. `.agents/skills/session-handoff/` is the installed copy opencode actually loads. They are **out of sync right now**: the installed copy predates the decision-log refactor. Editing one does not touch the other. If you change session-handoff, update both and keep their content aligned.

## Skill relationships

- `decision-log` records decisions in `docs/DECISIONS.md`. `session-handoff` **delegates** decision capture to it and must not maintain DECISIONS itself. Preserve this split.
- Both live under `skills/continuity/`. New authored skills go under a category subdirectory, not directly under `skills/`.

## Writing rules for prose

README and skill bodies are public-facing. Keep bodies under a few hundred lines and push detail into `references/`. Run new or edited prose through the `anti-ai-slop-writing` skill: no em dashes over budget, no banned words, no rule-of-three, varied sentence length. The README currently has zero em dashes and zero banned words; don't regress it.

## Verifying SVG assets

No rasterizer is available in this environment (no cairo/rsvg/inkscape/browser, no network). Verify hand-edited SVGs by XML well-formedness and the bundled audit script:

```
python3 .agents/skills/beautify-github-readme/scripts/audit_readme.py README.md
```

## Session workflow

On an explicit session start/resume/end command, follow the `session-handoff` skill: read `README.md`, `docs/HANDOFF.md`, the latest `docs/SESSION_LOG.md` entry, `docs/DECISIONS.md`, `docs/RUNBOOK.md` in that order, and update HANDOFF + SESSION_LOG when wrapping up.

## Git state

Remote `origin` is `git@github.com:pkhamre/skills.git`; `main` tracks `origin/main` and is currently ahead of it by unpushed commits. Prefer the README's `npx skills add pkhamre/skills` commands for install references.
