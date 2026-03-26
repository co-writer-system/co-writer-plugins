---
name: co-writer-update
description: Audit your CLAUDE.md and workspace folder structure, then walk through targeted updates. Use when things have changed — new tools, new products, new content channels — and you need to keep your system current.
---

# Co-Writer System Update

You are helping the user update their existing Co-Writer System. This is a quick checkup, not a full re-interview. The goal is to catch what's stale, flag what's missing, and make targeted updates.

**If no CLAUDE.md exists**, tell the user: "You don't have a CLAUDE.md yet. Run `/setup:setup` to build one from scratch." Then stop.

## Step 1: Read and Scan

Read the user's CLAUDE.md. Then scan their actual workspace folder structure.

Map what you find to these expected section categories (the user may have named them differently — match by content, not by header):

| Expected Section | What it covers |
|-----------------|----------------|
| User Profile | Name, role, background, timezone, working style |
| Business Profile | Business name, products, positioning, revenue, online presence, content channels |
| Ideal Client Profile | Who they serve, problems, aspirations, objections, language |
| Tools & Infrastructure | Platforms and tools they use |
| Voice | Pointer to voice skill or writing style notes |
| Workspace Structure | Folder layout documentation |

Note:
- Which sections exist and how complete they are
- What folders exist on disk vs. what's documented in Workspace Structure

## Step 2: Key Facts Check

Before the full audit, read back 3-4 critical facts from their CLAUDE.md and ask if they're still accurate:

```
Quick check — are these still right?

- **Business:** [business name] — [one-line description]
- **Main product:** [product name] at [price]
- **Content channels:** [list from Content Strategy or Workspace Structure]
- **Target audience:** [one-liner from ICP]

Anything changed?
```

This catches the most common problem — content that exists but is outdated. If they flag changes, note them for Step 4.

## Step 3: Generate Audit Report

Present a concise audit. Don't overwhelm — just flag what matters.

For each expected section, report:
- **Good** — section exists and has real content
- **Thin** — section exists but has very little content or [TBD] placeholders
- **Missing** — section doesn't exist but probably should based on their setup
- **Outdated** — content exists but the key facts check revealed changes

Show as a simple table:

```
## System Checkup

| Section | Status | Notes |
|---------|--------|-------|
| User Profile | Good | — |
| Business Profile | Outdated | Product pricing has changed |
| ICP | Thin | Missing "How They Talk About It" |
| Tools | Good | — |
| Voice | Missing | No writing style documented |
| Workspace Structure | Outdated | 2 folders on disk not documented |
```

Then report workspace mismatches. **If there are more than 10 mismatches**, summarize by category instead of listing each one:

```
### Workspace Mismatches

- 5 new folders under `content/` not in your CLAUDE.md (podcast/, social/drafts/, etc.)
- 2 documented folders that don't exist on disk

Want to see the full list?
```

If 10 or fewer, list them individually:

```
### Workspace Mismatches

- `content/podcast/` exists on disk but isn't in your CLAUDE.md
- `content/social/pipeline/` is in your CLAUDE.md but doesn't exist on disk
```

If there are no issues and the key facts check was clean: "Everything looks current. Your CLAUDE.md matches your workspace and all sections look solid. If you want to review a specific section anyway, just tell me which one."

## Step 4: Walk Through Updates

**Batch related items** to keep this fast. Don't ask about each mismatch one at a time — group them:

**Workspace mismatches as a batch:**
```
I found 3 folders on disk that aren't in your CLAUDE.md: `content/podcast/`, `product/templates/`, `content/social/drafts/`. Want me to add all of them to your documentation, or pick which ones?
```

**Thin sections as a group:**
```
Two sections could use more detail:
- **ICP** — missing the "How They Talk About It" part (the actual phrases your customers use)
- **Voice** — no writing style notes or voice skill pointer

Want to flesh out either of these now?
```

**Missing sections individually** (these need user input):
```
You don't have a Content Strategy section yet. This tells Claude what content to help you create, your editorial angle, and what's out of scope. Want to add one? I'll ask you a few quick questions.
```

**For missing or thin sections that need real input**, run a mini-interview inline — 2-3 targeted questions, then write the section. Don't send them back to `/setup:setup`.

**For outdated facts** flagged in the key facts check, ask what changed and update directly.

Keep it conversational. If they say "skip" or "not now," move to the next item. Don't push.

## Step 5: Show Changes and Apply

After walking through all flagged items, show the complete set of changes:

```
Here's what I'm going to update:

1. **Business Profile** — Updated pricing from $49 to $97
2. **ICP** — Added customer language section
3. **Workspace Structure** — Added podcast/ and templates/ documentation
4. **Content Strategy** — New section with your editorial angle and scope

Want me to apply all of these, or do you want to adjust anything first?
```

Wait for approval. Then apply all changes to the CLAUDE.md at once.

If workspace folders need to be created (documented but don't exist), create them after approval.

If workspace folders exist but shouldn't (documented but user says remove), **do not delete them**. Just remove them from the CLAUDE.md documentation and tell the user they can delete the folder manually if they want.

## Step 6: Confirm

After applying:

```
Updated! Here's what changed:
[Brief list of what was updated]

Your CLAUDE.md is current. Run `/setup:update` anytime things change — new tools, new content channels, new products.
```

## Rules

- **Quick, not thorough** — this is a checkup, not a re-interview
- **Batch related items** — group workspace mismatches and thin sections together; only ask individually when you need new information from the user
- **Mini-interview for missing sections** — if a section needs to be written from scratch, ask 2-3 quick questions and write it inline; don't punt to `/setup:setup`
- **Accept "skip"** — if they don't want to update something, move on
- **Never delete folders** — only remove documentation references, never actual directories
- **Show all changes before applying** — no surprises
- **Be specific** — "Your ICP section is thin" is useless. "Your ICP is missing customer language — the actual phrases they use" is actionable.
