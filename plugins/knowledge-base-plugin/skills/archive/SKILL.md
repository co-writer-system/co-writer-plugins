---
name: archive
description: Archive published content into your wiki knowledge base. Copies the file to wiki/raw/, ingests it (creates source summary, updates topic pages, updates patterns), and updates the wiki index and log. Run this after publishing any piece of content.
---

# Archive — Ingest Published Content into Your Wiki

Takes a published piece of content, archives it into your wiki knowledge base, and runs the full ingest workflow. Your wiki grows smarter with every piece you publish.

> **Setup required:** Make sure you have a `wiki/` folder set up in your workspace with the standard structure. See the plugin README for setup instructions and the CLAUDE.md section to add.

## When to Use

- After publishing a video, podcast, newsletter, or article
- When you want to add any finished content to the knowledge base
- "Archive this," "add this to the wiki," "ingest this"

## What You Need

The user provides one of:
- A file path to the published content
- A filename to find in the workspace
- "Archive my latest [content type]" — find the most recent one

## Process

### Step 1: Identify the Source

Find the published file. Look in the workspace content folders for the file the user referenced. If the user says "latest," find the most recently dated file.

### Step 2: Move to Wiki Raw

Move the file to the appropriate `wiki/raw/` subfolder based on its content type. For example:
- Video transcripts go to `wiki/raw/transcripts/`
- Newsletters go to `wiki/raw/newsletters/`
- Articles go to `wiki/raw/articles/`
- Podcast notes go to `wiki/raw/podcasts/`

Create the subfolder if it doesn't exist yet.

The original is removed from the active content workspace — the wiki is now the source of truth for published content. The active workspace stays clean with only in-progress work.

### Step 3: Read and Discuss

Read the full source file. Before proceeding, briefly share the key takeaways with the user:
- Main topics covered
- Key arguments or positions taken
- Notable examples or stories used
- Anything surprising or new compared to previous content

Keep this brief — 3-5 bullet points. Get a thumbs up before proceeding.

### Step 4: Create Source Summary Page

Create a page in `wiki/pages/sources/` named after the source file (e.g., `2026-01-07-voice-profiles.md`).

Include:
- Date, format (video/newsletter/article/podcast), type (free/paid if applicable)
- Summary of key ideas
- Arguments and positions taken
- Examples, stories, and analogies used
- Audience addressed
- Performance data if available
- Historical context — where this fits in the content timeline

### Step 5: Update Topic Pages

For each topic covered in the source:
- Check if a topic page exists in `wiki/pages/topics/`
- If yes: update it — add the new source, update positions if evolved, add new examples
- If no: create a new topic page

Topic pages should capture:
- Your position on the topic
- Which sources cover it (with dates)
- How your thinking has evolved
- Key examples and stories used
- Connections to other topics

### Step 6: Update Pattern Pages

If the source reveals content patterns, update or create pages in `wiki/pages/patterns/`:
- Content performance observations
- Audience language and pain points
- Recurring analogies or examples
- Positioning patterns
- Content gaps identified

### Step 7: Update Index

Update `wiki/pages/index.md` — add entries for any new pages created.

### Step 8: Update Log

Append an entry to `wiki/pages/log.md`:

```markdown
## [YYYY-MM-DD] ingest | Title of the Content

**Source:** `wiki/raw/[type]/[filename]`

**Pages created:**
- list of new pages

**Pages updated:**
- list of updated pages

**Notes:** Brief note about what was notable in this ingest.
```

### Step 9: Report

Tell the user:
- How many wiki pages were created/updated
- Any interesting patterns spotted
- Any topic gaps or contradictions found

## Page Format

All wiki pages use this frontmatter:

```yaml
---
title: "Page Title"
type: source | topic | pattern
sources: ["filename1.txt", "filename2.md"]
related: ["other-page.md"]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

## Tips

- One source might touch 10-15 wiki pages. That's normal — knowledge ripples.
- When updating topic pages, show how thinking evolved over time. Don't just append — integrate.
- If you spot contradictions between this source and existing wiki pages, flag them.
- Keep topic pages focused. If a topic page is getting too broad, split it.
