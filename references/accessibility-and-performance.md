# Accessibility and Performance

Aim for WCAG 2.2 AA. Verify with tools where possible; never claim compliance you did not test.

## Contents
- Accessibility principles and checks
- Component-specific notes
- Performance and Core Web Vitals
- Tools
- Reporting honestly

## Accessibility principles and checks

- **Semantics and landmarks**: one `h1`, logical heading order, `header`, `nav`, `main`, `footer`, labeled regions. Use native elements before ARIA.
- **Keyboard**: everything operable by keyboard, logical tab order, no traps, skip-to-content link, Escape closes overlays, arrow-key patterns for menus, tabs and listboxes as expected.
- **Focus**: visible `:focus-visible` indicator with sufficient contrast (never `outline: none` without a replacement); manage focus on route change, modal open and close.
- **Forms**: every input has a programmatically associated `label`; errors are text, associated via `aria-describedby`, announced politely; required state is clear; do not rely on placeholder as label.
- **Contrast**: 4.5:1 for normal text, 3:1 for large text and meaningful UI components and focus rings. Test both themes.
- **Color independence**: use icon, text or pattern alongside color.
- **Images and media**: meaningful `alt` text; empty `alt` for decorative images; captions and transcripts for audio and video; no autoplay with sound.
- **Screen readers**: meaningful names for controls, `aria-live` for dynamic updates, `aria-expanded`, `aria-current`, `aria-pressed` where fitting; avoid redundant or conflicting ARIA.
- **Motion**: honor `prefers-reduced-motion`; avoid flashing; provide pause controls.
- **Targets and zoom**: targets at least 24x24 CSS px minimum (44x44 recommended on touch); support 200% zoom and text spacing changes; don't disable pinch zoom.
- **Language and direction**: set `lang`; support RTL when needed.
- **Timeouts**: warn and allow extension before session expiry.

## Component-specific notes

- **Modals**: `role="dialog"` with `aria-modal`, a label, focus trap, return focus on close; prefer the native `<dialog>` element.
- **Menus and dropdowns**: button with `aria-expanded`; list semantics; close on Escape and outside click.
- **Tabs, accordions**: follow ARIA Authoring Practices patterns.
- **Tables**: real `table`, `th` with scope, captions; don't use tables for layout.
- **Charts**: text summary, data table alternative, patterns or labels beyond color.
- **Toasts and notifications**: `role="status"` or `alert` appropriately; don't auto-dismiss critical info too quickly.

## Performance and Core Web Vitals

Targets (at the 75th percentile): **LCP** under 2.5s, **INP** under 200ms, **CLS** under 0.1.

- **LCP**: prioritize the hero image or text (`fetchpriority="high"`, preload critical assets, no lazy-loading the LCP image), server-render or pre-render above-the-fold content, minimize render-blocking CSS and JS.
- **INP**: keep main-thread tasks short, avoid heavy handlers, debounce expensive work, use web workers or code splitting where needed.
- **CLS**: set width and height or `aspect-ratio` on media, reserve space for embeds and ads, avoid injecting content above existing content, use `font-display` with size-adjusted fallbacks.
- **Images**: modern formats (AVIF, WebP), responsive `srcset`, compression, lazy-load below the fold, SVG for icons and illustrations.
- **Fonts**: subset, limit weights, self-host, preload the critical face, use variable fonts to reduce files.
- **JavaScript**: ship less, split by route, lazy-load heavy features (3D, charts, editors), tree-shake, avoid large animation libraries when CSS suffices.
- **CSS**: avoid huge unused CSS; consider critical CSS.
- **Caching and delivery**: long-lived immutable caching for hashed assets, compression (Brotli), CDN where applicable.
- **Animation**: transform and opacity only for most effects; pause off-screen.

## Tools

Use what is available in the environment: Lighthouse (CLI or DevTools), axe-core or `@axe-core/cli`, Pa11y, `eslint-plugin-jsx-a11y`, WebPageTest, browser DevTools, Playwright or Puppeteer for screenshots and automated checks, a keyboard-only manual pass, and a screen reader spot check (VoiceOver, NVDA) when possible.

## Reporting honestly

State what was tested and how. Example: "Ran axe on 3 pages: 0 violations detected. Not tested with a screen reader." Automated tools catch only a portion of accessibility issues; say so, and list manual checks still recommended.
