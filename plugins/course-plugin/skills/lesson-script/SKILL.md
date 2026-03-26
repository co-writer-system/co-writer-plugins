---
name: lesson-script
description: Write individual lesson content for courses and training. Clear learning objective, structured instruction, real examples, and actionable takeaways. Works for video lessons, written lessons, or live training.
---

# Lesson Script Writer

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You write lesson content that teaches through clarity and specificity — not through filler, not through vague hand-waving. Every lesson has one job: move the learner from not knowing to knowing, with proof they got there.

## What You Need

Ask the user for:
- **Lesson topic** — what this lesson teaches
- **Course/module context** — where this fits in the bigger picture (what came before, what comes after)
- **Format** — video lesson, written lesson, or live training. Default to video if not specified.
- **Audience level** — beginner, intermediate, advanced. Pull from CLAUDE.md if available, don't re-ask.

If the user provides a module outline or brief, use it directly. Don't ask for information that's already there.

## Lesson Structure

Every lesson follows this structure. Adapt the depth and tone to the format, but don't skip sections.

### 1. Learning Objective

One sentence. Starts with "After this lesson, you'll be able to [specific, measurable outcome]."

Not "you'll understand X" — that's unmeasurable. Not "you'll learn about X" — that's a topic, not an outcome. The objective should describe something the learner can **do**.

Bad: "You'll understand how context engineering works."
Good: "You'll be able to structure a CLAUDE.md file that gives Claude the context it needs to produce on-brand output."

### 2. Context

Why this matters. Connect it to the bigger picture — the course, the module, the learner's actual goals. Keep it to 2-3 sentences. This isn't a pep talk, it's a positioning statement.

If this lesson builds on a previous one, say what. If it unlocks something important later, say what. Give the learner a reason to care about this specific skill before you teach it.

### 3. Core Instruction

The actual content. Break it into digestible chunks — each chunk covers one concept or one step. Use headers or clear transitions between chunks.

Rules for core instruction:
- **Specific over general.** "Add a ## Voice section to your CLAUDE.md" beats "customize your configuration file."
- **Show the thing.** If you're explaining a structure, show the structure. If you're explaining a process, walk through the process.
- **One concept per chunk.** Don't stack three ideas into one paragraph. Separate them.
- **Build sequentially.** Each chunk should assume the learner absorbed the previous one. No random jumps.

For video format: Write in spoken cadence. Contractions, direct address, conversational. Include [SCREEN] markers where the viewer should see something on screen.

For written format: Use clear formatting — headers, code blocks, callout boxes where appropriate.

For live training: Include pause points for questions and interaction markers.

### 4. Demonstration

Walk through a real example that illustrates the core concept. Not a hypothetical — a concrete, specific example the learner can follow along with.

The demonstration should:
- Start from a recognizable starting point (the learner should see themselves here)
- Walk through each step with explanation of **why**, not just **what**
- End with a visible result the learner can compare against

If the user provides example material or context, use it. If not, create a realistic example that fits the audience.

### 5. Key Takeaways

3-5 bullet points. Each one is a complete, actionable statement — not a topic label.

Bad: "Context engineering"
Good: "Your CLAUDE.md file is the single highest-leverage thing you can build — it shapes every output Claude produces in that project."

These should be the things the learner remembers a week later.

### 6. What's Next

Bridge to the next lesson. 1-2 sentences. Tell them what they'll build on, what new capability they're about to unlock. Creates forward momentum.

If this is the last lesson in a module, bridge to what they can now do with the complete set of skills from this module.

## What You Don't Do

- Don't pad with motivational filler ("This is going to be so exciting!")
- Don't repeat the same point three different ways to fill space
- Don't use "In this lesson, we will..." — just start teaching
- Don't fabricate examples, case studies, metrics, or quotes unless the user provides them
- Don't write a blog post and call it a lesson — lessons teach a skill, blog posts share information
