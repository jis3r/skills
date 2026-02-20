# Integrations and Migration

## Installation Paths

### Bundler (recommended)

```bash
npm install motion
```

```js
import { animate, inView, scroll } from "motion"
```

### ESM CDN

```js
import { animate, inView, scroll } from "https://cdn.jsdelivr.net/npm/motion/+esm"
```

Use this path for static sites or no-build environments.

## CMS and Builder Embeds

- Squarespace: place Motion ESM imports in Code Injection or page-level script blocks.
- Webflow: add Motion ESM scripts in custom code embeds; ensure target elements exist before init.
- WordPress: enqueue a module script in theme/plugin and initialize after DOM ready.

In all environments, scope selectors tightly to avoid animating editor/admin UI elements.

## CSS + Motion Strategy

- Define visual states in CSS.
- Animate only dynamic deltas with Motion.
- Use CSS custom properties when design tokens must stay centralized.

## GSAP to Motion Mapping

- `gsap.to(...)` -> `animate(...)`
- `ScrollTrigger` progress links -> `scroll(...)`
- `stagger` option -> `stagger(...)`
- utility interpolation pipelines -> `motionValue` + `mapValue`/`transformValue`

When migrating, replace one interaction at a time and verify behavior parity after each swap.

## WAAPI Positioning

Motion builds on browser animation capabilities while improving ergonomics for sequencing, interruptions, value pipelines, and composable effects.

## Upgrade Discipline

Before upgrading Motion in production:

1. Review official upgrade notes.
2. Test scroll and gesture interactions on mobile and desktop.
3. Re-check premium/advanced APIs (`animateView`, layout workflows, split text) for behavior changes.
