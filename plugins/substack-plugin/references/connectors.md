# Substack Connector

If the Substack connector is set up, you have access to tools that pull live newsletter data. Check if Substack MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| list_published_posts | Recent posts with titles, publish dates, types |
| get_post_analytics | Views, reads, read ratio, likes, comments, shares for a post |
| get_email_stats | Email open rate, click rate, delivery stats for a post |
| get_subscriber_growth_sources | Where subscribers are coming from |
| get_revenue_summary | Paid subscriber count, revenue metrics |

## How Skills Should Use These

- **Before writing a newsletter:** Pull recent post analytics to see what topics and formats get the best engagement. Check email open rates to inform subject line strategy.
- **For topic selection:** Look at top-performing posts to identify patterns.
- **For paid vs free decisions:** Check subscriber growth sources and revenue data to inform which posts should be paywalled.

## If the Connector Isn't Available

The skills work without the connector — they just won't have live performance data. Write based on the context in their CLAUDE.md and any information they provide.

## Setup

The Substack connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need their publication URL and a session token (connect.sid cookie from Substack).
