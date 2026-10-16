# Stories: Drink Tonight, M1 "Tonight's outing" (Kèo tối nay)

- Slug: `drink-tonight-m1` · PRD: `prd.md` · Requirements signed off 2026-10-16 by Cong Dang
- Story AC limit (`limits.story_max_ac`): 5

## Stories
| ID | Title | Priority | ACs | Covers |
|---|---|---|---|---|
| S-01 | Health check for the hosting platform | P0 | 3 | FR-10 |
| S-02 | Browse and add venues | P0 | 5 | FR-02, FR-03 |
| S-03 | Create an outing and get its link | P0 | 5 | FR-01, FR-04, FR-05 |
| S-04 | Say whether I am going | P0 | 5 | FR-01, FR-06, FR-08, FR-09 |
| S-05 | Vote for a venue | P0 | 5 | FR-07, FR-08, FR-09 |
| S-06 | My vote is removed when I am not going | P1 | 3 | FR-14 |
| S-07 | See the leading venue | P1 | 4 | FR-09 |
| S-08 | See today's and upcoming outings on the home page | P1 | 4 | FR-11 |
| S-09 | Organiser edits an outing | P2 | 5 | FR-12 |
| S-10 | Organiser cancels an outing | P2 | 5 | FR-13, FR-11 |
| S-11 | Change my display name | P2 | 5 | FR-15, FR-01 |

## FR → Story traceability
| FR | Stories |
|---|---|
| FR-01 | S-03, S-04, S-11 |
| FR-02 | S-02 |
| FR-03 | S-02 |
| FR-04 | S-03 |
| FR-05 | S-03 |
| FR-06 | S-04 |
| FR-07 | S-05 |
| FR-08 | S-04, S-05 |
| FR-09 | S-04, S-05, S-07 |
| FR-10 | S-01 |
| FR-11 | S-08, S-10 |
| FR-12 | S-09 |
| FR-13 | S-10 |
| FR-14 | S-06 |
| FR-15 | S-11 |

Cross-cutting NFRs, applying to every story: NFR-01..NFR-09 (stakeholder technical
constraints), NFR-10 (Vietnamese-only UI), NFR-11 (works on phone browsers), NFR-12 (no live
auto-update; refresh shows current state).

## How users reach each screen
| Screen | Way in | Story providing it |
|---|---|---|
| Home page | App root address | S-02 (created), S-03 (create button), S-08 (outing list) |
| Venue list | Link on the home page | S-02 |
| Create outing form | "Create outing" button on the home page | S-03 |
| Outing page | Its own link (chat), redirect after creating, home page list | S-03, S-08 |
| Edit outing | Edit option on the outing page (organiser only) | S-09 |
| Change name | Current name shown on every page | S-11 |

## Size self-check
| Story | ACs | ≤ limit? | Split pattern used |
|---|---|---|---|
| S-01 | 3 | yes | channel (operator endpoint) |
| S-02 | 5 | yes | CRUD: read + create only |
| S-03 | 5 | yes | workflow: create happy path with validation |
| S-04 | 5 | yes | workflow: respond |
| S-05 | 5 | yes | workflow: vote |
| S-06 | 3 | yes | business rule (vote removal) |
| S-07 | 4 | yes | business rule (leader and tie) |
| S-08 | 4 | yes | simple version first (listing, cancelled filter added by S-10) |
| S-09 | 5 | yes | role (organiser) + CRUD update |
| S-10 | 5 | yes | role (organiser) + workflow (cancel) |
| S-11 | 5 | yes | CRUD update (identity) |

## To confirm at GATE 2 (interpretations, no new scope)
- S-07 AC 4: no leading venue is shown while there are no votes.
- S-07 Notes: "reached that count first" uses the moment each venue most recently reached its current count.
- S-11 AC 3: the person's current name is shown everywhere, including earlier outings.
