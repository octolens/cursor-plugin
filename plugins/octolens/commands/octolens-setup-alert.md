---
name: octolens-setup-alert
description: Set up an Octolens notification — create a feed (saved filter) and attach a Slack, email, or webhook destination with a cadence.
---

# Octolens: set up an alert

Wire up a notification so the user gets matching mentions in Slack, email, or a webhook.

## Gather first (never invent these)

- **What to match:** keyword(s), sources, sentiment, tags, follower bounds, date logic.
  Resolve keyword names to numeric IDs (`find_keyword` / `list_keywords`). The user may
  point at an existing feed instead (`list_feeds`).
- **Where to deliver:**
  - **Slack** — run `search_slack_channels` to resolve the channel name(s) to channel IDs.
  - **Email** — the exact recipient address(es).
  - **Webhook** — the exact URL.
- **Cadence:** frequency (e.g. realtime / hourly / daily / weekly) and time-of-day if asked.

## Steps

1. Confirm the matching criteria and the destination details back to the user.
2. Create the feed with the filter, or reuse an existing feed id, via `create_feed`
   (or `update_feed` / `add_feed_destination` to attach a destination to an existing feed).
3. Read back what was created: feed name, filter summary, destination, and cadence.

⚠️ These are **write** operations on the live workspace — confirm before creating, and
never fabricate emails, channels, URLs, or frequencies.

REST fallback: `POST /api/v2/feeds` (+ `PATCH /api/v2/feeds/{id}`) per the octolens skill.
