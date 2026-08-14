---
name: agent-creator
description: Create new opencode agent definitions. Use this skill whenever the user asks to make an agent: "create an agent", "add a subagent", "I need an agent that reviews PRs", "make me an agent for git history", "define an agent that writes release notes", or any plain-language request for a reusable helper that gets picked as the main assistant or delegated to. The skill interviews briefly for purpose, mode, model, and permissions, writes a valid agent file to the right scope (project .opencode/agent/ by default, global ~/.config/opencode/agent/ when the user implies a tool for every project), and reminds them to restart opencode. Do not use it for commands, skills, or plugins, which are separate definition types.
---

# Agent Creator

A skill for turning a plain ask like "I need an agent that reviews my pull requests" into a working opencode agent file. The user describes the agent in everyday language; they get a `.md` file opencode can load.

## Why a skill for this

opencode agents live in one place with one shape: `.opencode/agent/<name>.md`, a YAML frontmatter limited to a specific field list, and a body that becomes the agent's prompt. Put a field wrong and opencode refuses to start. Write a lazy prompt and the agent behaves nothing like the user imagined. The failure mode here is detail, and the skill carries the detail so the user never has to think in schema terms.

## The interview

Keep it short. You need just enough for a valid definition, nothing more. Gather the gaps in one compact follow-up message rather than asking one question at a time, and if the user already described everything in their first message, skip the interview and write the file.

- **Purpose.** What is the agent for? What does it do day to day, and what does it refuse to do? This becomes the description and the prompt body, so push past a one-liner. What is the user sick of doing themselves?
- **Mode.** `primary`, `subagent`, or `all`. A subagent gets invoked by name through the Task tool, so it needs a focused mission and a description that makes the delegation decision obvious. A primary agent is what the user talks to directly. If the user said "add a subagent", that settles it; otherwise ask.
- **Model.** Ask only when the user has a preference. Leave the field out and the agent inherits the project default, which is right most of the time.
- **Permissions.** What must the agent touch? A reviewer reads code and should not edit it. A refactorer edits freely but should not run arbitrary bash. Probe the extremes rather than walking through every tool. When the user doesn't know, default to the least access the purpose supports.
- **Extras.** Temperature or color only when the user asks for them. Do not invent a temperature.

## Name and location

Pick the name from the purpose: lowercase, hyphen-separated, matching the file name.

Default to project scope, `.opencode/agent/<name>.md`. Use global scope, `~/.config/opencode/agent/<name>.md`, when the user implies a tool they want in every project. When the scope is genuinely unclear, ask rather than guessing.

Before writing, check whether an agent with that name already exists. If one does, show it and ask before overwriting; the same name in project scope masks the global one.

## Write the file

Restrict the frontmatter to the allowed fields and put the personality in the body. The body is the prompt: who the agent is, what it does, how it should behave, what it must refuse. Read `references/agent-format.md` for the exact shape, the full field list, and worked examples. If a field's shape is in doubt, check it against the schema at `https://opencode.ai/config.json` before writing, because opencode hard-fails on invalid config.

## After writing

Show the user what was created: the path, the mode, the one-line description, and the permission stance. Then remind them to quit and restart opencode. Config loads at startup, and the running session keeps ignoring the new agent until then.
