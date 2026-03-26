---
name: show-notes
description: Companion show notes for published podcast episodes. Episode summary, key takeaways, timestamps, resources, guest info, and CTA — generated from a transcript, outline, or episode description.
---

# Show Notes

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You write companion show notes that make a podcast episode more useful after someone listens — and more discoverable before they press play. Show notes are a reference document, not a transcript summary. They should be scannable, linkable, and worth bookmarking.

## What You Need

The user provides one of:
- **A transcript** of the recorded episode
- **An episode outline** (from the episode-outline skill or their own)
- **A description or summary** of what was discussed

Plus optionally:
- **Guest info** — name, title, bio, links
- **Resources or links** mentioned during the episode
- **Episode number and title** if they have a naming convention

Don't ask for information that's already in the source material. If the user gives you a transcript, extract everything you can from it.

## Show Notes Structure

### Episode Summary

2-3 sentences. What was covered and why it matters to the listener. This is the "what you'll get" pitch — not a blow-by-blow of the conversation.

Rules:
- Lead with the value to the listener, not a description of the format ("In this episode, Alex and guest discuss..." is weak)
- Be specific about the takeaway — "how to build X" beats "a conversation about X"
- Write it so someone who reads only this section knows whether the episode is for them

### Key Takeaways

3-5 bullet points — the actionable highlights someone would screenshot or write down.

Rules:
- Each takeaway stands alone — no "as mentioned above" references
- Actionable where possible ("Start with X before Y" not just "X is important")
- Prioritize surprising or counterintuitive points over obvious ones
- Pull direct phrasing from the source material when it's sharp — don't genericize a good line

### Timestamps

Major sections with brief descriptions. Format:

```
[MM:SS] — Section title or description
```

Rules:
- Include the episode hook/opening as the first timestamp
- One timestamp per major topic shift — not every 30 seconds
- Descriptions should tell the listener what they'll hear, not just label the topic ("Why most people get X wrong" not just "Discussion of X")
- If working from a transcript with timing data, use exact times. If working from an outline or description, use approximate markers and note they're estimates.
- If no timing information is available, produce a logical section breakdown without timestamps and note that the user should add times after editing

### Resources & Links

Everything mentioned in the episode that a listener might want to find:
- Tools, software, platforms
- Books, articles, studies
- People referenced (with links where appropriate)
- The host's own content if referenced (newsletter, course, previous episodes)

Format as a clean bulleted list with hyperlinks where URLs are provided. If a resource was mentioned but you don't have the URL, include it with a `[link needed]` flag.

### Guest Info (if applicable)

- Guest name and title/role
- One-sentence bio focused on why they're credible on this topic
- Links: website, social profiles, relevant project
- Where to find more of their work

Keep it tight — this is a reference card, not a full biography.

### CTA

The standard closing ask:
- Subscribe / follow on the listener's platform
- Leave a review (if the host prioritizes this)
- Related content to check out (specific episode, newsletter, resource)
- Where to connect (social, community, email)

Pull the host's standard CTA from CLAUDE.md if one exists. If not, write a simple, non-pushy version.

## Formatting Rules

- Use markdown headers and bullets — show notes need to be scannable
- Bold key terms and names on first mention
- Keep the total length appropriate — show notes for a 30-minute episode shouldn't be 2,000 words
- If working from a transcript, don't just summarize chronologically — reorganize around value to the reader
- Include the episode title at the top if provided

## What You Don't Do

- Don't transcribe or heavily quote the episode — show notes complement the audio, they don't replace it
- Don't fabricate resources, links, or guest credentials — use what's provided or flag gaps
- Don't write generic CTAs ("be sure to like and subscribe!") — match the host's voice and actual asks
- Don't include every minor tangent as a takeaway — curate the highlights
- Don't pad with filler sections — if there's no guest, skip guest info. If no resources were mentioned, skip resources.
