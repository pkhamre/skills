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

## 2026-08-09 — Repo layout for public release

- **Decision:** Authored skills live under `skills/<name>/` as the tracked canonical source; installed upstream skills under `.agents/skills/` and the opencode install manifest (`skills-lock.json`) are gitignored and untracked. `session-handoff` is duplicated (canonical in `skills/continuity/`, installed copy kept at `.agents/skills/session-handoff/`).
- **Rationale:** The repo is a home for skills the user authors; upstream-installed dependencies are not part of the authored collection and shouldn't be published. Keeping an installed copy lets the skill keep working locally while the repo holds the source.
- **Rejected:** Tracking installed skills in the repo; moving `session-handoff` out of `.agents/skills/` entirely (it needs to stay installed for local use).
- **Decision:** README documents only the authored skill (`session-handoff`), omits upstream skills, and includes install + maintenance sections. License is MIT.
- **Rationale:** The README is a project overview aimed at the user and the public; it should describe what this repo actually contains.

## 2026-08-09 — README content

- **Decision:** README documents only the authored skill (`session-handoff`), omits upstream skills, and includes install + maintenance sections.
- **Rationale:** The README is a project overview aimed at the user and the public; it should describe what this repo actually contains.

## 2026-08-09 — Continuity category and decision-log

- **Decision:** Introduce category subdirectories under `skills/`; both session-handoff and the new decision-log skill live under `skills/continuity/`.
- **Rationale:** The category names the shared intent: both skills preserve knowledge across time, so they sit together under a label that says so. It scales as more skills are added.
- **Rejected:** `skills/decisions/` for decision-log; keeping session-handoff at `skills/session-handoff/` while adding a sibling category.

- **Decision:** decision-log captures why a decision was made (context, options, tradeoffs, rejected alternatives, what would change it) in `docs/DECISIONS.md`. It replaces session-handoff's responsibility for DECISIONS.md, which now delegates to it.
- **Rationale:** A dedicated skill holds a richer, more honest record than a maintenance step inside session-handoff, and it triggers on decision moments rather than on session lifecycle commands.
- **Rejected:** Keeping DECISIONS.md maintenance inside session-handoff.

- **Decision:** README now documents both authored skills (Session Handoff and Decision Log) and the category layout.
- **Rationale:** The repo contains two authored skills; the overview should match that.
