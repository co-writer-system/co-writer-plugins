---
name: co-writer-update
description: Update and strengthen your CLAUDE.md — runs an internal audit, then walks you through fixing every weak or missing section using the same template and principles as the original setup. Use when your system file needs a refresh, not a full rebuild.
---

# Co-Writer System Update

You are updating an existing CLAUDE.md. This skill runs a quick internal audit, identifies what's weak or missing, then walks the user through fixing each section — using the same structure and principles as the original setup skill.

**This is not a rebuild.** Strong sections stay untouched. You only touch what needs work.

**If no CLAUDE.md exists**, tell the user: "You don't have a CLAUDE.md yet. Run `/setup:co-writer-setup` to build one from scratch." Then stop.

---

## Step 1: Read and Diagnose

Read the user's CLAUDE.md. Also scan:
- Their workspace folder structure on disk
- Whether a voice profile skill is installed
- Whether connectors are configured
- Any `context/` folder with reference documents

Evaluate every section against what a strong CLAUDE.md looks like. Use `references/example-claude-md.md` as the structural benchmark.

### Rating Scale

| Rating | Meaning |
|--------|---------|
| **Strong** | Complete, specific, actionable — leave it alone |
| **Adequate** | Has content but could be more detailed or specific |
| **Thin** | Too vague, has [TBD] placeholders, or lacks specifics |
| **Missing** | Section doesn't exist but should based on their setup |
| **Outdated** | Content doesn't match what's actually on disk or seems stale |

### What "Strong" Looks Like

**Opening directive** — Strong when: speaks TO Claude ("You are [name]'s co-writer..."), not ABOUT Claude. States who the user is, what the co-writer handles, and the working style.

**User Profile** — Strong when: has name, role, timezone, background with specifics (not just "marketing professional"), and online presence with URLs.

**Business Profile** — Strong when: clear one-liner, each product/service has type + pricing + what buyers get, revenue model is explicit, content model is clear (self/clients/both), content channels listed, in scope and out of scope defined.

**Ideal Client Profile** — Strong when: specific about who they are (not just "business owners"), problems are real frustrations, aspirations are specific outcomes, objections/barriers named.

**Tools & Infrastructure** — Strong when: split into Connected (with connector details) and Other, connected tools have config fields filled in, connector source noted.

**Voice** — Strong when: points to voice skill, nothing more. Does NOT contain word lists, tone rules, or style descriptions.

**Workspace Structure** — Strong when: documented tree matches what actually exists on disk, each folder has a brief description.

---

## Step 2: Present the Diagnosis

Show a quick summary:

```
## Quick Audit

| Section | Status |
|---------|--------|
| Opening | Strong ✓ |
| User Profile | Adequate — background is generic |
| Business Profile | Thin — products listed without pricing |
| ICP | Missing |
| Tools | Adequate — 2 connector opportunities |
| Voice | Strong ✓ |
| Workspace | Outdated — 3 folders on disk not documented |

I'll walk you through updating the [X] sections that need work. Strong sections stay as-is.
```

Then immediately proceed to Step 3 — don't wait for permission. The user invoked this skill to fix things, not to read a report.

---

## Step 3: Update Each Weak Section

Work through each non-strong section **one at a time, in order.** For each section:

1. Show what currently exists (quote the relevant lines from their CLAUDE.md)
2. Explain specifically what's weak and why it matters
3. Ask targeted questions to fill the gap — **only ask what's missing, don't re-interview on stuff they already have**
4. Write the updated section and show it to the user for approval
5. Move to the next section

### Section-Specific Update Flows

---

### Opening Directive

**If missing or weak:**
```
Your CLAUDE.md should open by telling Claude who it is and what it does for you.
Here's what you have now: [quote it]

A strong opening looks like:
"You are [name]'s co-writer. You handle [what]. [Working style]. You [key behavior]."

What does your co-writer handle for you? (content production, business copy, client work, all of the above?)
```

Write a directive opening that speaks TO Claude. Keep it to 2-3 sentences. Direct, not flowery.

---

### User Profile

**If thin or missing pieces:**

Only ask about what's missing. If they have a name and timezone but no background:
```
Your User Profile has the basics but your background is generic. Claude writes better content when it knows your actual expertise.

What's your background? Not a resume — just the key experience and expertise that shapes your work.
```

If online presence is missing:
```
You don't have any URLs listed. What's your online presence? Websites, social handles, newsletter — anything you actively use.
```

---

### Business Profile

**If thin or missing:**

Check what's there and only ask about gaps:

- **No products/services detail:** "You mention [product] but there's no pricing or description of what buyers get. Walk me through: what is it, what does it cost, and what does someone get when they buy?"
- **No revenue model:** "How do you make money? Subscriptions, one-time sales, retainers, a mix?"
- **No content model:** "Are you creating content for yourself, for clients, or both?"
- **No in scope / out of scope:** "What topics should Claude help you with? And what's off-limits?"
- **Missing content channels:** "What content do you actually produce? Newsletter, YouTube, social, blog, podcast?"

Don't re-ask things they've already answered in other sections.

---

### Ideal Client Profile

**If thin or missing:**

This is the section most commonly thin. Be specific about what you need:

```
Your ICP is [missing / too vague]. Claude uses this to write content that resonates with your audience — generic descriptions produce generic content.

I need four things:
1. Who specifically are they? (role, industry, experience level — not just "business owners")
2. What are their top 3 frustrations? (the actual pain that makes them look for help)
3. What do they want? (specific outcomes, not "grow their business")
4. What stops them from buying? (objections, fears, barriers)
```

If they struggle with customer language, skip it rather than forcing generic answers.

---

### Tools & Infrastructure

**If adequate or thin:**

Cross-reference their tools list against available connectors (read `references/connectors.md`).

```
Your tools section [has issues]. Here's what I'd fix:

[List specific issues — e.g.:]
- YouTube is listed but not connected — there's a connector available
- Kit is connected but has no tag structure documented
- Airtable isn't mentioned but you have it connected in Cowork
```

For each connector opportunity, offer to walk them through setup using the steps in `references/connectors.md`.

Split tools into **Connected** (with connector details, config fields, and source) and **Other** (table format).

---

### Voice

**If it contains word lists, tone rules, or style descriptions:**

```
Your Voice section has [word lists / tone rules / style descriptions] in it. These should live in your voice profile skill, not in CLAUDE.md.

I'll replace this with a clean pointer:

> Before any writing task, check for an installed voice profile skill and invoke it. If no voice skill is installed, match the user's natural voice from writing samples in the workspace. **Do not generate voice guidelines, word lists, or tone rules in this file — voice lives in the voice skill, not here.**

The voice content that was here should go into your voice plugin. Want me to move it there, or just clean up the CLAUDE.md?
```

---

### Workspace Structure

**If outdated or missing:**

Scan the actual folder structure on disk. Compare against what's documented.

```
Your workspace documentation doesn't match what's on disk:

Added since last update (exist but undocumented):
- content/podcast/
- content/social/drafts/

Documented but don't exist (ghost entries):
- content/blog/published/

I'll update the workspace section to match reality.
```

Generate the corrected tree and show for approval. Don't ask questions — this is a factual update.

---

## Step 4: Apply All Changes

After walking through every weak section:

1. **Show a summary of all changes** — what was updated, what was left alone
2. **Write the updated CLAUDE.md** — preserve everything that was strong, replace the sections that were updated
3. **Create any missing workspace folders** if the workspace section was updated

```
## Updates Applied

✅ Opening — rewritten with directive voice
✅ Business Profile — added pricing and deliverables for 2 products
✅ ICP — rebuilt with specific roles, frustrations, and objections
✅ Workspace — synced with actual folder structure, added 2 missing folders
⏭ User Profile — already strong, no changes
⏭ Voice — already strong, no changes
⏭ Tools — already strong, no changes

Your CLAUDE.md is updated. Run `/setup:co-writer-audit` anytime for another health check.
```

---

## Rules

- **Don't touch strong sections** — if it's good, leave it alone
- **One section at a time** — don't dump all questions at once
- **Only ask what's missing** — if they have name and timezone but no background, only ask about background
- **Show before writing** — quote the current version, show the proposed update, get approval before writing
- **Use the same template as setup** — sections should match the structure in `references/example-claude-md.md`
- **Preserve their voice** — if they wrote their CLAUDE.md in a specific style, maintain that. Don't sterilize it into generic corporate markdown
- **No voice content in CLAUDE.md** — voice section is always and only a pointer to the voice skill
- **CLAUDE.md opens in directive voice** — "You are [name]'s co-writer..." not "This file tells Claude..."
- **Workspace is factual** — scan disk, report what exists, don't ask the user to describe their own folder structure
- **Connector guidance is specific** — don't just say "you could connect YouTube." Walk them through setup using `references/connectors.md`
- **Write the file at the end** — collect all changes, then write once. Don't do incremental saves
- **If everything is strong** — say so and stop. "Your CLAUDE.md looks solid. Nothing to update right now." Don't invent work
