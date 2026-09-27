---
name: claude-code-cloud
description: Start and steer Claude Code cloud sessions (claude --cloud) that run on Anthropic infrastructure. Use when the user wants Claude Code on the web/cloud, parallel cloud tasks, follow-ups to a cloud session, or teleport.
---

# Claude Code Cloud

Use this skill when the user wants a Claude Code session to run on Anthropic infrastructure, be viewed on the web, or be continued remotely.

## Prerequisites

The Claude Code CLI must be installed and authenticated with a Claude.ai account:

```bash
claude auth login
claude auth status
```

Cloud is not available with a Bedrock- or Vertex-only configuration. Claude Cloud requires a Pro, Max, or Team plan, or an Enterprise account with premium seats. If login is interactive or missing, stop and ask the user to complete it before continuing.

## Start a new cloud session

Start from a Git repository:

```bash
claude --cloud "task description"
```

Claude Cloud clones the GitHub remote at the current branch. Push local commits first so the remote contains the intended work. Capture the session ID or URL from the CLI output and report it to the user. Never invent a session ID or URL.

View sessions at <https://claude.ai/code>.

## Follow up on an existing session

Queue a message for an existing cloud session and exit:

```bash
claude -p "message" --cloud <session_id_or_url>
```

This queues the message; it does not wait for the cloud reply. Use only a session ID or URL obtained from CLI output or supplied by the user.

## Teleport to local

Bring a cloud session to the local CLI with:

```bash
claude --teleport
```

Or teleport a specific session:

```bash
claude --teleport <session-id>
```

Use only a session ID obtained from CLI output or supplied by the user.

## Parallel sessions and bundling

Each invocation of `--cloud` creates a separate session, so independent tasks can run in parallel when the user requests that. If there is no remote or no GitHub App, Claude Code uses a local bundle upload. Set `CCR_FORCE_BUNDLE=1` to force bundle upload when needed.
