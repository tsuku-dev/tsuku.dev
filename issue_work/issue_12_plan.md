# Issue 12 Implementation Plan

## Summary

Add `--no-telemetry` flag to install.sh that persists opt-out in the env file, and print a disclaimer when telemetry is enabled.

## Approach

Extend the existing argument parsing to handle `--no-telemetry`. When used, add `export TSUKU_NO_TELEMETRY=1` to the env file. When not used (and env var not already set), print the disclaimer to stderr and create the marker file.

### Alternatives Considered
- **Config file instead of env file**: More complex, env file already exists and is sourced
- **Prompt during install**: Non-interactive install is important for scripting

## Files to Modify
- `install.sh` - Add flag parsing, env file modification, disclaimer printing

## Files to Create
- None

## Implementation Steps
- [x] Add --no-telemetry to argument parsing
- [x] Check for existing TSUKU_NO_TELEMETRY environment variable
- [x] Add TSUKU_NO_TELEMETRY=1 to env file when flag used or env var set
- [x] Print disclaimer to stderr when telemetry enabled (no flag, no env var)
- [x] Create marker file when disclaimer shown

## Testing Strategy
- Manual: Run with --no-telemetry, verify env file contains export
- Manual: Run without flag, verify disclaimer printed to stderr
- Manual: Set TSUKU_NO_TELEMETRY=1 before running, verify no disclaimer
- CI: ShellCheck validation

## Risks and Mitigations
- **Marker file path**: Use same path as CLI design (~/.tsuku/telemetry_notice_shown)
- **stderr vs stdout**: Use >&2 for disclaimer to not interfere with piping

## Success Criteria
- [ ] --no-telemetry flag accepted
- [ ] Flag adds export to env file
- [ ] Disclaimer printed when flag not used
- [ ] Marker file created when disclaimer shown
- [ ] Respects existing TSUKU_NO_TELEMETRY env var

## Open Questions
None - requirements are clear from issue and design doc.
