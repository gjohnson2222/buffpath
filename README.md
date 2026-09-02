# BuffPath

An internship-finding mobile app for CU Boulder students. Design prototype, not production software.

**Status:** interactive prototype, round 2. No backend, no real data, no institutional partnership. Everything in the app runs on mock data.

## Read this first

This project has one rule: **the `.dc.html` prototypes are the only source of truth for what the app is. The docs are the source of truth for why it is that way and what comes next.** Nothing is described in both places. If a doc contradicts the prototype, the prototype wins and the doc is stale — fix it.

## What's here

```
README.md                  this file
CLAUDE.md                  ground rules — auto-loads into every Claude Code session in this folder
docs/
  decisions.md             16 decisions, rationale, what would reverse each
  product.md               screen-by-screen mechanics
  dependencies.md          real vs. assumed vs. unavailable data
  open-questions.md        8 questions, each with how to resolve it
handoff/
  design.md                paste into Claude Design
  code.md                  paste into Claude Code
  chat.md                  paste into a strategy conversation
data/
  postings.json            mock dataset — the de facto data contract
prototypes/
  BuffPath Internships v2.dc.html    CURRENT. Start here.
  BuffPath Internships.dc.html       Round 1, comparison only
  Path to Reality.dc.html            Printable plan
  _ds/ support.js ios-frame.jsx doc-page.js    assets the prototypes load
```

The `prototypes/` folder is self-contained — open any `.dc.html` in a browser and it works, because the design system and helper files sit alongside it.

## Where to start, by role

| You are | Read |
| --- | --- |
| Designing | `handoff/design.md`, then the v2 prototype |
| Building | `handoff/code.md`, then `data/postings.json` |
| Thinking about strategy | `handoff/chat.md`, then `docs/open-questions.md` |
| Just catching up | This file, then `docs/decisions.md` |

## The app in one paragraph

Every posting is sorted into one of three tiers by how contested it is. **Priority** roles have hundreds of applicants for a handful of seats, and you cannot fast-apply to them — you pick one requirement from the posting and write a line about it, and that line is the first thing a recruiter reads. **Basic** is the middle of the market and most of the volume, triaged in a swipe deck. **Last Call** is closing inside three days and still unapplied. Underneath all three, the app reads the real posting text and sorts every requirement into met, worded-differently, or missing against the student's resume — the resume stays the primary object, never replaced by a profile.

## Which prototype is current

v2. It replaced v1's single flat daily deck with the three tiers, added requirement extraction, comment-to-apply, the recruiter preview, and the split between synced and self-reported application status.

## The one thing to test next

Whether students actually write the Priority line. Everything distinctive rests on it. See `docs/open-questions.md`, Q1.

## Working on this

Read `docs/decisions.md` first. Most of what looks like an obvious improvement to this app was considered and rejected for a stated reason. If you disagree with a decision, say so and cite the entry — do not silently revert it.
