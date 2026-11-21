# Animation Guidelines

Motion should clarify, guide attention, confirm actions, and express personality. If it does none of these, remove it.

## Contents
- Principles
- Technique catalog
- Choosing technology
- Timing and easing
- Performance rules
- Accessibility and reduced motion
- Anti-patterns
- Reusable snippets

## Principles

1. **Purposeful**: every animation answers "what does this help the user understand or feel?"
2. **Consistent**: one motion language per project (shared durations, easings, distances).
3. **Responsive**: feedback within ~100ms; never block input while animating.
4. **Natural**: ease and spring physics over linear motion.
5. **Subtle by default**, bold only where the concept calls for it (portfolios, campaigns).
6. **Accessible and performant**: honor `prefers-reduced-motion`; animate cheap properties.

## Technique catalog

Smooth page and route transitions; scroll-triggered reveals; scroll-based storytelling (pinning, scrubbing); hover effects and button micro-interactions; parallax (restrained); animated gradients; text reveal (line, word or character, with proper accessible text); staggered entrances; SVG path and shape animation; animated or generative backgrounds; 3D and WebGL interactions where they add real value; sophisticated loaders and skeletons; interactive charts; animated navigation and menus; modal, drawer and popover transitions; spring-based interactions (drag, toggle, reorder).

## Choosing technology

Pick the lightest tool that does the job.

| Need | Prefer |
|---|---|
| Hover, focus, simple state changes, small reveals | CSS transitions and keyframes |
| Scroll-linked effects in modern browsers | CSS scroll-driven animations (`animation-timeline`) with a graceful fallback or `IntersectionObserver` |
| Page transitions in supported browsers | View Transitions API (feature-detect; fall back to none) |
| Imperative control without a library | Web Animations API |
| Complex timelines, scroll pinning, SVG, text splitting | GSAP (with ScrollTrigger) |
| React component and layout animation, gestures, springs | Motion (formerly Framer Motion) |
| Designer-authored vector animation | Lottie (or dotLottie) |
| 3D scenes | Three.js; React Three Fiber in React projects |
| Particle or custom effects | Canvas or WebGL, only when needed |
| Illustrations and icons | Inline SVG |

Check current versions and licenses before adding a library. Do not use every library in every project. Do not add a heavy library for an effect CSS can do.

## Timing and easing

- Micro-interactions: 100 to 200ms.
- Component transitions (menus, modals): 200 to 350ms.
- Page and section transitions: 300 to 600ms.
- Entrance stagger: 40 to 100ms between items, cap the total sequence under about 800ms.
- Easing: ease-out for entrances, ease-in for exits, ease-in-out for movement across the screen, springs for playful or physical interactions. Define tokens, for example `--ease-out: cubic-bezier(0.22, 1, 0.36, 1)`.
- Exits should be faster than entrances.

## Performance rules

- Animate `transform` and `opacity`. Avoid animating `width`, `height`, `top`, `left`, `box-shadow` and `filter` on large areas.
- Use `will-change` sparingly and remove it afterward.
- Avoid layout thrash: batch reads and writes; use `requestAnimationFrame` for JS-driven motion.
- Pause or destroy animations off-screen; dispose Three.js resources; cap device pixel ratio for canvases.
- Lazy-load heavy animation code and 3D assets. Keep the largest content visible without waiting for animation libraries.
- Test on a mid-range phone and with CPU throttling.

## Accessibility and reduced motion

- Respect `prefers-reduced-motion: reduce`: disable parallax, scrubbed scroll animation, autoplaying loops, large movement; replace with instant or opacity-only changes. Keep essential feedback.
- No flashing content above 3 flashes per second.
- Provide pause or stop controls for any autoplaying motion longer than 5 seconds.
- Do not hide content until JavaScript animates it in; content must be readable if scripts fail.
- Split-text effects must preserve the original text for screen readers (`aria-label` on the container and `aria-hidden` on the split spans).
- Maintain focus order and visible focus during transitions.

## Anti-patterns

Scroll-jacking that fights the user; animation that delays access to content or controls; loaders that last longer than the task; parallax causing motion sickness; text animating while the user is trying to read; infinite decorative loops; heavy 3D on content pages with no purpose.

## Reusable snippets

```css
:root {
  --ease-out: cubic-bezier(0.22, 1, 0.36, 1);
  --dur-fast: 150ms;
  --dur-base: 250ms;
  --dur-slow: 500ms;
}

.reveal {
  opacity: 0;
  transform: translateY(12px);
  transition: opacity var(--dur-slow) var(--ease-out),
              transform var(--dur-slow) var(--ease-out);
}
.reveal.is-visible { opacity: 1; transform: none; }

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
  .reveal { opacity: 1; transform: none; }
}
```

```js
// Scroll reveal with IntersectionObserver
const io = new IntersectionObserver((entries) => {
  for (const e of entries) {
    if (e.isIntersecting) { e.target.classList.add('is-visible'); io.unobserve(e.target); }
  }
}, { threshold: 0.15 });
document.querySelectorAll('.reveal').forEach((el) => io.observe(el));
```
