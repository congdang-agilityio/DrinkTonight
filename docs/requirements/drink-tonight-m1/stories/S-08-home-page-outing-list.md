# S-08: See today's and upcoming outings on the home page

- **Priority:** P1
- **Covers:** FR-11 · **Decisions:** Q-03, Q-17
- **Depends on stories:** S-03

## User story
As a member, I want the home page to list today's and upcoming outings, so that I can find an outing even without its chat link.

## Acceptance criteria
1. **Today's and upcoming outings listed**
   - Given outings exist for today and for future dates
   - When I open the home page
   - Then each one is listed with its date and seating time, ordered by date and seating time, soonest first
2. **Past outings not listed**
   - Given an outing whose date is before today (Vietnam time)
   - When I open the home page
   - Then it is not in the list
3. **Open an outing from the list**
   - Given the home page lists an outing
   - When I select it
   - Then I land on that outing's page
4. **Empty list**
   - Given there are no outings for today or later
   - When I open the home page
   - Then I see a message in Vietnamese that there are no outings yet, and the "create outing" button

## Out of scope
- Hiding cancelled outings (S-10).
- History of past outings (M2).

## Notes
- "Today" uses Vietnam time (`Asia/Ho_Chi_Minh`, NFR-07).
- Everyone sees the same list (one shared space).
