# Quality Assurance Checklist

Run before delivery (Phase 5, steps 7 and 8). Fix issues, re-check, and report only what you verified.

## Contents
- Build and code health
- Functionality
- Visual and design review
- Responsive review
- Motion review
- Accessibility pass
- Performance pass
- Cross-browser
- Content and copy
- Delivery checklist
- Final report template

## Build and code health

- [ ] Installs and builds from a clean checkout with the documented commands.
- [ ] No console errors or warnings in normal use.
- [ ] Linter, formatter and type-check pass (if configured).
- [ ] No broken imports, missing assets, 404s, or dead links.
- [ ] No hardcoded secrets; `.env.example` documents required variables.
- [ ] No unused dependencies or dead code.

## Functionality

- [ ] Every visible button, link, form and control does what it appears to do, or is clearly disabled or labeled as sample or out of scope.
- [ ] Forms validate, show errors, handle success.
- [ ] Loading, empty, error and success states exist and look designed.
- [ ] Routes, back button, deep links and refresh behave correctly.
- [ ] Features needing a backend or API are identified as such.

## Visual and design review

- [ ] Matches the approved concept (palette, type, layout, component style).
- [ ] Clear hierarchy: the first thing seen is the right thing.
- [ ] Consistent spacing rhythm, alignment and grid.
- [ ] Type scale applied consistently; no orphaned headings or awkward wraps.
- [ ] Components consistent across screens; all states present (hover, focus, active, disabled, loading).
- [ ] Imagery and icons consistent in style and quality; no stretched or pixelated assets.
- [ ] Light and dark themes both polished (if both are in scope).
- [ ] Does not read as a generic AI template (see anti-patterns in `modern-ui-patterns.md`).

## Responsive review

Walk through `responsive-design-checklist.md` at 360, 390, 768, 1024, 1280, 1440 and 1920 widths. Capture screenshots at the main breakpoints when tooling is available.

## Motion review

- [ ] Motion has a purpose and is consistent.
- [ ] No jank at normal speed; tested with CPU throttling if possible.
- [ ] `prefers-reduced-motion` handled and tested.
- [ ] Nothing hides content behind animation; works with scripts delayed.

## Accessibility pass

Complete `accessibility-and-performance.md`: keyboard-only walkthrough, focus visibility, labels, contrast, headings, alt text, automated scan results.

## Performance pass

Lighthouse or equivalent on key pages (mobile profile). Record LCP, INP or TBT, CLS. Check bundle size and image weight. Fix the biggest wins first.

## Cross-browser

Check current Chrome, Safari (including iOS), Firefox and Edge for layout, fonts, and any newer CSS or API features. Provide fallbacks or feature detection for features not yet universally supported.

## Content and copy

- [ ] Realistic sample content; no lorem ipsum in final output.
- [ ] Microcopy is clear, consistent in tone, and free of typos.
- [ ] Sample data is labeled as such.

## Delivery checklist

- [ ] Runnable project, organized folders.
- [ ] README with setup and run instructions.
- [ ] Design system documentation.
- [ ] Technologies list, animation details, responsive details.
- [ ] External dependencies listed.
- [ ] Limitations and incomplete items stated.

## Final report template

```
Verified: <what you ran and the result>
Not verified: <what you could not test and why>
Known limitations: <list>
Needs backend/API: <list>
Suggested next steps: <list>
```
