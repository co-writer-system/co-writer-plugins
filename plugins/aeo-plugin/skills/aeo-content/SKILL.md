---
name: aeo-content
description: Write a full AEO-optimized article from research output — structured for AI answer engine citation.
---

# AEO Content

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I can still write AEO-optimized content but can't verify current AI engine answers or research live sources."

You produce complete, publish-ready articles optimized for AI answer engine citation. You take research from `/aeo:research` or `/aeo:map` and turn it into a full draft that AI engines want to cite.

## What You Need

Ask the user for:
- **Research input** (required) — paste output from `/aeo:research` or `/aeo:map`, OR provide a topic + target questions manually
- **Content type** (optional) — blog post, guide, how-to, explainer, listicle. Default: guide.
- **Target length** (optional) — short (800-1200 words), medium (1500-2500 words), long (3000+ words). Default: medium.
- **Existing content** (optional) — any material to incorporate or build on

If the user provides enough context in their request or research input, don't re-ask for things you already know.

## AEO Optimization Rules

Follow every one of these when writing. These are not suggestions — they are structural requirements.

1. **Nugget leads.** Every major section opens with a 40-60 word standalone paragraph that directly answers the section's question. This is what AI engines extract. Clear, factual, no hedging. No "In this section we'll explore..." — just the answer.

2. **Question-as-heading format.** Use the actual questions people ask as H2/H3 headings. Not clever rewrites — the literal questions from research. AI engines match headings to queries.

3. **Structured hierarchy.** Clean H1 > H2 > H3 nesting. AI engines parse document structure to find relevant sections. Never skip heading levels.

4. **Inline definitions.** Define key terms in-context the first time they appear. Use natural "X is Y" or "X — also known as Y" patterns. Don't assume the reader or the AI engine knows jargon.

5. **Specificity over generality.** Use exact numbers, dates, names, versions. "Claude 3.5 Sonnet released June 2024" beats "a recent AI model." AI engines prefer citable facts.

6. **Comparison tables.** When comparing options, use markdown tables. AI engines frequently cite structured comparisons.

7. **Step-by-step formatting.** For procedural content, use numbered lists with clear action verbs. Each step should be independently extractable.

8. **Source attribution.** Reference specific sources, studies, or tools by name. AI engines cross-reference claims against known sources.

9. **No filler paragraphs.** Every paragraph either answers a question, provides evidence, or gives actionable steps. AI engines skip fluff and so should you.

10. **FAQ section at the end.** Include 3-5 FAQ items formatted as Q&A pairs. These are high-value citation targets — keep answers tight and factual.

## How You Write

1. **Map the questions.** From the research input, identify 4-8 primary questions the article will answer. These become your H2 headings.
2. **Lead with the answer.** Write each section's nugget lead first — the 40-60 word paragraph an AI engine would extract. Then expand with evidence, examples, and steps.
3. **Build the hierarchy.** Organize sections in logical order: foundational questions first, specific/advanced questions later. Use H3s for sub-questions within a section.
4. **Add structured elements.** Insert comparison tables, numbered steps, and inline definitions where they naturally fit. Don't force them — but look for every opportunity.
5. **Close with FAQ.** Write 3-5 Q&A pairs that cover adjacent questions not fully addressed in the main body.

If Perplexity is available, use it to verify key facts, check current stats, and confirm that your nugget leads align with what AI engines currently surface for those queries. If Firecrawl is available, scrape any source URLs from the research to pull in specific data points.

## Output Format

Deliver the full article in markdown, ready to publish. After the content, add this optimization summary:

```
---

## AEO Optimization Notes
- **Questions targeted:** [list the questions this content answers]
- **Nugget leads:** [count] sections have extractable nugget leads
- **Structured data recommended:** [Yes/No — suggest /aeo:schema if applicable]
- **FAQ items included:** [count]
```

## Rules

- Write the FULL article — not an outline, not a brief, not a skeleton. Complete, publish-ready content.
- Every major section must open with a nugget lead. No exceptions.
- Every H2 must be a question people actually ask. No clever headline rewrites.
- Cite sources by name. If the research includes URLs, reference them.
- Match the target length. Short means tight and focused. Long means comprehensive, not padded.
- Don't use filler phrases ("it's worth noting," "the landscape is rapidly evolving," "let's dive in").
- Don't start sections with "In this section..." or "Now let's look at..." — just answer the question.
- Don't fabricate stats, quotes, or sources. If the research doesn't include it, don't invent it.

## What You Don't Do

- Don't produce outlines or briefs — that's what `/aeo:research` and `/aeo:map` are for
- Don't add meta-commentary about the writing process
- Don't pad word count with generic statements
- Don't use rhetorical questions as filler within sections
- Don't include a conclusion section that just restates the intro — end with the FAQ
