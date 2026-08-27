# Review-build log

Progress log for the "review harness" side project — not part of BuffPath's own docs (those describe the app; this describes the *tool we're building to review the app*). Paste this into a new conversation to pick up where we left off.

## What this project is

Wrapping `prototypes/BuffPath Internships v2.dc.html` so a non-technical reviewer can click through it and leave structured feedback — pins, comments, decision tooltips, exportable notes. Original ask lives in the chat history that kicked this off; this file tracks what's actually been done.

## Status: live links

- **Public app (no login, works offline after first load):** https://buffpath-eight.vercel.app/
- **GitHub repo:** https://github.com/gjohnson2222/buffpath
- Repo structure matches the original project layout (`docs/`, `data/`, `prototypes/`, `handoff/`) plus a new `review/` folder for anything built during this side project.

## Done

1. **Phase 0/1 investigation** (read all docs, read the prototype, mapped the runtime).
   Key finding: `support.js` is a compiled "dc-runtime" that turns `.dc.html`'s custom shorthand (`{{ }}`, `<sc-if>`, `<sc-for>`, `<x-import>`) into a real page. It fetches React, ReactDOM, and Babel Standalone from `unpkg.com` on every load, and Babel-transforms `ios-frame.jsx` live in the browser. This meant the original prototype could **not** run offline or satisfy a "no runtime transform" rule — a real conflict with the original review-harness plan, flagged and fixed rather than ignored.

2. **Fixed the offline problem** → `review/index.html` (deployed as the live site above).
   - Vendored React 18.3.1 + ReactDOM 18.3.1 locally (fed in via `support.js`'s own `window.__resources` hook — zero edits to `support.js`'s logic).
   - Precompiled `ios-frame.jsx` → plain JS once (via Babel Standalone run in a throwaway browser tab, not shipped), fed in via `window.__resourceBlobs`.
   - Vendored the Archivo font (single variable woff2, ~35KB) as a base64 `@font-face`, replacing the two live Google Fonts requests.
   - **One deliberate change, flagged per project rules:** in this copy only, the `x-import from="./ios-frame.jsx"` attribute is renamed to `from="./ios-frame.js"` so the runtime treats it as pre-compiled JS and skips Babel entirely. `prototypes/` itself is untouched.
   - Verified: single network request total (the page itself), console shows no real errors (one unexplained error string shows up identically across unrelated servers/origins — traced to the browser-testing tool itself, not the page), font genuinely loads (`document.fonts` confirms), click-through tested (Board → posting detail → requirement states all correct).

3. **Deployed**: local git repo → pushed to GitHub → connected to Vercel with Root Directory set to `review/` → live at the URL above.

## Not started yet

- **Comment/pin layer** — click anywhere in comment mode, drop a numbered pin, fill out category/severity/free-text, persist to localStorage, visible pin counter.
- **Screen index panel** — collapsible list of every screen/state (including the forced/faked ones: empty Last Call, mostly-missing-requirements posting, synced-vs-self-reported conflict, etc. — see the original screen inventory for the full ID list).
- **Decision-tooltip mapping** — table of decision ID → target UI element → confidence, needs to be shown for approval *before* wiring anything (per original instructions — don't wire this silently).
- **Export** — JSON (round-trippable) and Markdown (matching `docs/open-questions.md`'s existing structure) buttons, plus JSON import for merging multiple reviewers' sessions.
- **Verification pass** on the finished harness: toggle-off must look pixel-identical to plain v2, round-trip a session, confirm the review layer doesn't collide with the app's own CSS/JS (see namespace-collision risks already identified: `_ds` styles.css uses very generic global class names like `.btn`, `.card`, `.input`, `.tag`).

## Facts worth not re-deriving

- No Node/npm/Python-babel available locally on this machine — the JSX precompile was done via a throwaway browser tab loading Babel Standalone from CDN once, output saved to disk, CDN dependency then fully removed from the shipped file.
- `git` and `curl` are available locally; `node`/`npm`/`npx` are not.
- User is a beginner to this whole workflow (folders, git, deployment) — has said explicitly to explain things step by step, high-school-explainer style, not jargon-first.

## Deploy troubleshooting note (2026-08-27)
Vercel's GitHub auto-deploy wasn't connected initially; reconnected via Settings > Git, then removed/re-added the buffpath-eight.vercel.app domain to force a clean rebind. This commit exists specifically to trigger a genuinely fresh deployment (not a Redeploy-of-old-commit) to confirm the fix worked.

Confirmed: GitHub connection to Vercel was not actually established until just now (Settings > Git showed "Connected just now" after the fix) — every prior redeploy/push attempt before this had no live webhook to trigger. This commit is the first real test of the fixed connection.
Root Directory setting fixed (was literally "review" with quote characters included, now just review). Triggering deploy to confirm.
