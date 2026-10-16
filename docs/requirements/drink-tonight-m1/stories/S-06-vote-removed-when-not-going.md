# S-06: My vote is removed when I am not going

- **Priority:** P1
- **Covers:** FR-14 · **Decisions:** Q-05
- **Depends on stories:** S-05

## User story
As an organiser, I want a person's vote to be removed when they switch to Not going, so that the vote counts only reflect people who are actually coming.

## Acceptance criteria
1. **Vote removed on switching to Not going**
   - Given I am Going and voted for venue A
   - When I change my response to Not going
   - Then A's count decreases by 1 and my name is no longer listed next to A
2. **Must vote again after switching back**
   - Given I switched from Going to Not going after voting
   - When I change back to Going
   - Then I have no vote until I vote again
3. **Creator follows the same rule**
   - Given I created the outing and voted
   - When I change to Not going
   - Then my vote is removed as in AC 1

## Out of scope
- Any other effect of responses (S-04).

## Notes
- BR-07.
