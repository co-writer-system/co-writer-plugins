---
name: co-writer-setup
description: Build a complete Co-Writer System from scratch — creates a CLAUDE.md file and workspace folder structure through a guided interview. Use when setting up a new project, starting fresh, or building a system file for Claude.
---

# Co-Writer System Setup

You are walking the user through building their complete Co-Writer System. This creates two things:

1. **CLAUDE.md** — Their system file that Claude reads every conversation. It tells Claude who they are, what they do, who they serve, and what tools they use.
2. **Workspace folders** — Organized folders for their content pipeline (drafts, published work, assets)

This is a guided, conversational interview. Ask questions **one section at a time**. Never dump everything at once. Be warm but efficient — these are professionals, not students.

## Before You Start

Check if a CLAUDE.md already exists in the current directory:
- If it exists, read it and ask: "You already have a CLAUDE.md. Want to rebuild it from scratch, or update specific sections? (If you just want to update, try `/setup:update` instead.)"
- If updating, skip to the relevant section
- If starting fresh, proceed with the full interview

Also check if there's an existing workspace folder structure. Note what exists so you don't overwrite their work.

## The Interview

### Opening

```
Let's build your Co-Writer System. This creates a CLAUDE.md file — a system file that Claude reads at the start of every conversation. It's how Claude knows who you are, what you do, and who you create content for, so you never have to explain yourself again.

I'll also set up your workspace — a set of folders to organize your content pipeline.

I'm going to walk you through four things:

1. **You** — who you are and how you work
2. **Your business** — what you do, what you sell, how you're positioned
3. **Your ideal client/customer** — who you're creating content for
4. **Your tools** — what platforms and tools you use

Then I'll set up your workspace folders based on what content you produce.

This usually takes about 10-15 minutes. Ready?
```

Wait for response before proceeding.

---

### Section 1: User Profile

Ask:
```
First, tell me about you:

1. **Your name**
2. **What you do** (role, title, or how you'd describe yourself)
3. **Your background** — what's your expertise? What have you done?
4. **Your timezone**
5. **How you like to work** — fast and iterative? Methodical? Anything about your working style that an AI assistant should know?

Drop as much or as little as you want. If you have a website or bio you can paste, even better — I'll pull from it.
```

If they provide a URL, fetch it and extract what you can before asking follow-up questions. If they paste text content, extract from that.

Accept partial answers. Mark genuine gaps as something to fill later — don't push for information they don't have.

After receiving answers, **confirm what you captured** in a brief summary before moving on. Don't write the file yet — we build it all at the end.

---

### Section 2: Business Profile

Ask:
```
Now your business:

1. **What's your business?** (company name, what it does)
2. **Products or services** — what do you sell? Pricing if you know it
3. **Your positioning** — what makes you different? How do you describe what you do vs. competitors?
4. **Your online presence** — website, social links
5. **Revenue model** — how do you make money? (subscriptions, services, products, courses, etc.)
6. **What content do you produce?** (newsletter, YouTube, blog posts, social media, podcast, courses, etc.)
7. **What topics are in scope for your content?** What should Claude help you create?
8. **Anything out of scope?** Topics or content types Claude should NOT create?

Same as before — paste a website or about page if you have one. Partial answers are fine.
```

After receiving answers, confirm the summary.

---

### Section 3: Ideal Client Profile

Ask:
```
Who are you creating content for?

1. **Who is your ideal client/customer?** (role, industry, experience level)
2. **What problems do they face?** (the top 3-5 frustrations)
3. **What do they want?** (desired outcomes, aspirations)
4. **What's stopping them?** (fears, objections, barriers to buying)
5. **How do they talk about their problems?** Think about the last few emails or DMs you got from someone asking for help — what words did they use?

This section makes your content resonate. Even rough answers help a lot.
```

After receiving answers, confirm the summary.

---

### Section 4: Tools & Infrastructure

Ask:
```
What tools and platforms do you use? I'll document these so your system knows what's available.

Think about:
- **Content platforms** — Substack, WordPress, Medium, YouTube, podcast host?
- **Social platforms** — Twitter/X, LinkedIn, Instagram, TikTok?
- **Business tools** — Stripe, Gumroad, ConvertKit/Kit, Mailchimp?
- **Other** — Notion, Airtable, Google Workspace, anything else core to your operation?

Just list what you actually use. No need to be exhaustive.
```

After receiving answers, confirm the summary.

---

### Section 5: Workspace Folder Structure

Now build their workspace based on everything they told you.

```
Alright, let's set up your workspace folders. Based on what you told me, here's what I'd create:
```

**Generate the folder structure** using these defaults based on the content channels they mentioned:

**Content channels** — create for each channel they mentioned:
- **Newsletter/Substack/Blog:** `content/<channel>/published/` and `content/<channel>/pipeline/`
- **YouTube:** `content/youtube/transcripts/`, `content/youtube/pipeline/briefs/`, `content/youtube/pipeline/scripts/`, `content/youtube/presentations/`
- **Podcast:** `content/podcast/published/`, `content/podcast/pipeline/outlines/`, `content/podcast/pipeline/scripts/`
- **Social media** (if they listed any social platforms): `content/social/`
- **Other channels:** `content/<channel>/published/` and `content/<channel>/pipeline/`

**Standard folders:**
- `assets/` — always create (logos, images, brand materials)
- `product/` — if they have products or services, create with relevant subdirectories
- `clients/` — if they do client work (with a note that each client gets its own subfolder)
- `playbooks/` — if they mentioned processes, SOPs, or strategy work

**Show the proposed structure as a tree** and ask:

```
Want to adjust anything? Add folders, rename things, remove what doesn't fit?
```

Wait for their response. Adjust as needed. Only create the folders after they approve.

---

## Building the CLAUDE.md

After all sections are complete and the workspace structure is approved, generate the CLAUDE.md file.

**Quality gate:** Before writing, review what you collected. If the User Profile or Business Profile sections are mostly empty, say: "Your system file will be pretty lean with what we have. The most important sections to fill in are [User Profile / Business Profile]. Want to take another pass at those, or save what we have and come back to it later?"

**Use this template structure. Adapt it to their actual content — skip sections that don't apply, add sections that do. The template is a guide, not a rigid form.**

```markdown
# [Business Name or User Name] — Claude Instructions

[One-line description of what this system does for them]

---

## User Profile

- **Name:** [name]
- **Role:** [role/title]
- **Timezone:** [timezone]
- **Background:** [background summary]
- **Working Style:** [how they work]

---

## Business Profile

**[Business name]** — [one-line description]

[Business overview paragraph]

### Products & Services

[List with descriptions and pricing if available]

### Revenue Model

[How they make money]

### Online Presence

| Platform | URL |
|----------|-----|
| Website | [url] |
| [Platform] | [url] |

---

## Ideal Client Profile

**[One-line description of who they serve]**

### Who They Are

[Role, industry, experience level]

### Their Problems

[Bulleted list of frustrations]

### What They Want

[Bulleted list of aspirations/desired outcomes]

### What's Stopping Them

[Bulleted list of objections/barriers]

### How They Talk About It

[Key phrases and language they use — if they didn't provide this, omit the subsection rather than leaving it empty]

---

## Tools & Infrastructure

| Tool | Purpose |
|------|---------|
| [Tool] | [What they use it for] |

[Any additional notes about integrations or workflows]

---

## Voice

When producing content, invoke a voice skill if one is available. If no voice skill is installed, pick up the user's natural voice from their writing samples and the context in this file.

---

## Workspace Structure

[Document the folder structure that was created, formatted as a directory tree with brief descriptions of what goes where]

---

*This file evolves. Update it as your system grows — new products, new platforms, new audience insights. Run `/setup:update` anytime to audit and refresh.*
```

**Write the CLAUDE.md file** to the current working directory.

**Then create the workspace folders** using `mkdir -p` commands.

---

## After Setup

Show them what was created:

```
Your Co-Writer System is set up:

✅ **CLAUDE.md** — Your system file with everything Claude needs to know
✅ **Workspace folders** — Your content pipeline, ready to use

## What's in your CLAUDE.md:
[Brief summary of each section — just the section names and a one-liner each]

## Your workspace:
[Show the folder tree]

## What to do next:

### Set up your voice (recommended)
Your CLAUDE.md gives Claude your context, but to write in your authentic voice, you'll want a voice profile. Install the voice plugin from the Co-Writer System marketplace and run the voice capture skill with 3-5 writing samples.

### Install more plugins
Head to the Co-Writer System marketplace for skills covering newsletters, social media, YouTube, and more — all of which use your CLAUDE.md as context.

### Start creating
Even without a voice profile, you can start using skills right away. Your CLAUDE.md ensures everything is on-brand and audience-aware.

### Keep it updated
As your business evolves, update your CLAUDE.md. Run `/setup:update` anytime to audit and refresh, or just edit the file directly.
```

---

## Rules

- Ask questions **one section at a time** — never dump all questions at once
- **Accept partial answers** — mark gaps with [TBD] if needed, but don't push
- **Extract from URLs and documents** — if they paste a website URL, fetch it and pull content. If they paste text, extract from that. Don't re-ask what they already told you.
- **Confirm each section** before moving on — brief summary, not a full readback
- **Adapt the template** — skip sections that don't apply, add sections that do
- **Quality gate** — if critical sections (User Profile, Business Profile) are mostly empty, prompt them before writing
- Save everything at the end, not incrementally (the CLAUDE.md is one file)
- **Create folders only after approval** — show the tree, get confirmation, then mkdir
- Keep the tone conversational and helpful — these are professionals setting up a tool, not filling out a form
- **No separate content strategy section** — content channel info from the Business Profile feeds into the workspace folder structure, not its own CLAUDE.md section
