---
name: octolens-add-keyword
description: Track a new keyword in Octolens — confirm the phrase, platforms, and any excludes, then create it and review AI keyword suggestions.
---

# Octolens: add a keyword

Start monitoring a new phrase (a brand, competitor, or product term).

## Gather first (never invent these)

- The exact **keyword phrase** to track.
- **Platforms / sources** to monitor (default: all) — Reddit, Twitter/X, LinkedIn,
  YouTube, TikTok, Bluesky, Hacker News, GitHub, news, podcasts, the open web.
- Any **exclude terms** or filters the user wants applied.

## Steps

1. **Check for duplicates.** `list_keywords` (or `find_keyword`) to confirm the phrase
   isn't already tracked.
2. **Confirm** the phrase, platforms, and excludes with the user.
3. **Create** it with `add_keyword`.
4. **Review suggestions.** Call `list_keyword_suggestions` — if Octolens proposes related
   keywords or refinements, surface them and let the user `accept_keyword_suggestion` /
   `reject_keyword_suggestion`.
5. Read back the created keyword (id, phrase, platforms) and note that mentions will
   start flowing in shortly.

⚠️ `add_keyword` mutates the live workspace and may affect quota (`get_usage`) — confirm
before creating.

REST fallback: `POST /api/v2/keywords` per the octolens skill.
