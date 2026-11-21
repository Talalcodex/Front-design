# Modern UI Patterns

Pattern library for concept and build phases. Use patterns because they serve the content, not because they are fashionable.

## Contents
- Layout approaches
- Navigation patterns
- Typography
- Color systems
- Components and states
- Patterns by product category
- Generic-AI look: what to avoid and what to do instead

## Layout approaches

- **CSS Grid and Flexbox** as the default engine; use `gap`, `minmax()`, `clamp()`, and container queries for component-level responsiveness.
- **Bento grids**: use sparingly, when content blocks genuinely differ in importance. Not for every feature section.
- **Asymmetric layouts**: offset columns, uneven splits, intentional whitespace for tension and focus.
- **Editorial layouts**: strong type hierarchy, pull quotes, multi-column text, large imagery with captions. Good for content, portfolios, education.
- **Layered compositions**: overlapping image and type, sticky elements, depth through scale. Keep text legible.
- **Full-screen experiences**: immersive hero or chapter sections; always provide clear navigation and an exit.
- **Dashboard layouts**: persistent sidebar or top nav, clear page header, KPI row, primary visualization, secondary detail. Control density with spacing and grouping.

## Navigation patterns

- Top bar with a compact CTA; collapse thoughtfully on mobile.
- Sidebar (collapsible) for apps with many sections; command palette (Cmd/Ctrl+K) for power users.
- Bottom tab bar for mobile apps (3 to 5 destinations), thumb-reachable.
- Sticky or auto-hiding headers; scroll progress indicators for long pages.
- Breadcrumbs and in-page tables of contents for documentation and long-form content.
- Overlay menus for expressive sites, with focus trapping and an obvious close.

## Typography

- Pick a display face and a text face with contrast in personality but harmony in proportion, or use one versatile family in several weights.
- Candidates: Inter, Geist, Manrope, DM Sans, Plus Jakarta Sans, Space Grotesk, Sora, Playfair Display, plus others suited to the brand (serif, grotesk, mono, variable fonts). Do not repeat the same pairing across projects.
- Build a type scale (for example a 1.2 to 1.333 ratio) with `clamp()` for fluid sizes. Body 16 to 18px minimum on screens, line-height 1.5 to 1.7, line length 60 to 75 characters.
- Use tabular numerals for data. Check language and script coverage (Latin, Arabic, Devanagari, CJK) when the audience needs it.
- Always specify fallback stacks. Self-host or use `font-display: swap`.

## Color systems

- Define roles, not just hues: background, surface (levels), text (primary, secondary, muted), border, accent, accent-hover, and semantic colors (success, warning, danger, info).
- Provide light and dark themes from the same tokens; dark mode is a redesign of elevation and contrast, not an inversion.
- Check contrast (WCAG AA: 4.5:1 body text, 3:1 large text and UI components).
- Prefer a restrained palette with one confident accent. Consider OKLCH for perceptually even scales.
- Never rely on color alone to convey meaning.

## Components and states

Cover: navigation, buttons, cards, forms, search, tables, charts, modals, dropdowns, sidebars, dashboards, notifications, loading, empty, error.

For each: default, hover, focus-visible, active, disabled, loading, and (where relevant) error, success, selected. Provide skeletons for loading, helpful empty states with a next action, and error states that explain and offer recovery. Forms: visible labels, inline validation, clear error text, correct input types and autocomplete.

## Patterns by product category

- **Healthcare**: calm palette, high contrast, generous targets, plain language, clear privacy cues, step-by-step flows, prominent emergency or support paths.
- **Finance / analytics**: strict hierarchy, restrained color for data, consistent number formatting, clear time-range controls, accessible charts with tables as fallback.
- **Education**: clear progress, chunked content, readable typography, navigation that never loses the learner, encouraging but not childish tone unless the audience is children.
- **AI apps**: conversation as the primary surface, streaming text, visible status and stop control, citations and source transparency, feedback affordances, graceful failure and retry, prompt suggestions that fit the task.
- **E-commerce**: fast search, filters and sorting, rich product media, price and availability clarity, trust signals, one-page-feel checkout, guest checkout.
- **Portfolio / creative**: strong art direction, custom cursor or scroll narratives if they enhance, case-study structure, performance care for heavy media.
- **SaaS / admin**: dense but legible tables, bulk actions, saved views, role-aware UI, onboarding and empty states.
- **Social**: infinite or paginated feeds with performance care, optimistic UI, notifications, safety and reporting tools.
- **Mobile / PWA**: bottom nav, gestures with visible alternatives, safe areas, install prompts, offline states.

## Generic-AI look: avoid and replace

| Avoid by default | Do instead |
|---|---|
| Purple/blue gradient everywhere | Palette derived from the brand and audience; one purposeful accent |
| Glassmorphism on everything | Solid surfaces with deliberate use of translucency for layered UI only |
| Identical rounded cards in grids | Vary scale, alignment and treatment; use lists, tables, or editorial blocks when appropriate |
| Stock photos | Custom illustration, product screenshots, real photography direction, abstract generative art, typography as image |
| Oversized headline with nothing behind it | Headline that states value, supported by hierarchy and a clear action |
| Floating blobs and orbs | Purposeful depth: shadows, layering, motion tied to content |
| Pill buttons and max radius everywhere | A radius system chosen for the brand (sharp, soft, mixed) |
| Same dashboard template | Dashboard organized around the user's real tasks and decisions |
