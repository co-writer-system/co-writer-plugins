# YouTube Connector

If the YouTube connector is set up, you have access to tools that pull live data from the user's channel. Check if YouTube MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| get_channel_info | Channel stats — subscribers, total views, video count |
| list_videos | Recent uploads with titles, dates, view counts |
| get_video_stats | Views, likes, comments, watch time for a specific video |
| get_video_comments | Top comments on a video |
| search_videos | Search the user's channel for videos by keyword |
| get_playlist_items | Videos in a specific playlist |

## How Skills Should Use These

- **Before writing a script:** Pull recent video performance to understand what's working. Check top comments for audience questions and language.
- **For titles and descriptions:** Search existing videos to avoid duplicate titles. Reference performance data when suggesting formats.
- **For SEO:** Pull stats on similar videos to benchmark.

## If the Connector Isn't Available

The skills work without the connector — they just won't have live channel data. Don't error or tell the user something is broken. Just write based on the context in their CLAUDE.md and any information they provide.

## Setup

The YouTube connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Google Cloud API key with YouTube Data API v3 enabled.
