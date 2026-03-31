# Perplexity Connector

If the Perplexity connector is set up, you have access to tools that perform web research with citations. Check if Perplexity MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| search | Quick web search with cited sources |
| search_pro | Advanced search with more comprehensive results and `related_questions` |
| deep_research | In-depth research reports with full citations |

## How Skills Should Use These

- **aeo-research:** Use `search_pro` as the primary tool. The `related_questions` in responses are critical — they reveal what AI engines are answering next. Chain 2-3 rounds for deep dives.
- **aeo-map:** Heavy use of `search_pro` across 3 rounds. Each round follows `related_questions` from the previous to build the complete question landscape. This is the most Perplexity-intensive skill.
- **aeo-content:** Use `search_pro` to verify what AI engines currently answer for target questions before writing. Ensures the content addresses real gaps.
- **aeo-faq:** Use `search_pro` to discover the top questions people ask about a topic when no research/map input is provided.
- **aeo-audit:** Use `search_pro` with the content's topic to see what AI engines currently cite, then compare against the audited content for completeness scoring.

## If the Connector Isn't Available

The skills work without the connector — but lose their main advantage. Without Perplexity, question discovery relies on Claude's training data instead of live AI engine behavior. Research and map skills lose the `related_questions` chaining that makes them powerful. Audit can't compare against current AI citations.

## Setup

The Perplexity connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Perplexity API key (starts with pplx-) from perplexity.ai/settings/api.

---

# Firecrawl Connector

If the Firecrawl connector is set up, you have access to tools that scrape and crawl web pages. Check if Firecrawl MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| scrape | Scrape a URL and get clean markdown — articles, docs, any web page |
| crawl | Crawl an entire site or section (async, returns job ID) |
| crawl_status | Check crawl progress and retrieve results |
| map | Discover all URLs on a website |
| extract | Pull structured data from a page using a schema |

## How Skills Should Use These

- **aeo-audit:** Primary user of Firecrawl. When the user provides a URL to audit, use `scrape` to pull the content. This is the main way audit handles URLs — without it, users must paste content manually.
- **aeo-schema:** Use `scrape` when the user provides a URL to generate schema for. Pulls the content so the skill can analyze structure and extract data for JSON-LD generation.
- **aeo-content:** Use `scrape` if the user provides existing content URLs to build on or incorporate.

## If the Connector Isn't Available

Skills that accept URLs (audit, schema, content) lose URL support — users must paste content directly or provide a local file path instead. The core AEO optimization logic works identically either way.

## Setup

The Firecrawl connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Firecrawl API key (starts with fc-) from firecrawl.dev.
