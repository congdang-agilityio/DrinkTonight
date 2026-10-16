# Clarifying questions: Drink Tonight, M1 "Tonight's outing" (Kèo tối nay)

- Slug: `drink-tonight-m1`
- Open: 0 · Answered: 0 · Confirmed: 20 · Deferred: 0
- Next batch to ask: none (requirements clear; ready for GATE 1)

Rules: the PM asks each question **verbatim** (translation allowed, no rephrasing, merging or
answering) and records the answer verbatim plus an English translation. Only the BA changes a
status to `confirmed` or `deferred`.

---

### Q-01: What happens at the decision deadline in M1?
- **Question:** The README says people can change their vote "while the outing is still open", but automatic closing at the decision deadline (giờ chốt) is listed under M2. In M1, what should happen when the decision deadline passes?
- **Why it matters:** It decides whether M1 must block changes after the deadline or only display the time; this shapes several stories and how M2 builds on M1.
- **Related:** FR-08, BR-03, AMB-01, R-03
- **Options:**
  - A) Nothing happens in M1: the deadline is only shown; people can keep responding and voting. Closing comes in M2.
  - B) M1 already locks the outing after the deadline (no more Going/Not going or vote changes); M2 adds cancellation, early close, tie-break and history.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Nothing happens in M1: the deadline is only shown; people can keep responding and voting. Closing comes in M2.
- **Status:** confirmed
- **BA note:** Applied: AMB-01 resolved; FR-08 and BR-03 updated (in M1 an outing is always open, the deadline is displayed only). R-03 kept for M2.

### Q-02: Who can manage the venue list?
- **Question:** Who can add venues to the list, and should venues also be editable or removable?
- **Why it matters:** Decides who sees the "add venue" function and whether edit/delete features are in M1.
- **Related:** FR-02, FR-03, G-01
- **Options:**
  - A) Anyone can add; nobody can edit or delete in M1.
  - B) Anyone can add, edit and delete.
  - C) Anyone can add; only the person who added a venue can edit or delete it.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Anyone can add; nobody can edit or delete in M1.
- **Status:** confirmed
- **BA note:** Applied: G-01 resolved; FR-03 states anyone can add; editing and deleting venues added to "Out of this slug".

### Q-03: How do people find an outing?
- **Question:** Besides the link shared in chat, should the app's home page list outings so people can find them?
- **Why it matters:** Decides what the home page shows and how users reach each screen.
- **Related:** FR-05, G-02, A-02
- **Options:**
  - A) Yes: the home page lists today's and upcoming outings, with a button to create one.
  - B) No: the home page only has "create an outing" and the venue list; outings are reached only by their link.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Yes: the home page lists today's and upcoming outings, with a button to create one.
- **Status:** confirmed
- **BA note:** Applied: G-02 resolved; new FR-11 (home page lists today's and upcoming outings, with a create button). How cancelled outings appear in this list is asked in follow-up Q-17.

### Q-04: Leading venue when votes are tied
- **Question:** In M1, if two or more venues have the same highest number of votes, what should the outing page show as the leading venue?
- **Why it matters:** The tie-break rule ("venue not visited for the longest wins") is in M2 and needs visit history that M1 does not have.
- **Related:** FR-09, AMB-02
- **Options:**
  - A) Show all tied venues as joint leaders.
  - B) Show "tied" and no single leader.
  - C) Pick one by a simple rule for now (for example, the one that reached that count first).
  - D) Other (please describe)
- **Answer (original):** C
- **Answer (English):** Option C: Pick one by a simple rule for now (for example, the one that reached that count first).
- **Status:** confirmed
- **BA note:** Applied: AMB-02 resolved in principle; FR-09 shows a single leading venue chosen by a simple interim rule. The option text gives the rule only as an example, so the exact rule is asked in follow-up Q-16.

### Q-05: Switching from Going to Not going after voting
- **Question:** If someone has voted and then changes to Not going, what happens to their vote?
- **Why it matters:** Only Going people may vote; the vote counts must stay consistent with the headcount.
- **Related:** FR-06, FR-07, BR-01, G-04
- **Options:**
  - A) The vote is removed; if they switch back to Going they vote again.
  - B) The vote is kept but not counted while they are Not going, and counts again if they switch back.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: The vote is removed; if they switch back to Going they vote again.
- **Status:** confirmed
- **BA note:** Applied: G-04 resolved; new FR-14 and BR-07 (switching to Not going removes the vote).

### Q-06: Can the organiser change or cancel an outing?
- **Question:** After creating an outing, can the organiser change it (date, times, venues on the ballot) or cancel it in M1?
- **Why it matters:** Decides whether M1 needs edit and cancel functions and what happens to existing votes when a venue is removed.
- **Related:** FR-04, G-03, A-04
- **Options:**
  - A) No changes in M1: to fix a mistake, create a new outing.
  - B) The organiser can edit the date and times and add venues, and can cancel the outing.
  - C) The organiser can edit everything including removing venues (votes for a removed venue are cleared), and can cancel.
  - D) Other (please describe)
- **Answer (original):** B
- **Answer (English):** Option B: The organiser can edit the date and times and add venues, and can cancel the outing.
- **Status:** confirmed
- **BA note:** Applied: G-03 resolved; new FR-12 (edit date, seating time, deadline; add ballot venues) and FR-13 (cancel). Removing ballot venues is out of scope. What a cancelled outing looks like is asked in follow-up Q-17; organiser identity by cookie (A-04) is asked in follow-up Q-18.

### Q-07: Language of the app
- **Question:** What language should the app's screens use?
- **Why it matters:** Affects every screen and every label written in the stories.
- **Related:** NFR-10, G-05
- **Options:**
  - A) Vietnamese only.
  - B) English only.
  - C) Both, user can switch.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Vietnamese only.
- **Status:** confirmed
- **BA note:** Applied: G-05 resolved; NFR-10 updated (all user-facing text in Vietnamese). Project artifacts stay in English.

### Q-08: Outing date and time rules
- **Question:** Which dates can an outing be created for, and must the decision deadline be before the seating time?
- **Why it matters:** Decides validation on the create form and the default date.
- **Related:** FR-04, G-08
- **Options:**
  - A) Today or a future date (default today); the deadline must be before the seating time.
  - B) Today only (it is "tonight's outing"); the deadline must be before the seating time.
  - C) Any date; no rule between the two times.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Today or a future date (default today); the deadline must be before the seating time.
- **Status:** confirmed
- **BA note:** Applied: G-08 resolved; FR-04 and BR-10 updated (date today or later, default today; deadline before seating time). Whether the same rules apply when the organiser edits is asked in follow-up Q-20.

### Q-09: Venue details
- **Question:** When adding a venue, which details are required, and are notes free text or chosen from a fixed list?
- **Why it matters:** Decides form validation and how notes are shown.
- **Related:** FR-03, G-06, R-04
- **Options:**
  - A) Only the name is required; address, Google Maps link and notes are optional; notes are free text.
  - B) Name and address are required; the rest optional; notes are free text.
  - C) Name required; notes are chosen from a fixed list (e.g. parking, draft beer) plus free text.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Only the name is required; address, Google Maps link and notes are optional; notes are free text.
- **Status:** confirmed
- **BA note:** Applied: G-06 resolved; FR-03 and BR-11 updated (only name required; notes free text). R-04 stays: links are stored as given.

### Q-10: Entering and changing your name
- **Question:** When should the app ask for a person's name, can they change it later, and is it OK if two people use the same name?
- **Why it matters:** Decides when the name prompt appears and how people are shown in lists.
- **Related:** FR-01, A-01, R-01
- **Options:**
  - A) Ask the first time they do something (create, respond, vote); they can change it later; duplicate names are allowed.
  - B) Ask on first visit to any page; name cannot be changed; duplicates allowed.
  - C) Ask the first time they do something; they can change it; a name already used in the same outing is refused.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Ask the first time they do something (create, respond, vote); they can change it later; duplicate names are allowed.
- **Status:** confirmed
- **BA note:** Applied: A-01 confirmed; FR-01 updated and new FR-15 (change name). Viewing pages needs no name.

### Q-11: What the outing page shows about people and votes
- **Question:** On the outing page, besides who is going, should it show who said Not going, and should it show who voted for which venue?
- **Why it matters:** Decides what is displayed and whether votes are public.
- **Related:** FR-09, AMB-03
- **Options:**
  - A) Show Going and Not going lists; votes are public (names next to each venue).
  - B) Show Going and Not going lists; votes show counts only.
  - C) Show only the Going list; votes show counts only.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Show Going and Not going lists; votes are public (names next to each venue).
- **Status:** confirmed
- **BA note:** Applied: AMB-03 resolved; FR-09 updated (Going and Not going lists; voter names shown per venue).

### Q-12: Minimum venues on an outing
- **Question:** How many venues must an outing have on its ballot?
- **Why it matters:** Decides validation when creating an outing.
- **Related:** FR-04, G-09
- **Options:**
  - A) At least 1 (a single venue just means "are you coming?").
  - B) At least 2.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: At least 1 (a single venue just means "are you coming?").
- **Status:** confirmed
- **BA note:** Applied: G-09 resolved; FR-04 and BR-12 updated (at least one ballot venue).

### Q-13: Is the organiser automatically going?
- **Question:** When someone creates an outing, should they automatically be marked as Going?
- **Why it matters:** Affects the headcount right after creation.
- **Related:** FR-04, FR-06, AMB-04
- **Options:**
  - A) Yes, automatically Going (they can change it).
  - B) No, they respond like everyone else.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Yes, automatically Going (they can change it).
- **Status:** confirmed
- **BA note:** Applied: AMB-04 resolved; FR-04 and BR-15 updated (creator starts as Going, without a vote, and can change it).

### Q-14: Health check when the database is down
- **Question:** The README says `/healthz` returns 200 when the app and the database are running. What should it return when the database is not reachable?
- **Why it matters:** The deployment platform and monitoring use this to tell if the app is healthy.
- **Related:** FR-10, G-07
- **Options:**
  - A) An error status (503 Service Unavailable).
  - B) Any non-200 status; the exact code does not matter.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: An error status (503 Service Unavailable).
- **Status:** confirmed
- **BA note:** Applied: G-07 resolved; FR-10 updated (503 when the database is not reachable).

### Q-15: Phones and live updates
- **Question:** Must the web pages work well on phone browsers, and should the outing page update by itself when others respond, or is refreshing the page enough?
- **Why it matters:** Links are opened from chat, usually on phones; live updates are significant extra work.
- **Related:** NFR-09, A-03, A-05
- **Options:**
  - A) Must work on phones; refreshing is enough.
  - B) Must work on phones; the page should update by itself.
  - C) Desktop is enough; refreshing is enough.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Must work on phones; refreshing is enough.
- **Status:** confirmed
- **BA note:** Applied: A-03 and A-05 confirmed; new NFR-11 (usable on phone browsers) and NFR-12 (no live auto-update; refresh shows the current state).

### Q-16: Which simple rule picks the leading venue on a tie?
- **Question:** You chose to pick one leading venue by a simple rule when votes are tied (follow-up to Q-04). Which rule should it be?
- **Why it matters:** The leading venue is what the organiser books; the rule must be fixed so everyone sees the same result.
- **Related:** FR-09, AMB-02, Q-04
- **Options:**
  - A) The venue that reached the tied count first.
  - B) The venue listed first on the outing's ballot.
  - C) Alphabetical order of venue name.
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: The venue that reached the tied count first.
- **Status:** confirmed
- **BA note:** Applied: G-11 and AMB-02 resolved; FR-09 and BR-09 updated (on a tie, the venue that reached the tied count first leads).

### Q-17: What does a cancelled outing look like?
- **Question:** When the organiser cancels an outing (follow-up to Q-06), what should people see, and can they still respond or vote?
- **Why it matters:** Decides what cancel does on the outing page and on the home page list of outings.
- **Related:** FR-11, FR-13, Q-03, Q-06
- **Options:**
  - A) The outing page shows "cancelled" and nobody can respond or vote; it disappears from the home page list.
  - B) The outing page shows "cancelled" and nobody can respond or vote; it stays in the home page list marked "cancelled".
  - C) The outing is deleted; its link shows "not found".
  - D) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: The outing page shows "cancelled" and nobody can respond or vote; it disappears from the home page list.
- **Status:** confirmed
- **BA note:** Applied: G-10 resolved; FR-13, FR-11 and BR-13 updated. Whether a cancellation can be undone or the outing edited afterwards is asked in follow-up Q-19.

### Q-18: Organiser who loses their browser cookie
- **Question:** Without accounts, the app recognises the organiser only by the cookie in the browser they used to create the outing. If they switch phone or clear their browser, they lose the ability to edit or cancel that outing. Is that acceptable?
- **Why it matters:** Edit and cancel (Q-06) are organiser-only; there is no login to recover the role.
- **Related:** FR-01, FR-12, FR-13, A-04, R-01
- **Options:**
  - A) Yes, acceptable for M1.
  - B) No: anyone with the outing link can edit and cancel it.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Yes, acceptable for M1.
- **Status:** confirmed
- **BA note:** Applied: A-04 confirmed; BR-08 updated (organiser recognised by the creator's cookie only; no recovery in M1).

### Q-19: Can a cancelled outing be restored?
- **Question:** Once the organiser cancels an outing (follow-up to Q-17), can it be restored or edited afterwards?
- **Why it matters:** Decides whether cancelling is final and whether the organiser still sees edit controls on a cancelled outing.
- **Related:** FR-12, FR-13, Q-17
- **Options:**
  - A) No: cancelling is final; a cancelled outing cannot be edited or restored.
  - B) Yes: the organiser can restore it, and it reappears on the home page with its earlier responses and votes.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: No: cancelling is final; a cancelled outing cannot be edited or restored.
- **Status:** confirmed
- **BA note:** Applied: G-12 resolved; FR-13 and BR-13 updated (cancelling is final; no edit or restore).

### Q-20: Date and time rules when the organiser edits
- **Question:** When the organiser edits an outing, do the same rules as at creation apply (date today or later; decision deadline before seating time)? (Follow-up to Q-08.)
- **Why it matters:** Decides validation on the edit form, and what happens to an outing whose date has already passed.
- **Related:** FR-04, FR-12, BR-10, Q-08
- **Options:**
  - A) Yes, the same rules apply when editing.
  - B) Only "deadline before seating time" applies; any date is allowed when editing.
  - C) Other (please describe)
- **Answer (original):** A
- **Answer (English):** Option A: Yes, the same rules apply when editing.
- **Status:** confirmed
- **BA note:** Applied: G-13 resolved; FR-12 and BR-10 updated (same date/time rules on create and edit).
