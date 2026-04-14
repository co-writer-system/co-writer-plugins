# Knowledge Base Plugin

Turn your published content into a living knowledge base. Every time you publish something, archive it here — Claude extracts the key ideas, builds topic pages, tracks how your thinking evolves, and connects everything together. Over time, your wiki becomes a searchable map of everything you've ever published.

## Skills

| Skill | What it does |
|-------|-------------|
| archive | Ingests a published piece of content — creates a source summary, updates topic pages, spots patterns, and logs everything |
| audit-wiki | Runs a health check — finds contradictions, stale info, orphan pages, topic gaps, and broken cross-references |

## Setup

### 1. Create the wiki folder

Add this folder structure to your workspace:

```
wiki/
├── raw/                   <- Your published content lands here
│   ├── transcripts/       <- Video transcripts
│   ├── newsletters/       <- Published newsletters
│   ├── articles/          <- Published articles
│   └── podcasts/          <- Podcast notes or transcripts
├── pages/
│   ├── index.md           <- Master catalog of all wiki pages
│   ├── log.md             <- Chronological record of every archive
│   ├── sources/           <- One summary page per piece of content
│   ├── topics/            <- Topic pages (your positions, examples, evolution)
│   └── patterns/          <- Content patterns, audience insights
```

Create the folders and two starter files:

**wiki/pages/index.md:**
```markdown
# Wiki Index

Master catalog of all knowledge base pages.

## Sources
(Pages will be added here as you archive content)

## Topics
(Pages will be added here as topics emerge)

## Patterns
(Pages will be added here as patterns are spotted)
```

**wiki/pages/log.md:**
```markdown
# Wiki Log

Chronological record of every archive and update.
```

### 2. Add to your CLAUDE.md

Copy this section into your CLAUDE.md file so Claude knows about the wiki on every session:

```markdown
## Content Wiki (Knowledge Base)

A living knowledge base at `wiki/` that Claude maintains. Published content goes in, Claude extracts structured knowledge, and the system gets smarter over time.

### Structure

- `wiki/raw/` — Finished published content (transcripts, newsletters, articles, podcasts)
- `wiki/pages/index.md` — Master catalog of all wiki pages
- `wiki/pages/log.md` — Chronological record of archives and updates
- `wiki/pages/sources/` — One summary page per ingested piece of content
- `wiki/pages/topics/` — Topic pages (positions, examples, how thinking evolved)
- `wiki/pages/patterns/` — Content performance patterns, audience insights

### How It Works

Content gets produced in the active workspace. When something publishes, it gets archived to `wiki/raw/` and ingested. The active workspace stays clean with only in-progress work. The wiki becomes the source of truth for all published content.

### Page Format

All wiki pages use this frontmatter:

---
title: "Page Title"
type: source | topic | pattern
sources: ["filename1.txt", "filename2.md"]
related: ["other-page.md"]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

### Using the Wiki

- **Archive content:** After publishing, run `/archive` to ingest it into the wiki
- **Find past content:** Read `wiki/pages/index.md` to find relevant pages, then read those pages
- **Check health:** Run `/audit-wiki` periodically to catch contradictions, stale info, and gaps
- **Plan content:** Use topic pages to see what you've covered and where the gaps are
```

## How to Use

### Archiving content

After you publish something, tell Claude:
- "Archive this" (with a file path)
- "Archive my latest newsletter"
- "Add this transcript to the wiki"

Claude will move the file to your wiki, read it, discuss the key takeaways with you, then create and update all the relevant wiki pages.

### Auditing the wiki

Run an audit periodically — especially after archiving several pieces at once:
- "Audit the wiki"
- "Check the wiki for issues"

Claude will read every page, find problems, and present a report. Nothing gets changed until you approve the fixes.
