# Final Technical Report

**Type:** Team submission (one report per team)  
**Points:** 40 (separate "Final Project" deliverable, not part of W10 weekly)  
**Due:** See Camino for submission details and due date.

## Overview

The technical report is the team's written account of the methodical software engineering process used across the quarter. The demo night and demo video show what the product does. The report shows how the team got there: how the product vision evolved, how the architecture evolved, what was tested and what was not, what security issues were found and fixed, where the team got stuck and how they unstuck, and what they would tell next quarter's CSEN 174 teams.

The grader cares more about the process narrative than the final result. A team that pivoted twice and explains both pivots clearly with code references will score higher than a team that built the original spec and writes "everything went smoothly."

## Where the report lives

The report is both a markdown file in the repository and a PDF.

- Write the report as a markdown file in the repo (for example, `TECHNICAL_REPORT.md`), linked from the README. It stays public so anyone visiting the repo can read it.
- Export that same report to PDF and submit the PDF to Camino for grading.
- Keep the two in sync. The PDF is a snapshot of the markdown at code freeze.

Open the markdown (and therefore the PDF) with a short identifier block under the H1: project name, team members, and quarter (for example, `Team GazeReader · Alex Kim, Priya Shah, Jordan Lee, Sam Park · Spring 2026`). No separate title page.

## The repo is the portfolio

Treat the repository as a portfolio piece. A hiring manager, a future teammate, or next quarter's CSEN 174 team should be able to land on the repo and understand what the product is, what the engineering was, and how to run it, without anyone walking them through it.

- A clear README leads: a one-line description, a screenshot or short GIF, the embedded or linked demo video, the live URL, and a "how to run it" section.
- The README links to the technical report and the demo video so both are reachable from the front page.
- Top-level structure is legible: source, tests, docs, and infrastructure are in sensibly named directories a stranger can navigate.
- Someone can clone the repo, read the README, watch the video, and follow the technical report end to end without asking the team a question.

## Length and format

- 4 to 6 pages for the PDF, 11-pt body text minimum, 1-inch margins. The identifier block at the top is part of the first page, not a separate title page.
- Figures and diagrams go in the body and count toward the page budget. Lean on them. Architecture diagrams, sprint-board snapshots, screenshots of the product, before-and-after code, and other artifacts from the engineering process make the report stronger than prose alone.
- Every numbered section below ends with at least one **repo reference**: a specific file path, commit SHA, PR number, sprint-board column screenshot, or comparable artifact. "We refactored the API" without a link is not credit; "we extracted `services/agent.py` from `app.py` in PR #47 after the security review flagged it" is.
- Reference and link specific decisions and changes in the code, not summaries from memory. If a change removed code, link to the version-controlled instance of it (the commit or PR that removed it, or the file at an earlier tag); removed work still counts when it is traceable in version control.

## What to include

### 1. Product vision and evolution (pull from W2)

Open with a one- to two-sentence summary of the team's W2 product vision, then describe how it changed: who the product is for, what problem it solves, what got cut, what got added, and what triggered each change (persona insight, storyboard feedback, technical constraint, gallery walk comment, mid-quarter feedback, demo dry run).

- Summarize the original W2 vision and the current vision so the reader sees the before and after. No need to paste the full W2 statement verbatim; capture what it was and what it is now.
- Name the 2 to 4 decisions that bent the vision from one to the other.
- Reference at least one storyboard or persona artifact from W2 or W3 and explain whether the product still serves that user, or which user it serves instead.

### 2. Architecture evolution (pull from W4 and W8)

Show the W4 initial architecture, the W8 revised architecture, and the current architecture as of code freeze. Use C4 container or component diagrams (the format used in W4 and W8). Narrate the changes.

- Make the final architecture diagram genuinely human-readable. Do not dump the system into a diagramming tool and ship the raw output. Group related components, label edges, use a clear and restrained color scheme, and cut anything that does not help a reader understand the system. A diagram a stranger can read in 30 seconds beats an exhaustive one no one can parse.
- Include the diagrams across the three stages. A side-by-side beats two pages of prose.
- For each change between stages: what changed, what triggered the change (constraint, scaling concern, security review, AI tool output, team velocity), and which file or PR captures the change in the repo.
- Reference at least 3 specific code paths or PRs that implement architectural decisions.

### 3. Current state of the prototype

Describe what the product does today, what it does not do yet, and where the seams are.

- Link to the live deployed URL, the `demo-night` tagged commit, and the demo video.
- For each major feature, link to the entry point in the repo (route handler, top-level component, or service module).

### 4. Engineering process: testing, security, deployment (pull from W5, W6, W7)

This is the methodical-process section. Not "we wrote tests," but "here is what we chose to test, what we chose not to test, why, and what changed when AI was in the loop."

For each of testing, security, and deployment, address:

- The strategy as planned (W5 testing plan, W7 security audit scope, W6 CI/CD setup).
- The strategy as implemented. Show this through representative examples, not exhaustive lists. For testing, highlight one test that demonstrates the team's methodical approach and link to where it lives in the code, rather than cataloging every test. For security, name a finding and the fix that shipped. For deployment, name which pipeline stages run on every PR.
- The split between work the AI generated and work that required human judgment. A specific example of each helps.
- Links to the example test file, the PRs that fixed security findings, the CI workflow file, and the deployment configuration.

### 5. Successes, setbacks, and what would change

The heart of the process retrospective. Draw on the team retrospectives from the ends of Sprint 1, Sprint 2, and Sprint 3. Those notes are the raw material; the report distills them into a narrative. Avoid generic statements ("communication was important"). Name specific incidents and what the team learned from them.

- 2 to 3 notable successes. For each: what happened, why it worked, what practice the team would keep.
- 2 to 3 notable setbacks. For each: what happened, why it happened, what early signal the team missed, and what they would do differently. Link to the commit, PR, or sprint-board card where each setback is visible if one exists.
- One paragraph on AI tools across the quarter: where the team's AI coding tools pulled their weight, and where the team had to override or unwind AI output. Avoid summarizing tool features; name moments.

### 6. Future work

What the team would build next, in priority order, with rationale.

- 3 to 5 items, briefly. For each: what it is, why it matters, and a rough sense of effort (afternoon, week, sprint).
- Distinguish "we would build this if we had another sprint" from "this is a research problem."

### 7. Advice to future CSEN 174 teams

Short. Concrete. Written for next quarter's W1 students.

- 3 pieces of advice. One sentence each, no more.
- Earn each one with something the report already established.

## What to submit

Upload to Camino:

- One PDF (4 to 6 pages, with the identifier block at the top of page 1) per team, exported from the `TECHNICAL_REPORT.md` in the repo.
- Repo URL accessible to the grader (public repo by default per course policy). The README should lead with the product description, demo video, and live URL, and link to the technical report.

The repo carries the rest: the markdown report, the demo video in the README, the sprint board (linked or screenshotted), and the prior assignment artifacts the report references. The grader should be able to reach all of it from the repo front page.

## Grading

| Criteria | Points |
|----------|--------|
| Process narrative: how clearly the report shows the methodical SE process across the quarter, not just outcomes; specific incidents rather than generic statements | 10 |
| Architecture evolution: W4 → W8 → current narrative, with human-readable diagrams and at least 3 repo links to architectural decisions | 8 |
| Engineering process sections (testing, security, deployment): planned vs. implemented, AI-vs-human split, an example test that shows methodical practice, links to fix PRs / CI workflow | 8 |
| Successes, setbacks, and advice: specific to this team, drawn from the sprint retrospectives, with links to commits or sprint-board cards where setbacks are visible | 7 |
| Repo as portfolio: README leads with product, demo video, and live URL; repo is organized so a stranger can navigate it; the markdown report and prior artifacts are reachable from the front page; every section includes specific repo references | 4 |
| Writing quality: clarity, parallel phrasing, figures earn their space, page budget respected | 3 |
| **Total** | **40** |

## Tips

- **Show the process, not just the outcome.** The point is how the team got there. Write in verbs of process: "we tried X, it failed, we replaced it with Y." A report that describes what was built without showing how it was built misses what the grader is reading for.
- **Link to artifacts, or embed them directly.** Every claim should be reachable. Link the file, commit, PR, or sprint-board card, or drop the figure, screenshot, or diagram into the document itself. A claim with nothing behind it does not earn credit.
- **Mine past submissions before writing.** The W2 vision, W4 and W8 architecture, W5 testing plan, W7 security audit, W9 ethics reflection, and AI Learning Journal entries are most of what the report needs. The report ties them into a process narrative; it does not rewrite them.
- **Walk the sprint board before drafting.** The board is a memory aid: each card was a decision. Skim it from W3 forward and the setbacks section writes itself.
- **Diagram first, prose second.** The architecture section reads faster as a side-by-side diagram with a short caption than as three paragraphs of description.
- **Pull repo links as you write.** Open the repo in another window. When a sentence refers to "the agent service," paste the file path in the same edit. Going back to add links later is how links get missed.

## Why this report

The demo and the video show the product to people who were not in the room while it was built. The technical report shows the process to people who care how engineering work gets done: hiring managers reading a portfolio link, the next CSEN 174 cohort, the team's future selves. The methodical software engineering process, not the product, is what transfers to the team's first job.
