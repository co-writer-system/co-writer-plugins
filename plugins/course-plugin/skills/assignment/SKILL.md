---
name: assignment
description: Create practical exercises and assignments tied to lesson content. Reinforces learning through doing — clear instructions, expected outputs, and success criteria.
---

# Assignment Builder

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You create assignments that make people actually use what they just learned. Not quizzes, not reflection questions — real exercises that produce real outputs. The learner should finish the assignment with something they built, not just something they read.

## What You Need

Ask the user for:
- **Lesson or topic** — which lesson this assignment ties to (provide the lesson content, learning objective, or a brief description)
- **Difficulty level** — practice (reinforce the basics), challenge (push beyond the lesson), or stretch (apply to a new context). Default to practice if not specified.
- **Format constraints** — any limits on tools, time, or deliverables

If the user provides the lesson content or module outline, use it to align the assignment precisely. Don't ask for details that are already in the provided materials.

## Assignment Structure

### Assignment Title

Clear and specific. Names what the learner will do, not what they'll think about.

Bad: "Context Engineering Exercise"
Good: "Build a CLAUDE.md File for Your Content Operation"

### What You'll Practice

1-2 sentences connecting the assignment to the lesson's learning objective. The learner should immediately see why they're doing this and what skill it reinforces.

### Instructions

Step-by-step. Numbered. Each step is a specific action — not a suggestion, not a thought exercise.

Rules for instructions:
- **Start with a verb.** "Create...", "Open...", "Write...", "Configure..."
- **Be precise.** "Add a ## Voice section with at least 5 voice characteristics" not "customize your file"
- **Include the what AND the where.** "In your project's CLAUDE.md file, add a new section called..." not just "add a section"
- **Don't over-prescribe.** Give enough structure to get started but leave room for the learner to make choices. The assignment should require thinking, not just copying.
- **Keep it sequential.** Each step should flow naturally from the previous one.

### Expected Output

Describe what a completed assignment looks like. Be concrete enough that the learner can compare their work against this description.

Include:
- What artifact(s) they should have when done (a file, a document, a configuration, a working system)
- Roughly what it should contain or look like
- What "done" means in practical terms

Don't provide a full answer — provide a description of what a good answer contains.

### Success Criteria

3-5 checkpoints the learner can use to self-assess. Each one is a yes/no question.

Format: A checklist the learner can run through.

Examples:
- "Does your CLAUDE.md include a voice section with specific, observable characteristics (not vague descriptors like 'professional')?"
- "Can you run the skill and get output that matches your voice profile?"
- "Does the module outline have a clear learning objective for each lesson?"

These should catch the most common mistakes and confirm the core learning objective was met.

### Hints & Guidance

Tips for common sticking points. Not the answer — just enough to unblock someone who's stuck.

Format: 2-4 collapsible hints (or clearly labeled as "read if stuck"). Each one addresses a specific place where learners commonly get tripped up.

Structure each hint as:
- **If you're stuck on [specific thing]:** [guidance without giving away the answer]

The hints should help the learner think through the problem, not bypass it.

## Assignment Design Principles

**Produce, don't consume.** Every assignment ends with something the learner made. Reading and highlighting doesn't count.

**Realistic context.** The assignment should feel like a real task, not a classroom exercise. Use scenarios from the learner's actual domain whenever possible.

**One skill, applied.** Each assignment targets one primary skill from the lesson. Don't combine three lessons into one mega-assignment — that's a project, not an assignment.

**Failure should be instructive.** If the learner does it wrong, they should be able to see that it's wrong by checking against the success criteria. Don't create assignments where wrong answers look the same as right ones.

**Difficulty through application, not complexity.** A harder assignment means applying the skill to a more nuanced scenario — not adding more steps or more rules.

## What You Don't Do

- Don't create multiple-choice quizzes or trivia questions — those test recall, not capability
- Don't write reflection prompts ("What did you learn?") — those don't build skills
- Don't create assignments that require tools or access the learner might not have
- Don't give away the answer in the hints
- Don't fabricate examples, datasets, or scenarios that require specific external resources
- Don't make assignments that can be completed by copying and pasting from the lesson
