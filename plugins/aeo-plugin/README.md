# AEO Plugin

Answer Engine Optimization — get your content cited by AI answer engines like Perplexity, ChatGPT, Google AI Overviews, and Claude. Covers the full AEO workflow from question discovery to content writing to structured data to auditing existing content.

**Requires connectors:** This plugin works best with the **Perplexity** connector for live question discovery and answer engine analysis, and the **Firecrawl** connector for scraping existing content to audit. Skills work without them but with limited capabilities.

## Skills

| Skill | What it does |
|-------|-------------|
| aeo-research | Perplexity-powered question discovery — find the exact questions AI engines are answering about a topic |
| aeo-map | Map every question AI answer engines handle for a topic using chained queries. Groups by intent, ranks by citation density |
| aeo-content | Write a full AEO-optimized article structured for AI answer engine citation |
| aeo-faq | Generate FAQ sections with FAQPage JSON-LD schema, optimized for AI citation |
| aeo-audit | Score existing content against AEO best practices — detailed scorecard with fix recommendations |
| aeo-schema | Generate JSON-LD structured data (FAQPage, Article, HowTo, combined) for any content |

## Connector

This plugin requires the **Perplexity** connector for full functionality. **Firecrawl** is needed for the audit skill when working with URLs.

| Feature | Without Connectors | With Connectors |
|---------|-------------------|----------------|
| Question discovery | Limited to Claude's training data | Live questions from Perplexity with citation sources |
| Content auditing | Can only audit pasted text or local files | Scrapes any URL via Firecrawl for full audit |
| Answer engine analysis | No visibility into current AI answers | See what AI engines are actually saying and citing |
| Citation mapping | General knowledge only | Maps real citation sources and patterns |

**Setup:** Connect at app.alexmcfarland.ai/connectors
