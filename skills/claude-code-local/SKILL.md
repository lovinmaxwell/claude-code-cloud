---
name: claude-code-local
description: Run Claude Code locally via the CLI for coding tasks in a working directory. Use when the user wants Claude Code on this machine (not cloud), headless claude -p, continue/resume, or local agentic coding.
---

# Claude Code local

Use this skill when the user wants Claude Code to run on this machine rather than on Anthropic infrastructure.

## Working directory and authentication

Prefer the working directory to be the repository or path named by the user. Before running a task, check authentication:

```bash
claude auth status
```

If it fails, use the setup skill and have the user complete any required interactive login. Do not print credentials or API keys.

## Headless one-shot tasks

Run a prompt without an interactive terminal:

```bash
claude -p "prompt" --output-format json
```

Add `--bare` for scripted or faster startup when project hooks and skills are not needed:

```bash
claude -p "prompt" --bare --output-format json
```

Parse the JSON output and report the result to the user, including relevant errors and the task outcome.

## Continuing and resuming

Continue the most recent conversation in the current directory:

```bash
claude -c -p "prompt"
```

Resume a specific session by ID or name:

```bash
claude -r "session-id-or-name" "prompt"
```

Only use a session identifier supplied by the CLI or the user.

## Useful controls

Use these options when appropriate:

- `--model` to select a model.
- `--permission-mode` with `default`, `acceptEdits`, `plan`, or `bypassPermissions`.
- `--allowedTools` to constrain tool access.
- `--max-turns` to limit agent turns.
- `--max-budget-usd` to cap spend.

Never skip or weaken permissions unless the user explicitly asked for it. Prefer the narrowest permissions that complete the task.

Do not use `--cloud` in this skill. For long interactive work, prefer the cloud skill or tell the user to run interactive `claude` themselves.
