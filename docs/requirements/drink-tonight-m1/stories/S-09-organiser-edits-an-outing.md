# S-09: Organiser edits an outing

- **Priority:** P2
- **Covers:** FR-12 · **Decisions:** Q-06, Q-18, Q-20
- **Depends on stories:** S-03

## User story
As an organiser, I want to change my outing's date and times and add venues to its ballot, so that I can fix mistakes or widen the choice without starting over.

## Acceptance criteria
1. **Only the organiser can edit**
   - Given an outing created in another browser
   - When I open its page
   - Then I see no edit option, and an edit attempt from my browser is refused
2. **Edit date and times**
   - Given I am the organiser and open the edit option from the outing page
   - When I change the date, seating time or decision deadline and save
   - Then the outing page shows the new values, and existing responses and votes are unchanged
3. **Same rules as creating**
   - Given I am editing my outing
   - When I save a date before today or a decision deadline that is not before the seating time
   - Then nothing changes and I see a message in Vietnamese explaining which rule failed
4. **Add venues to the ballot**
   - Given I am editing my outing
   - When I add venues from the venue list and save
   - Then the new venues appear on the ballot with 0 votes and can be voted for
5. **Venues cannot be removed**
   - Given I am editing my outing
   - When I look at the ballot venues already on the outing
   - Then there is no way to remove them

## Out of scope
- Editing a cancelled outing (not allowed, S-10).
- Notifying people about changes (out of product scope).

## Notes
- The organiser is recognised only by the creator's browser cookie; losing it loses edit
  rights, accepted for M1 (Q-18).
