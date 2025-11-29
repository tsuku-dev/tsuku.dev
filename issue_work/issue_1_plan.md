# Issue 1 Implementation Plan

## Summary

Update install.sh to match the versioned binary naming pattern produced by goreleaser.

## Approach

Fix install.sh to construct the correct binary name using the pattern `tsuku-{os}-{arch}_{version}_{os}_{arch}` where version comes from the git tag (e.g., `v0.1.0` becomes `0.1.0`).

### Alternatives Considered
- **Fix release workflow in tsuku repo**: Would require changes to goreleaser config in a different repository and potentially break other tooling. The goreleaser naming is standard practice.

## Files to Modify
- `install.sh` - Update BINARY_NAME construction to include version and duplicate os/arch

## Files to Create
None

## Implementation Steps
- [ ] Update BINARY_NAME to use pattern `tsuku-{os}-{arch}_{version}_{os}_{arch}`
- [ ] Strip `v` prefix from version for the filename (v0.1.0 -> 0.1.0)
- [ ] Update checksum grep pattern to match new binary name

## Testing Strategy
- Manual verification: Run the script and verify the constructed URL matches actual release assets

## Risks and Mitigations
- **Version format change**: If future releases change the naming pattern, the script will break. Mitigation: This is a known risk with any hardcoded pattern; document the expected format in comments.

## Success Criteria
- [ ] install.sh constructs correct download URL matching release asset names
- [ ] Checksum verification works with the new binary name pattern
- [ ] Script downloads successfully from actual release

## Open Questions
None
