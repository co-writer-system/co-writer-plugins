---
name: aeo-map
description: Map every question AI answer engines handle for a topic using chained Perplexity queries. Groups by intent cluster, ranks by citation density, identifies content gaps.
---

# AEO Question Map

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

Check if Perplexity MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity connector set up on the Co-Writer platform. Without it, I'm limited to my training data — which means the map may miss current questions AI engines are handling."

## What You Need

Ask the user for:
- **Topic, keyword, or `/aeo:research` output** — paste research output directly or give a topic
- **Chaining rounds** — how many rounds of `related_questions` to follow (default: 3)

If the user pastes `aeo-research` output, extract the questions and key themes as seed queries. Don't ask for a topic separately — you already have it.

## How You Map

### Seed Query Generation
If starting from a topic: generate 3-5 seed queries that cover different angles. Make them specific enough to get useful `related_questions` back. Example for "Claude Code": "how to use Claude Code for non-developers", "Claude Code MCP servers setup", "Claude Code custom slash commands", "Claude Code vs Cursor".

If starting from `aeo-research` output: extract the strongest questions and themes as seeds. Prioritize questions that showed high citation counts or appeared across multiple engines.

### Chaining Rounds

**Round 1:** Run `search_pro` on each seed query. For every response, collect:
- The `related_questions` array
- Citation count (number of unique sources cited)
- Answer quality (comprehensive vs. thin)

**Round 2:** Take the most promising `related_questions` from Round 1 — prioritize ones that open new sub-areas rather than rehashing. Run `search_pro` on each. Collect the same data.

**Round 3:** Same process. By this round, you're deep in the long tail — niche questions that most content doesn't cover. These are often the best AEO opportunities.

If the user requested fewer or more rounds, adjust accordingly.

### Post-Processing

1. **Deduplicate.** Many questions overlap across rounds. Merge near-duplicates (same intent, different phrasing) — keep the version with the most natural phrasing.
2. **Cluster by topic sub-area.** Group questions into intent clusters based on what the person is actually trying to accomplish — not generic intent types like "informational" or "transactional." For "Claude Code," clusters might be "Getting Started," "MCP Servers," "Custom Slash Commands," "Performance," "Pricing & Plans," etc.
3. **Rank within clusters.** Sort by citation density (sources cited in the Perplexity response). More sources = more competitive but also more demand.
4. **Flag content gaps.** Questions where Perplexity's answer was thin, incomplete, cited only 1-2 sources, or hedged heavily. These are the biggest AEO opportunities — weak existing answers mean your content can become the cited source.

## Output Format

```
# AEO Question Map: [Topic]

## Overview
[Total questions discovered, number of clusters, rounds completed, key landscape insight — e.g., "Most questions cluster around setup and configuration, but answer quality drops off sharply for advanced use cases."]

## Question Clusters

### [Cluster Name]
**[X] questions | Avg citation density: [X] sources**

| Priority | Question | Citations | Gap? |
|----------|----------|-----------|------|
| HIGH | [question] | [X] | Yes — [reason: thin answer / 1 source / hedged] |
| MED | [question] | [X] | No |
| LOW | [question] | [X] | No |

### [Next Cluster]
...

## Top AEO Opportunities
[Rank the 5-10 best opportunities by opportunity score: high demand (appeared in multiple rounds or has high citation density) + weak current answers (gaps flagged above). For each, one sentence on WHY it's an opportunity.]

## Content Plan Suggestion
[Based on the map, suggest the minimum content needed to cover the landscape — e.g., "4 pillar articles covering [clusters X, Y, Z, W] + 1 FAQ page for the long-tail questions would cover ~80% of these queries." Be specific about which clusters each piece would target.]

## Next Steps
- Use `/aeo:content` to write AEO-optimized content for specific clusters
- Use `/aeo:faq` to generate FAQ sections from question clusters
- Use `/aeo:schema` to generate structured data for completed content
```

## Rules

- Prioritize breadth in early rounds, depth in later rounds
- Don't skip deduplication — duplicate questions inflate the map and waste the user's time
- Cluster names should be immediately useful for content planning — "Getting Started" beats "Introductory Informational Queries"
- If a round produces no new questions (all duplicates), stop early and note it
- Citation density is a proxy, not gospel — a question with 2 citations and a bad answer is a better opportunity than one with 8 citations and a great answer
- Flag when the landscape is saturated (most questions have 6+ sources with comprehensive answers) vs. wide open (many gaps)
- Don't fabricate citation counts — report exactly what Perplexity returns
