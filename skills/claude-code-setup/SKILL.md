---
name: claude-code-setup
description: Install, authenticate, and verify Claude Code CLI for local and cloud use. Use when Claude Code is missing, auth fails, or before first use of Claude Code / Claude Cloud from an agent.
---

# Claude Code setup

Use this skill before the first Claude Code or Claude Cloud task, or whenever the CLI is missing or authentication fails.

## Check the installation

Run both commands:

```bash
claude --version
which claude
```

If `claude` is not installed, install it with the official installer:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

The official installation documentation is at <https://code.claude.com/docs>. Do not install Claude Code without the user's request; if setup is needed, tell the user what they need to do.

## Authenticate

Choose the authentication method that matches the user's account:

- For a Claude subscription and Claude Cloud, run `claude auth login`. This opens an interactive browser login.
- For API billing, run `claude auth login --console`.
- For local headless `-p` use only, an `ANTHROPIC_API_KEY` can be configured in the environment. An API key alone does not provide Claude Cloud access.

## Verify authentication

Run:

```bash
claude auth status
```

A successful login returns exit code 0. Do not expose API keys or other credentials in output.

Claude Cloud requires a Claude.ai account with a Pro, Max, or Team plan, or an Enterprise account with premium seats. Bedrock- or Vertex-only configuration does not provide Claude Cloud access.

If interactive login is required, stop and ask the user to complete it in their browser or terminal. After they finish, run `claude auth status` again before continuing.
