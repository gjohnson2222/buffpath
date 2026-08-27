# Project rules

_Portable copy of the project root `CLAUDE.md`. In the live project that file sits at the root so it loads automatically into every conversation. If you re-establish this scaffold as its own project, rename this file back to `CLAUDE.md` and put it at the root._

---

BuffPath is an internship-finding app for CU Boulder students. Design prototype.

## Before changing the app

Read `buffpath/docs/decisions.md`. It records why the app is shaped as it is, including choices that look wrong until you know the reason. Do not silently revert a logged decision — raise it.

## Ground rules

- **Current prototype is `BuffPath Internships v2.dc.html`.** `BuffPath Internships.dc.html` is round 1, kept only for comparison.
- **The prototype is the source of truth for behavior.** The docs explain rationale and direction. Never document the same thing twice — a doc that restates the UI will drift.
- **Mock data lives in the logic class**, mirrored to `buffpath/data/postings.json`. Change both or neither.
- **Modernist design system, bound at `_ds/modernist-61c7caaf-aecb-40c5-b834-61a5171af5d6/`.** No rounded corners, flush-left everything including button labels, 2px rules, accent red used sparingly.
- **Substantial revisions get a new version file** (v3), leaving v2 intact.

## Tone

Warm and encouraging, but never inflated. The app tells a student the truth about a stretch role rather than flattering them. No streaks, no gamification, no engagement metrics — the daily deck is finishable on purpose.

## Do not

- Add a fit score as a single opaque number. Requirements are shown individually with their state.
- Make the app scarce (application caps). Tier is sorting, not rationing.
- Replace the resume with a profile as the primary object.
- Push-notify anything except Last Call.
