# Issue 12 Summary

## What Was Implemented

Added `--no-telemetry` flag to install.sh that allows users to opt out of telemetry at install time, plus a post-install disclaimer when telemetry is enabled.

## Changes Made
- `install.sh`:
  - Added `--no-telemetry` flag to argument parsing
  - Added check for existing `TSUKU_NO_TELEMETRY` environment variable
  - Added `TELEMETRY_NOTICE_FILE` variable for marker file path
  - Added conditional append of `export TSUKU_NO_TELEMETRY=1` to env file
  - Added telemetry disclaimer printed to stderr when telemetry enabled
  - Added marker file creation when disclaimer is shown

## Key Decisions
- **Disclaimer wording**: Used exact wording from DESIGN-telemetry-cli.md for consistency
- **Marker file path**: Used `~/.tsuku/telemetry_notice_shown` as specified in design
- **stderr for disclaimer**: Keeps disclaimer separate from normal output, matches CLI behavior
- **Respect env var**: If `TSUKU_NO_TELEMETRY` is already set, treat as if `--no-telemetry` was passed

## Trade-offs Accepted
- **Always shows disclaimer**: Even on reinstall, disclaimer appears if telemetry enabled (marker file only prevents CLI from showing it)

## Test Coverage
- CI: ShellCheck validation
- CI: Integration tests on Linux and macOS

## Known Limitations
- Marker file is created even if CLI is not yet installed (harmless)
- Disclaimer appears on every install without `--no-telemetry` (intentional transparency)

## Future Improvements
- Could check if marker file exists before showing disclaimer
