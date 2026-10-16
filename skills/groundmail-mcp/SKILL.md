---
name: groundmail-mcp
description: >-
  Use when installing, configuring or using the Groundmail MCP server in Claude,
  Claude Code, ChatGPT, Cursor or another MCP client: hosted
  https://mcp.groundmail.dev/mcp with OAuth, the groundmail-mcp npm package
  (stdio or --http), GROUNDMAIL_API_KEY / Bearer gm_, and tools such as
  send_email, verify_domain, create_template and get_deliverability.
license: MIT
metadata:
  author: groundmail
  homepage: https://docs.groundmail.dev/ai/agent-skills
  source: https://github.com/Groundmail/groundmail-skills
  documentation: https://docs.groundmail.dev/ai/mcp
---

# Groundmail MCP

- Hosted: `https://mcp.groundmail.dev/mcp` (Streamable HTTP). OAuth sign-in, or `Authorization: Bearer gm_…`.
- Local: `npx -y groundmail-mcp` (stdio) or `npx -y groundmail-mcp --http` (`http://127.0.0.1:3000/mcp`), with `GROUNDMAIL_API_KEY=gm_…`. Optional `GROUNDMAIL_API_URL`.

Always use the full hosted URL including `/mcp`. For API rules (sandbox, idempotency, error codes) also load the `groundmail` skill.

---

## Install

### Claude Code

```bash
claude mcp add --transport http groundmail https://mcp.groundmail.dev/mcp
```

Then `/mcp` → **groundmail** → **Authenticate**, and sign in to Groundmail in the browser. Headless or CI:

```bash
claude mcp add --transport http groundmail https://mcp.groundmail.dev/mcp \
  --header "Authorization: Bearer $GROUNDMAIL_API_KEY"
# or local stdio
claude mcp add groundmail --env GROUNDMAIL_API_KEY=gm_your_key_here -- npx -y groundmail-mcp
```

### Claude (claude.ai / Desktop)

Settings → Connectors → **Add custom connector** → URL `https://mcp.groundmail.dev/mcp` → Connect → sign in to Groundmail.

### ChatGPT

Developer mode (Settings → Apps & Connectors → Advanced) → **Create** connector → URL `https://mcp.groundmail.dev/mcp`, authentication OAuth → sign in to Groundmail.

### Cursor

`.cursor/mcp.json` or `~/.cursor/mcp.json`, hosted with an API key:

```json
{
  "mcpServers": {
    "groundmail": {
      "url": "https://mcp.groundmail.dev/mcp",
      "headers": { "Authorization": "Bearer gm_your_key_here" }
    }
  }
}
```

Or local stdio:

```json
{
  "mcpServers": {
    "groundmail": {
      "command": "npx",
      "args": ["-y", "groundmail-mcp"],
      "env": { "GROUNDMAIL_API_KEY": "gm_your_key_here" }
    }
  }
}
```

Restart Cursor after editing. The dashboard **Install in Cursor** button writes this with the key filled in. Keep config files with keys out of git.

---

## Tools

| Tool | Purpose |
|------|---------|
| `send_email` | `from`, `to`, `subject`, `html`/`text`/`reply_to`, or `template_id`/`template_alias` + `variables` |
| `list_emails` / `get_email` | Recent sends, status of one send |
| `list_domains` / `create_domain` | Sending domains |
| `apply_domain_dns` / `verify_domain` | Publish DNS (Cloudflare, GoDaddy), then verify |
| `list_templates` / `get_template` / `create_template` / `publish_template` | Templates |
| `list_webhooks` / `create_webhook` / `delete_webhook` | Webhook endpoints |
| `send_test_webhook_event` | Simulated event to webhooks; no email sent |
| `list_suppressions` / `add_suppression` / `remove_suppression` | Suppression list |
| `get_deliverability` | Best-effort metrics for `7d` or `30d` (not inbox placement guarantees) |

## Rules for agents

1. First send: `from` `noreply@mail.groundmail.dev`, `to` the user's Groundmail account email. Other recipients are refused until a domain is verified and a payment method is on file.
2. Confirm with the user before `send_email` to anyone but them, `create_domain`, `delete_webhook` or `remove_suppression`.
3. Failed tool calls return the API message, `code: …` with the HTTP status, and a `how to fix` link to https://docs.groundmail.dev/errors#<code>. Follow it instead of retrying blindly.
4. `send_email` does not take an idempotency key. For app code that retries, use the SDK or HTTP with `Idempotency-Key`.

## MCP vs SDK

| Prefer MCP | Prefer SDK / HTTP in app code |
|------------|-------------------------------|
| Interactive setup, DNS, one-off sends, checking status | Production send paths, CI, retries with idempotency |

Never put the API key in client-side code, even when using MCP during development.
