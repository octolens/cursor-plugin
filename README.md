# Octolens — Cursor plugin

The official [Octolens](https://octolens.com) plugin for Cursor. One-click social
listening: it auto-configures the Octolens MCP server and ships a skill, rule, slash
commands, and an analyst agent for working with brand mentions, keywords, feeds,
analytics, and Slack/email/webhook alerts — across Reddit, Twitter/X, LinkedIn, YouTube,
TikTok, Bluesky, Hacker News, GitHub, news, podcasts, and the open web.

## Install

**From the Cursor Marketplace** — search for **Octolens** and install.

**Local (development / preview)** — clone this repo into Cursor's local plugins folder
(or symlink it), then enable it in Cursor:

```bash
git clone https://github.com/octolens/cursor-plugin.git \
  ~/.cursor/plugins/local/octolens-cursor-plugin
```

On first use of an MCP tool, Cursor opens an Octolens OAuth login in the browser — no API
key to manage.

## What you get

| Component | Description |
|---|---|
| **MCP server** | Auto-configures `https://app.octolens.com/api/mcp/v2` |
| **Skill** | MCP-vs-REST guidance, auth, mention filters, gotchas, full REST v2 catalog |
| **Rule** | Octolens conventions for social-listening work |
| **Commands** | `/octolens-mentions`, `/octolens-report`, `/octolens-setup-alert`, `/octolens-add-keyword` |
| **Agent** | `social-listening-analyst` — mentions → insight and actions |

The plugin lives under [`plugins/octolens`](plugins/octolens). See its
[README](plugins/octolens/README.md) for details.

## Repo layout

```
.cursor-plugin/marketplace.json     # marketplace manifest (one plugin)
plugins/octolens/                   # the Octolens plugin
scripts/validate-template.mjs       # manifest + frontmatter validator
```

## Develop

Validate manifests and component frontmatter before committing:

```bash
node scripts/validate-template.mjs
```

## License

MIT
