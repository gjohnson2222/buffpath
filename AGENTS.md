# Agent instructions

Read this before making any change in this repo — human or AI agent.

## What this is

BuffPath is a **design prototype** for an internship-finding app for CU Boulder students. There is no backend, no real data, and no institutional partnership. Everything runs on mock data. Not production software.

## The one rule that governs everything else

`prototypes/*.dc.html` is the only source of truth for what the app *is*. Everything in `docs/` is the source of truth for *why* it's that way and what comes next. Nothing is described in both places — if a doc contradicts the prototype, the prototype is right and the doc is stale.

## Before changing anything

1. Read `docs/decisions.md` — 16 numbered decisions with rationale and what would reverse each. Most things that look like an obvious improvement here were already considered and rejected for a stated reason. If you disagree with one, say so and cite the entry — do not silently revert it.
2. Read `docs/dependencies.md` before promising any timeline — most of the app's distinctive data needs an institutional partnership that doesn't exist yet.

## Hard rules

- **Never edit anything under `prototypes/`.** Not one character. It's the historical record of what v2 is — copy content out into `review/` or elsewhere, never edit in place. (Enforced by a hook in `.claude/settings.json` for Claude Code; other agents must still follow this manually.)
- **Current prototype is `BuffPath Internships v2.dc.html`.** Round 1 (`BuffPath Internships.dc.html`) is kept only for comparison.
- **Mock data lives in the prototype's own logic class**, mirrored to `data/postings.json`. Change both or neither.
- **No fit score as a single opaque number.** Requirements are shown individually with their state (met / worded differently / missing).
- **No application caps.** Tier is sorting, not rationing.
- **Resume stays the primary object** — never replaced by a structured profile.
- **Push notifications only for Last Call**, nothing else.

## Repo map

```
CLAUDE.md          ground rules for Claude Code specifically (this file's Claude-specific twin)
README.md          human-facing overview, start here as a person
docs/               why the app is shaped as it is (decisions, product spec, data dependencies, open questions)
data/postings.json  mock dataset — the de facto data contract
prototypes/         the actual app — DO NOT EDIT
review/             a separate offline-safe build of the prototype + a feedback-collection tool built on top of it
review-build.md     status log for the review/ side project — read it before touching review/
```

## No build step

This is static HTML/CSS/JS. There is nothing to install, compile, or run to view it — open a `.dc.html` file in `prototypes/` directly, or `review/index.html` for the packaged offline build. `review/index.html` is deployed as-is to Vercel with no build command.
