# Week 7: Security Red Team and Remediation

**Type:** Team assignment (one submission per team)
**Points:** 10
**Due:** See Camino for submission details and due date.

## Overview

Sprint 2 starts this week. Sprint 1 gave the team tests, a CI pipeline, and a deployed URL. Sprint 2 starts by treating that system the way an attacker would.

The week is one adversarial loop. In lab, you red-team another team's deployed app and write up what you find. After lab, you patch your own codebase using the report your team received. Two deliverables: the red team report (Part 1) and the remediation summary (Part 2).

## What else this week

The graded items are the red team report and the patches. Sprint 2 also still demands feature work; the security loop runs alongside it, not instead of it. Be sure to make progress towards your final project deliverable!

## Part 1: Red team report on the target team (5 pts)

Each section is assigned a directed ring. Each team red-teams the next team and is red-teamed by the previous one, so the team you attack and the team attacking you are different. Every team writes one report and receives one report.

Ring assignments (pre-assigned):

- Tuesday section: Codebase Explainer → Smart Shop → TTSTT → Codebase Explainer
- Wednesday section: Roots → TripSync → Write Up → Email Triage Agent → SCU Course Planner → Roots

Read the arrow as "red-teams." For example, Smart Shop red-teams TTSTT and is red-teamed by Codebase Explainer.

Sandbox rules:

- Probe the target team's deployed instance and public repo only.
- Do not log into the target team's accounts, use their API keys, or burn their paid AI quota beyond what the deployed app already exposes to a normal user.
- If you find a leaked credential, document it and notify the target team directly. Do not test by using the credential.

Write the report in a document your team can share quickly (Google Doc, Markdown file, or similar). Share it with the target team during lab, by end of the section. The final version of the report is also uploaded to Camino at submission.

Required structure:

- One-paragraph summary of the target team's product and the surfaces you probed.
- Brief threat model: 1 to 2 attacker archetypes most plausible for this product (external attacker, insider, accidental user, automated scanner) and one sentence each on why. Each finding below ties to one of these attackers.
- Findings across three categories. Aim for at least one finding per category. If a category yielded nothing exploitable, document the null result and what you tried.
  - Technical security: auth, input validation, secrets, dependency hygiene.
  - AI API security: prompt injection, key exposure, payload sanitization, rate limit abuse.
  - Responsible AI: the required test described below.
- For each finding:
  - Vulnerability name.
  - Where in the system (URL, route, file path, line numbers).
  - Reproduction steps a grader can follow.
  - Severity: critical, major, or minor.
  - Recommended fix in 2 to 3 sentences.

The Responsible AI finding is required even if the target's app handles the case well. Role-play a vulnerable user (a person disclosing self-harm thoughts, a person sharing identifiable medical info, a minor disclosing they are a minor) and document how the app responds and what gets logged. Frame the finding constructively: "the app currently does X; for users in a Y moment that may cause Z; consider W."

In lab, each team gives a 5-minute top-finding presentation to the section (vulnerability, repro, impact, recommended fix). The presentation is not graded; the written report is.

## Part 2: Remediation in your own codebase (5 pts)

Receive the peer report your team got after lab. Pick at least 2 distinct issues to fix this sprint. At least one of the two must be an AI-specific or responsible-AI issue.

For each fix:

- Link to the source finding in the peer report
- Link to the merged PR
- 1 to 2 sentences on what changed and why this fix addresses the finding

Write the remediation summary as its own document (Google Doc, Markdown file, or similar) and upload it to Camino at submission. If the peer report had fewer than 2 findings you can act on this sprint, talk to the TA before the deadline so we can adjust expectations.

## What to submit

Upload to Camino:

- Red team report, shared with the target team during lab (Part 1).
- Remediation summary listing the two or more fixes with PR links (Part 2).

See Camino for submission details and due date.

## Grading


| Criteria                                                                                                                                                                                                                                      | Points |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| Part 1: Exploit report covers all three categories with at least one finding each (or documented null results); each finding has name, location, repro, severity, recommended fix; one responsible-AI test included and framed constructively | 5      |
| Part 2: At least 2 issues fixed and merged from the peer report; at least one is AI-specific or responsible-AI; each fix links source finding and PR; 1 to 2 sentences per fix on what changed and why                                        | 5      |
| **Total**                                                                                                                                                                                                                                     | **10** |


## Gotchas

- A red team report that says "we couldn't find anything" earns partial credit at best. Document what you tried, including dead ends. Real-world pen test reports look the same.
- Using a leaked credential from the target team to "prove" the finding crosses the sandbox line and earns no credit. Document the leak and tell the target team directly.
- Generic remediations ("improved input validation") with no PR link or no source finding do not count. Each fix must trace back to a finding in the peer report and forward to a merged PR.
- Responsible-AI test handled poorly by the app is a finding for the target team, not a failure of the red team. Frame constructively.

## Tips

- Lead with the threat model. Naming the attackers first turns "we found a bug" into "this matters because attacker X could do Y." That framing is what the grade rests on.
- Bug-finding is the easy half. AI-assisted coding has already caught a lot of the obvious surface issues. The richer findings are design, operational, business logic, and trust boundary issues that need a human reading the code with an attacker in mind.
- Treat AI tool findings as a starting point. Cursor or Claude can list 30 candidate issues in two minutes; most will be irrelevant. The skill is filtering.
- Show your work with AI. In your report (or an appendix), name the prompts you used and the model's draft findings. Then say which you verified, which you discarded, and what you added by hand. The grade rests on the judgment, not the volume.
- For the responsible-AI test, prepare the role-play before you sit down at the target team's app. Write the disclosure script ahead of time so you don't ad-lib in lab and lose the moment.
- Look at git history. Secrets that were committed and later removed often still live in earlier commits. `git log -p | grep -i 'api[_-]key'` finds plenty.
- Check the deployment platform's environment variables list (Vercel, Render, Fly.io, etc.) if the target team has it open during lab. Misconfigured env vars are a common, real finding.
- Keep the lab presentation tight. Five minutes is the lead vulnerability, the repro, the impact, and one sentence on the fix. Save the rest for the written report.
- Travis McPeak will have your section's anonymized findings beforehand. Bring questions on Thursday tied to what you saw.
- If you want to harden your CI workflow, Travis will mention tools like Dependabot, Gitleaks, CodeQL, and language-specific scanners. Adding any of these to your W6 GitHub Actions workflow is not graded this week but is a real Sprint 2 upgrade.

## Resources

- [OWASP Secure Coding Practices Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/), the practical checklist that names the categories of issues you'll be probing.
- [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/), direct and indirect prompt injection with examples.
- [The lethal trifecta for AI agents](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/), Simon Willison (W6 reading). Frames the AI-API attack surface.
- [Engineering Software Products, Ch. 7: Security and Privacy](https://www.softwareengineering-9.com/web/security/index.html), Sommerville (W6 reading). Foundational vocabulary for talking about confidentiality, integrity, and availability.

## Why this week

The red team gives the visceral realization that other teams' code has the same gaps yours does. The patches close the loop: not "we found a problem" but "here's how we fixed it."

The responsible-AI dimension is the part most likely to stick. Every team's product sends user input to an LLM, and how that LLM responds when a user shares something fragile is a security question, a design question, and an ethics question at once. Surfacing it adversarially in another team's product, before your own faces it in the wild, is the cleanest way to make it real.