# Week 6: CI/CD, Deployment, and Sprint 1 Retrospective

**Type:** Team assignment (one submission per team)  
**Points:** 10  
**Due:** See Camino for submission details and due date.

## Overview

Week 6 closes Sprint 1. GitHub Actions runs your W5 test suite on every pull request. Your product is reachable at a public URL. On Thursday in class, the team holds a Sprint 1 retrospective and turns the takeaways into Sprint 2 Kanban cards.

The deliverable has three parts: a working CI workflow, a live deployment, and a Sprint 1 retrospective.

## What else this week

The graded items are CI, deployment, and the retro. Sprint 1 also still demands feature work: ship the product features that realize your team's vision. By the deadline, GitHub Actions runs your W5 suite on every PR. Your deployment URL serves the landing page, and the team has converted retro takeaways into Sprint 2 Kanban cards.

## Part 1: Working CI workflow (4 pts)

Set up GitHub Actions so the W5 test suite runs on every pull request to `main`.

Required:

- A workflow file in `.github/workflows/` that triggers on `pull_request` to `main` and on `push` to `main`.
- The workflow checks out the code, installs dependencies, and runs the W5 test suite.
- At least one merged PR in the repo's history shows a passing CI run. CI passes when every unskipped test passes. Tests the team has deferred to a later sprint must be marked with a skip, xfail, or `test.todo` decorator and a `reason=` (or equivalent) string explaining the deferral. Most teams will mark the W5 integration test and AI behavior test this way, which is the expected case.
- API keys, database URLs, and other secrets handled through **Settings > Secrets and variables > Actions** in the repo, referenced in the workflow as `${{ secrets.NAME }}`. Secrets must never appear in code, in the workflow file, or in commit history.

A minimal Node example:

```yaml
name: CI
on:
  pull_request:
    branches: [main]
  push:
    branches: [main]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: "20"
      - run: npm ci
      - run: npm test
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
```

Python teams swap in `actions/setup-python` and `pip install -r requirements.txt` with `pytest`. Same shape.

In `docs/sprint-1-cicd.md`, include:

- A link to one merged PR showing the passing CI check.
- A short paragraph (3 to 5 sentences) on how the team handled secrets: which secrets exist, which environment surface (CI, deployment, or both) needs each one, and how the workflow reads them at runtime.

## Part 2: Live deployment (4 pts)

Deploy the application to a public URL.

Required:

- A reachable URL, accessible from off-campus, that returns a working landing page.
- The deployment is stable for the 24 hours leading into the deadline. "Working" means the landing page loads without server errors and the core entry point of your product is visible (a homepage, a sign-in screen, the main UI). It does not need every feature wired up.
- Secrets used in deployment (API keys, database credentials, etc.) live in the deployment platform's environment settings, not in code.

In `docs/sprint-1-cicd.md`, include:

- The live URL.
- A screenshot of the deployment platform's dashboard showing successful deploys (Vercel, Netlify, Render, Fly.io, Railway, AWS Amplify, and similar all expose a "Deployments" view). Commit the image to the repo (e.g., `docs/img/deploy.png`) and embed it inline in the markdown with `![Deploy dashboard](img/deploy.png)`.
- A short paragraph (3 to 5 sentences) describing which platform the team chose, why it fit your stack, and what tripped you up the first time.

Choose any platform that offers a free tier and supports your stack. A few common picks: Vercel and Netlify for front-end-heavy stacks, Render and Fly.io for full-stack apps with a back end, Railway for projects with a database. Many platforms can also auto-deploy on push to `main`, which pairs well with Part 1. Auto-deploy is not required for credit, but it is the workflow most teams will want for Sprint 2.

## Part 3: Sprint 1 retrospective (2 pts)

The team participates in the in-class Sprint 1 retrospective on Thursday (W6D2). After class, each team posts the write-up at `docs/sprint-1-retro.md`.

The in-class session walks through three retro prompts. All three prompts are answered in the write-up, organized into four required sections:

- **What went well (Celebrate).** Answer to the first retro prompt. Name specific people and specific contributions. "Maya unblocked the auth flow on Saturday by rewriting the token refresh logic" beats "everyone worked hard."
- **What could be improved.** Answer to the second retro prompt. Be specific about frictions, gaps, or process problems the team noticed during Sprint 1.
- **AI tools reflection.** Two short paragraphs. Describe what AI tools (Cursor, Claude, Copilot, agent skills, Jolli, etc.) made easier this sprint and what they made harder. Use concrete examples instead of generalities.
- **Sprint 2 commitments.** Answer to the third retro prompt. Two or three improvements the team will act on, each translated into a specific Kanban card on the team's Sprint 2 board. Link each card directly from the retro write-up.

Aim for one to two pages of prose. Specifics carry the grade.

## What to Submit

Two write-ups live in the team repo. Both are markdown files committed alongside the rest of the code.

`docs/sprint-1-cicd.md` covers Parts 1 and 2. It contains:

- A link to the merged PR with a passing CI run.
- The secrets paragraph (3 to 5 sentences).
- The live deployment URL.
- The deployment dashboard screenshot. Commit the image to the repo (e.g., `docs/img/deploy.png`) and embed it inline in the markdown with `![Deploy dashboard](img/deploy.png)`.
- The platform paragraph (3 to 5 sentences).

`docs/sprint-1-retro.md` covers Part 3. It contains:

- The three retro questions answered.
- The celebrate section with specific names and contributions.
- The AI tools reflection (two short paragraphs).
- Links to 2 to 3 Sprint 2 Kanban cards.

On Camino, submit:

- The repo URL.
- A direct link to `docs/sprint-1-cicd.md` in the repo.
- A direct link to `docs/sprint-1-retro.md` in the repo.

See Camino for the due date.

## Grading

| Criteria | Points |
|----------|--------|
| Part 1: GitHub Actions workflow runs the W5 test suite on every PR; at least one merged PR shows a passing CI run; deferred tests are marked with a skip or xfail decorator and a `reason=` string; secrets handled via repo settings | 4 |
| Part 2: Public URL reachable off-campus, landing page returns cleanly, stable for the 24 hours before the deadline, deployment dashboard screenshot included | 4 |
| Part 3: Retro posted at `docs/sprint-1-retro.md` with all four required sections: what went well (celebrate, with specific names and contributions), what could be improved, AI tools reflection, and Sprint 2 commitments (2 to 3 improvements, each linked to a specific Sprint 2 Kanban card) | 2 |
| **Total** | **10** |

## Gotchas

- Secrets in code (or in commit history, even if removed in a later commit) cost points, not just a code review comment.
- "Deployed but broken" earns no Part 2 credit. If the landing page 500s when the grader visits it, the part is unscored.
- Generic retro action items ("communicate better," "improve testing") do not count. Each commitment must point to a specific Sprint 2 Kanban card with a clear owner and acceptance criteria.
- A passing CI run that skips the actual tests (because the test command was misconfigured or no tests were collected) does not earn Part 1 credit. The workflow log must show the W5 suite running.
- Skipping a test the team needs to ship costs Part 1 credit. Graders spot-check `reason=` strings against the team's Sprint 2 Kanban; a skip with no matching backlog item does not pass review.
- Empty or generic `reason=` strings (`"todo"`, `"flaky"`, `"fix later"`) are scored the same as no reason. Name the sprint or the ticket the deferral points to.
- Free tiers on some deployment platforms sleep after inactivity. If the URL takes 30+ seconds to wake up, you are still scored, but plan for the lag during demos.

## Tips

- **Set up CI before deployment.** A passing CI run on a PR catches bugs before they reach the live URL. Teams that flip the order often spend Part 2 debugging issues that Part 1 would have caught.
- **Start with the minimal workflow.** Get one workflow file, one test command, one passing run. Add caching, matrix builds, and other extras later if they help.
- **Mark deferred tests, do not delete them.** A spec test from W5 that the team has consciously pushed to a later sprint should stay in the repo with a skip or xfail decorator and a real reason. Pytest: `@pytest.mark.xfail(reason="W7: payment webhook not implemented")` or `@pytest.mark.skip(reason="Sprint 2: Maya owns")`. Jest: `test.skip(name, fn)` or `test.todo("Sprint 2: payment webhook")`. The reason string is the audit trail for Part 1 grading.
- **Use the same secrets in CI and deployment.** Most teams need an LLM API key in both. Set the secret once per surface (GitHub Actions, deployment platform), reference it by name, and never paste the value into a file.
- **Pick a deployment platform that auto-deploys from `main`.** Vercel, Netlify, Render, and Fly.io all do this with a few clicks. Auto-deploy plus CI on PRs gives you the standard modern workflow: PRs run tests, merges go live.
- **Block 30 minutes after Thursday's class to draft the write-up together.** The conversation is freshest right after the in-class retro. One person at the keyboard, the rest of the team weighing in.
- **Tie commitments to ownership.** A Kanban card with no owner tends to stall. Assign each Sprint 2 commitment to a specific person before you submit.

## Resources

- [GitHub Actions: Quickstart](https://docs.github.com/en/actions/quickstart), the official 5-minute setup guide.
- [Encrypted secrets in GitHub Actions](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions), how to add and reference secrets without committing them.
- [pytest: skipping and xfail](https://docs.pytest.org/en/stable/how-to/skipping.html) and [Jest: test.skip / test.todo](https://jestjs.io/docs/api#testskipname-fn), the syntax for marking deferred tests.
- [DevOps Culture](https://www.atlassian.com/devops/what-is-devops/devops-culture), Atlassian (W5 reading, applies here too).
- [The CI/CD Handbook](https://www.freecodecamp.org/news/learn-continuous-integration-delivery-and-deployment/), freeCodeCamp (W5 reading, applies here too).
- [Vercel docs: Deploy a project](https://vercel.com/docs/deployments/overview), [Netlify docs](https://docs.netlify.com/get-started/), [Render docs](https://render.com/docs), [Fly.io docs](https://fly.io/docs/). Pick the one that matches your stack.
- [Atlassian: Running an agile retrospective](https://www.atlassian.com/team-playbook/plays/retrospective), a clean template if your team has not run a retro before.

## Why this week

GitHub Actions runs your W5 suite on every change. The deployed URL puts your product in front of users beyond your team laptop. With both in place, Sprint 2 can ship features without the constant fear of breaking what already works.

In the retro, the team converts a sprint's worth of decisions and frictions into a small, ranked set of changes for Sprint 2. The Kanban cards make those changes durable past Friday.
