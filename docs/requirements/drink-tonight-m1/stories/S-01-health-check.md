# S-01: Health check for the hosting platform

- **Priority:** P0
- **Covers:** FR-10 · **Decisions:** Q-14
- **Depends on stories:** none

## User story
As an operator, I want a health address that reports whether the app and its database are working, so that the hosting platform and monitoring can tell when the app is unhealthy.

## Acceptance criteria
1. **Healthy app and database**
   - Given the app is running and its database is reachable
   - When `GET /healthz` is requested
   - Then the response status is 200
2. **Database not reachable**
   - Given the app is running but its database is not reachable
   - When `GET /healthz` is requested
   - Then the response status is 503 (Service Unavailable)
3. **No name needed**
   - Given a request without any cookie
   - When `GET /healthz` is requested
   - Then it is answered as in AC 1 or 2, without asking for a name

## Out of scope
- Any user-facing page (other stories).
- Monitoring dashboards or alerts.

## Notes
- Source: README §M1 ("`GET /healthz` trả `200` khi app và database đều chạy").
- Stakeholder constraints apply to the whole epic (NFR-01..NFR-09): Node.js 22, TypeScript,
  Hono, server-rendered HTML, PostgreSQL with migrations before start, Vitest, Railway
  staging/production, configuration by environment variables.
