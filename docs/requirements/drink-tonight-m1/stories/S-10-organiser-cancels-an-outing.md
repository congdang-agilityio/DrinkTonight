# S-10: Organiser cancels an outing

- **Priority:** P2
- **Covers:** FR-13, FR-11 · **Decisions:** Q-06, Q-17, Q-18, Q-19
- **Depends on stories:** S-08, S-09

## User story
As an organiser, I want to cancel my outing, so that nobody keeps planning for an evening that is not happening.

## Acceptance criteria
1. **Only the organiser can cancel**
   - Given an outing created in another browser
   - When I open its page
   - Then I see no cancel option, and a cancel attempt from my browser is refused
2. **Cancelled outing is marked**
   - Given I am the organiser
   - When I cancel the outing from its page
   - Then the outing page shows that it is cancelled (đã huỷ)
3. **No responses or votes after cancelling**
   - Given an outing is cancelled
   - When anyone tries to respond Going/Not going or vote
   - Then nothing is recorded and the page offers no way to respond or vote
4. **Hidden from the home page**
   - Given an outing is cancelled
   - When anyone opens the home page
   - Then the outing is not listed
5. **Cancelling is final**
   - Given an outing is cancelled
   - When the organiser opens its page
   - Then there is no option to edit or restore it

## Out of scope
- Automatic cancellation for fewer than 3 people (M2).
- Restoring a cancelled outing (Q-19).

## Notes
- The cancelled outing's link still opens its page (Q-17 option A, not deletion).
