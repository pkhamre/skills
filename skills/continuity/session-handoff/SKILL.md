---
name: session-handoff
description: Manage project docs across a session lifecycle, including resuming. Use this skill when the user gives an explicit session command — starting a session ("start a session", "kick off"), resuming one ("I'm back", "let's continue", "resume", "pick up where we left off", "continue where we left off", "what's the state of things", "what should I do next"), or ending one ("wrap up", "end the session", "update the handoff", "log this session", "write the session log"). When resuming, the skill loads the docs, orients on the current state, and proposes the highest-value next action. When ending, it updates HANDOFF.md and SESSION_LOG.md so the next session picks up cleanly. Decisions are captured by the decision-log skill, not here. Do NOT trigger on ordinary tasks or completion signals on their own — this skill runs only when the user explicitly asks to begin, resume, or end a documented session.
---

# Session Handoff

A skill that maintains a small set of project docs so work survives across sessions. It runs in three phases: **Start**, **During**, and **End**. The goal is that any future session — human or model — can reconstruct context in a few reads instead of re-discovering everything.

## Why this matters

Sessions are ephemeral. The model and the human forget context between them. These docs are the durable memory. The whole point is that you should never have to ask "what was I doing again?" — the docs answer it. Everything below exists to serve that goal, so keep the docs honest and current rather than treating them as paperwork.

## Phase 1: Session Start or Resume

When the user asks to start, resume, or check on the state of a session, load context in this **exact order**:

1. `README.md`
2. `docs/HANDOFF.md`
3. the latest (most recent) entry in `docs/SESSION_LOG.md`
4. the decision log at `docs/DECISIONS.md` (maintained by the decision-log skill)
5. `docs/RUNBOOK.md`

Read them in this order on purpose: README gives the project's purpose, HANDOFF gives where things currently stand, the latest session log entry adds recent narrative, the decision log explains why past choices were made (maintained by the decision-log skill, not here), and RUNBOOK holds the operational commands. Each builds on the last.

**If a file doesn't exist yet:** note it, don't error. This usually means the repo hasn't been bootstrapped. If the user expects the docs to exist and they don't, offer to bootstrap them (see Phase 1 bootstrap below).

### Orient
After reading, summarize your understanding back briefly: current state, recent activity, and what the last session intended to do next. Ask for confirmation if anything is ambiguous.

### Propose next action (resume)
If the user is resuming (rather than starting fresh), go one step further than orienting: recommend the single highest-value next action based on `docs/HANDOFF.md`'s top next actions. State it concretely enough to act on immediately — reference the specific file or task and the first step to take. Present it as a suggestion and ask for confirmation before starting work. Don't silently begin the task; the user may want to redirect.

### Bootstrap (only if the docs don't exist)
If this is the first documented session and the user wants the docs created, create:
- `docs/HANDOFF.md` — with a `Last updated` timestamp, current state, and empty next-actions section
- `docs/SESSION_LOG.md` — with a header and the current session's first entry
- `docs/RUNBOOK.md` — with a header and any known operational commands

Do not create `docs/DECISIONS.md` yourself. Decisions belong to the decision-log skill; if the user wants the decision log set up, invoke decision-log to bootstrap it. Use the templates in `references/templates.md`. Don't fabricate history that isn't real.

## Phase 2: During Work

Keep the docs aligned as the session proceeds. You don't need to update them after every micro-step — update them when meaningfully things change.

- **`docs/HANDOFF.md`** — keep the current state and next actions in sync with reality as the work progresses. This is the primary "where we are" document.
- **`docs/RUNBOOK.md`** — record changes to operational commands: new build/test/deploy commands, changed flags, commands the team should know. If you run a notable command or discover a required setup step, capture it here so it's not rediscovered later.

**Decisions are not handled here.** When a durable decision is made — a chosen approach, a rejected alternative, a scope call — do not log it yourself. Invoke the decision-log skill to capture it in `docs/DECISIONS.md`. You keep the decision log in sync only in the narrow sense of reading it for context.

Follow whatever format those files already use; if there's no established format, use the templates in `references/templates.md`.

## Phase 3: Session End

When the user asks to wrap up, update `docs/HANDOFF.md`:
- **`Last updated`** — timestamp in `YYYY-MM-DD HH:MM UTC` format
- **current state** — a concise description of where things stand now
- **top 3 next actions** — the most important next steps, in priority order
- **blockers** — anything blocking progress, or "None" if nothing

Then append a new timestamped entry to `docs/SESSION_LOG.md` summarizing what happened this session.

Finally, verify no secrets were added to tracked files: scan the files you touched for API keys, tokens, passwords, or credentials. If you find any, remove them. This is a real safety step, not a formality.

## Templates

Use `references/templates.md` for exact formats of HANDOFF current-state sections, SESSION_LOG entries, and RUNBOOK entries. For decision records, see the decision-log skill's `references/templates.md` instead.
