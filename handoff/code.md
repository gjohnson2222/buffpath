# Handoff — code agent

Paste this into a new Claude Code conversation.

---

I'm working on **BuffPath**, an internship-finding mobile app for CU Boulder students. There's a working design prototype and no production code yet.

**Read these first:**
1. `buffpath/data/postings.json` — the mock dataset, extracted from the prototype. Treat it as the data contract.
2. `buffpath/docs/product.md` — behavioral spec, screen by screen.
3. `buffpath/docs/dependencies.md` — **read this before estimating anything.** Most of the app's distinctive data is not available without an institutional partnership that doesn't exist yet.
4. `buffpath/docs/decisions.md` — sixteen decisions with rationale. Several constrain implementation.
5. `BuffPath Internships v2.dc.html` — the prototype. Design-tool HTML, not a codebase; read it for behavior, don't port it.

**What the prototype is.** A single-file interactive design artifact with all state in one component class and all data inline. It is not an architecture proposal. Nothing in it should be treated as a structural decision.

## The data model, as the design implies it

**Posting** — id, tier (Priority / Basic / Last Call), company, title, meta, source (Handshake or public board), applicants, seats, cuHired, deadline, hoursLeft, body, requirements.

**Requirement** — text (the employer's phrasing, quoted where it matters), state (met / reword / missing), and the matching resume line where one exists. State is *derived* per student, not stored on the posting — the same posting produces different states for different resumes.

**Application** — id, posting reference, status (Applied / Interview / Offer / Draft / Closed), synced (boolean), note, due, resume version.

**Resume version** — name, note, usage count. A student has several and picks one per application.

## Implementation constraints from the decisions

- **Requirement state is computed, not stored** (D6). Three states, no aggregate score. The reworded state — student has the thing but phrased it differently — is the hard one and the reason the feature exists.
- **Dismissals are per student, per posting, per requirement** (D7), and they change the match count. Also a useful correction signal for extraction quality.
- **Rewording never writes to the resume automatically** (D8). The flow asks the student what they did first.
- **`synced` drives tracker behavior** (D9). Synced rows are read-only and update from the source; unsynced rows are user-editable and trigger the nudge after a quiet period. Do not collapse this into one status field.
- **Tier sorts on applicant volume** (D2), which is the least available data in the system. Build the tier as a computed field with a pluggable signal so it can fall back to proxies.
- **Notifications fire for Last Call only** (D11).

## Before writing much

`dependencies.md` says the pivotal question is whether CU Career Services will sponsor a Handshake integration. Until that's answered, the buildable version is public-board postings plus the student's own resume — which still supports extraction, the three-state match, comment-to-apply, the tracker with self-reported status, and Last Call. Scraping Handshake is a terms-of-service problem, not a technical one.

Validation comes before production code. See `buffpath/docs/open-questions.md` — Q1 in particular, since a negative answer changes what's worth building.
