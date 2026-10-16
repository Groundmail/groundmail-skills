# Groundmail skills, plugin and rules

Official agent packaging for [Groundmail](https://groundmail.dev), the transactional email API.

| What | Install |
|------|---------|
| Agent Skills (Claude Code, Cursor, Codex, …) | `npx skills add Groundmail/groundmail-skills -y` |
| Claude Code plugin (skills + hosted MCP) | `/plugin marketplace add Groundmail/groundmail-skills` then `/plugin install groundmail@groundmail` |
| Cursor rule | `curl -fsSL https://docs.groundmail.dev/ai/groundmail.mdc -o .cursor/rules/groundmail.mdc` |
| MCP server only | `claude mcp add --transport http groundmail https://mcp.groundmail.dev/mcp` |

## Skills

| Skill | Use it for |
|-------|------------|
| [`groundmail`](skills/groundmail/SKILL.md) | Sending with the API, an official SDK (Node, Python, Go, PHP, Ruby), or SMTP; test sends; idempotency; error codes |
| [`groundmail-mcp`](skills/groundmail-mcp/SKILL.md) | Connecting the MCP server in Claude, Claude Code, ChatGPT and Cursor |
| [`groundmail-cli`](skills/groundmail-cli/SKILL.md) | Terminal workflows with the `groundmail` CLI |
| [`email-best-practices`](skills/email-best-practices/SKILL.md) | DNS, suppressions, key hygiene, deliverability |

Docs: https://docs.groundmail.dev/ai/agent-skills · Agent index: https://docs.groundmail.dev/llms.txt
