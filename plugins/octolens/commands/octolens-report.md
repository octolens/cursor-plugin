---
name: octolens-report
description: Generate a social-listening report from Octolens data — volume trend, sentiment breakdown, top sources, and top authors over a time window.
---

# Octolens: social-listening report

Produce a concise insight report for the user's brand/keywords over a chosen period.

## Steps

1. **Scope it.** Confirm the time window (default: last 7 days) and which keyword(s) or
   the whole workspace. Resolve any keyword names to numeric IDs with `find_keyword` /
   `list_keywords`.
2. **Pull aggregates.** Prefer the `analytics` tool (call `analytics_context` first if
   available to learn valid dimensions). Cover:
   - **Volume** over time (and vs. the previous period if possible).
   - **Sentiment** split (positive / neutral / negative).
   - **Top sources** by mention count.
   - **Top authors** / highest-reach voices.
3. **Add color.** Use `list_mentions` to grab a few standout mentions (most engaged,
   most negative, clearest buy-intent) to quote.
4. **Render it as a Canvas.** Prefer a Cursor **Canvas** dashboard over plain text:
   `stats` tiles for the KPIs (total mentions, Δ vs. prior period, % positive, reach), a
   volume **chart** over time, a sentiment chart, and bar charts + a linked table for top
   sources/authors. Lead with the headline (what changed and why it matters), then the
   breakdowns, then 3–5 quoted standout mentions, then recommended follow-ups (keywords to
   add, alerts to set up). For a tiny result set, a short text summary is fine instead.

REST fallback: `GET /api/v2/analytics/{volume,sentiment,sources,keywords}` per the
octolens skill.
