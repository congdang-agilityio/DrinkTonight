# S-02: Browse and add venues

- **Priority:** P0
- **Covers:** FR-02, FR-03 · **Decisions:** Q-02, Q-07, Q-09, Q-15
- **Depends on stories:** none

## User story
As a member, I want to see the team's list of venues (quán) and add a new one, so that it can be put on an outing's ballot later.

## Acceptance criteria
1. **Reach the venue list from the home page**
   - Given I open the app's home page
   - When I follow the link to the venue list
   - Then I see the venue list page, with every venue added so far showing its name and, when given, its address, Google Maps link and notes
2. **Add a venue with only a name**
   - Given I am on the venue list page
   - When I submit a new venue with the name "Bia Hơi Hà Nội" and leave address, Google Maps link and notes empty
   - Then the venue appears in the list with that name
3. **Add a venue with all details**
   - Given I am on the venue list page
   - When I submit a venue with name, address, a Google Maps link and the note "có chỗ để xe, bia tươi"
   - Then the venue appears with its address, a clickable Google Maps link and the note as written
4. **Name is required**
   - Given I am on the venue list page
   - When I submit a new venue with an empty name
   - Then no venue is added and I see a message in Vietnamese that the name is required
5. **No edit or delete**
   - Given venues exist in the list
   - When I look at the venue list
   - Then there is no way to edit or delete a venue

## Out of scope
- Editing or deleting venues (Q-02).
- Validating that a Google Maps link really points to Google Maps (R-04).
- The outing list and create button on the home page (S-03, S-08).

## Notes
- This story creates the home page with at least a link to the venue list; S-03 adds the
  "create outing" button and S-08 adds the list of outings.
- Anyone can add a venue; no name prompt is required for this action (Q-10 names the actions
  create, respond and vote).
- All text in Vietnamese (NFR-10); pages work on phone browsers (NFR-11).
