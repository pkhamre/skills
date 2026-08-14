# opencode agent file format

The authoritative reference is the published JSON Schema at `https://opencode.ai/config.json`. This file covers the common surface; when a field is not documented here, read the schema.

## Locations

| Scope | Path |
| --- | --- |
| Project | `.opencode/agent/<name>.md` or `.opencode/agents/<name>.md` |
| Global | `~/.config/opencode/agent/<name>.md` |

A project agent with the same name masks a global one. Config is loaded once at startup; a new agent requires restarting opencode.

## Frontmatter

Allowed top-level fields: `name`, `model`, `variant`, `description`, `mode`, `hidden`, `color`, `steps`, `options`, `permission`, `disable`, `temperature`, `top_p`. Any unknown field is silently routed into `options`, which is almost never what the author meant, so stay on the list.

- `name`: the agent identifier. Lowercase, hyphen-separated, matches the file name.
- `description`: one or two sentences on what the agent is for. For subagents this is what a delegator reads when deciding, so name the situations where the agent should be reached for.
- `mode`: `primary`, `subagent`, or `all`. `primary` runs as the main assistant when selected. `subagent` runs only when delegated to through the Task tool. `all` is both.
- `model`: provider-prefixed, e.g. `anthropic/claude-sonnet-4-6`. Omit to inherit the project default.
- `temperature`: a float. Omit unless the user has a reason to set it.
- `color`: a hex color that tints the agent in the TUI.
- `hidden`: boolean. Hidden agents stay out of the TUI list.
- `disable`: boolean. Turns the agent off. This is how a built-in gets disabled.
- `variant`: a model-variant override.
- `steps`: a short task list the agent can pull up.
- `permission`: tool access rules, described below.

The file body becomes the agent's `prompt`. Never put `prompt:` in the frontmatter.

## Permission

`permission` is either a flat action or an object keyed by tool name. Actions are `allow`, `ask`, `deny`.

A flat string means every tool:

```yaml
permission: allow
```

Per-tool with per-tool patterns:

```yaml
permission:
  edit: deny
  bash:
    "git *": allow
    "rm *": deny
    "*": ask
```

Within a per-tool object, insertion order matters: opencode evaluates the last matching rule, so put broad rules first and narrow rules last.

Known permission keys: `read`, `edit`, `glob`, `grep`, `list`, `bash`, `task`, `external_directory`, `todowrite`, `question`, `webfetch`, `websearch`, `lsp`, `doom_loop`, `skill`. A few of these, `todowrite`, `question`, `webfetch`, `websearch`, and `doom_loop`, accept only a flat action.

Per-agent `permission` overrides the top-level `permission` in `opencode.json`.

## Built-in agents

opencode ships with `build`, `plan`, `general`, and `explore`, plus the hidden internals `compaction`, `title`, and `summary`. Defining an agent under one of those names overrides the built-in's fields; `disable: true` turns it off. `default_agent` in config must point to a non-hidden, primary-mode agent.

## Inline form

`opencode.json` can hold agents inline instead of a file:

```json
{
  "agent": {
    "my-reviewer": {
      "description": "Reviews PRs for style and correctness.",
      "mode": "subagent",
      "model": "anthropic/claude-sonnet-4-6",
      "permission": { "edit": "deny", "bash": "ask" },
      "prompt": "You are a strict PR reviewer..."
    }
  }
}
```

Prefer the file form for anything non-trivial, because the file body is the prompt. Inline agents carry `prompt` in the JSON.

## Worked examples

A reviewer subagent, `.opencode/agent/code-reviewer.md`:

```markdown
---
description: Reviews pull requests for correctness, style, and security. Reach for this when a change needs a second pair of eyes.
mode: subagent
permission:
  edit: deny
  bash: deny
---

You are a strict code reviewer. Read the diff in the request and report findings grouped by severity: bugs first, then style, then security. Suggest fixes in the comment text but never apply them yourself. If the change is sound, say so plainly instead of inventing nitpicks.
```

A git-history primary agent, `.opencode/agent/git-historian.md`:

```markdown
---
description: Explores git history to answer how and why the codebase changed. Pick this agent when the question is about the past.
mode: primary
permission:
  read: allow
  bash:
    "git *": allow
    "*": deny
---

You are a git historian. Answer questions about the codebase's past using git: log, blame, show, diff, and reflog. Trace when a line was introduced and why it might have changed. Cite your answers with commit hashes and dates.
```

A release-notes subagent, `.opencode/agent/release-notes.md`:

```markdown
---
description: Drafts release notes from the git log since the last tag. Use when asked to write release notes.
mode: subagent
permission:
  bash:
    "git *": allow
    "*": deny
  edit: allow
---

You draft release notes. Read the log since the last tag, group commits by theme, and write a note a user would actually want to read: what changed, what to watch for, and any migration steps. Do not invent version numbers or dates that are not in the log.
```
