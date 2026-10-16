<p align="center">
  <a href="https://groundmail.dev">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://app.groundmail.dev/images/github/readme-logo-dark.png">
      <img alt="Groundmail" src="https://app.groundmail.dev/images/github/readme-logo-light.png" height="44">
    </picture>
  </a>
</p>

<h1 align="center">Groundmail agent skills</h1>

<p align="center">
  Teach Claude Code, Cursor, Codex and other coding agents to add transactional email to your app.<br>
  Agent skills, a Claude Code plugin and a Cursor rule for the Groundmail email API.
</p>

<p align="center">
  <a href="./LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-b48f62"></a>
  <a href="https://github.com/Groundmail/groundmail-mcp"><img alt="MCP server" src="https://img.shields.io/badge/MCP-mcp.groundmail.dev-241c15"></a>
</p>

<p align="center">
  <a href="https://docs.groundmail.dev/ai/agent-skills">Docs</a> ·
  <a href="https://app.groundmail.dev/signup">Get a free account</a> ·
  <a href="https://groundmail.dev">groundmail.dev</a>
</p>

---

## Install

| What | Install |
|------|---------|
| Agent Skills (Claude Code, Cursor, Codex, Gemini CLI and more) | `npx skills add Groundmail/groundmail-skills -y` |
| Claude Code plugin (skills + hosted MCP) | `/plugin marketplace add Groundmail/groundmail-skills` then `/plugin install groundmail@groundmail` |
| Cursor rule | `curl -fsSL https://docs.groundmail.dev/ai/groundmail.mdc -o .cursor/rules/groundmail.mdc` |
| MCP server only | `claude mcp add --transport http groundmail https://mcp.groundmail.dev/mcp` |

Then ask your agent something like:

> "Add Groundmail to this app and send a password reset email through it."

The agent signs in through your browser with `groundmail login`, so there's no API key to paste into chat.

## Skills

| Skill | Use it for |
|-------|------------|
| [`groundmail`](skills/groundmail/SKILL.md) | Sending with the API, an official SDK (Node, Python, Go, PHP, Ruby), or SMTP; test sends; idempotency; error codes |
| [`groundmail-mcp`](skills/groundmail-mcp/SKILL.md) | Connecting the MCP server in Claude, Claude Code, ChatGPT and Cursor |
| [`groundmail-cli`](skills/groundmail-cli/SKILL.md) | Terminal workflows with the `groundmail` CLI |
| [`email-best-practices`](skills/email-best-practices/SKILL.md) | DNS (SPF, DKIM, DMARC), suppressions, key hygiene and deliverability |

Agent index for any model: [docs.groundmail.dev/llms.txt](https://docs.groundmail.dev/llms.txt)

## Why Groundmail

- **Our own mail servers and IP space.** Your password resets and receipts don't share a pool with bulk marketing senders.
- **Transactional email only.** No newsletters or cold outreach on the platform, which keeps the sending reputation clean.
- **Start free.** 3,000 emails a month on the Free plan; Pro is 50,000 emails for $20/month. Dedicated IPs on Scale.
- **Built for code and for agents.** REST API, SMTP, SDKs for Node, Python, Go, PHP and Ruby, a CLI, and an MCP server for Claude, ChatGPT and Cursor.

## All Groundmail libraries

| Use | Package |
|-----|---------|
| Node.js / TypeScript | [`groundmail`](https://www.npmjs.com/package/groundmail) on npm |
| Python, Go, Ruby | [Groundmail/groundmail-sdks](https://github.com/Groundmail/groundmail-sdks) |
| PHP | [Groundmail/groundmail-php](https://github.com/Groundmail/groundmail-php) |
| Laravel | [Groundmail/groundmail-laravel](https://github.com/Groundmail/groundmail-laravel) |
| Symfony Mailer | [Groundmail/groundmail-symfony-mailer](https://github.com/Groundmail/groundmail-symfony-mailer) |
| Nodemailer | [Groundmail/groundmail-nodemailer](https://github.com/Groundmail/groundmail-nodemailer) |
| CLI | [`groundmail-cli`](https://www.npmjs.com/package/groundmail-cli) on npm |
| MCP server (Claude, ChatGPT, Cursor) | [Groundmail/groundmail-mcp](https://github.com/Groundmail/groundmail-mcp) |
| Agent skills and Claude Code plugin | [Groundmail/groundmail-skills](https://github.com/Groundmail/groundmail-skills) |

[Website](https://groundmail.dev) · [Docs](https://docs.groundmail.dev) · [Pricing](https://groundmail.dev/pricing) · [Sign up free](https://app.groundmail.dev/signup)
