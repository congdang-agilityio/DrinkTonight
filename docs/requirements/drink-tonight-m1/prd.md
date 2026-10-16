# PRD: Drink Tonight, M1 "Tonight's outing" (Kèo tối nay)

- Slug: `drink-tonight-m1` · Analysis: `requirements.md` (signed off 2026-10-16 by Cong Dang) · Version: 1
- Epic title: Drink Tonight M1: tonight's outing (Kèo tối nay)

## 1. Summary
A small web app, in Vietnamese and usable on phones, that turns "drinks tonight?" in team chat
into an outing (kèo) with a date, a seating time, a decision deadline, a ballot of venues and a
clear headcount. M1 delivers the core loop: a shared venue list, creating and sharing an outing,
responding Going / Not going (Đi / Không đi), voting for one venue, and seeing the live result,
plus organiser edit/cancel and a health check. Automatic closing and the other "Game rules"
(Luật chơi) come in M2.

## 2. Goals and success metrics
| Goal | Metric | Target |
|---|---|---|
| The organiser knows the headcount before booking | Outing page shows number Going and who they are | Always visible on the outing page (FR-09) |
| The team converges on one venue | Outing page shows votes per venue and one leading venue | Always visible once votes exist (FR-09) |
| Easy to join from chat | Outing reachable from its own link; responding needs only a name | One link, no account (FR-01, FR-05) |
| Platform can monitor the app | `/healthz` reflects app and database health | 200 healthy / 503 database down (FR-10) |

## 3. Users
- Organiser (chủ kèo): creates, edits and cancels an outing.
- Member (thành viên): adds venues, responds, votes, views results.
- Operator: monitors health.
(Analysis §2.)

## 4. Scope
- **In this release:**
  - FR-01: name asked at first action, remembered by cookie; duplicates allowed
  - FR-02: shared venue list
  - FR-03: anyone adds a venue (name required, other fields optional); no edit/delete
  - FR-04: create an outing (date, seating time, deadline, ≥1 venue; creator auto-Going)
  - FR-05: each outing has its own shareable link
  - FR-06: Going / Not going
  - FR-07: one vote per Going person
  - FR-08: responses and votes can change at any time (no closing in M1)
  - FR-09: outing page: headcount, Going and Not going lists, public votes, one leading venue
  - FR-10: `/healthz` 200 / 503
  - FR-11: home page lists today's and upcoming, non-cancelled outings; create button
  - FR-12: organiser edits date/times and adds ballot venues
  - FR-13: organiser cancels (final)
  - FR-14: switching to Not going removes the vote
  - FR-15: change display name
- **Out / later:**
  - M2 "Game rules" (Luật chơi): auto-close at deadline, early close, cancel below 3 people,
    tie-break by least recently visited, history (requirements.md §5; Q-01)
  - Editing or deleting venues (Q-02); removing ballot venues (Q-06); restoring a cancelled
    outing (Q-19); live auto-update (Q-15); organiser recovery after cookie loss (Q-18);
    languages other than Vietnamese (Q-07)
  - Product-level out of scope: login, permissions, multiple teams, bill splitting, venue-app
    booking, Slack/email notifications, maps, separate mobile UI (SRC-1 §Ngoài phạm vi)

## 5. Requirements
| ID | Summary | Decided by |
|---|---|---|
| FR-01 | Name at first action, cookie, duplicates allowed | SRC-1, Q-10 |
| FR-02 | Venue list | SRC-1 |
| FR-03 | Add venue; only name required; no edit/delete | Q-02, Q-09 |
| FR-04 | Create outing with rules and defaults; creator Going | Q-08, Q-12, Q-13 |
| FR-05 | Shareable outing link | SRC-1 |
| FR-06 | Going / Not going | SRC-1 |
| FR-07 | One vote, Going only | SRC-1 |
| FR-08 | Always open in M1 | Q-01 |
| FR-09 | Outing page contents and leader rule | Q-04, Q-11, Q-16 |
| FR-10 | Health check | SRC-1, Q-14 |
| FR-11 | Home page list | Q-03, Q-17 |
| FR-12 | Organiser edit | Q-06, Q-20, Q-18 |
| FR-13 | Organiser cancel, final | Q-06, Q-17, Q-19 |
| FR-14 | Not going removes vote | Q-05 |
| FR-15 | Change name | Q-10 |
| NFR-01..NFR-09 | Stakeholder technical constraints (Node 22, TypeScript, Hono, server-rendered HTML, PostgreSQL with migrations before start, Vitest, Railway staging/production, env-var config, Vietnam time) | SRC-1 §Kỹ thuật |
| NFR-10 | Vietnamese-only UI | Q-07 |
| NFR-11 | Works on phone browsers | Q-15 |
| NFR-12 | No live auto-update; refresh shows current state | Q-15 |

## 6. Key decisions
| Question | Decision |
|---|---|
| Q-01 | No closing in M1; the deadline is only displayed |
| Q-02 | Anyone adds venues; no edit/delete |
| Q-03 | Home page lists today's and upcoming outings with a create button |
| Q-04, Q-16 | One leading venue; on a tie the venue that reached that count first |
| Q-05 | Switching to Not going removes the vote |
| Q-06 | Organiser edits date/times, adds venues, cancels |
| Q-07 | Vietnamese UI only |
| Q-08, Q-20 | Date today or later (default today); deadline before seating time; same on edit |
| Q-09 | Only venue name required; notes free text |
| Q-10 | Name at first action; changeable; duplicates allowed |
| Q-11 | Going and Not going lists; public votes |
| Q-12 | At least one ballot venue |
| Q-13 | Creator automatically Going |
| Q-14 | `/healthz` 503 when database is down |
| Q-15 | Must work on phones; refresh is enough |
| Q-17, Q-19 | Cancelled: shown as cancelled, no responses, hidden from home, final |
| Q-18 | Cookie-only organiser accepted for M1 |

## 7. Assumptions, deferred items and risks
- Remaining assumptions (each accepted at GATE 1): none.
- Story-level interpretations to confirm at GATE 2 (detail, no new scope):
  - S-07: with no votes yet, no leading venue is shown.
  - S-07: "reached that count first" means the earliest moment each tied venue reached its
    current count (if a venue loses a vote and regains it, the later moment counts).
  - S-11: after a name change, the person's current name is shown everywhere they appear,
    including outings they responded to earlier.
- Deferred: none (all 20 questions confirmed).
- Risks: R-01 impersonation and duplicate identities by name (accepted); R-03 M2 will add
  locking to behaviour users saw as unrestricted; R-05 edits are not notified; R-06 duplicate
  names look identical.

## 8. Story map
1. S-01: Health check for the hosting platform
2. S-02: Browse and add venues
3. S-03: Create an outing and get its link
4. S-04: Say whether I am going
5. S-05: Vote for a venue
6. S-06: My vote is removed when I am not going
7. S-07: See the leading venue
8. S-08: See today's and upcoming outings on the home page
9. S-09: Organiser edits an outing
10. S-10: Organiser cancels an outing
11. S-11: Change my display name
