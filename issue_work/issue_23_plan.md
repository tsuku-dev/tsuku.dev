# Issue 23 Implementation Plan

## Summary

Add JavaScript to fetch recipes from registry.tsuku.dev, validate each recipe, render cards using safe DOM APIs, and handle all error cases gracefully.

## Approach

Add inline JavaScript at the bottom of recipes/index.html (before closing body tag) following the pattern used by other pages (index.html, stats/index.html). Use fetch API with proper error handling and DOM manipulation with textContent for XSS safety.

### Alternatives Considered

- **External JS file**: Could create `assets/recipes.js`. Rejected because other pages use inline JS for simplicity and this keeps the page self-contained.
- **Template literals with innerHTML**: Faster to write but rejected due to XSS risk from recipe metadata.

## Files to Modify

- `recipes/index.html` - Add JavaScript for fetch, validate, render, error handling

## Files to Create

None

## Implementation Steps

- [x] Add fetch logic on DOMContentLoaded with 10s timeout
- [x] Add recipe validation function (name, description, homepage; HTTPS URL)
- [x] Add renderRecipes function using createElement/textContent
- [x] Add recipe count display logic
- [x] Add error state rendering with retry button
- [x] Add fetch guard to prevent concurrent requests
- [x] Add empty state handling

## Testing Strategy

- Manual verification with local server
- Test: Normal load shows recipes
- Test: Search input filters (future issue, but verify it doesn't break)
- Test: Network error shows retry button
- Test: Rapid retry clicks don't cause issues

## Risks and Mitigations

- **CORS issues**: Design assumes registry has CORS headers; show GitHub fallback if CORS fails
- **Slow network**: 10s timeout with clear loading state

## Success Criteria

- [ ] Recipes load and display as cards on page load
- [ ] Recipe count shows "Showing X recipes"
- [ ] Loading spinner replaced by cards
- [ ] Error state shows retry button
- [ ] No XSS vulnerabilities (textContent only)

## Open Questions

None
