# Issue 24 Implementation Plan

## Summary

Add debounced search input handler to filter recipes by name and description.

## Approach

Add debounce function and search event listener to existing JavaScript. Reuse renderRecipes() for filtered results.

## Files to Modify

- `recipes/index.html` - Add debounce function, search handler, update count format

## Implementation Steps

- [ ] Add debounce utility function (150ms)
- [ ] Add search input event listener
- [ ] Add filterRecipes function (case-insensitive match on name/description)
- [ ] Update recipe count to show "X of Y" format when filtering
- [ ] Handle empty search (show all recipes)

## Success Criteria

- [ ] Typing filters recipes after 150ms debounce
- [ ] Case-insensitive matching works
- [ ] Count shows "Showing X of Y recipes" when filtered
- [ ] Empty search shows all recipes
- [ ] No results shows appropriate message
