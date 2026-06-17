# Final Technical Report

**Type:** Team submission (one report per team)  
**Points:** 40 (separate "Final Project" deliverable, not part of W10 weekly)  
**Due:** See Camino for submission details and due date.

## Overview

The technical report is the team's written account of the methodical software engineering process used across the quarter. The demo night and demo video show what the product does. The report shows how the team got there: how the product vision evolved, how the architecture evolved, what was tested and what was not, what security issues were found and fixed, where the team got stuck and how they unstuck, and what they would tell next quarter's CSEN 174 teams.

The grader cares more about the process narrative than the final result. A team that pivoted twice and explains both pivots clearly with code references will score higher than a team that built the original spec and writes "everything went smoothly."

Write for a person. The report should read as plain English a stranger can follow, not as a wall of tables, clipped fragments, or a list of commit links. Traceability matters, but the reader should understand each point before they ever click a reference.

## Where the report lives and how it is graded

The report is a markdown file in the repository, and the grader reads it rendered on GitHub.

- Write the report as a markdown file in the repo (for example, `TECHNICAL_REPORT.md`), linked from the README. It stays public so anyone visiting the repo can read it, and it can keep evolving after the course as the team's portfolio.
- The grader reads the report rendered on GitHub, where Markdown, diagrams, and screenshots display cleanly and links work. Make sure it renders correctly there.
- Submit one thing to Camino: a link to the report frozen at a specific commit. Use a GitHub permalink to `TECHNICAL_REPORT.md` (open the file on GitHub and press `y` to get a URL containing the full commit SHA), or paste the commit SHA itself. That commit is the version graded; anything pushed after it does not count. No PDF.
- Open the report with a short identifier block under the H1: project name, team members, and quarter (for example, `Team GazeReader · Alex Kim, Priya Shah, Jordan Lee, Sam Park · Spring 2026`). No separate title page.

## The repo is the portfolio

Treat the repository as a portfolio piece. A hiring manager, a future teammate, or next quarter's CSEN 174 team should be able to land on the repo and understand what the product is, what the engineering was, and how to run it, without anyone walking them through it.

- A clear README leads: a one-line description, a screenshot or short GIF, the embedded or linked demo video, the live URL, and a "how to run it" section.
- The README links to the technical report and the demo video so both are reachable from the front page.
- Top-level structure is legible: source, tests, docs, and infrastructure are in sensibly named directories a stranger can navigate.
- Someone can clone the repo, read the README, watch the video, and follow the technical report end to end without asking the team a question.

## Length and format

- Roughly 5 to 7 pages of body content as it renders on GitHub, excluding the identifier block. Markdown has no fixed page size, so treat this as a length target, not a hard count.
- Figures and diagrams go in the body and count toward the length. Lean on them where they help: architecture diagrams, sprint-board snapshots, product screenshots, before-and-after code. A figure that does not earn its space costs you room you need elsewhere.
- Every numbered section below includes at least one **repo reference**: a specific file path, commit SHA, PR number, sprint-board screenshot, or comparable artifact, with a sentence of plain English saying what it shows. "We refactored the API" with no link is not credit; a wall of links with no explanation is not credit either. Explain the point, then cite the evidence.
- Reference specific decisions and changes in the code, not summaries from memory. If a change removed code, link to the version-controlled instance of it (the commit or PR that removed it, or the file at an earlier tag); removed work still counts when it is traceable in version control.

## What to include

### 1. Product vision and evolution (pull from W2)

Open with a one- to two-sentence summary of the team's W2 product vision, then describe how it changed: who the product is for, what problem it solves, what got cut, what got added, and what triggered each change (persona insight, storyboard feedback, technical constraint, gallery walk comment, mid-quarter feedback, demo dry run).

- Summarize the original W2 vision and the current vision so the reader sees the before and after. No need to paste the full W2 statement verbatim; capture what it was and what it is now.
- Name the 2 to 4 decisions that bent the vision from one to the other.
- Reference at least one storyboard or persona artifact from W2 or W3 and explain whether the product still serves that user, or which user it serves instead.

### 2. Architecture and current state (pull from W4 and W8)

Show the architecture with two diagrams, the initial W4 design and the final design as of code freeze, narrate what changed between them, then describe what the product does today.

- Two C4 container diagrams only: the W4 starting point and the current/final system. No intermediate W8 diagram; fold the W8 changes into the narrative.
- Make the diagrams real C4 and human-readable: containers and the relationships between them, at a consistent altitude, concise enough to read in about 30 seconds. Not flowcharts, not a map of code files or modules, not a raw export from a diagramming tool. If a stranger cannot tell what the system is from the diagram alone, simplify it.
- Narrate the change from W4 to now: what changed, what triggered it (constraint, scaling concern, security review, AI tool output, team velocity), and which file or PR captures it in the repo. Reference at least 3 specific code paths or PRs behind architectural decisions.
- Describe the current state in a short paragraph: what the product does today, what it does not do yet, and where the seams are. Link the live deployed URL, the `demo-night` tagged commit, and the demo video, and point to the entry point in the repo for each major feature.

### 3. Engineering process: testing, security, deployment (pull from W5, W6, W7)

This is the methodical-process section. Not "we wrote tests," but "here is what we chose to test, what we chose not to test, why, and what changed when AI was in the loop." Write it as prose a reader can follow. A table is fine as support, but the point of each subsection should be clear in sentences, not left for the reader to reconstruct from a grid of links.

For each of testing, security, and deployment, address:

- The strategy as planned (W5 testing plan, W7 security audit scope, W6 CI/CD setup).
- The strategy as implemented. Show this through representative examples, not exhaustive lists. For testing, highlight one test that demonstrates the team's methodical approach and link to where it lives in the code, rather than cataloging every test. For security, name a finding and the fix that shipped. For deployment, name which pipeline stages run on every PR.
- The split between work the AI generated and work that required human judgment. A specific example of each helps.
- Links to the example test, the PRs that fixed security findings, the CI workflow, and the deployment configuration, each with a sentence saying what it shows.

### 4. Successes, setbacks, and what would change

The heart of the process retrospective. Draw on the team retrospectives from the ends of Sprint 1, Sprint 2, and Sprint 3. Those notes are the raw material; the report distills them into a narrative. Avoid generic statements ("communication was important"). Name specific incidents and what the team learned from them, in full sentences rather than clipped fragments.

- 2 to 3 notable successes. For each: what happened, why it worked, what practice the team would keep.
- 2 to 3 notable setbacks. For each: what happened, why it happened, what early signal the team missed, and what they would do differently. Link to the commit, PR, or sprint-board card where each setback is visible if one exists.
- One paragraph on AI tools across the quarter: where the team's AI coding tools pulled their weight, and where the team had to override or unwind AI output. Avoid summarizing tool features; name moments.

### 5. What's next (future work and advice)

Close with where the team would take the product and what they would tell the next cohort.

- Future work: 3 to 5 items, briefly. For each: what it is, why it matters, and a rough sense of effort (afternoon, week, sprint). Distinguish "we would build this with another sprint" from "this is a research problem."
- Advice to future CSEN 174 teams: 3 pieces, one sentence each, each earned by something the report already showed.

## What to submit

Upload to Camino:

- A frozen link to the report: a GitHub permalink to `TECHNICAL_REPORT.md` containing the full commit SHA, or the commit SHA itself, taken at code freeze. That commit is the version graded; later edits do not count. No PDF.
- Repo URL accessible to the grader (public repo by default per course policy). The README should lead with the product description, demo video, and live URL, and link to the technical report.
- A live deployment that stays reachable by anyone through the end of the grading period. Hosted URLs, demo accounts, invite links, and any API tokens behind the live version must remain valid, with no expiry, until grades are posted. An expired invite link, a revoked or expired token, or a host torn down after demo night counts as a non-functional deployment.

The repo carries the rest: the markdown report, the demo video in the README, the sprint board (linked or screenshotted), and the prior assignment artifacts the report references. The grader should be able to reach all of it from the repo front page.

## Grading

| Criteria | Points |
|----------|--------|
| Process narrative: how clearly the report shows the methodical SE process across the quarter, not just outcomes; specific incidents rather than generic statements | 9 |
| Architecture and current state: W4 → current narrative, two human-readable C4 container diagrams (before and final), at least 3 repo links to architectural decisions, and a clear account of the current state | 8 |
| Engineering process (testing, security, deployment): planned vs. implemented, AI-vs-human split, an example test that shows methodical practice, links to fix PRs / CI workflow | 8 |
| Successes, setbacks, and what's next: specific to this team, drawn from the sprint retrospectives, with links to commits or sprint-board cards where setbacks are visible | 6 |
| Repo as portfolio: README leads with product, demo video, and live URL; repo is organized so a stranger can navigate it; the report and prior artifacts are reachable from the front page; sections cite specific repo references | 4 |
| Writing quality and readability: plain English a stranger can follow, claims explained before they are cited, no code-style fragments or unexplained walls of links or tables; clear prose, parallel phrasing, figures earn their space, length respected | 5 |
| **Total** | **40** |

## Tips

- **Show the process, not just the outcome.** The point is how the team got there. Write in verbs of process: "we tried X, it failed, we replaced it with Y." A report that describes what was built without showing how it was built misses what the grader is reading for.
- **Write for a reader, then cite the evidence.** Make each point in plain sentences first, then link the file, commit, PR, or sprint-board card behind it. A grid of links with no explanation, or a setback written as "Why: ... Missed: ... Next time: ...", makes the grader do your work.
- **Two clean diagrams beat three messy ones.** Show the W4 starting point and the final system as C4 container diagrams a stranger can read in 30 seconds, and narrate the rest. Do not ship a raw diagramming-tool export or a map of your code files.
- **Mine past submissions before writing.** The W2 vision, W4 and W8 architecture, W5 testing plan, W7 security audit, W9 ethics reflection, and AI Learning Journal entries are most of what the report needs. The report ties them into a process narrative; it does not rewrite them.
- **Walk the sprint board before drafting.** The board is a memory aid: each card was a decision. Skim it from W3 forward and the setbacks section writes itself.
- **Freeze before you submit.** Get the report right, commit it, then grab the permalink or SHA for that commit. Anything pushed afterward will not be graded.

## Why this report

The demo and the video show the product to people who were not in the room while it was built. The technical report shows the process to people who care how engineering work gets done: hiring managers reading a portfolio link, the next CSEN 174 cohort, the team's future selves. The methodical software engineering process, not the product, is what transfers to the team's first job.
