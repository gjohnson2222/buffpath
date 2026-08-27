# How the app works

Behavioral reference for the current prototype (`BuffPath Internships v2.dc.html`). Rationale lives in `decisions.md`; this file covers mechanics only. Where this contradicts the prototype, the prototype is right.

## Navigation

Five bottom tabs: Board, Search, Tracker, Alumni, You. Board and its triage deck share the first tab.

## Board

The home screen. Three tiers stacked, each with a count.

**Priority** — full cards, one per posting. Company, title, source tag, applicants-last-cycle against seats, requirements met, and a "Read it" affordance. Two postings in the mock data (Charles Schwab, 680 applicants / 24 seats; Vail Resorts, 512 / 9).

**Basic** — collapsed into a single stacked-card affordance showing how many are left to triage. Tapping opens the deck.

**Last Call** — compact rows with hours remaining instead of dates. Three in mock data, from 19h to 63h.

## Basic triage deck

Swipe-style card stack. Six cards: four Basic postings interleaved with two prep cards. Pass and Save buttons animate the card out (translate plus rotate, 260ms). Job cards show the top three requirements with state markers and a "Full posting" link. Prep cards are full-bleed accent red with the step, what it unlocks, and the effort required.

The deck ends. The completion state reports what was saved and passed and points back at Priority.

## Posting detail

Opens over everything. Shows tier badge, applicants / seats / CU-hired stats, then the requirement list — the core of the screen.

Each requirement row carries:
- a square marker (filled for met, accent outline for reworded, grey outline for missing)
- a state label
- the requirement text, in the employer's exact phrasing where it was quoted
- for met and reworded: the matching resume line, indented behind a rule
- for reworded: "Match their wording" — which asks what the student did rather than editing
- for missing: "Add a prep step"
- a dismiss control that removes the line from the match count

Footer action is tier-dependent: Priority reads "Write a line and apply," everything else "Apply with a resume."

## Apply flow

**Priority — four steps.** Pick one requirement you can speak to (missing ones are not offered), write one or two sentences, pick a resume version, see the recruiter card, submit.

**Basic and Last Call — three steps.** Resume, recruiter card, submit.

The recruiter card shows name and program, requirement count, the written line on accent red, resume version, and CU hiring history. Submitting inserts the application at the top of the tracker as Applied with the chosen resume version, and the confirmation states whether status will sync or be self-reported.

## Tracker

Two tabs: List and Deadlines.

**List** — three computed counters (in flight, interviewing, due this week), then the nudge card if any application has gone quiet, then the applications. Each row shows company, title, a status chip, a note, the due or follow-up date, the resume version used, and its sync source. Self-reported rows have a tappable status chip opening a sheet with Applied / Interview / Offer / Closed. Synced rows are not editable.

**Nudge card** — appears for a quiet self-reported application. One question, two answers: "Heard back" opens the status sheet, "Still waiting" confirms the row and clears the prompt.

**Deadlines** — August month grid with today filled in ink and deadline days tinted, then a chronological list with day, month, title, and a note tying each entry back to an application or posting.

## Alumni

Leeds Mentor Match. Unjoined state explains the program — one semester, four conversations, one resume review, warm introduction if the fit is there — with a three-step how-it-works and a request button. Joined state shows three matched alumni with initials, role, Leeds year, major, why they were matched, and a request button that latches to "Request sent."

## You

Resume versions at the top with usage counts, stated as the thing every requirement is measured against. Below, rows for skills and coursework, class year, sources, dismissed requirements, and notifications — several of which surface a note rather than navigating, since they are not built out.

## Not built

Interview prep as a real screen. Onboarding (it exists in v1 only). Notification settings. Search filter sheet beyond the chips. Any employer-side software.
