<p align="center">
  <img src="./assets/readme/hero.svg" width="100%" alt="Open Agent Skills: hand-maintained skills for agents that last. Shows session-handoff keeping project docs across the start, during, and end phases of a session.">
</p>

<p align="center">
  <a href="#installation"><strong>Install</strong></a> ·
  <a href="#session-handoff"><strong>Session Handoff</strong></a> ·
  <a href="#maintaining-this-collection"><strong>Add a skill</strong></a> ·
  <a href="#license"><strong>License</strong></a>
</p>

A small, hand-maintained collection of [open agent skills](https://opencode.ai/docs/skills) I keep improving. Each one lives in its own folder under [`skills/`](skills/) and stays small enough to read in full. Drop the ones you want into your own skills directory.

Right now there's one. That will change.

## Session Handoff

Sessions are ephemeral; the model and the human both forget context between them. Session Handoff keeps a tiny set of project docs so work survives. When a session starts it reads them in order, orients on where things stand, and proposes the highest-value next step. When it ends it writes current state and next actions back down, so the next session picks up cleanly instead of re-discovering everything.

<p align="center">
  <img src="./assets/readme/workflow.svg" width="100%" alt="Session Handoff lifecycle: start reads the docs and orients, during keeps them in sync, end writes state back down.">
</p>

The docs it maintains:

- **`HANDOFF.md`** holds where things stand and what's next.
- **`SESSION_LOG.md`** is a running record of each session.
- **`DECISIONS.md`** records durable choices and why they were made.
- **`RUNBOOK.md`** lists the commands worth not rediscovering.

It ships with `references/templates.md` (exact formats for each doc) and `references/read-order.md`.

### Installation

Install every skill in this repo:

```
npx skills add pkhamre/skills
```

Or add a single one:

```
npx skills add pkhamre/skills --skill session-handoff
```

The skill triggers on explicit session commands such as "start a session", "I'm back", or "wrap up", and ignores ordinary task-completion signals.

## Maintaining this collection

Adding a skill means creating `skills/<name>/SKILL.md` with a `name` and `description` in the frontmatter, plus any bundled `references/`, `scripts/`, or `assets/` it needs. The description is what makes it trigger, so it should say both what the skill does and when to reach for it. Keep the body under a few hundred lines and push detail into reference files. See [opencode's skill docs](https://opencode.ai/docs/skills) for the layout.

Installed upstream skills and the opencode install manifest aren't tracked here. Authored skills are the contents of `skills/`.

## License

MIT. See [LICENSE](LICENSE).
