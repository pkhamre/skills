# Document Templates

## Decision record (DECISIONS.md)

Append new entries at the end of `docs/DECISIONS.md`. Each entry is a dated heading followed by the decision, its context, the options, the tradeoffs, and what would change it.

```markdown
## YYYY-MM-DD — <Short decision title>

- **Decision:** <What was chosen, in one sentence. For a scope call, what's in and what's deferred.>
- **Context:** <Why this was on the table: the problem, constraint, or pressure that forced it.>
- **Options considered:** <The real alternatives, with what each bought and cost.>
- **Tradeoffs:** <The accepted tradeoffs, including the painful one. Be specific about numbers and constraints.>
- **Rejected:** <Alternatives passed over and why. Brief.>
- **Would change if:** <The condition under which you'd flip: a scale threshold, new requirement, failure mode, new information. "None known" if nothing.>
- **Follow-up:** <A revisit date, condition to re-check, or consequence to watch. Omit if none.>
```

Write the entry as you'd explain the reasoning to a sharp engineer who wasn't in the room. Be specific, say what the decision does NOT do, and record the strongest counterargument — a log that only has the winning side's reasons is a press release, not a record.

Only log durable decisions that shape future work, not routine operational choices.
