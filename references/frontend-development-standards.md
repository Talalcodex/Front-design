# Frontend Development Standards

## Contents
- Choosing the stack
- Existing projects
- Project structure
- Design tokens
- Code standards
- Data, state and errors
- Security
- Dependencies
- Mobile application interfaces
- Documentation to deliver

## Choosing the stack

Choose by requirements, not popularity.

| Situation | Reasonable choice |
|---|---|
| Static marketing page, simple site | HTML, modern CSS, minimal JS; or Astro |
| Content site needing SEO and routing | Next.js, Nuxt, SvelteKit or Astro |
| Complex interactive web app | React (Vite or Next.js), Vue/Nuxt or Svelte, with TypeScript |
| Dashboard or admin panel | React or Vue with a table and chart library suited to the data volume |
| Animation-heavy or 3D experience | Vanilla or React with GSAP, Motion, Three.js or React Three Fiber |
| PWA | Any web framework plus manifest, service worker and offline strategy |
| Mobile app (native feel, cross-platform) | React Native (with Expo) or Flutter |
| Team already uses a stack | Use that stack |

Styling: Tailwind CSS, CSS Modules, Sass, styled-components, or modern native CSS (custom properties, `@layer`, container queries, nesting). Pick one primary strategy and stay consistent. Use TypeScript for anything beyond a small prototype unless the user prefers otherwise.

State the choice and the reason in one or two sentences.

## Existing projects

Before changing anything: read `package.json`, framework config, folder layout, styling approach, lint and format rules, existing components and tokens. Match conventions. Do not swap frameworks or add overlapping libraries without asking. Make the smallest change that achieves the design goal, and keep diffs reviewable.

## Project structure

Example for a component-based web app:

```
project/
├── public/                # static assets, favicons, manifest
├── src/
│   ├── app/ or pages/     # routes
│   ├── components/
│   │   ├── ui/            # primitives: Button, Input, Card, Modal
│   │   └── features/      # composed, domain-specific components
│   ├── styles/            # tokens.css, global.css, utilities
│   ├── lib/               # helpers, api clients, constants
│   ├── hooks/             # reusable hooks
│   ├── data/              # sample or static data (clearly labeled)
│   └── types/
├── README.md
└── package.json
```

Keep components small and single-purpose. Co-locate styles and tests with components when the stack encourages it.

## Design tokens

Define tokens once and consume them everywhere: color roles (light and dark), type scale, spacing scale, radius, shadows or elevation, z-index layers, breakpoints, motion durations and easings. Expose as CSS custom properties (and mirror into Tailwind config or a theme object if used). No magic numbers scattered through components.

## Code standards

- Semantic HTML first (`header`, `nav`, `main`, `section`, `article`, `footer`, `button`, `a`, `label`). Use `button` for actions and `a` for navigation.
- Clean, readable, consistently named code. Meaningful names; no dead code or commented-out blocks.
- Reusable components with clear props and sensible defaults.
- No unnecessary inline styles; no duplicated style blocks.
- No broken imports, no missing assets, no placeholder links or buttons that do nothing. If an action is out of scope, disable it with an explanation or omit it.
- Handle loading, empty, error and success states for every async view.
- Respect user preferences: `prefers-color-scheme`, `prefers-reduced-motion`, `prefers-contrast` where practical.
- Internationalization readiness: avoid hardcoding strings in deeply nested components when i18n is likely; support RTL with logical properties (`margin-inline`, `padding-block`).
- Images: set width and height, use modern formats, responsive `srcset`, and lazy loading below the fold.

## Data, state and errors

Keep state as local as possible; lift only when needed. Separate server state (fetching, caching) from UI state. Wrap network calls with error handling and user-facing messages. Use realistic sample data when a backend is missing and mark it clearly (for example in `src/data/sample-*.ts` with a comment). Never simulate a backend response as if it were real behavior without saying so.

## Security

No hardcoded secrets or API keys; use environment variables and document them in `.env.example`. Sanitize or escape user-generated content; avoid `dangerouslySetInnerHTML` and `innerHTML` with untrusted data. Use `rel="noopener noreferrer"` for external `target="_blank"` links. Do not expose private keys to the client; if a feature needs a secret, it needs a backend, and you should say so.

## Dependencies

Add a library only if it clearly reduces complexity or risk. Prefer well-maintained packages with compatible licenses. Check the installed or current version rather than guessing API shapes. Remove unused dependencies. Pin or document versions in the README.

## Mobile application interfaces

- **React Native / Expo**: use platform conventions for navigation (stack, tabs), safe areas, gesture handling and haptics; test on iOS and Android sizes.
- **Flutter**: Material 3 or Cupertino adaptations as fitting; a clear theme and component structure.
- **PWA / responsive web**: manifest, icons, service worker, offline fallback, `display: standalone` behavior, safe-area insets, `100dvh` handling.
Mobile design means touch targets of at least 44x44 pt (48 dp), thumb-friendly placement, and native-appropriate patterns, not a shrunken desktop layout.

## Documentation to deliver

README with: overview, tech stack, prerequisites, install, run, build, test, environment variables, folder structure, design system summary (tokens and components), animation notes, browser support, known limitations.
