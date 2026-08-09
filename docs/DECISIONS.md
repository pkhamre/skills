# Decisions

## 2026-08-09 — session-handoff skill scope

- **Decision:** Build a `session-handoff` skill that manages project docs across session start / during / end, stored at `.agents/skills/session-handoff/`.
- **Rationale:** Sessions are ephemeral; a durable doc set (HANDOFF, SESSION_LOG, DECISIONS, RUNBOOK) lets any future session reconstruct context quickly.
- **Rejected:** A bare `AGENTS.md` header note (the original Reddit suggestion) — a skill is more reusable and self-contained.

## 2026-08-09 — Triggering model

- **Decision:** The skill triggers only on explicit session commands ("start a session", "wrap up", "end session", "resume", "update the handoff", "log this session"). It must NOT trigger on ordinary completion signals.
- **Rationale:** Predictable behavior; avoids over-triggering mid-task. The user chose this over an opportunistic/pushy description.
- **Rejected:** Opportunistic triggering on "done" or task-completion signals.

## 2026-08-09 — Template strategy

- **Decision:** Bundle exact doc templates in `references/templates.md`, but prefer each file's existing format when one is established.
- **Rationale:** Consistent output across sessions without fighting repos that already have their own doc conventions.
