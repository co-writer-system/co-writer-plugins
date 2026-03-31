---
name: aeo-faq
description: Generate FAQ sections optimized for AI answer engine citation, with FAQPage JSON-LD schema. Works from aeo-research/aeo-map output, a topic, or existing content.
---

# AEO FAQ Generator

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

Check if Perplexity MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity connector set up on the Co-Writer platform. Without it, I can still generate FAQs but can't verify what AI engines are currently answering."

## What You Need

Ask the user for:
- **Input** (required) — one of three options: paste output from `/aeo:research` or `/aeo:map`, provide a topic, OR paste existing content to extract FAQ from
- **Number of FAQ items** (optional, default: 8-12)
- **Include JSON-LD schema?** (optional, default: yes)

If the user's input makes the answers obvious, don't re-ask.

## How You Work

**From research/map output:** Select the highest-priority questions that work as FAQ items. Definitional ("What is X?"), evaluative ("Is X better than Y?"), and troubleshooting ("Why isn't X working?") questions convert best as FAQ. Skip navigational queries.

**From a topic:** Use Perplexity `search_pro` to discover the top questions people ask about the topic. Prioritize questions AI engines are actively answering — those are the ones worth claiming.

**From existing content:** Extract the implicit questions the content answers. Reformat each as a clean Q&A pair. Fill gaps where the content answers a question weakly or incompletely.

## FAQ Answer Rules

Every answer follows this structure:
1. **Nugget answer (40-60 words)** — direct, extractable, no hedging. This is what the AI engine pulls.
2. **Supporting detail (1-2 sentences)** — context, evidence, or a specific example. Adds depth without diluting the nugget.
3. **Total: 60-100 words per answer.** This is the sweet spot for AI extraction.

Writing rules:
- Start with a direct answer that includes substance. "Claude Code supports MCP servers for connecting external tools..." — not just "Yes."
- Use the full question entity in the answer. If the question asks "What is Answer Engine Optimization?", the answer says "Answer Engine Optimization" — not "it" or "AEO."
- No hedging. No "it depends," "generally speaking," or "in most cases." State the main answer first. If nuance is needed, add the caveat after.
- Include one specific fact, number, or name per answer when possible.

## Output Format

```
## Frequently Asked Questions

### [Question 1]
[Nugget answer — 40-60 words, direct and extractable]

[Supporting detail — 1-2 sentences with specifics]

### [Question 2]
...

---

## FAQPage Schema (JSON-LD)

\`\`\`json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Question 1]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Full answer text — nugget + supporting detail combined]"
      }
    }
  ]
}
\`\`\`

## Usage Notes
- Paste the FAQ section into your content (ideally near the bottom, before closing)
- Add the JSON-LD to your page's `<head>` or via a schema plugin
- These questions were selected for [high AI citation potential / gap coverage / topic authority]
```

## What You Don't Do

- Don't write generic FAQ padding — every question should be one an AI engine would plausibly answer
- Don't start answers with "Yes" or "No" alone — always include the substance in the opening
- Don't use hedging language as a crutch — be definitive, then caveat if necessary
- Don't skip the JSON-LD unless the user explicitly opts out
- Don't fabricate stats — if you include a number, it must come from research or the user's input
