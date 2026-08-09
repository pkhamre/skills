# Document Templates

Use these templates so the docs stay consistent across sessions. If a doc already has an established format that differs from these, follow the existing format instead — consistency with the file's own history matters more than matching these exact templates.

## HANDOFF.md

```markdown
# Handoff

## Last updated
YYYY-MM-DD HH:MM UTC

## Current state
<A concise paragraph describing where the project/work currently stands.>

## Next actions
1. <Top priority action>
2. <Second priority action>
3. <Third priority action>

## Blockers
<Nothing blocking progress.> — or list the specific blockers.
```

The top-3 next actions should be the most valuable things to do next, in priority order, stated concretely enough that a fresh session can act on them.

## SESSION_LOG.md entry

Append new entries at the end (or top, if the file's existing convention puts newest first — match it). Each entry is a dated heading followed by a short summary:

```markdown
## YYYY-MM-DD HH:MM UTC
<Brief narrative of what happened in this session: tasks done, findings, key events, open threads. A few sentences is usually enough.>
```

Each session gets one entry. The timestamp should match the session's end time.

## DECISIONS.md entry

Add durable decisions as dated entries. Each should capture what was decided, why, and (optionally) what was rejected:

```markdown
## YYYY-MM-DD — <Short decision title>

- **Decision:** <What we decided.>
- **Rationale:** <Why this choice.>
- **Rejected:** <Alternatives considered and why they were passed over, if any.>
```

Only log decisions that will shape future work — not routine operational choices.

## RUNBOOK.md entry

Add or update operational commands. Organize by purpose so commands are easy to find:

```markdown
## <Area, e.g., Build / Test / Deploy / Setup>

<What this does>: `<exact command>`
```

Use verbatim commands (flags and arguments intact) so they can be copied and run directly. Note any environment prerequisites inline.
