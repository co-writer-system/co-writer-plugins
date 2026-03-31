---
name: aeo-audit
description: Score existing content against Answer Engine Optimization best practices. Works with a URL (scraped via Firecrawl), pasted content, or a local file. Produces a detailed scorecard with specific fix recommendations.
---

# AEO Audit

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

Check if Perplexity and Firecrawl MCP tools are available. If Firecrawl isn't available and the user provides a URL, tell them: "I need the Firecrawl connector to scrape URLs. Either set it up at app.alexmcfarland.ai/connectors, or paste the content directly."

## What You Need

Ask the user for:
- **Content source** — a URL (requires Firecrawl), paste the content directly, or provide a path to a local file
- **Topic context** (optional) — the topic or query this content should rank for in AI answers. Helps evaluate relevance to what answer engines are citing.

If any of this is available in CLAUDE.md or provided materials, use it directly. Don't re-ask.

## How You Audit

### 1. Get the Content

- **URL provided:** Use Firecrawl `scrape` to pull the page content
- **Local file:** Read the file at the given path
- **Pasted content:** Use it directly

### 2. Check What AI Engines Are Citing (Optional)

If Perplexity is available and topic context was provided, run `search_pro` on the topic. Compare what AI engines currently cite against the audited content. This informs the Completeness and Extractability scores.

### 3. Score Across AEO Criteria

Score each criterion 0-10:

| Criterion | What it measures | 10 = |
|-----------|-----------------|------|
| **Nugget Leads** | Do sections open with 40-60 word direct answers? | Every major section has an extractable nugget |
| **Question Targeting** | Are headings phrased as questions people actually ask? | Headings match real search/AI queries |
| **Structure Quality** | Clean heading hierarchy, logical flow, no skipped levels? | Perfect H1>H2>H3 nesting, scannable |
| **Specificity** | Concrete facts, numbers, names vs. vague generalities? | Packed with citable specifics |
| **Extractability** | Can AI engines pull standalone answers from this content? | Multiple sections work as standalone answers |
| **Structured Data** | Does it have JSON-LD schema (FAQPage, Article, HowTo)? | Appropriate schema present |
| **Comparison Format** | Tables, lists for comparisons? | Structured formats where applicable |
| **Source Attribution** | References to specific sources, tools, studies? | Clear attributions throughout |
| **Completeness** | Does it cover the questions AI engines are asking? | Covers top questions for the topic |
| **Freshness Signals** | Dates, version numbers, "updated" indicators? | Clear temporal signals present |

### 4. Calculate Overall Score

Average all criteria, weighted — **Nugget Leads and Extractability count double** (12 total weights, not 10).

### 5. Deliver Specific Fixes

For each criterion scoring below 7, provide a specific, actionable fix with examples pulled from the actual content. No generic advice.

## Output Format

```
# AEO Audit: [Title or URL]

## Overall Score: [X]/10

## Scorecard

| Criterion | Score | Assessment |
|-----------|-------|------------|
| Nugget Leads (2x) | [X]/10 | [one-line assessment] |
| Question Targeting | [X]/10 | [one-line assessment] |
| Structure Quality | [X]/10 | [one-line assessment] |
| Specificity | [X]/10 | [one-line assessment] |
| Extractability (2x) | [X]/10 | [one-line assessment] |
| Structured Data | [X]/10 | [one-line assessment] |
| Comparison Format | [X]/10 | [one-line assessment] |
| Source Attribution | [X]/10 | [one-line assessment] |
| Completeness | [X]/10 | [one-line assessment] |
| Freshness Signals | [X]/10 | [one-line assessment] |

## Top 3 Fixes (Highest Impact)

### 1. [Fix title]
**Current:** [What the content does now]
**Recommended:** [Specific change with example]
**Impact:** [Why this matters for AEO]

### 2. [Fix title]
...

### 3. [Fix title]
...

## All Recommendations
[Bullet list of every specific fix, grouped by criterion]

## Next Steps
- Use `/aeo:content` to rewrite with AEO optimization
- Use `/aeo:faq` to add a FAQ section
- Use `/aeo:schema` to generate structured data
```

## What You Don't Do

- Don't give generic advice — every recommendation references the actual content
- Don't inflate scores to be nice. A 3 is a 3.
- Don't recommend changes that would make the content read like it was written for robots
- Don't fabricate Perplexity results — if the connector isn't available, skip the competitive citation check and note it
- Don't rewrite content unprompted — this skill audits. Point users to `/aeo:content` for rewrites.
