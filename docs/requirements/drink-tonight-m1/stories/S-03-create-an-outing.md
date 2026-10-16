# S-03: Create an outing and get its link

- **Priority:** P0
- **Covers:** FR-01, FR-04, FR-05 · **Decisions:** Q-08, Q-10, Q-12, Q-13, Q-18
- **Depends on stories:** S-02

## User story
As an organiser (chủ kèo), I want to create an outing (kèo) with a date, times and the venues to vote on, and get a link to share in chat, so that the team has one place to decide tonight's plan.

## Acceptance criteria
1. **Reach the form with defaults**
   - Given I am on the home page
   - When I press the "create outing" button
   - Then I see a form with date defaulting to today (Vietnam time), seating time (giờ ngồi) 18:30, decision deadline (giờ chốt) 16:00, and the venue list to choose from
2. **Asked for my name the first time**
   - Given my browser has no saved name
   - When I submit the create form
   - Then I am asked for my name once, and after giving it the outing is created; on later actions in the same browser I am not asked again
3. **Outing created with its own link**
   - Given I chose a date, times and at least one venue
   - When I submit the form
   - Then I land on the new outing's page, which has its own link to copy into chat and shows the date, seating time, decision deadline and the ballot venues
4. **I am Going automatically**
   - Given I just created an outing
   - When I look at its page
   - Then I am listed as Going (without a vote yet) and the number of people going is 1
5. **Invalid outings are refused**
   - Given the create form
   - When I submit a date before today, or a decision deadline that is not before the seating time, or no venue selected
   - Then no outing is created and I see a message in Vietnamese explaining which rule failed

## Out of scope
- Responding and voting (S-04, S-05); leading venue (S-07).
- The list of outings on the home page (S-08).
- Editing or cancelling (S-09, S-10).

## Notes
- The creator becomes the organiser, recognised only by this browser's cookie (Q-18).
- Duplicate names are allowed (Q-10).
- The default deadline comes from the configured `DEFAULT_CLOSE_AT` (16:00) (NFR-06).
- In M1 the deadline is only displayed; nothing locks when it passes (Q-01).
- A single-venue ballot is valid ("are you coming?") (Q-12).
