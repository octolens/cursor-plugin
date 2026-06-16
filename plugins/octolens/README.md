# Octolens for Cursor

Social listening, inside Cursor. This plugin auto-configures the **Octolens MCP server**
and bundles the guidance, commands, and an agent for working with brand mentions,
keywords, feeds, analytics, and Slack/email/webhook alerts — across Reddit, Twitter/X,
LinkedIn, YouTube, TikTok, Bluesky, Hacker News, GitHub, news, podcasts, and the open web.

## What's inside

- **MCP server** (`mcp.json`) — wires up `https://app.octolens.com/api/mcp/v2`. On first
  use you sign in to Octolens in the browser (OAuth) — no API key to manage.
- **Skill** (`skills/octolens/`) — when to use MCP vs REST, auth, mention filter syntax,
  gotchas, and the complete REST API v2 endpoint catalog.
- **Rule** (`rules/octolens.mdc`) — surfaces Octolens conventions when you're doing
  social-listening work.
- **Commands**:
  - `/octolens-mentions` — fetch + summarize recent mentions
  - `/octolens-report` — volume / sentiment / sources / authors report
  - `/octolens-setup-alert` — create a feed + Slack/email/webhook destination
  - `/octolens-add-keyword` — track a new keyword
- **Agent** (`social-listening-analyst`) — turns mentions into insight and actions.

Analytics render as interactive **Cursor Canvas** dashboards (stats, charts, tables) —
ask for a report and you get a live dashboard, not a wall of text.

## Requirements

- An Octolens account. The MCP server works on any plan via OAuth; the REST API v2
  fallback requires a plan with API access (Pro, Scale, or Enterprise) and an `ak_...`
  API key (Settings → API).

## REST fallback

When MCP isn't available, call the REST API v2 directly: base URL
`https://app.octolens.com/api/v2`, Bearer auth, interactive docs at
`https://app.octolens.com/api/v2/docs`. See `skills/octolens/SKILL.md` and
`skills/octolens/references/REST-API.md`.
