# Decisions

Numbered, with rationale and what would reverse each. Read this before changing the app. Most of what looks like an obvious improvement here was considered and rejected for a reason.

Dates are when the decision was made in design conversation.

---

## D1 · Three tiers replace a single ranked feed
**2026-08-26 · Settled**

Postings sort into Priority, Basic, and Last Call rather than one list ordered by fit.

**Why.** A flat list implies every posting deserves the same effort, which is the central lie of every job board. A 680-applicant program and a 58-applicant rolling posting demand completely different behavior from a student, and the interface should say so before they spend an hour on the wrong one.

**What would reverse it.** Testing showing students ignore the tier headers and treat the board as one scrolling list anyway.

---

## D2 · Tiers sort on applicant volume, not fit
**2026-08-26 · Settled, but see dependency risk**

Priority is defined by how contested a role is — applicants against seats — not by how well the student matches it.

**Why.** Fit-based sorting tells a student what they already suspect. Contest-based sorting tells them something they cannot see: that this posting is a lottery and that one is not. It also means the tiers stay stable across students, so the app can talk about them as shared categories.

**Risk.** Applicant volume is the least available data in the whole design. Public boards rarely publish it. See `dependencies.md`.

**What would reverse it.** If volume data proves unobtainable at scale, Priority has to be inferred from proxies (named program, company size, how long the posting stays open) and the tier becomes softer.

---

## D3 · No application caps — tier is sorting, not rationing
**2026-08-26 · Settled**

Considered limiting students to three Priority applications a week, on the Hinge model of scarce likes.

**Why rejected.** Scarcity works in dating because the supply is symmetrical and the cost of a bad match is mutual. In hiring, the student is the one with no leverage. Capping their applications takes away the only thing they control while employers face no equivalent limit. The friction of writing a real line (D4) is already a natural cap.

**What would reverse it.** Evidence that students spam Priority applications with throwaway lines. Then the cap becomes a quality mechanism rather than a rationing one.

---

## D4 · Comment-to-apply, Priority only
**2026-08-26 · Settled**

On Priority postings you cannot apply with a resume alone. You select one specific requirement from the posting and write one or two sentences about it. That line appears above your resume in the recruiter's view.

**Why.** This is the app's differentiator and the riskiest thing in it. Mass-applying is rational behavior in a system that rewards volume, so the only way to change it is to make volume impossible on the roles where it fails hardest. Reacting to one specific line — rather than writing a cover letter — is the Hinge mechanic translated: you cannot like the profile, only a thing on it.

**Why Priority only.** Requiring it everywhere makes the app exhausting and pushes students to a competitor for routine applications. Basic and Last Call apply with a resume.

**What would reverse it.** Students refusing to write the line. This is validation priority #1 in `Path to Reality.dc.html` — if the line reads as homework, the differentiator collapses and this is a nicer job board.

---

## D5 · Resume stays the primary object
**2026-08-26 · Settled**

The student's resume is what requirements are measured against. The app does not build a structured profile that replaces it.

**Why.** Explicitly chosen by the project owner. It also happens to be correct: a parallel profile means maintaining two representations of yourself, and the resume is the one employers actually receive. Multiple named resume versions (Business Analytics v3, Marketing v2, General v1) let a student pick per application without duplicating their identity.

**Consequence.** Extraction quality depends on resume quality, which is why "turn two class projects into three resume lines" is a prep card in the deck.

---

## D6 · Requirements shown in three states, individually
**2026-08-26 · Settled**

Every extracted requirement is *met*, *worded differently*, or *missing*. There is no aggregate fit score.

**Why.** A single number is unfalsifiable and unactionable — a student cannot do anything with "74% match." The three-state split is actionable in different ways: met is reassurance, missing is a prep step, and worded-differently is a fifteen-second resume edit. That middle state is the reason the feature exists; without it this is a checklist anyone could write.

**What would reverse it.** Testing showing the middle state reads as noise rather than sending students to their resume. Validation priority #2.

---

## D7 · Every extracted requirement is dismissible
**2026-08-26 · Settled**

Each requirement line has an ✕ that removes it from the match calculation.

**Why.** Extraction will be wrong. A parser that cannot be corrected teaches students to distrust the whole feature, or worse, to trust a machine reading of a posting they can read themselves. Dismissal makes the student the final authority, which is both honest and a useful correction signal.

---

## D8 · Rewording never happens silently
**2026-08-26 · Settled**

"Match their wording" does not edit the resume. It asks what the student actually did, then helps phrase it.

**Why.** The straight line from here is keyword-stuffing, which harms students (they cannot defend a bullet in an interview) and degrades the signal for employers. The app only offers a phrasing change when there is a real thing to point at.

---

## D9 · Application status splits by source
**2026-08-26 · Settled**

Handshake-sourced applications show "Status synced from Handshake." Public-board applications show "Self-reported — tap the status to change it," and get a one-question nudge card when they go quiet.

**Why.** The honest model. An app cannot see inside an employer's ATS for a posting it found on a public board, and pretending otherwise produces a tracker full of stale "Applied" rows. Stating the source per row makes the limitation legible instead of embarrassing.

**Why it matters strategically.** This is what makes the no-integration fallback survivable. If the Handshake partnership never happens, every row falls to self-reported and the nudge does the work. Nothing has to be redesigned.

---

## D10 · Last Call means closing soon AND unapplied
**2026-08-26 · Settled**

Not "leftovers," not "low fit," not "rolling and evergreen." Things you are about to lose.

**Why.** The alternative readings all make Last Call a bin for bad postings, which trains students to ignore it. Defining it as loss-framed and self-clearing — applying removes it — makes it the one tier that has earned a push notification.

---

## D11 · Notifications are Last Call only
**2026-08-26 · Settled**

Priority never pushes.

**Why.** A contested role is not an emergency, and a deadline is. Pushing Priority would train students to open the app anxious, which is the opposite of what a first-year needs. This also protects D12.

---

## D12 · The app is designed to be finishable
**2026-08-26 · Settled**

The Basic deck ends. There are no streaks, no daily goals, and no engagement metric anywhere in the design.

**Why.** Borrowed from Hinge's "designed to be deleted." The product's goal is a student leaving with an internship, and every retention mechanic works against that by rewarding time spent over outcome. An empty deck saying "nothing else needs your attention today" is a feature.

---

## D13 · First-years and juniors share one app
**2026-08-26 · Provisional**

Class year changes what the daily deck contains — first-years see more prep cards — but not the navigation or structure.

**Why.** Two apps is twice the surface for one audience that graduates into the other. Prep cards sitting in the same deck as postings means a student with no experience gets a next action rather than an empty state.

**Why provisional.** A first-year with a thin resume sees mostly *missing* requirements, which could read as discouraging rather than honest. Untested. Validation priority #4.

---

## D14 · Prep steps are cards in the deck, not a separate section
**2026-08-26 · Settled**

When nothing fits, the app hands back a prep step — a resume edit, a workshop, an alumni conversation — in the same deck as the postings, styled in accent red so it reads as a different kind of thing.

**Why.** A separate "improve yourself" tab is a tab nobody opens. Putting prep in the flow where the student is already triaging means the suggestion arrives at the moment of the gap, and each prep card states what it unlocks in postings.

---

## D15 · Leeds alumni is structured mentor matching, not browsing
**2026-08-26 · Settled**

A semester-long match with four conversations, not a searchable alumni directory with intro requests.

**Why.** Chosen by the project owner. Directory-plus-cold-outreach puts the burden on the student least equipped to do it, and alumni burn out on unstructured requests. A cohort model with stated expectations protects both sides.

---

## D16 · The recruiter preview is shown before submitting
**2026-08-26 · Settled**

The apply flow ends on a card showing what the recruiter sees: name, requirement count, the written line in accent red, resume version, and CU hiring history.

**Why.** It closes the loop on D4. A student writing a line needs to see that it is genuinely the first thing read, or the effort feels unrewarded.

**Caveat.** This is a *claim* about employer-side behavior. It should be verified with Career Services and real recruiters before it ships as a promise. See `open-questions.md`.
