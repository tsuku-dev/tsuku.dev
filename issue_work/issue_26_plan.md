# Issue 26 Implementation Plan

## Summary
Add "Recipes" navigation link to header nav on all pages and update existing Recipes link to point to `/recipes/`.

## Approach
Simple HTML modifications - add a nav link between logo and GitHub icon consistently across all pages. This is straightforward enough that no alternatives need consideration.

## Files to Modify
- `index.html` - add header nav link, update links section Recipes URL
- `stats/index.html` - add header nav link
- `telemetry/index.html` - add header nav link

## Files NOT to Create
- `recipes/index.html` - this will be created by issue #22, navigation there will be added when that page exists

## Implementation Steps
- [ ] Add "Recipes" link to header nav in `index.html`
- [ ] Update links section "Recipes" href from GitHub to `/recipes/` in `index.html`
- [ ] Add "Recipes" link to header nav in `stats/index.html`
- [ ] Add "Recipes" link to header nav in `telemetry/index.html`
- [ ] Add CSS for nav-link styling in `assets/style.css`

## Nav Link Pattern
Insert between logo and GitHub icon:
```html
<a href="/recipes/" class="nav-link">Recipes</a>
```

## Testing Strategy
- Manual: `python3 -m http.server 8000` and verify:
  - Link appears in nav on all 3 pages
  - Link is styled consistently
  - Link points to `/recipes/`
  - Mobile responsive (link visible on small screens)

## Success Criteria
- [ ] Header nav has "Recipes" link on index.html
- [ ] Header nav has "Recipes" link on stats/index.html
- [ ] Header nav has "Recipes" link on telemetry/index.html
- [ ] Links section "Recipes" points to `/recipes/` (not GitHub)
- [ ] Navigation visually consistent across all pages

## Open Questions
None - straightforward implementation.
