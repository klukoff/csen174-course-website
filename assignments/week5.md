# Week 5: Testing Strategy and TDD (Sprint 1)

**Type:** Team assignment (one submission per team)
**Points:** 10
**Due:** See Camino for submission details and due date.

## Overview

This is the first week of Sprint 1, the start of the final project phase. Sprint 1 runs across W5 and W6. The optimization targets shift from this week onward: instead of building fast for exploration, you build for robustness, reliability, security, and scalability. Same engineering, different constraints.

Most students walk in with the intuition that you build the application first, then add tests to see if it works. This week practices the inverse: **test-driven development**. You write failing tests that describe what your team is building, then implement code until the tests pass. The reason testing fits here, before your codebase is large, is exactly that: TDD works best when there isn't much code yet.

The deliverable has five parts: spec tests, implementation that turns some green, a testing skill installed and used, an AI critique of skill-loaded test generation, and a Jolli.ai connection.

## What else this week

The graded items are the testing artifacts. The implicit work of Sprint 1 is shipping product features that realize your team's vision. Tests are a tool for shipping safely, not the goal. Your week should look like feature work and testing work happening together, not in sequence. By the W6 deadline, your CI/CD pipeline runs the suite you started this week and your product has features that work end-to-end.

## Part 1: Spec tests in the repo (4 pts)

Write a set of failing tests that describe what your team is building in Sprint 1.

Required minimum:

- **One unit test per team member**, written by that member, in the area they own from the W4 consolidation plan.
- **At least one integration test** that exercises the seam between two components (an API endpoint touching the database, the back end calling the AI provider, etc.). Can be co-written by the team.
- **At least one test covering AI behavior.** Every team uses an AI API in this course. Assert on the category of output (e.g., the response is valid JSON with required fields, the response contains a recommendation, the response stays under N tokens), not exact text.

Each test includes a one-sentence plain-language comment describing the behavior it covers, written from the user's perspective when applicable. Use the **Arrange-Action-Assert** structure inside each test: set up the inputs, call the function, assert what should be true.

For example:

```javascript
// As a student, I see today's assignments sorted by due date so I can plan my evening.
test("dashboard sorts assignments by due date ascending", () => {
  // Arrange
  const assignments = [
    { id: 1, due: "2026-05-15" },
    { id: 2, due: "2026-05-10" },
    { id: 3, due: "2026-05-20" }
  ];

  // Action
  const sorted = sortByDueDate(assignments);

  // Assert
  expect(sorted.map(a => a.id)).toEqual([2, 1, 3]);
});
```

The tests collectively reflect your team's Sprint 1 plan, but a strict one-to-one mapping to Kanban cards is not required. Unit tests often cover sub-behaviors of a larger feature card, and that's expected.

All tests start RED. They fail because the features aren't built yet, or only partially built.

## Part 2: Turn some tests green (2 pts)

Implement enough code to flip at least 2 tests from RED to GREEN by the deadline.

In the write-up, describe in 2 to 3 sentences how your team ran the tests RED first, then implemented features to turn them GREEN. The remaining RED tests stay as future-sprint work; some will flip in W6, others later in the quarter. Some staying RED at the deadline is expected, not a failure.

## Part 3: Testing skill installed and used (1 pt)

Find one TDD or testing-related agent skill and install it in your team repo (`.cursor/skills/` or `.claude/skills/`). With the skill loaded, ask the AI to generate **at least 3 additional tests** beyond the ones your team wrote in Part 1. Commit those AI-generated tests to the repo.

AI tools are very good at generating tests; you may want to keep more than 3 if they're useful. Aim for tests that exercise meaningful behaviors of your product. AI will happily generate dozens of similar or trivial tests if you let it, so prune anything irrelevant or redundant before you commit.

The tests you keep are what you'll critique in Part 4, so make sure at least 2 of them are substantive enough to evaluate.

In Week 2 we gave you a fixed set of skills to install. This time, you choose. Picking the right skill is itself a course skill: it's how you tailor an AI agent to your team's stack and workflow.

### Where to look for skills

Skills live in public GitHub repositories as folders containing a `SKILL.md` file. The Agent Skills specification is open, so skills generally work across Claude Code, Cursor, GitHub Copilot, OpenAI Codex CLI, and others without modification.

**For testing and TDD specifically:**

- [obra/superpowers](https://github.com/obra/superpowers) — includes a TDD skill that enforces a RED-GREEN-REFACTOR workflow. Probably the most direct fit for this assignment.
- [mattpocock/skills](https://github.com/mattpocock/skills) — 17 developer-workflow skills including TDD, refactoring, codebase architecture, and PRD writing.

**Curated lists and aggregators:**

- [anthropics/skills](https://github.com/anthropics/skills) — official Anthropic skills repository.
- [karanb192/awesome-claude-skills](https://github.com/karanb192/awesome-claude-skills) — verified Claude Code skills covering TDD, debugging, git workflows, and more.
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) — 1000+ agent skills from official teams and the community, cross-platform.
- [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) — another curated awesome list, with a focus on Claude Code workflows.

**Searchable marketplaces and search:**

- [claudeskills.info](https://claudeskills.info/skills/) — browse and download Claude Code skills with topic filters.
- GitHub code search: `path:SKILL.md "test driven"` or `path:SKILL.md "testing"` finds skills not listed in any aggregator.

You're not limited to skills with "TDD" in the name. A coverage-analysis skill, a code-review-for-tests skill, or a refactoring skill that maintains test integrity are all valid choices, as long as they support your team's testing work this sprint.

### Tips for choosing a skill

- **Match your stack first.** A skill aimed at Python pytest won't help a JavaScript team using Jest. Confirm by reading the SKILL.md before installing.
- **Read the description out loud.** If it's vague, the skill probably is too. Specific, concrete descriptions point to specific, well-scoped skills.
- **Smaller is usually better.** A skill that focuses on one workflow (e.g., red-green-refactor for TDD) usually outperforms one that tries to do everything at once.
- **Check the last commit date.** Skills not updated in over a year often reference outdated tooling, and AI tooling moves fast.
- **Try it on one test before keeping it.** Load the skill, ask the AI to generate a test, then unload the skill and ask the same AI to generate the same test. If the output doesn't change, the skill isn't doing what you wanted.

In the write-up, 3 to 5 sentences: which skill, why this one fits your team's stack and approach, and what changed about your workflow when the skill was loaded.

## Part 4: AI critique (2 pts)

Pick 2 of the tests the AI generated in Part 3. For each, 3 to 4 sentences answering:

- Does the test express what the user needs, or just what the code happens to do?
- Would the test break if you refactored the code without changing the observable behavior?
- What input is missing? Is there a domain-specific case the AI didn't think to test?

Include one before/after diff showing a test you improved using these questions.

## Part 5: Jolli connection (1 pt)

Connect your team repo to [Jolli.ai](https://jolli.ai) using the course invite link (coming by Thu Apr 30, W5D2 at the latest). Include a screenshot of the connected repo in the write-up.

Jolli runs in the background W5 to W9, generating documentation as you build. You'll use the output in W8 (revised architecture) and W9 (peer code review). Nothing visible from Jolli is graded this week beyond the connection itself.

## What to Submit

Submit on Camino. The submission includes:

- Repo URL.
- Write-up file at `docs/sprint-1-testing.md` in the team repo. Include all five parts: a brief overview, the red-to-green narrative for Part 2, the skill description for Part 3, the AI critique for Part 4 with the before/after diff, and the Jolli screenshot for Part 5.

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Part 1: Spec tests present (one unit per member, one integration, one AI behavior), each with a plain-language comment, runnable with one command on `main` | 4 |
| Part 2: At least 2 tests pass, others fail cleanly. Coherent red-to-green narrative in the write-up | 2 |
| Part 3: Testing skill installed and used on at least one test. Reflection names a concrete workflow change | 1 |
| Part 4: Both AI critiques are specific to the test. Before/after diff is real, not cosmetic | 2 |
| Part 5: Jolli connection working. Screenshot in write-up | 1 |
| **Total** | **10** |

**Tests must pass for the right reason.** `assert true`, hardcoded expected values that mirror the implementation, or tests that mock the function under test do not earn Part 1 or Part 2 credit.

## Tips

- **Use the testing framework that fits your stack.** A testing framework gives you the tools to write tests (the `test()`, `expect()`, `assertEqual()` functions you saw in lecture) plus a single command to run them all and report which passed and failed. Jest is the standard for JavaScript and TypeScript; pytest is the standard for Python. Stick with whatever your team already has set up; don't switch frameworks for this assignment.
- **Start with the smallest unit test you can run.** Get one test to RED, then GREEN, before writing anything else. The first round through the loop is the most important.
- **Use Arrange-Action-Assert in every test.** It's the structure that makes tests readable and maintainable. Every test in your suite should have these three sections, even if the comment markers aren't always there.
- **Don't chase coverage.** Coverage percentages can be gamed (testing trivial getters and setters inflates the number without finding bugs). Focus on tests that would catch real failures in your team's core logic.
- **Use the AI behavior test to learn what your AI integration actually returns.** Run a few real prompts through your AI provider, look at the response shape, and assert on the things that matter for your product. Don't try to assert on the AI's exact wording; assert on structure and category.
- **Keep building features.** The graded items are the testing artifacts, but Sprint 1 is also when you ship features. Pair feature work with tests, not before or after.

## Resources

- [The Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html) — Ham Vocke (Week 5 reading)
- [Test-Driven Development with AI](https://www.builder.io/blog/test-driven-development-ai) — Builder.io (Week 5 reading)
- [DevOps Culture](https://www.atlassian.com/devops/what-is-devops/devops-culture) — Atlassian (Week 5 reading, seeds W6)
- [The CI/CD Handbook](https://www.freecodecamp.org/news/learn-continuous-integration-delivery-and-deployment/) — freeCodeCamp (Week 5 reading, seeds W6)
- [Cursor Skills documentation](https://cursor.com/docs/skills) — How to install and load a skill in `.cursor/skills/`

## Why this week

Tests are how you keep the system honest as it grows. Sprint 1 is the time to build the habit: write the spec as tests, implement to pass, refactor with confidence. Your W5 test suite is what the W6 CI/CD pipeline will run on every PR.

The skill component is the second phase of the course's two-phase skills plan. The foundational skills you installed in W2 (Problem Framing Canvas, Storyboard, Frontend Design) carried you through ideation and prototyping. The self-selected testing skill carries you through the engineering phase.
