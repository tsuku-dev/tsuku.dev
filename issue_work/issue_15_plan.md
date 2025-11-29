# Issue 15 Implementation Plan

## Summary

Add a new workflow that validates the quick-start commands shown on the landing page, running both on PR (when index.html changes) and daily to catch upstream breakages.

## Approach

Create a new workflow file `quickstart-validation.yml` that:
1. Installs tsuku via the install script
2. Runs the same commands shown in the quick-start section
3. Validates output patterns (not exact version numbers)

Use path filtering to only run on PRs that modify index.html, but always run daily.

### Alternatives Considered
- **Add to existing ci.yml**: Would make ci.yml too complex; separate workflow is cleaner
- **Parse HTML to extract commands**: Over-engineered; commands are stable, just hardcode them

## Files to Modify
- None

## Files to Create
- `.github/workflows/quickstart-validation.yml` - New workflow for quick-start validation

## Implementation Steps
- [x] Create workflow with PR trigger (path filter for index.html)
- [x] Add daily schedule trigger
- [x] Add manual trigger for testing
- [x] Install tsuku using install script
- [x] Run `tsuku install kubectl` and validate output
- [x] Run `tsuku install terraform helm k6` and validate output
- [x] Run `tsuku list` and validate output

## Testing Strategy
- Push to branch and verify workflow runs
- Verify output pattern matching works
- Test manual trigger

## Risks and Mitigations
- **GitHub rate limiting**: Use GITHUB_TOKEN for authenticated requests
- **Slow tool downloads**: Set reasonable timeout, use continue-on-error for non-critical tools
- **Flaky network**: Retry logic if needed

## Success Criteria
- [ ] Workflow runs on PRs modifying index.html
- [ ] Workflow runs daily at scheduled time
- [ ] Commands execute successfully
- [ ] Output patterns validated (version-agnostic)
- [ ] Failures produce visible alerts

## Open Questions
None
