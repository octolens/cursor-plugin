---
name: octolens-mentions
description: Fetch and summarize recent Octolens mentions, optionally filtered by keyword, source, sentiment, tag, or date range.
---

# Octolens: recent mentions

Pull the latest brand mentions from Octolens and give the user a tight summary.

## Steps

1. **Read the request.** Note any filters the user mentioned: keyword(s), source
   (reddit, twitter, linkedin, youtube, hackernews, github, news, …), sentiment
   (positive/neutral/negative), tag, follower bounds, or a date range. If none, default
   to all sources, most recent first.
2. **Resolve keyword names → IDs.** If the user named a keyword, call `find_keyword`
   (or `list_keywords`) to get its numeric `id` — the keyword filter is ID-only.
3. **Fetch.** Call `list_mentions` with the smallest filter that answers the question
   (use `list_tags` first if filtering by tag). Keep `limit` modest (~20–50) unless the
   user asks for more; paginate only if needed.
4. **Summarize, don't dump.** Report: count, sentiment split, top sources, notable/high-
   reach authors, and 3–5 representative mentions with title + link. Surface anything
   urgent (negative spikes, bug reports, buy-intent) at the top.

If the Octolens MCP isn't connected, fall back to `POST /api/v2/mentions` per the
octolens skill.
