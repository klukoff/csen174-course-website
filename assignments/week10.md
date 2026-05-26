# Week 10: AI Demo Night Deliverables

**Type:** Team assignment (one submission per team)

**Points:** 10

**Due:** See Camino for submission details and due date.

## Overview

The product ships this week. AI Kitchen Demo Night is a public, gallery-style showcase on Friday evening of W10, with industry guests, faculty, alumni, students, and other AI Kitchen teams in the room. The team's job is to communicate what was built and let visitors try it.

Three graded parts: a live deployed demo (Part 1), a demo video fallback (Part 2), and a one-page project summary card (Part 3). Demo night attendance is a pass/fail expectation on top of the three graded parts.

The three public deliverables show what the product does. Technical depth (architecture evolution, testing, security, deployment, process reflection) goes in the final technical report, a separate 40-pt deliverable graded against its own rubric.

## What else this week

Code freeze landed in W9. W10 is communication work, not new features. The graded items are the live demo, the demo video, and the summary card. The team also staffs the demo station Friday evening.

## Part 1: Live deployed demo (4 pts)

The product is reachable by any visitor at the demo station. For a web app, that means a public URL any visitor can open on their phone or laptop. For a mobile app, that means a public install or run path (TestFlight link, Expo Go QR, downloadable build, or a working build on a team-provided device at the station). The expectation is that visitors get a hands-on live demo. The Part 2 video is the fallback if the live demo cannot run.

Required:

- A visitor can reach the product without team-only credentials, localhost, or "you have to log in as me" caveats. If the product requires accounts, the team provides at least one demo account.
- The happy-path user flow (the one also shown in the demo video) completes end-to-end in under 90 seconds, with minimal team intervention.
- At least one in-flow failure is rehearsed: what the team shows if the API rate-limits, the model errors, or the demo account gets into a bad state. A 10-second fallback story counts. For whole-system failures (network down, deploy is down), the team plays the Part 2 video.
- The deployed build matches a tagged commit on `main`. Tag it `demo-night` before Friday and include the tag link in the Camino submission.

The grader walks up as an anonymous visitor during gallery hours, attempts the demo on whatever device the product runs on, and grades on whether it works.

## Part 2: Demo video (3 pts)

A 90-second to 2-minute screen recording of the product running through the happy-path user flow, with voiceover or on-screen captions narrating what the user is doing and what the product is delivering. The video is the team's fallback when the live demo cannot run at the station, and a visitor watching the video alone should be able to understand what the product does.

Required:

- 90 seconds to 2 minutes long. Same happy path shown in the live demo.
- Voiceover, on-screen captions, or both. A silent screen recording does not count.
- Shows the product doing the thing, framed from the user's point of view. The codebase, the architecture diagram, the dev tools panel, and "look how cool this prompt is" do not belong here. Technical depth goes in the technical report.
- Hosted at a public URL (unlisted YouTube or similar) and submitted to Camino as a link.
- A local MP4 copy of the video sits on a team-provided device at the demo station, queued in a media player and ready to play in under 10 seconds when the live demo cannot run.
- Due Wednesday of W10, the same cutoff as the summary card. A video recorded Friday afternoon is not a fallback.

The grader watches the video as if seeing the product for the first time and grades on whether a stranger can understand what the product does from the video alone.

## Part 3: One-page project summary card (3 pts)

Each team produces one 8.5 x 11 project summary card that sits on the demo table for visitors to pick up or read at a glance. Submit as a single-page PDF.

The card should communicate the project at a glance: what it is, what problem it solves, and how a visitor can try it. An example summary card for a fictional product called GazeReader is in the course assets folder (`Assignments/assets/summary-card-example/`). Use it as a reference for visual rhythm and level of detail. Teams are free to depart from the example layout.

The course will print one 8.5 x 11 copy of each card on regular paper for the demo table. Submit the PDF to Camino by Wednesday of W10 so printing can happen Thursday.

## Demo night attendance (pass/fail)

Not graded on this rubric, but a missing team member without a pre-approved conflict knocks the W10 group grade down by 2 points.

- All team members at the demo station during gallery hours (5:30 to 7:30pm Friday). If a team member has a hard conflict, email Kai by W10 Monday 10pm. Default expectation is full team attendance.

## What to submit

Upload to Camino:

- The live deployed URL and the `demo-night` git tag link (Part 1).
- The demo video URL, hosted publicly (Part 2).
- The one-page summary card as a single PDF (Part 3).

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Part 1: Live demo reachable by an anonymous visitor (public URL for web, public install or team-provided device for mobile); happy-path flow completes end-to-end in under 90 seconds with minimal team intervention; rehearsed in-flow failure fallback; deployed build matches the `demo-night` git tag on `main` | 4 |
| Part 2: 90-second to 2-minute demo video with voiceover or captions showing the happy-path user flow; user-facing framing (no codebase or dev-tools content); hosted publicly with the link submitted to Camino; local MP4 on the demo laptop ready to play in under 10 seconds; submitted by the Wednesday cutoff | 3 |
| Part 3: One-page 8.5 x 11 summary card that communicates the project at a glance (what it is, what problem it solves, how to try it); submitted to Camino by the Wednesday print cutoff | 3 |
| **Total** | **10** |

## Gotchas

- A demo video that needs network to play is not a fallback. Save the MP4 locally and rehearse playing it offline.
- A demo video where the audio walks through the architecture diagram or shows the code is a Part 2 fail. The video is for visitors, not classmates. Architecture and code live in the technical report.
- If the card includes an image, it should show the product doing the thing. Stock illustrations of brains or "a laptop on a desk" tell visitors nothing.

## Why this week

Demo night is the team's chance to put the product in front of people who were not in the room while it was built. The live demo proves the system works. The video proves what the system does even when the live demo cannot run. The card lets visitors orient themselves when the team is mid-conversation with someone else. All three feed into the same skill: communicating engineering work to a non-engineering audience. Engineering depth lives in the technical report.
