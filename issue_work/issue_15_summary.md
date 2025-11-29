# Issue 15 Summary

## What Was Implemented

A new GitHub Actions workflow that validates the quick-start examples shown on the landing page actually work and produce expected output.

## Changes Made
- `.github/workflows/quickstart-validation.yml`: New workflow that:
  - Runs on PRs modifying `index.html`
  - Runs daily at 06:00 UTC
  - Supports manual triggering
  - Installs tsuku via install script
  - Tests `tsuku install kubectl` with output validation
  - Tests `tsuku install terraform helm k6` with output validation
  - Tests `tsuku list` output contains all tools
  - Verifies installed tools are actually executable

## Key Decisions
- **Separate workflow**: Kept separate from ci.yml for clarity and independent scheduling
- **Version-agnostic validation**: Uses regex patterns like "Installed kubectl .* successfully" instead of exact version matches
- **Daily offset**: Runs at 06:00 UTC (offset from health-check at 00:00) to spread CI load
- **Tool executability test**: Added step to verify tools actually run, not just that tsuku reports success

## Trade-offs Accepted
- **Hardcoded commands**: Commands match landing page, need manual sync if page changes (but changes are rare)
- **Linux only**: Tests run on ubuntu-latest only (macOS would double CI time for minimal benefit)

## Test Coverage
- Validates all commands shown in quick-start section
- Verifies output patterns match expected format
- Confirms installed binaries are executable

## Known Limitations
- Version numbers in landing page examples will become stale (but that's a docs issue, not this workflow's concern)
- Single platform testing (Linux only)

## Future Improvements
- Could extract commands from HTML programmatically if landing page changes frequently
