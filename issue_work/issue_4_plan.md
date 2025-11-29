# Issue 4 Implementation Plan

## Summary

Create a scheduled GitHub Actions workflow that runs daily to verify the install endpoint is healthy.

## Approach

Create a simple workflow that:
1. Uses cron schedule to run daily
2. Fetches https://get.tsuku.dev/now with curl
3. Verifies HTTP 200 response
4. Verifies response body is non-empty

## Files to Modify
None

## Files to Create
- `.github/workflows/health-check.yml` - Scheduled health check workflow

## Implementation Steps
- [ ] Create health-check.yml with daily cron schedule
- [ ] Add curl command to fetch the endpoint
- [ ] Verify HTTP status code is 200
- [ ] Verify response body is non-empty
- [ ] Add workflow_dispatch for manual triggering

## Testing Strategy
- Manual trigger via workflow_dispatch to verify it works
- CI will validate the workflow syntax

## Risks and Mitigations
- Risk: Cron jobs may not run if no recent activity in repo. Mitigation: GitHub keeps scheduled workflows active for 60 days after last activity.

## Success Criteria
- [ ] Workflow runs on schedule (daily)
- [ ] Verifies HTTP 200 response
- [ ] Verifies non-empty response body
- [ ] Can be manually triggered

## Open Questions
None
