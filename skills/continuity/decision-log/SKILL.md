---
name: decision-log
description: Capture why a technical or product decision was made, not just what changed, so the reasoning survives. Use this skill when a decision is being made or revisited — choosing an approach, rejecting an alternative, a scope call, an architecture or design choice, a dependency or tool pick, or a reopened debate where the original tradeoffs have been forgotten. It records the decision in docs/DECISIONS.md along with the options considered, the tradeoffs, the chosen path, the rejected alternatives, and what would change the decision. Trigger when the user says "log this decision", "record why we chose X", "why did we decide Y", "re-litigating this", or when a durable decision is reached in conversation. Do NOT trigger on every operational or trivial choice — only durable decisions that shape future work.
---

# Decision Log

A skill that records **why** a decision was made, not just what changed. The point is to preserve the reasoning so that three months later, when the details have blurred, nobody has to re-litigate the same architecture debate because the tradeoffs were never written down.

## Why this matters

The "what" of a decision lives in the code, the config, the design. The "why" does not. Once the why is gone, the only way to recover it is to reconstruct the debate from memory — and memory is selective. Two people rarely remember the same tradeoffs, and the person who argued for the losing option often remembers the downside of the winner most vividly. A written decision log fixes that. It turns "why did we do this?" from an open argument into a lookup.

Decisions that get logged:

- a chosen approach over a rejected one
- a scope call (what's in, what's deferred)
- a dependency, library, or tool selection
- an architecture or design choice
- a tradeoff the team explicitly accepted

Decisions that do not get logged:

- routine operational picks with no lasting consequence
- micro-choices that don't shape future work
- anything that could be changed back in minutes with no loss

## When to record

Record when the decision is made, not later. A decision is durable if it will shape future work: it commits to a path, rejects an alternative, or sets a boundary. That's the test. If you're unsure, the safe call is to record it — a short entry costs little, and an absent entry is why the debate gets reopened.

Do not treat this as paperwork. The value is in capturing the reasoning while it's fresh and honest, before hindsight smooths the edges.

## Where decisions live

Decisions are recorded in `docs/DECISIONS.md`, one entry per decision, newest appended. This is the same file the session-handoff skill reads for context, so keeping the format stable matters — see `references/templates.md`.

## How to capture a decision

Walk through these in order. Not every field needs a full paragraph, but the reasoning must be real — do not pad a thin decision with generic justifications.

1. **State the decision plainly.** One sentence: what was chosen. If it's a scope call, say what's in and what's deferred.
2. **Give the context.** One or two sentences on why the decision was on the table at all — the problem, constraint, or pressure that forced it.
3. **List the options considered.** Name the real alternatives, not straw men. If there was only one workable option, say so.
4. **Record the tradeoffs.** What each option bought and cost. Be specific: performance, complexity, maintainability, risk, team familiarity, timeline.
5. **Note the rejected alternatives and why.** Brief. The rejected-options section is often the most valuable later, because it prevents someone from proposing the same losing option again.
6. **Capture what would change the decision.** This is the hard part and the most useful. Under what condition would you flip? A scale threshold, a new requirement, a failure mode, new information. If nothing would change it, say "none known" honestly.
7. **Add follow-up, if any.** A revisit date, a condition to re-check, a consequence to watch.

## Tone and honesty

Write the entry as you'd explain it to a sharp engineer who was not in the room. Assume they'll read it cold and should walk away understanding the reasoning without you there. That means:

- be specific about numbers and constraints, don't gesture at them
- say what the decision does NOT do, not just what it does
- name the real tradeoff you accepted, including the painful one
- if the decision was contested, record the strongest counterargument — a log that only contains the winning side's reasons is a press release, not a record

## When a decision is revisited

If a decision is reopened, read the existing entry first. Use it to ground the new debate: state whether the original tradeoffs still hold, whether the condition-that-would-change-it has been met, and what's new since. Revisit means the reasoning gets re-examined, not ignored. If the decision genuinely changes, append a new entry dated now rather than editing the old one — keep the history intact.

## Templates

Use `references/templates.md` for the exact decision-record format.
