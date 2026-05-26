# Final Technical Report

**Type:** Team submission (one report per team)

**Points:** 40 (separate "Final Project" deliverable, not part of W10 weekly)

**Due:** See Camino for submission details and due date.

## Overview

The technical report is the team's written account of the methodical software engineering process used across the quarter. The demo night and demo video show what the product does. The report shows how the team got there: how the product vision evolved, how the architecture evolved, what was tested and what was not, what security issues were found and fixed, where the team got stuck and how they unstuck, and what they would tell next quarter's CSEN 174 teams.

The grader cares more about the process narrative than the final result. A team that pivoted twice and explains both pivots clearly with code references will score higher than a team that built the original spec and writes "everything went smoothly."

## Length and format

- 3 to 5 pages of body content, single PDF, 11-pt body text minimum, 1-inch margins.
- Page count excludes the title page and the appendix.
- Figures and diagrams count toward the page budget. Use them when they earn their space.
- Every numbered section below ends with at least one **repo reference**: a specific file path, commit SHA, PR number, sprint-board column screenshot, or comparable artifact. "We refactored the API" without a link is not credit; "we extracted `services/agent.py` from `app.py` in PR #47 after the security review flagged it" is.

## What to include

### 1. Product vision and evolution (pull from W2)

Start with the team's W2 product vision sentence verbatim. Then describe how it changed: who the product is for, what problem it solves, what got cut, what got added, and what triggered each change (persona insight, storyboard feedback, technical constraint, gallery walk comment, mid-quarter feedback, demo dry run).

- Quote the original W2 vision sentence and the current vision sentence side by side.
- Name the 2 to 4 decisions that bent the vision from one to the other.
- Reference at least one storyboard or persona artifact from W2 or W3 and explain whether the product still serves that user, or which user it serves instead.

### 2. Architecture evolution (pull from W4 and W8)

Show the W4 initial architecture, the W8 revised architecture, and the current architecture as of code freeze. Use C4 container or component diagrams (the format used in W4 and W8). Narrate the changes.

- Include both diagrams. A side-by-side beats two pages of prose.
- For each change between the two: what changed, what triggered the change (constraint, scaling concern, security review, AI tool output, team velocity), and which file or PR captures the change in the repo.
- If the team used jolli.ai docs in W8, note where the generated documentation matched the team's mental model and where it diverged. Cite the jolli output file.
- Reference at least 3 specific code paths or PRs that implement architectural decisions.

### 3. Current state of the prototype

Describe what the product does today, what it does not do yet, and where the seams are.

- Link to the live deployed URL, the `demo-night` tagged commit, and the demo video.
- For each major feature, link to the entry point in the repo (route handler, top-level component, or service module).
- Name 1 to 2 known bugs or rough edges still present at code freeze. Hidden bugs surface at demo night anyway; flagging them shows judgment.

### 4. Engineering process: testing, security, deployment (pull from W5, W6, W7)

This is the methodical-process section. Not "we wrote tests," but "here is what we chose to test, what we chose not to test, why, and what changed when AI was in the loop."

For each of testing, security, and deployment, address:

- The strategy as planned (W5 testing plan, W7 security audit scope, W6 CI/CD setup).
- The strategy as implemented (which tests exist, which fixes shipped, which pipeline stages run on every PR).
- The split between work the AI generated and work that required human judgment. A specific example of each helps.
- Links to the actual test files, the PRs that fixed security findings, the CI workflow file, and the deployment configuration.

### 5. Successes, setbacks, and what would change

The heart of the process retrospective. Avoid generic statements ("communication was important"). Name specific incidents and what the team learned from them.

- 2 to 3 notable successes. For each: what happened, why it worked, what practice the team would keep.
- 2 to 3 notable setbacks. For each: what happened, why it happened, what early signal the team missed, and what they would do differently. Link to the commit, PR, or sprint-board card where each setback is visible if one exists.
- One paragraph on AI tools across the quarter: where Cursor, Claude Code, Copilot, or other agents pulled their weight, and where the team had to override or unwind AI output. Avoid summarizing tool features; name moments.

### 6. Future work

What the team would build next, in priority order, with rationale.

- 3 to 5 items, briefly. For each: what it is, why it matters, and a rough sense of effort (afternoon, week, sprint).
- Distinguish "we would build this if we had another sprint" from "this is a research problem."

### 7. Advice to future CSEN 174 teams

The last page. Short. Concrete. Written for next quarter's W1 students.

- 3 to 5 pieces of advice. One sentence each, no more.
- Earn each one with something the report already established.

## Appendix (does not count toward page budget)

- Repo URL and brief tour (1 paragraph naming the top-level directories).
- Sprint board link or screenshot (Trello, GitHub Projects, or whatever the team used). The board itself should reflect the methodical process: backlog, in progress, done, with cards tied to deliverables.
- Links to each prior assignment submission referenced in the report (W2 vision, W3 storyboards, W4 architecture, W5 testing plan, W7 security audit, W8 revised architecture, W9 ethics reflection).

## What to submit

Upload to Camino:

- One PDF (title page + 3 to 5 pages body + appendix) per team.
- Repo URL accessible to the grader (public repo by default per course policy).
- Sprint board accessible to the grader (public, or a screenshot in the appendix if the tool does not support public links).

## Grading

| Criteria | Points |
|----------|--------|
| Process narrative: how clearly the report shows the methodical SE process across the quarter, not just outcomes; specific incidents rather than generic statements | 10 |
| Architecture evolution: W4 → W8 → current narrative, with both diagrams and at least 3 repo links to architectural decisions | 8 |
| Engineering process sections (testing, security, deployment): planned vs. implemented, AI-vs-human split, links to test files / fix PRs / CI workflow | 8 |
| Successes, setbacks, and advice: specific to this team, with links to commits or sprint-board cards where setbacks are visible | 7 |
| Repo grounding: every section includes specific repo references (files, commits, PRs); past assignment submissions are integrated rather than restated | 4 |
| Writing quality: clarity, parallel phrasing, figures earn their space, page budget respected | 3 |
| **Total** | **40** |

## Gotchas

- A report that describes what was built without showing how it was built is the most common way to lose points. The grader's first scan looks for verbs of process: "we tried X, it failed, we replaced it with Y."
- "We used AI tools" with no specifics is not credit. Name the moment, the prompt or task, and the outcome (kept, unwound, partially merged).
- A repo link that 404s for a public viewer is a grading blocker. Test every link in an incognito window before submitting.
- Restating the W2 product vision deliverable verbatim and calling it Section 1 does not satisfy Section 1. Section 1 is about how the vision changed, not what it started as.
- A 7-page report with no figures and 8-pt margins reads as padding, not depth. Stay inside the budget.
- A successes / setbacks section that could have been written in W3 (generic team-formation lessons) misses the point. Tie each item to a specific quarter-of-CSEN-174 event.

## Tips

- **Mine past submissions before writing.** The W2 vision, W4 and W8 architecture, W5 testing plan, W7 security audit, W9 ethics reflection, and AI Learning Journal entries are most of what the report needs. The report ties them into a process narrative; it does not rewrite them.
- **Walk the sprint board before drafting.** The board is a memory aid: each card was a decision. Skim it from W3 forward and the setbacks section writes itself.
- **One author per section, one editor across all.** Parallel writing fits inside finals week; consistent voice does not happen by accident. Pick one teammate to do a final pass.
- **Diagram first, prose second.** The architecture section reads faster as a side-by-side diagram with a short caption than as three paragraphs of description.
- **Pull repo links as you write.** Open the repo in another window. When a sentence refers to "the agent service," paste the file path in the same edit. Going back to add links later is how links get missed.

## Why this report

The demo and the video show the product to people who were not in the room while it was built. The technical report shows the process to people who care how engineering work gets done: hiring managers reading a portfolio link, the next CSEN 174 cohort, the team's future selves. The methodical software engineering process, not the product, is what transfers to the team's first job.
