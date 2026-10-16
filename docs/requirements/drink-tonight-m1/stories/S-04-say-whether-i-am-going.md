# S-04: Say whether I am going

- **Priority:** P0
- **Covers:** FR-01, FR-06, FR-08, FR-09 · **Decisions:** Q-01, Q-10, Q-11
- **Depends on stories:** S-03

## User story
As a member (thành viên), I want to mark myself Going or Not going (Đi / Không đi) on an outing, so that the organiser knows how many people are coming.

## Acceptance criteria
1. **Asked for my name the first time**
   - Given I open an outing link and my browser has no saved name
   - When I choose Going or Not going
   - Then I am asked for my name once, and my response is saved under that name
2. **Mark Going**
   - Given I am on an outing page
   - When I choose Going
   - Then my name appears in the Going list and the number of people going increases by 1
3. **Mark Not going**
   - Given I am on an outing page
   - When I choose Not going
   - Then my name appears in the Not going list and not in the Going list
4. **Change my response**
   - Given I responded Going
   - When I choose Not going (or the reverse)
   - Then I appear only in the new list and the number of people going is updated
5. **Still possible after the deadline**
   - Given the outing's decision deadline has passed
   - When I choose Going or Not going
   - Then my response is saved as normal

## Out of scope
- Voting (S-05); what happens to a vote when switching to Not going (S-06).
- Closing at the deadline (M2).
- Live updates: other people see the change when they load or refresh the page (NFR-12).

## Notes
- Viewing an outing needs no name; only acting does (Q-10).
- One response per person (browser cookie) per outing.
- The Going and Not going lists are both shown (Q-11).
