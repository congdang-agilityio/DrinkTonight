# Drink Tonight M1: tonight's outing (Kèo tối nay)

A small Vietnamese-language web app, usable on phones, that turns "drinks tonight?" in team
chat into an outing (kèo) with a date, a seating time, a decision deadline, a ballot of venues
and a clear headcount. M1 delivers a shared venue list, creating and sharing an outing,
Going / Not going (Đi / Không đi) responses, one public vote per Going person with a single
leading venue, a home page listing today's and upcoming outings, organiser edit and cancel,
name-by-cookie identity, and a `/healthz` check. In M1 the decision deadline is only shown;
automatic closing, the 3-person minimum, the visit-based tie-break and history come in M2
"Game rules" (Luật chơi).

Requirements: `docs/requirements/drink-tonight-m1/requirements.md` (signed off 2026-10-16 by
Cong Dang). PRD: `docs/requirements/drink-tonight-m1/prd.md`.

## Stories
- S-01: Health check for the hosting platform (P0)
- S-02: Browse and add venues (P0)
- S-03: Create an outing and get its link (P0)
- S-04: Say whether I am going (P0)
- S-05: Vote for a venue (P0)
- S-06: My vote is removed when I am not going (P1)
- S-07: See the leading venue (P1)
- S-08: See today's and upcoming outings on the home page (P1)
- S-09: Organiser edits an outing (P2)
- S-10: Organiser cancels an outing (P2)
- S-11: Change my display name (P2)
