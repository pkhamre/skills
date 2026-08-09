# Runbook

## Docs / Session handoff

The session-handoff skill lives at `.agents/skills/session-handoff/`. It maintains these docs: `README.md`, `docs/HANDOFF.md`, `docs/SESSION_LOG.md`, `docs/RUNBOOK.md`. Decisions are captured separately by the decision-log skill in `docs/DECISIONS.md`. The canonical authored sources live under `skills/continuity/`.

Get current UTC timestamp for handoff/log entries: `date -u '+%Y-%m-%d %H:%M UTC'`
