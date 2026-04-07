# Week 2: Product Vision and Agent Skills

**Type:** Group assignment (one submission per team)
**Points:** 10
**Due:** See Camino for submission details and due date.

## Overview

This week your team will align around a shared product vision, set up AI agent skills in your project repository, and use one of those skills (the Problem Framing Canvas) to stress-test your product concept before committing to it.

By the end of this assignment, your team should have a clear product vision statement, a shared repo with skills installed, and evidence that you used a structured framework to examine the problem behind your product, including whose perspectives you might be missing.

## Part 1: Product Vision

Now that your team has chosen a product concept from the Week 2 pitch session, align on what you're building and why. You'll start drafting this together in lab; the assignment asks you to refine and complete it.

### Modified Product Vision Template

We're using Geoffrey Moore's product vision template (from Sommerville Ch. 1) with one addition. The original template helps you articulate what you're building, who it's for, and why they should care. We've added a seventh line, **POWERED BY**, that asks you to name the AI capability at the core of your product. This connects your Week 1 API exploration to your product concept.

> **FOR** (target customer)
> **WHO** (statement of the need or opportunity)
> **THE** (product name) is a (product category)
> **THAT** (key benefit, compelling reason to use it)
> **UNLIKE** (primary competitive alternative)
> **OUR PRODUCT** (statement of primary differentiation)
> **POWERED BY** (the AI capability that makes the core interaction possible)

The POWERED BY line should name a **type of capability**, not a specific vendor or API. You explored specific APIs in Week 1; now describe what that capability does at a higher level. Your team may still explore different APIs during prototyping.

Good: "real-time image recognition that identifies plant diseases from phone photos"
Good: "natural language generation that translates legal jargon into plain-English summaries"
Too specific: "the Google Cloud Vision API" or "OpenAI's GPT-4o"

### What to include

**1a. Product vision statement:** Fill in the modified template for your product. Every field should be specific, not generic. "College students" is too broad; "CS students managing group project deadlines across 3-4 courses" is grounded.

**1b. Vision narrative (half page max):** Expand on the vision statement with:

- **The problem in context:** Who experiences this problem, when, and why existing solutions fall short? Ground this in real observations, not assumptions. If someone on your team has personally experienced the problem, say so.
- **How AI makes this possible:** Which specific AI capability (from your POWERED BY line) enables the core interaction? What does the product do that wasn't feasible before this capability existed? Apply the "without AI" test: if you removed the AI, would the product be meaningfully worse, or just slightly less convenient?

## Part 2: Agent Skills Setup

In Thursday's class, you'll see a live demo of agent skills: how to install them, how to invoke them, and what a productive skill conversation looks like. After the demo, replicate that setup in your team repo.

AI coding agents like Cursor become significantly more capable when you give them domain knowledge through **skills**. A skill is a structured set of instructions (a `SKILL.md` file) that teaches the agent how to approach a specific type of task, whether that's designing a UI, framing a product problem, or planning a feature before writing code.

### The Three Skills

**1. Problem Framing Canvas** (deanpeters/Product-Manager-Skills)

A structured framework based on MITRE's Problem Framing Canvas for exploring problems before proposing solutions. Walks through three phases: Look Inward (examine your assumptions and biases), Look Outward (who experiences the problem, who benefits, who's excluded), and Reframe (restate the problem as a "How Might We" question). Produces a filled canvas and an actionable HMW statement.

- Repository: [deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills)
- Skill path: `skills/problem-framing-canvas/SKILL.md`

**2. Storyboard** (deanpeters/Product-Manager-Skills)

Creates a 6-frame visual narrative that illustrates a user's journey from problem to solution, using classic story structure (introduce the persona, show the problem, escalate, present the solution, show the "aha" moment, reveal the improved outcome). Draws on Pixar storytelling principles and emphasizes specificity over generic descriptions. This is an alignment and pitching tool, not a UI mockup.

- Repository: [deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills)
- Skill path: `skills/storyboard/SKILL.md`

**3. Frontend Design** (Anthropic official)

How to build distinctive, polished web interfaces that avoid generic "AI-generated" aesthetics. Covers typography choices, color systems, spatial composition, motion, and visual details. Emphasizes choosing a clear conceptual direction and executing it with precision.

- Repository: [anthropics/skills](https://github.com/anthropics/skills)
- Skill path: `skills/frontend-design/SKILL.md`

You'll use the Problem Framing Canvas skill in Part 3 of this assignment. The Storyboard skill will be used next week when your team creates a storyboard before building divergent prototypes. The Frontend Design skill will guide your prototype's visual quality. Install all three now so they're ready when you need them.

### Setup Reference

One team member should handle the initial setup, but everyone should read all three skills.

Create the skills directory in the root of your team's project repository:

```
.cursor/skills/
├── problem-framing-canvas/
├── storyboard/
└── frontend-design/
```

Download each SKILL.md using `curl` or by copying from the GitHub "Raw" view:

```bash
curl -o .cursor/skills/problem-framing-canvas/SKILL.md \
  https://raw.githubusercontent.com/deanpeters/Product-Manager-Skills/main/skills/problem-framing-canvas/SKILL.md

curl -o .cursor/skills/storyboard/SKILL.md \
  https://raw.githubusercontent.com/deanpeters/Product-Manager-Skills/main/skills/storyboard/SKILL.md

curl -o .cursor/skills/frontend-design/SKILL.md \
  https://raw.githubusercontent.com/anthropics/skills/main/skills/frontend-design/SKILL.md
```

Verify skills are loaded in Cursor by typing `/problem-framing-canvas` in the agent chat. Commit and push so all teammates have access.

## Part 3: Problem Framing Canvas

Before locking in your product concept, use the Problem Framing Canvas skill to stress-test it. You have a product vision, but how well do you actually understand the problem behind it? The canvas walks you through three phases: examining your own assumptions, understanding who experiences the problem (and who you might be overlooking), and reframing the problem into a "How Might We" question that opens up the design space for prototyping.

### How to use it

1. Open Cursor in your team repo (with skills installed from Part 2).
2. Invoke the Problem Framing Canvas skill by typing `/problem-framing-canvas` in the agent chat.
3. Start by giving the agent your product vision statement and a description of the problem you're trying to solve. The skill will then walk you through 8 questions across three phases:
   - **Look Inward (Q1-Q3):** What assumptions are you bringing? What biases might be shaping how you see the problem? What do you think you know, and what are you guessing?
   - **Look Outward (Q4-Q6):** Who actually experiences this problem? Who else is affected that you haven't considered? Who might be excluded from or harmed by your solution?
   - **Reframe (Q7-Q8):** Restate the problem based on what you've surfaced. Generate a "How Might We" question that sets boundaries for solution exploration without constraining ideas.
4. Work through the full canvas as a team. This is a conversation, not a form to fill out. Push back on the agent if its suggestions don't match your domain knowledge. Add perspectives it misses. The Look Outward phase is especially important: take it seriously and think about who you might be designing for (or against) without realizing it.

### What to submit

Include the completed Problem Framing Canvas (the filled canvas with your responses across all three phases, plus the final "How Might We" statement) along with a **brief reflection (half page max):** What did the canvas surface that you hadn't considered? Did the Look Inward phase reveal assumptions you weren't aware of? Did the Look Outward phase change who you think your users are? How does your "How Might We" question differ from where you started?

The goal is genuine engagement with the framework, not a polished deliverable. We want to see evidence that the skill shaped your thinking, not that you ran it and copy-pasted the output.

## What to Submit

A single document (PDF or Google Doc link) with:

1. **Product vision statement** using the modified Moore's template (all seven fields, including POWERED BY).

2. **Vision narrative** (half page max) covering the problem in context and how AI makes the product possible.

3. **Skills setup confirmation:** Screenshot or link showing your team repo's `.cursor/skills/` directory with all three SKILL.md files in place.

4. **Problem Framing Canvas output and reflection:** The completed canvas you generated with the skill, including your "How Might We" statement, plus a brief reflection on how it shaped your thinking.

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Product vision statement: specific, grounded, all seven fields filled in (including POWERED BY naming a capability, not a vendor) | 3 |
| Vision narrative: clear problem, AI capability is essential not decorative | 3 |
| Problem Framing Canvas demonstrates genuine engagement (examined assumptions, considered who's affected and excluded, produced a clear HMW statement) | 2 |
| Skills installed in the team repo (all three SKILL.md files present and committed) | 1 |
| Writing quality and overall coherence | 1 |
| **Total** | **10** |

## Tips

- Write the Moore's template first, then expand into the narrative. If you can't fill in the template concisely, your concept isn't clear enough yet.
- Run the Problem Framing Canvas skill after drafting your vision statement, not before. The vision gives the skill enough context to be useful; without it, the conversation will be too abstract.
- Your "How Might We" question will directly inform your Week 3 storyboard and divergent prototypes. A good HMW opens up the design space; a bad one constrains it to a single solution.
- Your vision will evolve. This is a starting point, not a contract. But starting with a clear, shared vision prevents your team from building in three different directions during prototyping.

## Resources

- [deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills) — Product management skills and frameworks (source for Problem Framing Canvas and Storyboard)
- [anthropics/skills](https://github.com/anthropics/skills) — Official Anthropic skills repository (source for Frontend Design)
- [Agent Skills open standard](https://agentskills.io) — Specification for cross-platform skill compatibility
- Sommerville, *Engineering Software Products*, Ch. 1 (Moore's product vision template)
