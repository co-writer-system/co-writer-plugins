---
name: audit-wiki
description: Audit your content wiki for contradictions, stale info, orphan pages, topic gaps, and missing cross-references. Run periodically to keep the knowledge base healthy.
---

# Audit Wiki — Health Check Your Knowledge Base

Runs a full health check on your wiki. Identifies problems, reports findings, and fixes with your approval.

> **Setup required:** Make sure you have a `wiki/` folder set up in your workspace with the standard structure. See the plugin README for setup instructions.

## When to Use

- Periodically (monthly or after a batch of archives)
- "Audit the wiki," "check the wiki," "lint the wiki"
- After archiving a bunch of new content
- When something feels off or inconsistent

## Process

### Step 1: Read the Full Index

Read `wiki/pages/index.md` to get the complete catalog of all wiki pages.

### Step 2: Check Every Page

Read each page listed in the index. For each page, check:

**Contradictions:**
- Does this page contradict any other page?
- Has your position changed but an old page still states the previous position as current?
- Are there dates/facts that conflict across pages?

**Stale Information:**
- Is anything clearly outdated? (e.g., references to tools you no longer use, numbers that have changed significantly, product details that evolved)
- Are there "as of" dates that are now months old?

**Cross-Reference Integrity:**
- Does the `related` frontmatter list pages that actually exist?
- Are there obvious connections between pages that aren't linked?
- Does the `sources` frontmatter reference files that exist in `wiki/raw/`?

**Orphan Pages:**
- Are any pages NOT listed in the index?
- Are any pages not referenced by any other page's `related` field?

### Step 3: Check for Topic Gaps

Compare the raw sources against the topic pages:
- Are there topics covered in multiple raw sources that don't have a topic page?
- Are there raw sources that aren't referenced by any source summary page?
- Are there obvious topics you cover that are missing from the wiki entirely?

### Step 4: Check for Pattern Gaps

Look across all source pages and topic pages:
- Are there recurring themes that don't have a pattern page?
- Are existing pattern pages missing recent data points?

### Step 5: Report

Output a structured report:

```
## Wiki Audit Report — [date]

### Contradictions Found
- [list each contradiction with the two conflicting pages]

### Stale Information
- [list each stale item with the page and what needs updating]

### Broken Cross-References
- [list any broken links or missing connections]

### Orphan Pages
- [list pages not in the index or not referenced anywhere]

### Topic Gaps
- [list topics that should exist but don't]

### Pattern Gaps
- [list patterns that should be captured but aren't]

### Summary
- Total pages checked: X
- Issues found: X
- Recommended actions: [brief list]
```

### Step 6: Fix (With Approval)

After presenting the report, ask which fixes to apply. Then:
- Update contradicted pages to reflect current positions
- Update stale information
- Fix broken cross-references
- Add missing pages to the index
- Create missing topic or pattern pages if approved

Don't auto-fix anything — always present the report first and get approval.

## Tips

- Run this after every major batch of archives
- The most common issue will be stale information — your thinking evolves fast
- Contradictions are actually valuable to flag — they show where thinking changed
- Keep the report concise — don't list things that are fine, only problems
