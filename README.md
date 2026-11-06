<p align="center">
  <a href="https://groundmail.dev?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://app.groundmail.dev/images/github/readme-logo-dark.png">
      <img alt="Groundmail" src="https://app.groundmail.dev/images/github/readme-logo-light.png" height="44">
    </picture>
  </a>
</p>

<h1 align="center">Groundmail agent skills</h1>

<p align="center">
  Teach Claude Code, Cursor, Codex and other coding agents to add Groundmail to your app.<br>
  Agent skills, plugins for Claude Code, Cursor and Codex, and a Cursor rule for the Groundmail email API.
</p>

<p align="center">
  <a href="./LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-b48f62"></a>
  <a href="https://github.com/Groundmail/groundmail-mcp"><img alt="MCP server" src="https://img.shields.io/badge/MCP-mcp.groundmail.dev-241c15"></a>
</p>

<p align="center">
  <a href="https://docs.groundmail.dev/ai/agent-skills?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills">Docs</a> ·
  <a href="https://app.groundmail.dev/signup?ref=plugin&utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills">Get a free account</a> ·
  <a href="https://groundmail.dev?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills">groundmail.dev</a>
</p>

---

## Install

| What | Install |
|------|---------|
| Agent Skills (Claude Code, Cursor, Codex, Gemini CLI and more) | `npx skills add Groundmail/groundmail-skills -y` |
| Claude Code plugin (skills + hosted MCP) | `/plugin marketplace add Groundmail/groundmail-skills` then `/plugin install groundmail@groundmail` |
| Codex plugin (skills + hosted MCP) | `codex plugin marketplace add Groundmail/groundmail-skills`, then `/plugins` in Codex and install **Groundmail** |
| Cursor rule | `curl -fsSL https://docs.groundmail.dev/ai/groundmail.mdc?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills -o .cursor/rules/groundmail.mdc` |
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

## What the plugin installs and connects to

- **Skills:** the four Markdown skills above. They contain instructions and code examples only; nothing in them runs on install.
- **MCP server:** one remote server, `https://mcp.groundmail.dev/mcp`. You sign in with your Groundmail account in the browser and choose Full, Send only or Read only access. Tool calls go to Groundmail and act on your account: sending and looking up email, domains, templates, webhooks and suppressions. Revoke access any time in the Groundmail dashboard under **Settings → CLIs & agents**.
- **Cursor rule:** `rules/groundmail.mdc`, the same guidance as the `groundmail` skill.

No hooks, no scripts and no local packages. When the agent writes code that uses Groundmail, that code calls `https://api.groundmail.dev` with your API key, the same as any integration you write yourself. [Privacy policy](https://groundmail.dev/legal/privacy?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills) · [Terms](https://groundmail.dev/legal/terms?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills)

Agent index for any model: [docs.groundmail.dev/llms.txt](https://docs.groundmail.dev/llms.txt?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills)

## Why Groundmail

- **Separate streams.** Your sign-in codes never wait behind a newsletter.
- **We run the servers.** Our own mail servers and IP space, so we can see and fix delivery problems ourselves.
- **Start free.** Free covers 3,000 emails a month. After that, pay as you go is $15 a month with 20,000 emails included, then from $0.70 per 1,000, less as you grow. [Pricing](https://groundmail.dev/pricing/?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills)
- **Built for code and for agents.** REST API, SMTP, SDKs for Node, Python, Go, PHP and Ruby, a CLI, and an MCP server for Claude, ChatGPT and Cursor.

## All Groundmail libraries

| Use | Package |
|-----|---------|
| Node.js / TypeScript | [`groundmail`](https://www.npmjs.com/package/groundmail) on npm |
| Python (Django), Go, Ruby (Rails Action Mailer) | [Groundmail/groundmail-sdks](https://github.com/Groundmail/groundmail-sdks) |
| PHP | [Groundmail/groundmail-php](https://github.com/Groundmail/groundmail-php) |
| Laravel | [Groundmail/groundmail-laravel](https://github.com/Groundmail/groundmail-laravel) |
| Symfony Mailer | [Groundmail/groundmail-symfony-mailer](https://github.com/Groundmail/groundmail-symfony-mailer) |
| Nodemailer | [Groundmail/groundmail-nodemailer](https://github.com/Groundmail/groundmail-nodemailer) |
| NestJS | [Groundmail/nestjs-groundmail](https://github.com/Groundmail/nestjs-groundmail) |
| Strapi | [Groundmail/strapi-provider-email-groundmail](https://github.com/Groundmail/strapi-provider-email-groundmail) |
| Medusa | [Groundmail/medusa-notification-groundmail](https://github.com/Groundmail/medusa-notification-groundmail) |
| AdonisJS | [Groundmail/adonisjs-groundmail](https://github.com/Groundmail/adonisjs-groundmail) |
| Phoenix (Swoosh) | [Groundmail/swoosh_groundmail](https://github.com/Groundmail/swoosh_groundmail) |
| CLI | [`groundmail-cli`](https://www.npmjs.com/package/groundmail-cli) on npm |
| MCP server (Claude, ChatGPT, Cursor) | [Groundmail/groundmail-mcp](https://github.com/Groundmail/groundmail-mcp) |
| Agent skills and Claude Code plugin | [Groundmail/groundmail-skills](https://github.com/Groundmail/groundmail-skills) |
| Email templates (React Email, MJML, HTML) | [Groundmail/email-templates](https://github.com/Groundmail/email-templates) |

[Website](https://groundmail.dev?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills) · [Docs](https://docs.groundmail.dev?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills) · [Pricing](https://groundmail.dev/pricing/?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills) · [Sign up free](https://app.groundmail.dev/signup?utm_source=github&utm_medium=readme&utm_campaign=groundmail-skills)
