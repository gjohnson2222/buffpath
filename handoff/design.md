# Handoff — design agent

Paste this into a new Claude Design conversation.

---

I'm working on **BuffPath**, an internship-finding mobile app for CU Boulder students. It exists as an interactive prototype and I want to keep iterating on the design.

**Read these first, in order:**
1. `BuffPath Internships v2.dc.html` — the current prototype. This is the source of truth for what the app does.
2. `buffpath/docs/decisions.md` — why it's shaped this way. Sixteen numbered decisions with rationale.
3. `buffpath/docs/product.md` — screen-by-screen mechanics.

**Design system.** Modernist, bound at `_ds/modernist-61c7caaf-aecb-40c5-b834-61a5171af5d6/`. Load the bundle in every component's helmet. Flat, architectural, Archivo throughout, accent red used sparingly, **zero corner radius anywhere**, 2px rules between sections, everything flush left including button labels. Photographs would go through `.grayscale` — there are none yet.

**Do not, without raising it first:**
- Add an aggregate fit score. Requirements are shown individually with their state (D6).
- Add streaks, daily goals, or any engagement metric. The deck is finishable on purpose (D12).
- Replace the resume with a structured profile (D5).
- Extend comment-to-apply beyond Priority (D4).
- Round a corner or center a button label.

**Where the design is genuinely unfinished:**
- Interview prep has no screen. It's referenced in the profile and nowhere else.
- Onboarding exists only in v1 (`BuffPath Internships.dc.html`) and hasn't been carried forward.
- The first-year experience is untested and may read as discouraging — a thin resume produces mostly *missing* requirements (D13, Q5).
- Search has filter chips but no filter sheet.
- Empty and error states are undesigned throughout.

**Conventions.** Substantial revisions go in a new version file (v3) leaving v2 intact. Small targeted changes edit v2 directly.

Tone is warm and encouraging but never inflated — the app tells a student the truth about a stretch role rather than flattering them.
