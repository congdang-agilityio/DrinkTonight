# S-05: Vote for a venue

- **Priority:** P0
- **Covers:** FR-07, FR-08, FR-09 · **Decisions:** Q-01, Q-11
- **Depends on stories:** S-04

## User story
As a member who is Going, I want to vote for one venue on the outing's ballot and change my vote, so that the team can see where most people want to go.

## Acceptance criteria
1. **Vote as a Going person**
   - Given I am Going on an outing with venues A and B
   - When I vote for A
   - Then A's vote count increases by 1 and my name is listed next to A
2. **Change my vote**
   - Given I voted for A
   - When I vote for B
   - Then A's count decreases by 1, B's count increases by 1, and my name moves from A to B; I never have more than one vote
3. **Only Going people can vote**
   - Given I have not responded or I am Not going
   - When I try to vote
   - Then no vote is recorded and I see a message in Vietnamese that only people who are going can vote
4. **Still possible after the deadline**
   - Given the decision deadline has passed
   - When a Going person votes or changes their vote
   - Then the vote is saved as normal
5. **Vote counts visible to everyone**
   - Given votes exist on an outing
   - When anyone opens the outing page
   - Then each ballot venue shows its vote count and the names of who voted for it

## Out of scope
- Removing the vote when switching to Not going (S-06).
- Showing the leading venue (S-07).

## Notes
- Votes are public (Q-11).
- Only venues on this outing's ballot can be voted for.
