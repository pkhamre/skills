# Open Agent Skills

A small collection of open agent skills I've written and keep maintaining. Each one lives in its own directory under [`skills/`](skills/), and you drop the folder you want into your own `.agents/skills/` to use it.

Right now there's one skill here. That will change.

## Session Handoff

Session Handoff keeps a tiny set of project docs so work survives between sessions. The model and the human both forget context between sessions; these docs are the durable memory. When you start a session it reads them in order — README, `docs/HANDOFF.md`, the latest `docs/SESSION_LOG.md` entry, `docs/DECISIONS.md`, `docs/RUNBOOK.md` — orients, and proposes the highest-value next step. When you wrap up it writes the current state and next actions back down so the next session picks up cleanly instead of re-discovering everything.

It runs in three phases:

- **Start / resume** — load the docs in a fixed order, orient on where things stand, and suggest what to do next.
- **During work** — keep `HANDOFF.md`, `DECISIONS.md`, and `RUNBOOK.md` in sync as meaningful things change.
- **End** — update the handoff, append a session log entry, and scan what you touched for secrets before closing.

It ships with `references/templates.md` (exact formats for each doc) and `references/read-order.md`.

### Install

Install every skill in this repo:

```
npx skills add pkhamre/skills
```

or add a single one:

```
npx skills add pkhamre/skills --skill session-handoff
```

The skill triggers on explicit session commands — "start a session", "I'm back", "wrap up" — and ignores ordinary task-completion signals.

## Maintaining this collection

Adding a skill means creating `skills/<name>/SKILL.md` with a `name` and `description` in the frontmatter, plus any bundled `references/`, `scripts/`, or `assets/` it needs. The description is what makes it trigger, so it should say both what the skill does and when to reach for it. Keep the body under a few hundred lines and push detail into reference files. See [opencode's skill docs](https://opencode.ai/docs/skills) for the layout.

Installed upstream skills and the opencode install manifest aren't tracked here. Authored skills are the contents of `skills/`.

## License

MIT. See [LICENSE](LICENSE).
