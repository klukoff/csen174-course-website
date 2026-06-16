# Week 9: Ethics Reflection and Code Freeze (Sprint 3)

**Type:** Team assignment (one submission per team)  
**Points:** 10  
**Due:** See Camino for submission details and due date.

## Overview

In Sprint 3, the team steps back from the codebase to ask who the product affects, what could go wrong, and where the IEEE/ACM Software Engineering Code applies. The W8 readings (737 MAX, Robodebt, Air Canada chatbot, IEEE/ACM SE Code) give the team a vocabulary for naming engineering choices that lead to harm. This week the team turns that vocabulary on its own product. In lab (Tue/Wed), the team walks through the case studies, then drafts the reflection against its own work.

The assignment also includes the Sprint 3 code freeze.

Two parts: a team ethics reflection (Part 1) and a code freeze on the team's repo (Part 2).

## What else this week

This is a light deliverable by design. The team's W9 time goes to finishing programming work, landing the code freeze, and getting the deployed app stable for demo night. The lightning pitch and the technical report belong to W10.

## Part 1: Team ethics reflection (8 pts)

Write up to two pages on the ethics of the team's product.

Required sections:

- **Product vision (one sentence).** Paste the team's current product vision statement (Moore template with POWERED BY line).
- **Stakeholders (one user, one non-user).** Name one user group and one non-user group the product affects. One sentence each. A non-user is a person the product acts on or about without their direct use. For example: an AI code-generation tool's non-users include the open-source maintainers whose repositories trained the model. They did not opt in, they get no attribution in the output, and the tool produces work that competes with their own.
- **Potential harms (3 harms).** Pick the 3 most important risks the product creates. For each harm, write a short block in this shape:
  - Harm: who is harmed and how, in concrete terms.
  - Principle: the IEEE/ACM SE Code clause that applies, named by number and short title (for example, 1.03 "Approve software only if...").
  - Mitigation: what the team has done, will do before demo night, or is choosing to accept and why. A disclaimer ("AI can make mistakes, double-check the output") is a starting point, not a real mitigation; it manages liability more than risk. For at least one of your three harms, go past the disclaimer and engineer for trust and safety: a test for the failure case, a path for users to flag bad output, a check on the sensitive cases, a guardrail or a rate limit. Name the residual risk that remains, since the model is non-deterministic and problem cases will still surface.
- **One concrete change.** Name one specific decision the team made (or will make before demo night) based on ethical reasoning. A line in the README, a disclaimer in the UI, a removed feature, a logged consent prompt, a rate limit, a test for biased outputs. The team can also draw the change from the responsible AI audit it ran in the W7 security review. One sentence on what changed and why.

Format: up to two pages, exported as PDF. Plain document, no cover page, no slide deck.

The team commits this reflection as a `.md` file to the team repo (suggested path: `docs/ethics-reflection.md`) and uploads the PDF export to Camino.

## Part 2: Code freeze (2 pts)

No new features merged to `main`. The deployed app must be live.

The freeze prevents scope creep. Maintenance work is fine.

- Allowed after freeze: bug fixes, deployment fixes, copy edits, README updates, accessibility fixes, security patches surfaced during demo prep, last-mile polish on existing features.
- Not allowed after freeze: new features, new pages, new API endpoints, new third-party integrations, new dependencies that change the architecture.

If a bug fix turns into a new feature, the team treats it as a scope decision: either cut it or document why the team is reopening the freeze. Note any post-freeze changes in the W10 technical report's process reflection.

## What to submit

- One PDF of up to two pages covering the ethics reflection (Part 1). The source `.md` lives in the team repo. The PDF export uploads to Camino.
- Deployed URL for the live app (Part 2). Paste into the submission text on Camino.

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Part 1: Product vision line, one user and one non-user stakeholder named, 3 harms each with a specific group harmed, a named IEEE/ACM SE Code clause, and a mitigation (at least one of the three goes beyond a disclaimer to an engineered trust-and-safety measure: a test, a user-flag path, a guardrail, with the residual risk named), one concrete change with one-sentence rationale, up to two pages, PDF on Camino with `.md` source in repo | 8 |
| Part 2: Deployed app live, no new features merged after freeze, allowed bug-fix changes traceable in PR history | 2 |
| **Total** | **10** |
