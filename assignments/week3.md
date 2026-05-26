# Week 3: Repo Setup, Storyboard, and Divergent Prototypes

**Type:** Individual assignment (each student submits their own storyboard and prototype)  
**Points:** 10  
**Due:** See Camino for submission details and due date.

**This is an async week.** There are no in-person lectures or labs due to the CHI conference. The three parts of this assignment are designed to flow sequentially: get the repo set up first, then think through the user journey, then build.

**Questions about repo setup?** Kiki (xzhang22@scu.edu) is the point person this week. You can also ask Cursor itself for help with Git commands, repo configuration, and troubleshooting.

## Overview

This week your team will set up your shared repository, and then each team member will individually create a storyboard of the product's core user journey and build a working divergent prototype. The repo setup is a team task; the storyboard and prototype are individual work, grounded in your team's shared product vision and "How Might We" statement from Week 2.

Making storyboards individual is deliberate: if everyone on the team thinks through the user journey independently, you'll get genuinely different interpretations of the same product vision. That divergence is exactly what makes the Week 4 gallery walk useful.

The async format gives you a large block of unstructured time. Use it. The prototypes you build this week are the raw material for the gallery walk, where your classmates will try your product and give you feedback that shapes the rest of the quarter.

## Part 1: Repo Setup (Team)

Get your team's GitHub repository set up and working **by Tuesday** so everyone can start building. One or two team members can handle the initial setup, but everyone should verify they can clone the repo and push a test commit before moving on.

### Repository configuration

Your team repo should be **public**. All team repos in this course are public by default. This supports cross-team learning, simplifies the peer code review later in the quarter, and connects with tools like jolli.ai that we'll use starting in Week 5.

Set up the following:

- **Product vision:** Include your team's product vision statement (from Week 2) as a `product-vision.md` file in the repo root. This is the shared reference point for the team and for your AI tools. Include the full modified Moore's template (all seven fields), your "How Might We" statement, and any key insights from your Problem Framing Canvas.

- **AI agent configuration:** Create a `.cursorrules` file in the repo root. This is Cursor's version of a project instruction file: it gives the AI context about your project so it generates suggestions that fit what you're building, instead of generic code. Other tools have their own equivalents (e.g., `CLAUDE.md` for Claude Code, `.github/copilot-instructions.md` for GitHub Copilot), so if you use other AI tools now or in the future, the same concept applies. Think of it as onboarding a new team member: what would they need to know to start contributing?

  Your `.cursorrules` should include:
  - A reference to your product vision (e.g., "See product-vision.md for the full product vision and HMW statement"). Don't duplicate the product vision text here; reference the file so you only have to update it in one place.
  - Any conventions the team has agreed on (naming, file structure, coding style)
  - Context that helps the AI understand the project's goals and constraints

  This file will grow over time. Start with what you know now and update it as the team makes decisions about tech stack, architecture, and coding conventions throughout the quarter. A good `.cursorrules` file is specific enough that Cursor's suggestions feel like they come from someone who knows your project. A bad one is generic boilerplate that could apply to any repo.

- **Secrets management:** This happens at two levels. At the **repo root**, create a `.gitignore` that excludes `.env` files anywhere in the directory tree, so no one on the team can accidentally commit API keys. Since your repo is public, this is not optional. Any API keys committed to a public repo risk being scraped and abused within minutes. Then, when you build your prototype, create a `.env` file in your own `prototypes/[yourname]/` directory with your personal API keys, and a `.env.example` next to it showing which variables your prototype needs (without actual values), so a teammate or reviewer could run your code by filling in their own keys.

  If you haven't worked with `.gitignore` and `.env` files before, ask Cursor: "Help me set up a .gitignore at the repo root that excludes .env files everywhere, and a .env and .env.example in my prototype directory for [your AI API provider]. This is a public repo and I need to make sure no API keys get committed." Cursor will generate the right files and walk you through how they work.

- **Directory structure for prototypes:** Create a top-level `prototypes/` directory with a subdirectory for each team member (e.g., `prototypes/maria/`, `prototypes/alex/`, `prototypes/jordan/`). Each person builds their prototype in their own directory. This keeps everyone's work separate without requiring branching or merge conflict resolution. Each prototype can use whatever stack the individual chooses.

- **README:** A brief README at the repo root with the team name, product name, one-sentence description, and team member names.

That's it for repo setup. Keep it simple. You do not need a shared project scaffold, a formal branching strategy, or pull request workflows at this stage. Each team member is building independently in their own directory. The shared infrastructure (branching strategy, CI/CD, code review) comes later when the team consolidates into one codebase in the final project phase.

### What to include

A properly configured public GitHub repo with the above in place. We'll verify this by looking at the repo.

## Part 2: Storyboard (Individual)

Before building anything, think through the core user journey for your product. A storyboard is a visual narrative that shows how a real person encounters your product's problem, discovers the solution, and experiences the outcome. It forces you to think in concrete scenarios rather than abstract features.

Each team member creates their own storyboard independently. You're all working from the same product vision and "How Might We" statement, but your interpretation of the user journey, and the persona you create, should be yours. Different storyboards will naturally lead to different prototype directions, which is the point.

### Using the Storyboard skill

Start by running the Storyboard skill you installed in Week 2. Open Cursor in your team repo and invoke `/storyboard` in the agent chat. Reference your product vision and "How Might We" statement (e.g., `@product-vision.md`) so the assistant has context.

The skill walks you through a 6-frame narrative structure:

1. **Introduce the persona.** Create a specific person who experiences the problem your product addresses. This is not a generic user type. Give them a name, a context, and a reason to care. "Busy college student" is not a persona. "Maria, a third-year CS major juggling three group projects who just realized two have conflicting deadlines" is a persona. The skill will push you on this. Let it.
2. **Show the emerging problem.** What's going wrong in this person's life or workflow?
3. **Escalate to an urgent or frustrating moment.** The problem gets worse. Something is at stake.
4. **Present the solution.** Your product appears. Show the moment of first contact.
5. **Show the "aha" breakthrough.** The product does something that changes the situation. This should connect to your POWERED BY capability.
6. **Reveal the improved outcome.** What does life look like now?

Your persona should be grounded in your team's product vision but doesn't have to be identical to your teammates' personas. In fact, exploring different personas (a power user vs. a first-time user, a student vs. an instructor, etc.) is a good way to generate divergent prototype directions.

### Creating the visual panels

Storyboards work best as **low-fidelity sketches**, not polished illustrations. Too much visual detail pulls attention away from the scenario and toward the artwork. You want someone looking at your storyboard to think about the user's problem and your product's solution, not admire the rendering.

You have two options for creating your 6 panels:

**Option A: Draw by hand.** Sketch each panel on paper (or a tablet) and photograph or scan them. Hand-drawn storyboards are a perfectly good approach. Keep them rough and loose: stick figures, simple environments, minimal shading. The goal is to communicate the scenario, not to showcase your drawing skills.

**Option B: Use Nano Banana (recommended AI route).** Use **Nano Banana** (Gemini's image generation, familiar from Week 1) to generate a visual panel for each frame. The key is maintaining visual consistency across all 6 panels, which takes a deliberate approach. Do all of the following in a single Nano Banana conversation.

**Step 1: Generate a character reference panel.** Before creating any story panels, generate a standalone image of your protagonist. Include their name, appearance details (hair, clothing, accessories), and your style instruction. For example:

> "Create a simple illustration of a college student named Maya. She has short curly brown hair, round glasses, and a green hoodie. She's standing in front of a campus building. Use a clean, low-fidelity sketch style with muted colors, like a UX storyboard."

This reference image anchors the model's understanding of your character for the rest of the conversation.

**Step 2: Generate each story panel in the same conversation.** Do not start a new chat for each panel. Stay in the same conversation thread so the model can reference the character it already generated. For each panel, explicitly ask for the same character and visual style:

> "Using the exact same character and visual style: Maya is sitting alone at a library table, looking frustrated at her laptop screen."

The phrase "exact same character and visual style" is doing real work here. Without it, the model will drift on details like facial features, clothing, and art style between panels.

**Step 3: Pick and retry.** Try multiple prompts per frame and pick the best output, but always stay in the same conversation and always include the consistency instruction. If a panel drifts too far from the others, regenerate it before moving on. The result should look like a cohesive visual narrative, not six unrelated illustrations.

### What to submit for this part

Your individual storyboard as a **PDF**, with:
- 6 visual panels (hand-drawn or generated in Nano Banana), all in the same low-fidelity sketch style
- A brief caption for each panel (1-2 sentences) explaining what's happening
- The persona name and a one-sentence description at the top

## Part 3: Divergent Prototypes (Individual)

Each team member builds their own working prototype of the team's product concept. The goal is to explore genuinely different directions so the team has real options to compare at the Week 4 gallery walk.

### Focus on your biggest risks

The question your prototype should answer is: **is this a good way to realize our product vision statement?** That looks different for different teams:

- **UX-heavy risk:** is this the right flow, look, and feel?
- **AI risk:** can the API generate output that actually addresses the user need?
- **Architecture risk:** can this flow of information realize the product?

The goal of the prototype is not technical sophistication. Invest in technical depth only insofar as it helps you chart a path toward your product vision. Avoid implementation and polish you already know can be done with more effort (those belong in the final product). At this stage, focus on the greatest risks for your product direction.

If you want to go deeper on prototyping theory, Houde and Hill's ["What Do Prototypes Prototype?"](https://hci.stanford.edu/courses/cs247/2009/readings/Houde-Hill-Prototypes.pdf) is a great read (covered in more depth in the HCI course).

### What "divergent" means

All prototypes should be grounded in the team's shared product vision and "How Might We" statement, and informed by your individual storyboard. But each team member should explore a meaningfully different direction. "Different" means different interfaces, interaction patterns, or implementation approaches, not cosmetic variations like swapping colors or moving a button.

Examples of genuinely divergent approaches:
- One team member builds a conversational chat interface while another builds a dashboard-style UI
- One prioritizes a mobile-first layout while another explores a desktop power-user workflow
- One focuses on a guided step-by-step experience while another builds an open-ended exploration tool

The point is to cast a wide net so the team has real options to compare. If a teammate could look at your prototype and say "that's basically the same as mine," it's not divergent enough.

### Technical requirements

Each prototype must include a **front end, back end, database, and at least one AI API integration**. The front end is typically a web interface, but if your product concept calls for a different client (e.g., a browser extension with a companion web dashboard), that's acceptable as long as the back end components are present. See the [project page](#project) for full technical requirements and what's not in scope.

Each prototype must also include an **intro screen** (or equivalent landing view) that communicates what the app is, who it's for, what problem it solves, and how to use it, so someone approaching your laptop at the gallery walk with zero context can immediately understand and try it.

You may use whatever tech stack you want for your individual prototype. Your team does not need to agree on a shared stack at this stage. That decision comes later when you consolidate.

**Not required for the prototype:** test suite, CI/CD pipeline, deployment to a live URL, branch protection, or setup instructions for other developers. The bar is "works on your laptop when someone walks up to it." Engineering rigor kicks in during the final project phase starting in Week 5.

### Building with AI tools

Building a working prototype with a front end, back end, database, and AI API integration in one week is a big lift if you try to code everything by hand. Don't. This is where vibe coding shines: use Cursor's agent mode (or another agentic coding tool) to scaffold your application, generate boilerplate, and iterate quickly. Describe what you want in natural language, let the AI generate the code, test it, and refine from there. You should be spending your time on product decisions (what should this do, how should it feel), not on writing Express middleware from scratch.

Use the Frontend Design skill you installed in Week 2 to guide the visual quality of your prototype. A well-designed interface makes your prototype more compelling at the gallery walk.

As you build, pay attention to what the AI does well and where you have to intervene. This will matter for your AI Learning Journal.

### What to submit for this part

Commit to your `prototypes/[yourname]/` directory in the team repo:

- Your prototype code, ready to run locally and demo at the gallery walk.
- A 1 to 2 minute demo video of your prototype (see the Week 3 Prototype Demo Video section below for details).

### Week 3 Prototype Demo Video

> **Updated requirement (added April 22, 2026):** The demo video was added after the Week 4 gallery walk, where many prototypes turned out to not be making real API calls. The video is now part of the Week 3 submission and is how we grade the AI API portion of your prototype.

Commit a 1 to 2 minute screen recording of your prototype to your `prototypes/[yourname]/` directory in the team repo. The video should cover:

- The name of the AI API(s) being used (stated on-screen or verbally)
- The prototype launching
- You giving it input
- The AI API answering or powering an element of the experience

Any screen recording tool works (Loom, QuickTime, OBS). In the Week 3 Prototype Demo Video assignment on Camino, paste the path or URL to your video in the repo (e.g., `https://github.com/your-team/your-repo/blob/main/prototypes/maria/demo.mp4`).

## What to Submit

Submit as a **PDF** to Camino with:

1. **Your storyboard:** 6 Nano Banana panels in a low-fidelity sketch style, with captions and your persona description.

2. **Repo link:** URL to your team's public GitHub repository, with `.cursorrules`, `product-vision.md`, secrets management, prototype directories, and README in place.

3. **Your prototype:** A brief description (2-3 sentences) of what direction your prototype explores and how it differs from your teammates' approaches. Include the path to your prototype directory in the repo (e.g., `prototypes/maria/`) and the filename of your demo video (e.g., `demo.mp4`).

The demo video itself lives in the repo, not the PDF. Submit the video's path or URL in the separate Week 3 Prototype Demo Video assignment on Camino.

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Storyboard: 6 panels in a consistent low-fidelity sketch style, specific persona, clear problem-to-outcome arc grounded in the product vision | 3 |
| Repo setup: public repo with .cursorrules, product-vision.md, .gitignore excluding .env files, prototype directories with .env.example, README | 1 |
| Prototype: working application (front end + back end + database + AI API) that explores a genuinely different direction from teammates, evidenced by a 1 to 2 minute demo video showing a real API call | 4 |
| Prototype intro screen communicates what the app is and how to use it (gallery walk readiness) | 1 |
| Prototype reflects the user journey and persona from your storyboard | 1 |
| **Total** | **10** |

## Tips

- **Repo setup by Tuesday.** The sooner everyone can push code, the fewer last-minute access issues you'll hit. If you're unsure how to do something in Git, ask Cursor: it's excellent at walking you through Git commands step by step.
- **Storyboard before coding.** It takes less time than you think, and it will shape the direction of your prototype. Building without thinking through the user journey first leads to prototypes that are technically interesting but don't tell a coherent story.
- **Vibe code your prototype.** Use Cursor's agent mode to scaffold and build. Describe what you want, let the AI generate it, test it, iterate. Trying to hand-code a full-stack app with an AI API integration in a few days is unnecessarily hard. Let the tools do what they're good at.
- **Don't over-engineer.** The bar is "works when someone tries it." You'll have weeks 5-9 to add testing, CI/CD, security, and deployment. Right now, focus on exploring the idea.
- **Demo prep.** Each team member should demo their own prototype at the gallery walk. Start thinking about how you'll reset the app between visitors so each person gets a clean experience.
- **Record the demo video as soon as it works.** Do not wait until the night before the deadline. Once your API call is working end to end, record the 1 to 2 minute video right then. If the API breaks later, you still have evidence it worked.
- **Commit early and often.** Your commit history is evidence of individual work.
- **Questions about repo setup?** Email Kiki (xzhang22@scu.edu).

## Resources

- [deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills) — Source for the Storyboard skill
- [anthropics/skills](https://github.com/anthropics/skills) — Source for the Frontend Design skill
- [Nano Banana (Gemini image generation)](https://gemini.google.com/) — For generating storyboard panels
