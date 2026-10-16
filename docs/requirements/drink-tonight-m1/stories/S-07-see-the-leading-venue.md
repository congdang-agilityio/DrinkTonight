# S-07: See the leading venue

- **Priority:** P1
- **Covers:** FR-09 · **Decisions:** Q-04, Q-16
- **Depends on stories:** S-05

## User story
As an organiser, I want the outing page to show one leading venue (quán đang dẫn), so that I know where to book a table.

## Acceptance criteria
1. **Single clear leader**
   - Given venue A has 3 votes and venue B has 1
   - When anyone opens the outing page
   - Then A is shown as the leading venue
2. **Tie: first to reach the count leads**
   - Given A reached 2 votes before B reached 2 votes, and both now have 2
   - When anyone opens the outing page
   - Then A is shown as the only leading venue
3. **Leader follows vote changes**
   - Given A was leading
   - When votes change so that B has strictly more votes than A
   - Then B is shown as the leading venue
4. **No votes yet**
   - Given no one has voted on the outing
   - When anyone opens the outing page
   - Then no leading venue is shown

## Out of scope
- The M2 tie-break (venue not visited for the longest wins) and visit history.

## Notes
- BR-09. Two interpretations to confirm at GATE 2:
  - AC 4 (no leader with zero votes) is a display detail not asked explicitly.
  - "Reached that count first" uses the moment each venue most recently reached its current
    count: if A drops from 2 to 1 and later returns to 2 after B reached 2, B leads.
