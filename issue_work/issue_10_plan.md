# Issue 10 Implementation Plan

## Summary

Build a stats dashboard page at `/stats` that fetches JSON from `telemetry.tsuku.dev/stats` and renders it with vanilla JavaScript, following the existing site's dark theme.

## Approach

Use the existing site patterns (HTML structure, CSS variables, minimal JS) to build a single-page dashboard. The page will:
1. Show loading state initially
2. Fetch from the telemetry API
3. Render charts and metrics on success
4. Show friendly error message on failure

### Alternatives Considered
- **JavaScript framework (React/Vue)**: Issue explicitly requires vanilla JS only
- **Server-side rendering**: Adds complexity, not needed for simple stats display
- **Canvas-based charts**: CSS bars are simpler and sufficient for this use case

## Files to Modify
- `stats/index.html` - Replace placeholder with full dashboard implementation

## Files to Create
- None (all changes in existing file)

## Implementation Steps
- [ ] Add HTML structure for stats sections (overview cards, recipe list, OS/arch charts)
- [ ] Add CSS for stat cards, bar charts, and responsive layout
- [ ] Add JavaScript to fetch API and render data
- [ ] Add error handling for API unavailability
- [ ] Add loading state

## Testing Strategy
- Manual verification: Test with mock data by temporarily overriding fetch
- Manual verification: Test error state by using invalid API URL
- Manual verification: Test mobile responsiveness in browser devtools
- CI: ShellCheck will still run (unrelated to this change)

## Risks and Mitigations
- **Backend not deployed**: Dashboard shows error state - acceptable per issue requirements
- **API response format changes**: Match exactly what's documented in tsuku-telemetry DESIGN.md
- **CORS issues**: Backend design says CORS is enabled for /stats

## Success Criteria
- [ ] Dashboard accessible at `/stats`
- [ ] Shows top recipes by install count (bar chart)
- [ ] Shows breakdown by OS and architecture
- [ ] Shows total install count
- [ ] Mobile-responsive
- [ ] Shows "last updated" timestamp
- [ ] Links to privacy policy (`/telemetry`)
- [ ] Displays friendly message if API is unavailable

## Open Questions
None - requirements are clear from issue and backend design doc.
