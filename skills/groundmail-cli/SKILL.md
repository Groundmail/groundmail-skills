---
name: groundmail-cli
description: >-
  Use when operating Groundmail from the terminal — groundmail CLI, emails send,
  domains add/apply/verify, webhooks, suppressions, templates, API keys, automations.
  Trigger for shell scripts, CI, or npx groundmail workflows.
license: MIT
metadata:
  author: groundmail
  homepage: https://docs.groundmail.dev/ai/agent-skills
  source: https://github.com/Groundmail/groundmail-skills
  documentation: https://docs.groundmail.dev/quickstart
---

# Groundmail CLI

Package: `groundmail-cli` (bin: `groundmail`). Wraps the `groundmail` SDK.

```bash
export GROUNDMAIL_API_KEY=gm_…
# optional local:
# export GROUNDMAIL_API_URL=http://localhost:3003/api

npx -y --package=groundmail-cli -- groundmail <command>
# or: npm install -g groundmail-cli && groundmail <command>
```

For API semantics (sandbox, errors, field names), also load the `groundmail` skill.

---

## Common flows

### Sandbox send

```bash
groundmail emails send \
  --from noreply@mail.groundmail.dev \
  --to owner@example.com \
  --subject "Sandbox check" \
  --html "<p>It works.</p>"
```

`to` must be the account email when using the sandbox `from`.

### Production send

```bash
groundmail emails send \
  --from you@verified.com \
  --to user@example.com \
  --subject "Hello" \
  --html "<p>Hi</p>"
```

### Domains

```bash
groundmail domains add example.com
groundmail domains apply example.com --provider cloudflare
groundmail domains verify example.com
groundmail domains list
```

### Emails ops

```bash
groundmail emails list --limit 25
groundmail emails get --id msg_…
groundmail emails insights --window 7d
groundmail emails cancel --id msg_…
groundmail emails resend --id msg_…
groundmail emails batch --file ./emails.json
```

### Webhooks

```bash
groundmail webhooks list
groundmail webhooks create --url https://yourapp.com/hooks
groundmail webhooks get --id wh_…
groundmail webhooks delete --id wh_…
```

### Suppressions

```bash
groundmail suppressions list
groundmail suppressions add --email user@example.com --reason bounced
groundmail suppressions remove --email user@example.com
```

### Templates

```bash
groundmail templates list
groundmail templates get --id tpl_…
groundmail templates publish --id tpl_…
```

### Agent mailboxes

```bash
groundmail mailboxes create --local-part signup-bot
groundmail mailboxes wait signup-bot@agents.groundmailbox.com --since 2026-11-05T12:00:00Z
groundmail mailboxes reply <mailbox> mbm_… --text …
```

See the `groundmail-mailboxes` skill.

### API keys

```bash
groundmail keys list
groundmail keys create --name ci
groundmail keys delete --id key_…
```

---

## Rules

- Never print full `gm_` secrets into logs or commits
- Prefer CLI for ops; prefer SDK inside application code
- Output is JSON for most commands — pipe to `jq` when needed
