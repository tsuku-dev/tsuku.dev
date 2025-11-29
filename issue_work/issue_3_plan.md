# Issue 3 Implementation Plan

## Summary

Create a GitHub Actions workflow that validates install.sh by running ShellCheck and actually executing the script on Linux and macOS.

## Approach

Follow the pattern from tsuku-dev/tsuku test.yml:
1. Run ShellCheck for static analysis
2. Execute install.sh on ubuntu-latest (Linux)
3. Execute install.sh on macos-latest (macOS)
4. Verify tsuku binary is installed and runnable

## Files to Modify
None

## Files to Create
- `.github/workflows/ci.yml` - CI workflow for install.sh validation

## Implementation Steps
- [ ] Create .github/workflows directory
- [ ] Create ci.yml with ShellCheck job
- [ ] Add Linux install test job (ubuntu-latest)
- [ ] Add macOS install test job (macos-latest)
- [ ] Verify installed binary works (tsuku --version)

## Testing Strategy
- CI will run on the PR itself, providing immediate validation

## Risks and Mitigations
- Risk: Install script downloads from GitHub releases which may rate limit. Mitigation: Use GITHUB_TOKEN for authenticated requests.
- Risk: Flaky network issues. Mitigation: GitHub-hosted runners have reliable connectivity.

## Success Criteria
- [ ] ShellCheck passes on install.sh
- [ ] Install script executes successfully on Linux
- [ ] Install script executes successfully on macOS
- [ ] Installed tsuku binary runs successfully

## Open Questions
None
