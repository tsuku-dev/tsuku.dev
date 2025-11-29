# Issue 5 Implementation Plan

## Summary

Modify install.sh to automatically configure the user's shell PATH by creating an env file and sourcing it from shell config files, following rustup's approach.

## Approach

Follow industry standard (rustup pattern):
1. Create `$INSTALL_DIR/env` file with PATH exports
2. Detect user's shell from $SHELL
3. Append source line to appropriate shell config file
4. Skip if source line already exists (idempotent)
5. Support `--no-modify-path` flag to opt out

### Alternatives Considered
- Inline PATH modification: Rejected because env file is cleaner, easier to update, and follows rustup precedent

## Files to Modify
- `install.sh` - Add shell configuration logic

## Files to Create
None (env file is created at runtime in user's home)

## Implementation Steps
- [ ] Add `--no-modify-path` flag parsing at script start
- [ ] Create function to write env file with PATH exports
- [ ] Create function to detect shell and return config file path
- [ ] Create function to add source line idempotently
- [ ] Replace manual PATH instructions with auto-configuration
- [ ] Add clear feedback messages for what was modified

## Testing Strategy
- Manual verification: Run script and verify shell config is modified
- Test idempotency: Run twice and verify no duplicate entries
- Test opt-out: Run with `--no-modify-path` and verify no modification

## Risks and Mitigations
- Risk: Modifying wrong shell config file. Mitigation: Only modify based on $SHELL, skip if unrecognized.
- Risk: Breaking existing shell config. Mitigation: Only append, never modify existing content.

## Success Criteria
- [ ] After installation, tsuku is in PATH in new shell sessions
- [ ] Reinstalling doesn't duplicate entries
- [ ] `--no-modify-path` skips shell modification
- [ ] Clear feedback on what was modified

## Open Questions
None
