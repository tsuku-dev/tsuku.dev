# Issue 22 Implementation Plan

## Summary

Replace the placeholder "Coming Soon" content in `recipes/index.html` with the static page structure for the recipe browser, including search input, recipe count display, recipe grid container, and loading skeleton.

## Approach

Follow the design document's Phase 1 specification. The page will show a loading skeleton by default, which will be replaced by JavaScript in subsequent issues (#23). This issue only creates the static HTML structure.

### Alternatives Considered

- **Inline skeleton CSS**: Could add skeleton styles inline in the HTML. Rejected because keeping styles in `style.css` maintains consistency.
- **Minimal skeleton (single element)**: Could use one large skeleton block. Rejected because individual card skeletons provide better visual feedback of expected layout.

## Files to Modify

- `recipes/index.html` - Replace placeholder content with recipe browser structure

## Files to Create

None (CSS changes will be added in issue #25)

## Implementation Steps

- [ ] Add search input with ARIA label and placeholder
- [ ] Add recipe count display element (hidden initially, shown by JS later)
- [ ] Add recipe grid container element
- [ ] Add loading skeleton with 6 placeholder cards
- [ ] Add `<noscript>` message with link to GitHub registry
- [ ] Remove old "Coming Soon" placeholder content

## Testing Strategy

- Manual verification: `python3 -m http.server 8000` and navigate to `/recipes/`
- Verify: Search input present with correct ARIA label
- Verify: Loading skeleton visible
- Verify: `<noscript>` message shows when JS disabled

## Risks and Mitigations

- **Skeleton looks off without CSS**: Acceptable for this issue; CSS comes in #25
- **Inconsistent with other pages**: Using existing `.content` section class for consistency

## Success Criteria

- [ ] `recipes/index.html` has search input with `aria-label="Search recipes"`
- [ ] Recipe count display element exists (empty/hidden initially)
- [ ] Recipe grid container element exists (`id="recipe-grid"`)
- [ ] Loading skeleton visible with multiple placeholder cards
- [ ] `<noscript>` message present with link to GitHub registry
- [ ] Page accessible at `/recipes/` locally

## Open Questions

None - design document provides clear specification.
