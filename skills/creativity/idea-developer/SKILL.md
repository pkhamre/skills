---
name: idea-developer
description: Turn a rough tech or product idea into an actionable plan through a short adaptive interview. Use this whenever the user shares a half-formed idea for an app, product, tool, startup, feature, or side project and wants it shaped into something concrete. Triggers whether they say "I have an idea", "help me flesh this out", "turn this into a plan", "is this worth building", "where do I start", or just dump a vague one-liner and ask what you think. The skill asks probing questions one at a time, pushes back on weak spots like a vague audience or a missing differentiator, fills a plan template as the conversation goes, and closes with a one-page plan. Reach for it even when the user never says "skill" or "plan" but clearly wants a product concept developed. Do not use it for writing or reviewing code, or for answering factual questions.
---

# Idea Developer

A skill for turning a rough tech or product idea into an actionable plan. The user shows up with a half-formed thought, something like "an app that finds parking" or "a CLI tool that summarizes git history", and should leave with a one-page plan: who it is for and what gets built first.

## Why a skill for this

Rough ideas fail in predictable places. "An app for X" turns out to have no named user, or the same thing already exists, or the scope covers four products stapled together. Conversations drift when nobody forces the questions. This skill forces them one at a time and writes the answers into a plan while they're fresh, so the vague idea hardens into something the user could actually start on.

## How the interview runs

Adaptive, not a checklist. The question bank in `references/questions.md` organizes questions by theme: problem, audience, solution, differentiators, scope, risks, next actions. Start with the theme the idea makes most urgent, then follow the user's answers into adjacent ones. Cover enough ground that every section of the plan template has something honest in it.

Ask one question at a time. A single question. Bundling three into one list looks efficient and ruins the approach, because the next question has to react to the answer that just arrived.

Probe. Most questions do two jobs: they collect information and they test the idea. When the user answers "everyone" for an audience, or "it's just better" for a differentiator, or lists an app that does X and Y and Z as the scope, name the gap and ask them to fill it. A plan built on "everyone will use it" is a plan built on nothing, and catching that in conversation is the entire point of the skill.

## When to stop asking

Five to ten questions is the range. Stop when every plan section has real content and the next question would just round the same corner. If the user is short on patience, take what you have and close; a one-page plan is the deliverable, not a perfect one.

## The plan template

The template is the scaffold. Fill each section as the answers arrive and keep the shape in front of you. When a section stays empty because the user genuinely doesn't know, write it as an open question rather than dropping it.

# [Idea name]

**One-liner:** what it is, in a sentence a stranger gets

**Problem:** who has it, why it hurts, how they cope today

**Audience:** the specific user and how you'd reach them

**Solution:** what you build and what the user does with it

**Differentiators:** why this beats the obvious alternative

**MVP scope:** the smallest version that still proves it

**Risks:** the assumptions most likely to kill it

**Next actions:** the concrete steps for the coming week

## Presenting the plan

Close with the filled template in the chat, plain markdown, the one-pager and nothing decorative around it. Then offer one or two natural follow-ups: tightening the scope or turning a section into its own deeper plan. Stop there.

## The question bank

`references/questions.md` holds the full question bank: core questions per theme, follow-up branches for common answers, and the weak spots to probe under each. Read it when the interview starts.
