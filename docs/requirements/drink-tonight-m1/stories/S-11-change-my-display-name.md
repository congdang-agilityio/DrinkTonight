# S-11: Change my display name

- **Priority:** P2
- **Covers:** FR-15, FR-01 · **Decisions:** Q-10
- **Depends on stories:** S-04

## User story
As a member, I want to change the name the app remembers for me, so that I can fix a typo or use the name my team knows.

## Acceptance criteria
1. **Reach the name change**
   - Given my browser has a saved name
   - When I open any page
   - Then I see my current name with an option to change it
2. **Name changed**
   - Given I am changing my name
   - When I save a new, non-empty name
   - Then the app shows the new name and remembers it in this browser
3. **New name shown on my outings**
   - Given I responded or voted on outings before
   - When I change my name and open those outings
   - Then my new name appears in the Going/Not going lists and next to my vote
4. **Empty name refused**
   - Given I am changing my name
   - When I save an empty name
   - Then my name is not changed and I see a message in Vietnamese
5. **Duplicate names allowed**
   - Given another person already uses the name "Minh"
   - When I set my name to "Minh"
   - Then the change is accepted

## Out of scope
- Accounts or recovering an identity on another device (out of product scope).

## Notes
- AC 3 is an interpretation to confirm at GATE 2: the person's current name is shown
  everywhere, including earlier outings.
