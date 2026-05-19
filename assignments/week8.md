# Week 8: Revised Architecture and Sprint 2 Retrospective

**Type:** Team assignment (one submission per team)
**Points:** 10
**Due:** See Camino for submission details and due date.

## Overview

Sprint 2 closes this week. In W4 the team drew the architecture it intended to build. Since then the system has shipped, the red team has probed it, and the code on `main` is the architecture the team built. Compare the two, write down what shifted and why, present the change in class on Thursday, and run the Sprint 2 retro.

Three parts: a retrospective architecture note (Part 1), a 3-minute in-class presentation on Thursday (Part 2), and a Sprint 2 retro (Part 3).

## What else this week

The graded items are the architecture note, the presentation, and the retro. Sprint 2 still needs feature work alongside this. W9 closes with code freeze, so anything that needs to ship belongs in this week or next.

## Part 1: Retrospective architecture note (5 pts)

Write a note at `docs/architecture-retrospective.md` that compares your W4 architecture to what you have built, classifies the tech debt you are carrying into code freeze, and explains the decisions that shifted along the way.

This is a modified ADR practice. ADRs are normally written at the time of the decision and kept as a living record. Most of your architectural decisions got made fast and undocumented during the prototype phase. The team is reverse-engineering a few of them now as a learning exercise.

Required structure:

- **Product vision (revisited).** Paste the W2 product vision statement. If anything has shifted (audience, problem, key differentiator, POWERED BY line), update the statement and add one or two sentences on what changed and why. If nothing has shifted, say so in one sentence.
- **W4 intended architecture.** Link to the C4 context and container diagrams the team submitted in W4. One-paragraph summary of what the team planned to build.
- **Current-state architecture.** Current C4 context diagram and current C4 container diagram, both reflecting what is on `main` today (not the W4 plan, not where you hope to be by code freeze). Use any tool the team likes: Mermaid, draw.io, Excalidraw, Lucidchart, a Cursor-generated draft you correct, hand-drawn on paper or a tablet. Embed in the note as PNG, SVG, or Mermaid, or link from a `docs/architecture/` subfolder.
- **Decisions that shifted.** Pick 1 to 3 architectural decisions that changed between W4 and now. For each, write a short block in this shape:
  - Context: what forced the call (a constraint, a surprise, a deadline, red team feedback, a teammate's Friday-night fix).
  - Decision: what the team chose.
  - Consequences: what the team accepts by choosing it (operational complexity, vendor lock-in, a new dependency, a deferred problem).
  - Classification: which Fowler quadrant the resulting state lives in (deliberate vs inadvertent, prudent vs reckless), with one sentence on why.
- **Tech debt heading into code freeze.** A short list of debt items the team is carrying. Each item gets a Fowler quadrant classification and one sentence on whether the team will address it before code freeze or live with it through demo night.
- **One sentence on what the team would do differently with another sprint.** This sentence feeds the W10 technical report.

Two to three pages of prose plus the diagrams.

## Part 2: In-class architecture presentation (2 pts)

Each team gives a 3-minute presentation in Thursday's lecture (W8D2) on the team's revised architecture. The presentation focuses on the team's key architectural decisions and one change the team made from W4 to W8 in either its understanding or its implementation of the system.

Required:

- Up to 4 slides added to the shared class deck (link on Camino, pinned to the W8D2 session) before Thursday's lecture.
- Show your revisited product vision statement, noting briefly whether anything changed from W2.
- Show your current C4 context diagram (introduces the product at the system boundary).
- Show your C4 container diagram with a before (W4) and after (W8) view that reflects the key architectural change your team made.
- Explain the change: what shifted, and why.
- One team member delivers the 3-minute talk. All team members present in class.

Hard stop at 3 minutes. No Q&A between teams; questions go to the project work time at the end of class.

## Part 3: Sprint 2 retrospective (3 pts)

The team participates in the in-class Sprint 2 retrospective on Thursday (W8D2). Each team posts the write-up at `docs/sprint-2-retro.md` after class.

The in-class session walks through three prompts, same shape as Sprint 1:

- What went well in Sprint 2?
- What could be improved?
- Which improvements will the team commit to in Sprint 3?

Required sections in the write-up:

- **Celebrate.** Name specific people and specific contributions, same as Sprint 1.
- **Red team response.** One paragraph on what the team did with the peer red team report you received in W7. Which findings did you act on, which did you defer, which did you reject, and why? Link to the W7 remediation PRs.
- **Sprint 3 commitments.** One or two improvements the team will act on, each translated into a specific Kanban card on the team's Sprint 3 board. Sprint 3 is the last sprint, so commitments need to land by W9 or get dropped. Link each card from the retro write-up.

A few short paragraphs, around half a page. AI tools reflection is covered in the weekly AI learning journals and is not repeated here.

## What to submit

Upload to Camino:

- Retrospective architecture note (PDF), exported from `docs/architecture-retrospective.md` in your repo (Part 1).
- Team's slides added to the shared class deck (Part 2) before Thursday's lecture. The 3-minute presentation happens in Thursday's W8D2 session.
- Sprint 2 retro (PDF), exported from `docs/sprint-2-retro.md` in your repo (Part 3).

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Part 1: Product vision revisited from W2 (updated if anything shifted); current C4 context and container diagrams that reflect the state of `main`; 1 to 3 decisions that shifted, each with context, decision, consequences, and Fowler-quadrant classification; tech debt list with per-item classification and a plan; one sentence on what the team would do differently | 5 |
| Part 2: Up to 4 slides on the shared deck before Thursday's lecture; show revisited product vision, current C4 context diagram, and C4 container diagram with a before/after that reflects the key architectural change; explain the change; 3-minute talk delivered on Thursday by one team member with the rest of the team present | 2 |
| Part 3: Retro posted at `docs/sprint-2-retro.md` with all three prompts answered, celebrate section naming specific people and contributions, red team response paragraph linking remediation PRs, and 1 to 2 Sprint 3 commitments linked to specific Kanban cards | 3 |
| **Total** | **10** |

## Gotchas

- "We did not change anything architecturally" rarely holds up. A new env var, a swapped library, an added cache, a renamed table all count. If the team is sure nothing shifted, document that with evidence: no architectural commits since W4, no new dependencies in `package.json` or `requirements.txt`.
- Tech debt items without a Fowler classification lose Part 1 credit.
- Running over 3 minutes on Thursday cuts into the next team's slot. The grader cuts at 3:00 sharp.
- "Communicate better" or "improve testing" as a Sprint 3 commitment does not count. Each commitment needs a Kanban card, an owner, and an acceptance criterion.
- Generic decisions ("switched databases") with no context or consequences earn less than specific decisions ("switched from Prisma to Drizzle in week 6 after the migration broke in CI; we accept rewriting two repository functions and lose Prisma Studio for debugging").

## Tips

- **Start with the diagram, not the narrative.** With the updated C4 in front of the team, the deltas are easier to spot and the decisions block is easier to draft.
- **Compare diagrams to find decision candidates.** Each container that moved, was added, or was renamed is one. Pick the 1 to 3 that mattered most.
- **Reuse the narrative.** The architecture section of the W10 technical report can pull straight from this note.
- **Tie commitments to ownership.** Assign each Sprint 3 commitment to a specific person before you submit. A card with no owner rarely gets done.

## Why this week

This assignment documents the gap between the architecture the team planned in W4 and the system the team has built by W8. Knowing the gap helps the team decide what to fix before code freeze, and the write-up becomes the first draft of the architecture section of the W10 technical report.
