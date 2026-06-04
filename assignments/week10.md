# Week 10: AI Demo Night Deliverables

**Type:** Team assignment (one submission per team)  
**Points:** 10  
**Due:** See Camino for submission details and due date.

## Overview

The product ships this week. AI Kitchen Demo Night is a public, gallery-style showcase on Friday evening of W10, with industry guests, faculty, alumni, students, and other AI Kitchen teams in the room. The team's job is to communicate what was built and let visitors try it.

Three graded parts: a live deployed demo (Part 1), a demo video fallback (Part 2), and a one-page project summary card (Part 3). On demo night itself, each team opens with a 90-second lightning pitch and staffs its station through the evening. Both are pass/fail participation expectations on top of the three graded parts.

The three public deliverables show what the product does. Technical depth (architecture evolution, testing, security, deployment, process reflection) goes in the final technical report, a separate 40-pt deliverable graded against its own rubric.

## What else this week

Code freeze landed in W9. W10 is communication work, not new features. The graded items are the live demo, the demo video, and the summary card. The team also staffs the demo station Friday evening.

While polishing the demo, tidy the repo into a portfolio piece: a README that leads with the product description, the demo video, and the live URL, plus a clean top-level structure a stranger can navigate. The repo-as-portfolio is graded in the final technical report, but the demo video belongs in the README this week regardless.

## Part 1: Live deployed demo (4 pts)

The product is reachable by any visitor at the demo station, and the team gets the product into each visitor's hands. For a web app, that means a public URL any visitor can open on their phone or laptop. For a mobile app, that means a public install or run path (TestFlight link, Expo Go QR, downloadable build, or a working build on a team-provided device at the station). The Part 2 video is the fallback if the live demo cannot run.

Required:

- A visitor can reach the product without team-only credentials, localhost, or "you have to log in as me" caveats. If the product requires accounts, the team provides at least one demo account.
- The happy-path user flow (the one also shown in the demo video) completes end-to-end in under 90 seconds, with minimal team intervention.
- At least one in-flow failure is rehearsed: what the team shows if the API rate-limits, the model errors, or the demo account gets into a bad state. A 10-second fallback story counts. For whole-system failures (network down, deploy is down), the team plays the Part 2 video.
- **Get the product into the visitor's hands.** Don't just tell visitors about it or show them what it does — have them actually use it. Greet them, hand over the device (or open the URL on their phone), and stay with them as they try it: observe how they use it, talk to them as they go, suggest cool features to try, point out things they might miss, answer questions, and let them poke at it. Don't sit silently behind the screen while a visitor taps through alone. The goal is a hands-on conversation as the visitor uses the product, including how it was built and what would come next. Visitors should leave knowing the team and the product, not just the URL.

The grader walks up as an anonymous visitor during gallery hours, tries the demo on whatever device the product runs on, and grades on whether it works AND whether the team gets the product into the grader's hands and stays engaged — observing, suggesting things to try, fielding questions, and discussing how it was built and what's next.

## Part 2: Demo video (3 pts)

A screen recording of up to 2 minutes showing the product running through the happy-path user flow, with voiceover or on-screen captions narrating what the user is doing and what the product is delivering. The video is the team's fallback when the live demo cannot run at the station, and a visitor watching the video alone should be able to understand what the product does.

Required:

- Up to 2 minutes long. Same happy path shown in the live demo. (This is separate from the 90-second pitch; the video walks through the product, the pitch is a verbal hook.)
- Voiceover, on-screen captions, or both. A silent screen recording does not count.
- Shows the product doing the thing, framed from the user's point of view. The codebase, the architecture diagram, the dev tools panel, and "look how cool this prompt is" do not belong here. Technical depth goes in the technical report.
- Hosted at a public URL (unlisted YouTube or similar) and submitted to Camino as a link.
- Linked or embedded in the repo README, so anyone landing on the repo can watch it. The README is the front door to the project as a portfolio piece.
- A local MP4 copy of the video sits on a team-provided device at the demo station, queued in a media player and ready to play in under 10 seconds when the live demo cannot run.
- Due before demo night (see Camino for the due date). A video recorded Friday afternoon is not a fallback.

The grader watches the video as if seeing the product for the first time and grades on whether a stranger can understand what the product does from the video alone.

## Part 3: One-page project summary card (3 pts)

Each team produces one 8.5 x 11 project summary card that sits on the demo table for visitors to pick up or read at a glance. Submit as a single-page PDF.

The card should communicate the project at a glance: what it is, what problem it solves, and how a visitor can try it. An example summary card for a fictional product called GazeReader is in the GazeReader repo README: https://github.com/The-AI-Kitchen/gaze-reader#example-summary-card (a print-ready PDF is linked there too). Use it as a reference for visual rhythm and level of detail. Teams are free to depart from the example layout.

Submit the PDF to Camino as part of this W10 assignment. Each team prints its own 8.5 x 11 copy on regular paper and displays it at the demo station on demo night.

## The lightning pitch (pass/fail)

Demo night opens with each team delivering a 90-second lightning pitch to the full room, before visitors fan out to browse the stations. The pitch is the hook that gets people to walk over and try the product. It is not a full explanation.

Required:

- **Strictly 90 seconds.** A timer at the front cuts in with obnoxious classical music when the 90 seconds are up. Rehearse to land inside the limit.
- Slides and a projector are allowed (not required). If using slides, bring the deck on a team-provided laptop with the file already open and queued on the first slide. Test the projector connection (and any adapter or cable) before the pitch session starts — Thursday rehearsal is one chance, Friday before pitches begin is another. If the deck has video or audio, definitely test it in advance. Any setup happens before a team's slot, not during the 90 seconds.
- Delivered by one or two team members (the team's choice). If two speakers, rehearse the handoff so the transition is clean and does not eat into the 90 seconds.
- Lead with the motivation (the problem and why it matters) and the cool outcomes. Leave out process and technical details. Save the depth for visitors who stop by the station, where the team can go as deep as anyone wants.
- Rehearsed in class on Thursday of W10 with peer feedback before the live event Friday (see the dress rehearsal below).

The pitch is a participation expectation, not a graded rubric item. Delivering it counts; skipping it is what costs the team.

## Dress rehearsal in class: Thursday of W10

Thursday's class (W10D2) is a full dress rehearsal for Friday, run in two parts.

- Pitches first. Every team delivers its 90-second lightning pitch once to the room (with the slides they plan to use Friday, if any) and gets quick peer and instructor feedback, then has a chance to adjust before Friday. Teams using slides can test their laptop, adapter, and projector connection here — a good chance to catch any video, audio, or display issues before Friday.
- Demo stations second. Teams set up the actual demo station as it will run Friday, then rehearse the walk-up: what a visitor sees first, who greets them, how the team hands the visitor the product, the under-90-second happy path, and the rehearsed failure fallback.

Bring a deployed build and whatever you will run the station on Friday (laptop, device, demo account, and the local MP4 backup). The point is that nothing about the station or the pitch is set up for the first time on Friday.

## Demo night attendance (pass/fail)

Not graded on this rubric, but a missing team member without a pre-approved conflict knocks the W10 group grade down by 2 points.

- All team members at the demo station during gallery hours (5:30 to 7:30pm Friday). If a team member has a hard conflict, email Kai by W10 Monday 10pm. Default expectation is full team attendance.

## What to submit

Upload to Camino:

- The live deployed URL (Part 1).
- The demo video URL, hosted publicly (Part 2).
- The one-page summary card as a single PDF (Part 3).

See Camino for submission details and due date.

## Grading

| Criteria | Points |
|----------|--------|
| Part 1: Live demo reachable by an anonymous visitor (public URL for web, public install or team-provided device for mobile); happy-path flow completes end-to-end in under 90 seconds with minimal team intervention; rehearsed in-flow failure fallback; team gets the product into visitors' hands and stays engaged — observing as they use it, suggesting features to try, fielding questions, and discussing how it was built and what's next, rather than sitting silently while visitors tap through alone | 4 |
| Part 2: Demo video of up to 2 minutes with voiceover or captions showing the happy-path user flow; user-facing framing (no codebase or dev-tools content); hosted publicly with the link submitted to Camino; local MP4 on the demo laptop ready to play in under 10 seconds | 3 |
| Part 3: One-page 8.5 x 11 summary card that communicates the project at a glance (what it is, what problem it solves, how to try it); submitted to Camino as a single-page PDF; printed copy displayed at the demo station | 3 |
| **Total** | **10** |

## Gotchas

- A demo video that needs network to play is not a fallback. Save the MP4 locally and rehearse playing it offline.
- A demo video where the audio walks through the architecture diagram or shows the code is a Part 2 fail. The video is for visitors, not classmates. Architecture and code live in the technical report.
- If the card includes an image, it should show the product doing the thing. Stock illustrations of brains or "a laptop on a desk" tell visitors nothing.
- "Scan the QR code and try it on your phone" is not the demo. Visitors will tap through and leave without understanding what they just used. Hand them the product, observe and talk to them as they use it, suggest features to try, and turn it into a short conversation about the product and the build.

## Why this week

Demo night is the team's chance to put the product in front of people who were not in the room while it was built. The live demo proves the system works. The video proves what the system does even when the live demo cannot run. The card lets visitors orient themselves when the team is mid-conversation with someone else. All three feed into the same skill: communicating engineering work to a non-engineering audience. Engineering depth lives in the technical report.
