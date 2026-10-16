# How I understand Drink Tonight M1 (final, for sign-off)

**What it is.** A small web app, with all screens in Vietnamese, that turns "drinks tonight?"
in chat into an outing (kèo): a date, a seating time, a decision deadline, a short list of
venues to vote on, and a clear headcount, so the organiser knows how many people are coming
and where to book. It must work well on phones; refreshing a page shows the latest state
(no live auto-update).

**Who uses it.** No accounts. Anyone can look at pages without a name. The first time you do
something (create an outing, respond, vote) the app asks your name and remembers it with a
cookie; you can change it later, and two people may use the same name. The person who creates
an outing is its organiser (chủ kèo), recognised only by that browser's cookie: if it is lost,
the organiser controls are lost, and that is accepted for M1. Everyone shares one space.

**What M1 includes.**
- **Home page:** lists today's and upcoming outings (not cancelled ones), with a button to
  create a new one.
- **Venue list (quán):** anyone can add a venue. Only the name is required; address, Google
  Maps link and free-text notes ("has parking", "draft beer") are optional. Venues cannot be
  edited or deleted in M1.
- **Create an outing:** date (today or later, default today), seating time (default 18:30),
  decision deadline (default 16:00, must be before the seating time), and at least one venue
  on the ballot. The outing gets its own link to paste into chat. The creator is automatically
  Going (without a vote yet) and can change that.
- **Organiser controls:** change the date and both times (same rules as creating), add more
  venues to the ballot (not remove them), and cancel. Cancelling is final: the outing shows
  "cancelled" (đã huỷ), accepts no more responses or votes, cannot be edited or restored, and
  disappears from the home page.
- **Responding:** each person says Going or Not going (Đi / Không đi). Only people who are
  Going vote, for one venue, and can change their vote. Switching to Not going removes the
  vote; coming back to Going means voting again.
- **No closing in M1:** the decision deadline is only shown. People can keep responding and
  voting after it. Closing comes in M2.
- **Outing page:** how many are going, who is Going and who is Not going, votes per venue with
  the names of who voted, and one leading venue. On a tie, the venue that reached that count
  first leads.
- **Health check** (`/healthz`): 200 when the app and database are up, 503 when the database
  is not reachable.
- Technical constraints from the README (Node 22, TypeScript, Hono, server-rendered pages,
  PostgreSQL with migrations before start, Vitest, Railway staging and production each with
  its own database, configuration by environment variables, Vietnam time zone) are recorded
  as given.

**Not in M1 (planned for M2 "Game rules" (Luật chơi)).** Automatic close at the deadline, early
close by the organiser, cancelling outings with fewer than 3 people, tie-break by the venue not
visited for the longest, and history of past outings and venue visits.

**Never in scope.** Login, permissions, multiple teams, bill splitting, booking through a
venue's app, Slack/email notifications, maps, a separate mobile app.

**Still assumed.** Nothing: all 20 questions are answered and confirmed. Accepted risks: names
can be impersonated or duplicated (no accounts), and a lost cookie means losing the organiser
role.
