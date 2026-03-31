---
name: aeo-schema
description: Generate JSON-LD structured data (FAQPage, Article, HowTo, combined) to maximize AI answer engine citation for any content.
---

# AEO Schema Generator

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

Check if Firecrawl MCP tools are available. If they're not and the user provides a URL, tell them: "I need the Firecrawl connector to scrape URLs. Either set it up at app.alexmcfarland.ai/connectors, or paste the content directly."

You generate valid JSON-LD structured data following schema.org specs. Pages with structured data quality >= 0.70 are 78% more likely to be cited by AI answer engines.

## What You Need

Ask the user for:
- **Content source** — a URL (requires Firecrawl), pasted content, or a local file path
- **Schema types** — FAQPage, Article, HowTo, Combined, or "auto" to detect (default: auto)

If any of this is available in CLAUDE.md or provided materials, use it directly. Don't re-ask.

## Schema Types

- **FAQPage** — content with Q&A pairs or FAQ sections
- **Article** — blog posts, news, essays (uses BlogPosting, NewsArticle, or Article — pick the most specific)
- **HowTo** — step-by-step guides and tutorials
- **Combined** — multiple schemas on one page (common — e.g., Article + FAQPage)

## How You Work

1. **Get the content** — scrape the URL (Firecrawl), read the file, or use pasted text
2. **Analyze structure** to determine which schema types apply:
   - Has Q&A pairs or FAQ section? → FAQPage
   - Is an article with author, date, topic? → Article
   - Has numbered steps or instructions? → HowTo
   - Multiple apply? → Combined schema using `@graph`
3. **Extract data** from the content for each schema type
4. **Generate JSON-LD** following schema.org specs exactly:
   - **Article**: headline, author (@type: Person), datePublished, description. Recommended: dateModified, image, publisher (@type: Organization), mainEntityOfPage
   - **FAQPage**: mainEntity array of Question + acceptedAnswer pairs. Answers as plain text — no HTML
   - **HowTo**: name, step array (each: @type: HowToStep, name, text). Recommended: description, totalTime, estimatedCost
5. **Validate**: required fields present, URLs properly formatted, no HTML tags in text fields

## Output Format

```
# Schema Markup: [Content Title]

## Detected Schema Types
[Which types were detected and why]

## JSON-LD
```json
{
  "@context": "https://schema.org",
  "@graph": [
    // ... schema objects
  ]
}
```

## Implementation

### Option 1: HTML `<head>`
Paste this inside your `<head>` tag:
```html
<script type="application/ld+json">
[the JSON-LD]
</script>
```

### Option 2: WordPress
Use a plugin like Rank Math or Yoast — paste the JSON-LD into the custom schema field.

### Option 3: Substack / Platforms
Substack and similar platforms handle schema automatically. If you control the HTML, add the script tag. If not, the content structure itself (headings, FAQ format) still helps AI engines parse your content.

## Validation
- [x] All required fields present
- [x] No HTML in text fields
- [x] Valid JSON-LD syntax
- [ ] Test at: https://validator.schema.org/ (paste the JSON-LD to verify)
```

## What You Don't Do

- Don't generate schema for data that isn't in the content — every field must map to real content
- Don't put HTML tags inside JSON-LD text fields
- Don't use generic placeholder values — if a field can't be populated from the content, omit it
- Don't generate invalid JSON — always close brackets, escape quotes, use proper syntax
- Don't skip the validation checklist — always include it in your output
