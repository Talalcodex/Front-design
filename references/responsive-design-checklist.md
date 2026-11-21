# Responsive Design Checklist

Target: smartphones, tablets, laptops, desktop monitors, large displays. Design mobile experiences deliberately; do not just shrink desktop.

## Contents
- Approach
- Breakpoints and testing widths
- Checklist
- Mobile-specific guidance
- Large displays

## Approach

- Mobile-first CSS where appropriate: base styles for small screens, enhance upward with `min-width` queries.
- Let content decide breakpoints; use fluid techniques first (`clamp()`, `minmax()`, `auto-fit` grids, flex-wrap), then add breakpoints where layouts break.
- Use container queries for components that live in different-width contexts.
- Rethink information architecture per device: what matters on a phone, what can wait, what becomes a bottom sheet, accordion or separate screen.

## Breakpoints and testing widths

Starting points (adjust to content): 360, 390, 430 (phones), 768, 834 (tablets), 1024, 1280, 1440 (laptop/desktop), 1920, 2560 (large). Also test landscape phone and a narrow desktop window.

## Checklist

**Layout**
- [ ] No horizontal scrolling at any width (check `overflow`, wide tables, code blocks, images).
- [ ] Grids reflow cleanly; no orphaned or cramped columns.
- [ ] Consistent spacing scale on every breakpoint; mobile spacing is comfortable, not squeezed.
- [ ] Max content width on large screens; line lengths stay readable.

**Navigation**
- [ ] Mobile nav is reachable, clear, and closes predictably; focus is managed.
- [ ] Current location is visible; back behavior works.
- [ ] Sticky elements don't cover content or the on-screen keyboard.

**Typography and images**
- [ ] Fluid type scales without breaking; no text under 16px for body on mobile.
- [ ] Text zooms to 200% without loss of content or function.
- [ ] Images and media scale, keep aspect ratio, use `srcset` and sensible `sizes`.

**Touch and input**
- [ ] Touch targets at least 44x44 px with spacing between them.
- [ ] No hover-only functionality; hover enhancements have touch equivalents.
- [ ] Gestures have visible alternatives.
- [ ] Forms use correct `type`, `inputmode`, `autocomplete`; labels stay visible; the keyboard doesn't hide the active field.

**Data-heavy UI**
- [ ] Tables become cards, stacked rows or scroll containers with clear affordance.
- [ ] Charts remain legible (simplified labels, tooltips on tap, tabular fallback).
- [ ] Dashboards prioritize key metrics first on small screens.

**Performance on mobile**
- [ ] Heavy animation and 3D reduced or disabled on low-power devices and `prefers-reduced-motion`.
- [ ] Images and scripts lazy-loaded; critical content loads first.
- [ ] Tested under throttled network and CPU.

## Mobile-specific guidance

- Use `100dvh` (with fallback) rather than `100vh` for full-height sections; handle iOS Safari bars.
- Respect safe areas with `env(safe-area-inset-*)` and `viewport-fit=cover`.
- Place primary actions in the thumb zone; consider bottom sheets and bottom navigation.
- Prevent accidental zoom on inputs by using 16px minimum font size.
- Avoid fixed elements that stack and consume most of the viewport.

## Large displays

Cap container widths, scale type modestly, use extra space for whitespace or additional columns only when content benefits, and keep imagery sharp for high-DPI and 4K.
