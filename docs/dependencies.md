# Data dependencies

What the app needs, where it would come from, and how confident we are. This is the file to read before promising anyone a timeline.

## Summary

| Data | Source | Availability | If unavailable |
| --- | --- | --- | --- |
| Postings — public boards | Board APIs and feeds | **Likely** | Nothing to fall back to; this is the floor |
| Postings — CU-only | CU Boulder Handshake | **Needs partnership** | Board-only listings, thinner board |
| Requirement text | The posting body itself | **Available** wherever the posting is | — |
| Resume content | The student uploads it | **Available** | — |
| Applicant volume | Handshake or employer-reported | **Doubtful** | Tier inferred from proxies (D2) |
| Seats per program | Employer-reported | **Doubtful** | Drop the ratio, keep raw volume |
| CU hiring history | CU Career Services | **Needs partnership** | Remove the stat |
| Application status sync | Handshake integration | **Needs partnership** | Self-reported, already designed (D9) |
| Leeds alumni pool | Leeds Alumni Relations | **Needs partnership** | Link out to the existing program |

## Handshake

The pivotal dependency. Three things ride on it: CU-only postings, applicant volume, and status sync.

Student-level application status is not generally readable by a third-party app on the strength of a student's personal login — that access normally comes through the university's own agreement, not consent alone. Scraping is a terms-of-service problem rather than a technical one, and building on it would put the project at risk exactly when it started working.

So the path is institutional: CU Career Services decides whether this is possible. That single conversation determines which product gets built.

## Status sync, in order of preference

1. **Official integration** through Career Services. Clean, needs institutional buy-in.
2. **Email as signal.** Confirmation and interview emails carry the same information, and a student can grant narrow read access. Messier, works without a partnership.
3. **Self-reported.** Always the floor, and the only option for public-board applications. Already the designed default (D9).

## Leeds alumni

Mentor Match as designed assumes Leeds Alumni Relations runs the matching and permits it to be surfaced in a student app. Without that agreement the tab becomes a link to the existing program — a real loss, but not a structural one.

## What survives with no partnerships at all

Requirement extraction, the three-state resume match, comment-to-apply, the tracker with self-reported status, the deadline calendar, and Last Call. That is still a differentiated product. Tiering weakens, and the CU-specific signals disappear.

This was designed for deliberately. See D9.
