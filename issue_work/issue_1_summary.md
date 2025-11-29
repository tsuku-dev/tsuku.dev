# Issue 1 Summary

## What Was Implemented
Updated install.sh to use the correct binary naming pattern that matches goreleaser output.

## Changes Made
- `install.sh`: Changed BINARY_NAME from `tsuku-{os}-{arch}` to `tsuku-{os}-{arch}_{version}_{os}_{arch}`. Added VERSION variable that strips the `v` prefix from the git tag.

## Key Decisions
- Fixed install.sh rather than release workflow: The goreleaser naming pattern is standard, and this repo only controls the install script.

## Trade-offs Accepted
- Hardcoded naming pattern: If goreleaser config changes in the future, install.sh will need updating. This is acceptable as naming patterns rarely change.

## Test Coverage
- No automated tests (static website project)
- Manual verification: URL pattern matches actual release assets

## Known Limitations
- None

## Future Improvements
- Could add a fallback mechanism to try alternative naming patterns if the primary fails
