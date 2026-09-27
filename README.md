# Claude Code & Cloud

A Cursor plugin for driving Claude Code locally with `claude -p` and Claude Code Cloud sessions with `claude --cloud` from Cursor or Grok Bot agents.

## Prerequisites

- Claude Code CLI installed.
- A Claude or Anthropic account.
- For Claude Cloud: a Claude.ai Pro, Max, or Team plan, or an Enterprise account with premium seats. Bedrock- or Vertex-only configuration is not sufficient.
- Authentication configured with `claude auth login` (or API-key authentication for local `-p` use only).

See the official documentation: <https://code.claude.com/docs>.

## Install for local testing

1. Copy this directory to:

   ```text
   ~/.cursor/plugins/local/claude-code-cloud
   ```

2. Reload Cursor with **Developer: Reload Window**.
3. Open Cursor's Customize settings and confirm the skills appear.

## Use from chat

Ask Cursor or Grok Bot to run Claude Code locally in a named repository, for example:

> Run Claude Code locally in `/path/to/repo` to inspect the failing tests.

For an Anthropic-hosted session, ask for Claude Code Cloud, for example:

> Start a Claude Code Cloud session for the current GitHub repository to implement the issue and report the session URL.

The skills explain authentication, permissions, headless output, cloud follow-ups, and teleporting a cloud session back to local.

## Publishing

This plugin can be published later through the Cursor marketplace: <https://cursor.com/marketplace/publish>.
