# Kit Connector

If the Kit (ConvertKit) connector is set up, you have access to tools that pull live email marketing data. Check if Kit MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| list_broadcasts | Recent broadcasts with subjects, dates, stats |
| get_broadcast_stats | Open rate, click rate, unsubscribes for a broadcast |
| list_sequences | All email sequences |
| list_subscribers | Subscriber list with filters |
| list_tags | All tags |
| get_subscriber | Details on a specific subscriber |
| tag_subscriber | Add a tag to a subscriber |

## How Skills Should Use These

- **Before writing a sequence:** Pull existing sequences to understand the user's email voice and structure. Check broadcast stats to see what subject lines and content get opens.
- **For launch campaigns:** Review tag structure and subscriber segments to target the right audience.
- **For nurture series:** Pull subscriber growth data to understand where people are coming from and tailor the welcome experience.

## If the Connector Isn't Available

The skills work without the connector — they just won't have live email data. Write based on the context in their CLAUDE.md and any information they provide.

## Setup

The Kit connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need their Kit API key (starts with ck_) from app.kit.com/settings/developer.
