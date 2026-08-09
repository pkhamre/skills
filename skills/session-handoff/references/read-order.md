# Read Order

At session start, read these files in this exact order. Each builds context that the next one assumes:

1. **`README.md`** — the project's purpose and scope. Answers "what is this project for?" before anything else.
2. **`docs/HANDOFF.md`** — where things currently stand. Answers "what's the state right now?" and "what's next?".
3. **latest entry in `docs/SESSION_LOG.md`** — the most recent session's narrative. Adds the recent "what happened and why" story on top of the handoff snapshot.
4. **`docs/DECISIONS.md`** — durable choices and their rationale. Explains why the project is shaped the way it is, so you don't re-litigate settled questions.
5. **`docs/RUNBOOK.md`** — operational commands. Gives you the exact commands to build, test, and deploy, so you don't rediscover them.

Read in this order so that broad context (purpose) narrows down to operational detail (commands). If a file is missing, note it and continue — the remaining files may still give you what you need. Offer to bootstrap missing docs if the user expects them to exist.
