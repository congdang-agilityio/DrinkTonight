# Requirement analysis: Drink Tonight, M1 "Tonight's outing" (Kèo tối nay)
Signed-off: 2026-10-16 by Cong Dang

- Slug: `drink-tonight-m1`
- Status: Signed off (GATE 1, 2026-10-16)
- Sources: see the table below

## Changelog
| Date | Round | Change |
|---|---|---|
| 2026-10-16 | 1 | Initial analysis |
| 2026-10-16 | 1 | Applied Q-01..Q-07: FR-08 (always open in M1), FR-03 (anyone adds, no edit/delete), FR-09 (single leader on tie), NFR-10 (Vietnamese UI); added FR-11..FR-14, BR-07; follow-ups Q-16..Q-18 |
| 2026-10-16 | 2 | Applied Q-08..Q-12, Q-16, Q-17: FR-01 (name on first action, changeable, duplicates allowed), FR-03 (only name required), FR-04 (date and venue rules), FR-09 (Not going list, public votes, tie rule), FR-11/FR-13 (cancelled outings); added FR-15, BR-10..BR-14, R-06; follow-ups Q-19, Q-20 |
| 2026-10-16 | 3 | Applied Q-13, Q-14, Q-15, Q-18, Q-19, Q-20: FR-04 (creator auto-Going), FR-10 (503 when DB down), FR-12 (same rules on edit), FR-13 (cancel is final), BR-08 (cookie-only organiser accepted); added NFR-11, NFR-12, BR-15. All questions confirmed; requirements clear |

## Sources
| ID | File (in `sources/`) | Origin | Retrieved | Notes |
|---|---|---|---|---|
| SRC-1 | `readme.md` | repository `README.md` | 2026-10-16 | Vietnamese. Product description, M1/M2 features, out of scope, technical constraints |
| SRC-2 | `stakeholder-brief.md` | stakeholder-brief | 2026-10-16 | "Xây Drink Tonight theo README này, M1 trước" (Build Drink Tonight per this README, M1 first) |

## 1. Business goal and problem statement
A team repeatedly tries to organise an evening drinking outing in chat and fails: everyone
suggests a different venue, nobody decides, and by 5 p.m. nobody knows how many people are
coming, so a table cannot be booked (SRC-1 §Vấn đề). Drink Tonight turns each invitation into
an **outing** (kèo) with a date, a list of venues to vote on, a decision deadline (giờ chốt)
and a headcount (SRC-1 §Vấn đề). It is also a small demo app for the squad plugin (SRC-1 intro).

M1 delivers the core loop: maintain a venue list, create an outing with a shareable link,
let people say whether they are going and vote for one venue, and show the live result
(SRC-1 §M1; SRC-2). Success for M1: an organiser can see at any moment how many people are
going and which venue is leading.

## 2. Actors / personas
| Actor | Description | Goals |
|---|---|---|
| Organiser (người rủ / chủ kèo) | The person who starts an outing (SRC-1 §Người dùng) | Create the outing, choose which venues are on the ballot, book a table based on the result |
| Member (thành viên) | Anyone who opens the outing link (SRC-1 §Người dùng) | Say Going / Not going (Đi / Không đi), vote for a venue, see the result |
| Operator | Whoever runs the deployment (SRC-1 §Kỹ thuật) | Check health of the app and database |

There are no accounts: a user enters their name once and the app remembers it with a cookie
(SRC-1 §Người dùng).

## 3. Functional requirements
| ID | Requirement | Source | Status |
|---|---|---|---|
| FR-01 | The system shall ask a user for their display name the first time they do something (create an outing, respond, vote) and remember it in a cookie; no account or password is used. Viewing pages needs no name. Duplicate names are allowed. | SRC-1 §Người dùng; Q-10 | confirmed |
| FR-02 | The system shall keep a list of venues (quán). | SRC-1 §M1 "Danh sách quán" | confirmed |
| FR-03 | Any user shall be able to add a venue with a required name and optional address, Google Maps link and free-text notes (e.g. "has parking" (có chỗ để xe), "draft beer" (bia tươi)). Venues cannot be edited or deleted in M1. | SRC-1 §M1 "Danh sách quán"; Q-02; Q-09 | confirmed |
| FR-04 | A user shall be able to create an outing (kèo) with a date (today or later, default today), a seating time (giờ ngồi, default 18:30), a decision deadline (giờ chốt, default 16:00, must be before the seating time) and at least one venue on the ballot. The creator becomes the organiser and is automatically marked Going (they can change it). | SRC-1 §M1 "Tạo kèo", §Người dùng; Q-08; Q-12; Q-13 | confirmed |
| FR-05 | Each outing shall have its own link that can be shared in chat. | SRC-1 §M1 "Tạo kèo" | confirmed |
| FR-06 | Within an outing, each person shall be able to mark themselves Going or Not going (Đi / Không đi). | SRC-1 §M1 "Trong kèo" | confirmed |
| FR-07 | Within an outing, each person who is Going shall be able to vote for exactly one venue from the outing's venues; people not marked Going cannot vote. | SRC-1 §M1 "Trong kèo" | confirmed |
| FR-08 | A person shall be able to change their Going/Not going response and their vote at any time. In M1 an outing never closes: the decision deadline is displayed only and nothing is enforced when it passes (closing comes in M2). | SRC-1 §M1 "Trong kèo"; Q-01 | confirmed |
| FR-09 | The outing page shall show the number of people going, the list of people Going and the list of people Not going, the vote count per venue with the names of who voted for it, and a single leading venue (quán đang dẫn). When venues tie on the highest count, the venue that reached that count first leads. | SRC-1 §M1 "Trang kèo"; Q-04; Q-11; Q-16 | confirmed |
| FR-10 | `GET /healthz` shall return HTTP 200 when both the app and the database are running, and HTTP 503 (Service Unavailable) when the database is not reachable. | SRC-1 §M1; Q-14 | confirmed |
| FR-11 | The home page shall list today's and upcoming outings, excluding cancelled ones, with a button to create an outing. | Q-03; Q-17 | confirmed |
| FR-12 | The organiser shall be able to edit an outing's date, seating time and decision deadline, and add venues to its ballot, under the same date/time rules as creation (BR-10). Removing ballot venues is not supported. | Q-06; Q-20; Q-18 | confirmed |
| FR-13 | The organiser shall be able to cancel an outing. A cancelled outing's page shows that it is cancelled (đã huỷ) and nobody can respond or vote on it. Cancelling is final: a cancelled outing cannot be edited or restored. | Q-06; Q-17; Q-19 | confirmed |
| FR-14 | When a person who has voted changes to Not going, their vote is removed; if they switch back to Going they must vote again. | Q-05 | confirmed |
| FR-15 | A user shall be able to change their display name later. | Q-10 | confirmed |

## 4. Non-functional requirements
These are stakeholder-stated constraints, recorded as given; they are not design decisions by the BA.

| ID | Category | Requirement | Source |
|---|---|---|---|
| NFR-01 | Platform | Node.js 22, TypeScript, Hono. | SRC-1 §Kỹ thuật |
| NFR-02 | Platform | HTML rendered on the server; not a single-page application. | SRC-1 §Kỹ thuật |
| NFR-03 | Data | PostgreSQL; database migrations run before the app starts. | SRC-1 §Kỹ thuật |
| NFR-04 | Quality | Tests with Vitest: unit tests and API tests against a test database. | SRC-1 §Kỹ thuật |
| NFR-05 | Deployment | Deployed on Railway with two environments, `staging` and `production`, each with its own PostgreSQL database. | SRC-1 §Kỹ thuật |
| NFR-06 | Configuration | Configuration via environment variables: `DATABASE_URL`, `PORT`, `APP_TZ=Asia/Ho_Chi_Minh`, `DEFAULT_CLOSE_AT=16:00`, `MIN_PEOPLE=3`. | SRC-1 §Kỹ thuật |
| NFR-07 | i18n / Time | Times are Vietnam time (`Asia/Ho_Chi_Minh`). | SRC-1 §M2 (first bullet), §Kỹ thuật (`APP_TZ`) |
| NFR-08 | Security / Access | No login and no permissions system; identity is a name stored in a cookie. | SRC-1 §Người dùng, §Ngoài phạm vi |
| NFR-09 | UI | No separate mobile interface (one web UI). | SRC-1 §Ngoài phạm vi |
| NFR-10 | i18n | All user-facing text is in Vietnamese only (no language switch). | Q-07 |
| NFR-11 | Usability | All pages must work well on phone browsers (links are opened from chat). | Q-15 |
| NFR-12 | Usability | No live auto-update is required: a page shows the current state when loaded or refreshed. | Q-15 |

## 5. Scope
- **In (M1):** FR-01 to FR-15: name-by-cookie identity with name change, venue list with add,
  outing creation with shareable link, home page listing today's and upcoming outings, organiser
  edit (date, times, add venues) and cancel, Going/Not going, one-venue vote with change, vote
  removed on Not going, outing page with headcount, Going and Not going lists, public per-venue
  votes and a single leading venue, health check; usable on phones (SRC-1 §M1; SRC-2; Q-01..Q-20).
- **Out of this slug (decided):** editing or deleting venues (Q-02); removing venues from an
  outing's ballot (Q-06); any locking at the decision deadline (Q-01, moves to M2); a UI
  language other than Vietnamese (Q-07); restoring a cancelled outing (Q-19); live
  auto-updating pages (Q-15); organiser-role recovery when the cookie is lost (Q-18).
- **Out of this slug, known future scope (M2 "Game rules" (Luật chơi), SRC-1 §M2):**
  - Automatic close at the decision deadline in Vietnam time; after closing no changes to
    Going/Not going or votes; the organiser can close early.
  - An outing with fewer than 3 people going at close time is cancelled ("not enough people"
    (không đủ quân)) (`MIN_PEOPLE`).
  - Tie-break: the venue not visited for the longest time wins; never-visited venues rank first.
  - History: closed outings (date, venue, headcount) and how many times each venue was visited.
- **Out of the product (SRC-1 §Ngoài phạm vi):** login, permissions, multiple teams, bill
  splitting, booking through a venue's app, Slack/email notifications, maps, a separate mobile UI.

## 6. Business rules and data entities
- BR-01: Only a person marked Going may vote (SRC-1 §M1).
- BR-02: Each person has at most one vote per outing (SRC-1 §M1 "vote 1 quán").
- BR-03: A vote may be changed while the outing is open (SRC-1 §M1). In M1 an outing is always open; the deadline is informational (Q-01).
- BR-04: Default seating time 18:30; default decision deadline 16:00 (`DEFAULT_CLOSE_AT`) (SRC-1 §M1, §Kỹ thuật).
- BR-05: The organiser chooses which venues are on the outing's ballot (SRC-1 §Người dùng, §M1).
- BR-06: A person's identity is the name entered once and remembered by cookie (SRC-1 §Người dùng).
- BR-07: Changing from Going to Not going removes the person's vote (Q-05).
- BR-08: Only the organiser may edit or cancel an outing (Q-06). The organiser is recognised only by the creator's cookie; if it is lost, the organiser controls are lost, with no recovery in M1 (Q-18).
- BR-09: Tie on the highest vote count: the venue that reached that count first is the leading venue (Q-04, Q-16). The M2 tie-break replaces it later.
- BR-10: An outing's date is today or later (default today, Vietnam time); its decision deadline is before its seating time (Q-08). The same rules apply when the organiser edits (Q-20).
- BR-11: A venue needs only a name; address, Google Maps link and notes are optional; notes are free text (Q-09).
- BR-12: An outing has at least one venue on its ballot (Q-12).
- BR-13: A cancelled outing accepts no responses or votes and is not listed on the home page (Q-17). Cancelling is final: no edit or restore (Q-19).
- BR-14: Votes are public: each venue shows the names of who voted for it (Q-11).
- BR-15: The creator of an outing starts as Going, with no vote yet, and can change it like anyone else (Q-13).
- Entities:
  - `Venue` (quán): name, address, Google Maps link, notes.
  - `Outing` (kèo): date, seating time (giờ ngồi), decision deadline (giờ chốt), organiser
    (chủ kèo), ballot venues, shareable link, cancelled flag.
  - `Participant`: display name (cookie identity); per outing: response Going / Not going (Đi / Không đi).
  - `Vote` (phiếu): participant, outing, venue; one per participant per outing.

## 7. Gaps (missing information)
- G-01: Who may add venues, and can venues be edited or removed? → Q-02 (resolved: anyone adds; no edit/delete)
- G-02: How users find an outing other than through the shared link (home page, list of outings)? → Q-03 (resolved: FR-11)
- G-03: Can the organiser edit or cancel an outing after creating it? → Q-06 (resolved: FR-12, FR-13)
- G-04: What happens to a vote when a person changes from Going to Not going? → Q-05 (resolved: FR-14)
- G-05: Language of the user interface. → Q-07 (resolved: Vietnamese, NFR-10)
- G-06: Which venue fields are required, and are notes free text or predefined tags? → Q-09 (resolved: BR-11)
- G-07: Expected `/healthz` behaviour when the database is down (status code) is not stated; only the success case is. → Q-14 (resolved: 503, FR-10)
- G-08: Rules for the outing date (today only, future dates, past dates) and for the relation between deadline and seating time. → Q-08 (resolved: BR-10)
- G-09: Minimum number of venues on an outing's ballot. → Q-12 (resolved: BR-12)
- G-10: What a cancelled outing shows, whether it still accepts responses, and whether it stays on the home page list. → Q-17 (resolved: FR-13, BR-13)
- G-11: Exact interim rule for picking one leading venue on a tie (Q-04 gave it only as an example). → Q-16 (resolved: BR-09)
- G-12: Whether a cancelled outing can be restored or edited. → Q-19 (resolved: final, BR-13)
- G-13: Whether the creation date/time rules also apply when the organiser edits. → Q-20 (resolved: yes, BR-10)

## 8. Ambiguities (more than one reading)
- AMB-01: M1 says a vote can be changed "while the outing is still open" (khi kèo còn mở), but
  closing is only defined in M2. Readings: (a) in M1 an outing is always open, nothing is
  enforced at the deadline, the deadline is only displayed; (b) M1 already blocks changes after
  the deadline, and M2 only adds cancellation, early close and the rest. → Q-01 (resolved: reading (a))
- AMB-02: "Leading venue" (quán đang dẫn) when two or more venues have the same top count; the
  tie-break rule is M2. Readings: (a) show all tied venues as leading; (b) show no leader;
  (c) apply the M2 tie-break already. → Q-04 (resolved: pick one by a simple rule; exact rule → Q-16)
- AMB-03: "Who is going" (ai đi): show only Going people, or also who said Not going and who has
  not answered; and whether individual votes are visible. → Q-11 (resolved: Going and Not going lists; public votes)
- AMB-04: Does the organiser automatically count as Going when creating the outing? → Q-13 (resolved: yes, BR-15)

## 9. Conflicts (sources disagree)
- None between SRC-1 and SRC-2. Note only: AMB-01 is an internal tension in SRC-1 (M1 "khi kèo
  còn mở" vs M2 "Kèo tự chốt đúng giờ chốt").

## 10. Assumptions (provisional until confirmed)
- A-01: A user is asked for a name the first time they act (e.g. create, respond or vote) and
  can change it later; two people with the same name are allowed and distinguished only by
  cookie. → Q-10 (confirmed: FR-01, FR-15)
- A-02: There is one shared space for everybody using the deployment (no teams, per §Ngoài
  phạm vi); all venues and outings are visible to anyone with the URL. Supported by Q-03 (the
  home page lists all today's and upcoming outings); no separate question needed.
- A-03: The outing page shows the current state when loaded or refreshed; live auto-update is
  not required. → Q-15 (confirmed: NFR-12)
- A-04: The organiser role is tied to the creator's cookie; if the cookie is lost, the
  organiser role is lost (no recovery, since there is no login). → Q-18 (confirmed: BR-08)
- A-05: The single web UI must work on phone browsers, because links are opened from chat. → Q-15 (confirmed: NFR-11)

No unconfirmed assumptions remain.

## 11. Risks and external dependencies
- R-01: Cookie-only identity: anyone can pick any name and impersonate another person, and a
  cleared cookie or a second device creates a second participant (accepted trade-off of
  "no accounts", SRC-1 §Người dùng).
- R-02: Railway hosting with two environments and a database each (SRC-1 §Kỹ thuật); deployment
  depends on the Railway project being available.
- R-03: AMB-01 was resolved as reading (a) (Q-01), so M2 must later add deadline enforcement
  to behaviour that users have already seen as unrestricted.
- R-04: Google Maps links are optional and stored as given (Q-09); a wrong link is only
  noticed by the people who click it.
- R-06: Duplicate display names are allowed (Q-10), so two people with the same name look
  identical in the Going/Not going lists and voter names.
- R-05: Organiser edits after people have responded (e.g. changing the date) may surprise
  members who already answered; no notifications exist (out of scope), so they see the change
  only when they open the outing.
