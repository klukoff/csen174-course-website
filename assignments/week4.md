# Week 4: Gallery Walk, Initial Architecture, and Kanban Setup

**Type:** Team assignment (one submission per team)  
**Points:** 10  
**Due:** See Camino for submission details and due date.

## Overview

This is the pivot week. You've spent three weeks exploring: trying APIs, building storyboards, and creating divergent prototypes. Now you converge. In Session 1, your classmates try every prototype and give you real feedback. In Session 2, you learn about software architecture and Kanban. In lab, you choose a direction, document the architecture of what you're about to build, and set up a project board for the final project phase.

The deliverable is a team submission with three parts: a gallery walk synthesis, initial architecture documentation with a consolidation plan, and a Kanban board populated with development tasks.

## Part 1: Gallery Walk Synthesis

### What happens in class (Session 1, Tue Apr 21)

Teams bring laptops with all prototypes running locally. Each prototype gets its own station, grouped by team (stations 1a, 1b, 1c for Team 1, etc.). Label each station with a sticky note: "Team X, [your name]: [prototype name]."

Students rotate through stations spending 3-5 minutes per prototype, actually using it. One team member stays at each station to observe how people interact and answer questions. No formal pitches. Reset the app between rotations so each visitor gets a clean experience.

Visitors leave sticky-note feedback using three prompts:

- **"I liked..."** — something that worked well, felt intuitive, or was interesting
- **"I wondered..."** — something confusing, unclear, or that raised a question
- **"I'd try..."** — a suggestion or variation worth exploring

One sentence per prompt. These are quick, specific, and actionable. After the walk, collect your sticky notes and look for patterns. Three "I wondered about the onboarding flow" notes is a signal. Five "I'd try adding X" suggestions is worth considering.

### What to write up

After the gallery walk, synthesize the feedback as a team. For each prototype, write 2-3 sentences covering:

- What direction it explored and what made it distinct
- The key feedback patterns from the sticky notes (what resonated, what confused people)
- Whether elements of this prototype should carry forward into the final product

## Part 2: Initial Architecture and Consolidation Plan

This section combines two things: your team's decision about which direction to pursue, and the architecture of what you plan to build. They go together because the architecture should reflect the direction you chose, not a theoretical system.

### Consolidation plan

Start with the direction your team will pursue based on the gallery walk feedback. Write roughly half a page addressing:

- **Direction and rationale:** Which prototype direction (or combination) will the team pursue, and why? Name the specific elements you're keeping from the prototypes and what you're leaving behind. Connect this to the gallery walk feedback: what did the feedback reveal that shaped your decision?
- **Starting point:** Which prototype (if any) serves as the foundation for the consolidated codebase? Or are you starting fresh?
- **Tech stack decisions:** What front-end framework, back-end language, database, and AI APIs will the consolidated product use? If the team is keeping the same stack as a prototype, say so. If you're switching, explain why.
- **Who owns what:** How will you divide ownership of the codebase? Each team member should own a distinct area (e.g., front end, back end, AI integration, database layer). Avoid having everyone work on everything. Clear ownership prevents merge conflicts and ensures each person has a defined contribution.

### C4 diagrams

Create two diagrams using the [C4 model](https://c4model.com/):

- **Context diagram:** Shows your system as a single box, surrounded by the people who use it and the external systems it talks to. "External" means a third-party service you call but do not build or run, like an LLM API or an email provider. Your own database and cache are not external. They are part of your system and show up in the container diagram, not here. Leave infrastructure (Kubernetes, cloud regions, servers) out of this diagram too; where things run is a deployment concern, not a context one. This answers: "Who uses our system, and what outside services does it depend on?"
- **Container diagram:** Opens up your system box and shows the runnable pieces inside it (front end, back end or API, database, cache, AI service layer) and how they communicate. Aim for roughly four to eight boxes, each a thing you could deploy or restart on its own. Do not drill down to individual files, modules, or functions. That is component-level detail, one level finer than this assignment needs, and it makes the diagram harder to read. This answers: "What are the big pieces, and how does data flow between them?"

The diagrams should be **visual and human-readable**: someone looking at your context diagram should immediately understand what your system connects to, and someone looking at your container diagram should see the major pieces and how data flows between them.

#### How to create the diagrams

**Iterate with AI feedback on your design.** Whatever tool you use to think through the architecture, the goal is a back-and-forth conversation with Cursor, Claude, or ChatGPT that stress-tests your decisions. Describe your direction, share whatever you have (a whiteboard photo, a pen-and-paper sketch, a rough draw.io diagram, or a first pass of Mermaid code), and ask the AI to weigh alternatives. Push on trade-offs: where would this architecture break at scale, what simpler options exist, which external dependencies are you missing, are the boundaries between containers right? Some teams prefer to sketch first and bring the sketch into the conversation. Others prefer to start by describing the product to the AI and letting it propose an initial structure. Either order works. What matters is that the final architecture reflects real deliberation, not the first plausible-looking boxes the tool produced.

The tools you use along the way are flexible: whiteboard sketches, pen and paper, [draw.io](https://draw.io/), Figma, or Mermaid directly. Pick whatever lets the team think clearly.

**Try Mermaid, but it is not required for the final diagrams.** Mermaid has built-in support for C4 diagrams using keywords like `C4Context`, `C4Container`, `Person()`, `System()`, `Container()`, and `Rel()`. The syntax reads naturally:

```
C4Context
  Person(student, "Student", "Uses the app to study")
  System(app, "StudyBuddy", "AI-powered study tool")
  System_Ext(openai, "OpenAI API", "Provides LLM capabilities")

  Rel(student, app, "Uses")
  Rel(app, openai, "Sends prompts, receives completions")
```

(Note that PostgreSQL is not in the context diagram above: your own database is part of your system, so it appears as a container in the container diagram, not as an external box here.)

GitHub renders Mermaid code blocks in `.md` files as diagrams, so committing Mermaid to your architecture doc lets anyone viewing it on GitHub see the picture, and your AI tools can read and update the code as the system evolves. Preview in the [Mermaid Live Editor](https://mermaid.live/) or in Cursor; see the [Mermaid C4 documentation](https://mermaid.js.org/syntax/c4.html) for syntax.

Mermaid is worth trying, especially as a fast first pass or a way to explore the structure with AI. Do not treat AI-generated Mermaid as the finished diagram, though. The model often misses the right logic (drawing your database as an external system, or turning every file into a box) and the output tends to be denser and less human-readable than a diagram you lay out yourself. Whatever tool you pick (Mermaid, draw.io, Figma, Excalidraw, or a clean hand sketch), the final diagrams must be accurate and easy for a person to read.

### Commit to your repo

Your architecture documentation must live in the team's GitHub repo, regardless of which diagramming tool you use. This is important for two reasons: it gives your AI tools (Cursor, jolli.ai) access to your architecture decisions, and it becomes the reference point for the revised architecture assignment in Week 8.

Create an `architecture/` directory at the repo root with:

- `architecture.md` — your consolidation plan and C4 diagrams. If you used Mermaid, paste the code blocks (GitHub renders them automatically). If you used another tool, embed the diagrams as images. Either way, include a brief text description alongside each diagram (what the major components are, what they connect to, and how data flows between them) so your AI tools can reason about the architecture, not just render the picture.
- Any additional sketches, working notes, or exploratory diagrams the team wants to keep

This becomes the living reference for your project. Keep it up to date as your architecture evolves. You'll formally revise it in Week 8 when you compare the actual system to the plan.

### Update your .cursorrules

Once your architecture doc is committed, add a reference to it in your `.cursorrules` file (e.g., "See architecture/architecture.md for the system architecture and consolidation plan"). Your `.cursorrules` already points to `product-vision.md` from Week 2. Together, these two documents give Cursor the context it needs to generate code that fits your project: the product vision tells it what you're building and why, and the architecture doc tells it how the system is structured.

### A workflow habit: plan before you build

As you move into the final project phase, start using **plan mode** when working with Cursor or other AI coding tools. The idea is simple: before asking the agent to build something, ask it to plan first. Describe what you want, then say "plan how you'd implement this and show me before writing any code." Review the plan, adjust it, and only then let the agent execute.

Cursor supports this directly: in agent mode, you can ask it to outline its approach before making changes. The same principle works with any AI tool. It takes thirty seconds and prevents the agent from going off in a direction that doesn't fit your architecture or creates problems for the rest of the codebase. This matters more now than it did during prototyping, because you're working in a shared codebase where one person's AI-generated code affects the whole team.

## Part 3: Kanban Board Setup

Set up a project board using **GitHub Projects**. You don't need a separate repository for this: GitHub Projects is built into GitHub and can be created directly from your team repo's "Projects" tab. The board will be visible to anyone who can see your repo (which is everyone, since your repos are public).

The board marks the transition from exploratory building to structured sprint work. Sprint 1 begins next week.

### Board structure

At minimum, create these columns:

- **Backlog** — work that needs to happen but isn't scheduled yet
- **To Do** — work planned for the current sprint
- **In Progress** — work someone is actively doing
- **Done** — completed work

### Populate the backlog

Add cards for the work you can see from your consolidation plan and architecture. Your board will naturally have two kinds of cards:

- **Feature cards** describe work that's visible to the user. Write these in user story format: "As a [user], I want [goal] so that [reason]." For example: "As a student, I want to save my study session so that I can review it later." The format keeps the team focused on why you're building something, not just what.
- **Engineering cards** describe infrastructure, setup, and plumbing work. Write these as plain task descriptions. For example: "Set up PostgreSQL with user and session tables" or "Configure OpenAI API integration with error handling." Not everything traces to a user story, and that's fine.

Both types belong on the board. Seeing them side by side helps the team stay balanced between building for users and building the foundation underneath.

Each card should be a concrete task that one person could complete, not a vague category. "Set up Express server with routes for /api/chat and /api/history" is a good card. "Build the back end" is not. If you're not sure how to break something down, describe the feature to Cursor and ask it to help you identify the implementation steps.

We're keeping this simple for now: two card types, no estimation or story points. The goal is a board full of concrete, actionable work that the team can start pulling from in Week 5.

### Include the link

Include a link to your GitHub Projects board in your submission. To verify it's visible: open the link in an incognito/private browser window. If you can see the board, so can we.

## What to Submit

Submit a **single, self-contained PDF** to Camino. Everything we grade has to be visible in the PDF itself. Include repo and board links for reference, but do not rely on a link as the only way to see your work. Repos get reorganized over the quarter and links break, and we will not chase a broken link to find your submission.

1. **Gallery walk synthesis:** For each prototype, what it explored and the key feedback patterns.

2. **Consolidation plan:** Written out in the PDF: the team's chosen direction and rationale (connected to gallery walk feedback), tech stack decisions, and the ownership split (who owns which area of the codebase).

3. **C4 diagrams:** Paste your context and container diagrams into the PDF as rendered images (a screenshot or image export, not raw Mermaid code and not a link). Also commit the source to your repo at `architecture/architecture.md`, since the Week 8 revision builds on it.

4. **Kanban board:** Paste a screenshot of your populated GitHub Projects board into the PDF, and include the board link beneath the screenshot.

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Gallery walk synthesis: each prototype summarized with feedback patterns identified | 2 |
| Consolidation plan: direction choice justified with gallery walk feedback, clear tech stack decisions, ownership split defined | 2 |
| C4 context and container diagrams: accurate, reflect trade-offs the team can defend, match the planned architecture | 3 |
| Kanban board: GitHub Projects set up with appropriate columns, populated with concrete development tasks, link included | 3 |
| **Total** | **10** |

## Tips

- **Collect sticky notes carefully.** They're your primary data source for the synthesis. Take a photo of each prototype's feedback cluster before cleaning up.
- **Don't over-architect.** Your C4 diagrams should reflect what you plan to build in the next six weeks, not a fantasy system. If your product is a web app with a database and an AI API, the container diagram might have four boxes. That's fine.
- **Discuss trade-offs with AI.** The first draft can come from a whiteboard sketch, a pen-and-paper doodle, a draw.io diagram, or a first pass of Mermaid code. That choice is up to the team. The back-and-forth with AI is what produces a defensible architecture: ask it to weigh alternatives, name weaknesses in the current design, and suggest simpler options. Iterate until the team can defend each box and arrow, then commit the final C4 diagrams as Mermaid to the repo.
- **Ownership prevents merge conflicts.** Dividing the codebase by area (not by feature) means team members mostly work in different files. This is simpler than it sounds and saves enormous pain later.
- **Start the Kanban board in lab.** Don't defer it. Having cards on the board by the end of lab means your team can hit the ground running in Week 5.
- **Your architecture will change.** That's expected. The Week 8 assignment explicitly asks you to compare your initial architecture to the actual system and explain what changed and why. Document your current thinking honestly, not optimistically.
- **Break cards down until they're actionable.** If a card feels too big to start on, it probably is. Split it. A board full of small, specific cards is more useful than a board with five intimidating ones.

## Resources

- [C4 Model](https://c4model.com/) — Simon Brown's C4 model for visualizing software architecture (context, container, component, code)
- [Visualising software architecture with the C4 model](https://www.youtube.com/watch?v=x2-rSnhpw0g) — Simon Brown's talk walking through the C4 model (Week 4 reading/viewing)
- [Mermaid C4 syntax](https://mermaid.js.org/syntax/c4.html) — Mermaid's C4 diagram types and syntax reference
- [Mermaid Live Editor](https://mermaid.live/) — Browser-based tool for rendering and previewing Mermaid diagrams
- [GitHub Projects quickstart](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/quickstart-for-projects) — Getting started with GitHub's built-in project management

<!--
INSTRUCTOR NOTE (internal, not student-facing): For future quarters, consider revising Part 2 so each team member produces a C4 context + container for their own Week 3 prototype, then the team writes a comparison (trade-offs surfaced, what each assumed) and the final consolidated architecture is justified by that comparison. This reinforces Outcome 3 (compare/contrast architectures and choose best) and mirrors the diverge/converge rhythm already established in Weeks 1-3. Not feasible to introduce mid-S26 because labs (Tue + Wed) have already passed by the W4D2 Thursday lecture, and the assignment is due Monday with no additional lab time in between. To implement: update Part 2, redistribute the 5 architecture points (e.g., 2 prototype architectures + 2 comparison + 2 final), schedule time in W3 or W4 lab for students to draft individual architectures before Thursday's converge session.
-->

