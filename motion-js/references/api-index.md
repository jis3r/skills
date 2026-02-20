# Motion JS API Index

## Import Patterns

```js
// Full vanilla API surface
import {
  animate,
  animateView,
  inView,
  scroll,
  hover,
  press,
  resize,
  motionValue,
  mapValue,
  transformValue,
  springValue,
  styleEffect,
} from "motion"

// Smallest runtime for simple animation
import { animate } from "motion/mini"
```

## Core APIs

- `animate`: Core keyframe/tween/spring animation function.
- `scroll`: Link animation state to page or container scroll.
- `inView`: Trigger enter/leave behavior with Intersection Observer.
- `hover`: Run logic on hover start/end.
- `press`: Run logic on press start/end.
- `resize`: React to viewport or element size changes.
- `animateView`: Drive animation by view progress (advanced).
- `layout animations`: Animate layout transitions between state changes (advanced).

## Timing and Math Utilities

- `easing functions`: Built-in easing and cubic-bezier helpers.
- `delay`: Schedule one-off delayed callbacks.
- `frame`: Hook into frame read/update/render phases.
- `mix`: Interpolate between values.
- `spring`: Create reusable spring easing/value behavior.
- `stagger`: Generate sequential delays.
- `transform`: Map numeric domains to ranges.
- `wrap`: Wrap numbers into a cyclic range.

## Value APIs

- `motionValue`: Mutable animation state container.
- `mapValue`: Derive value from another value.
- `transformValue`: Transform one value stream into another.
- `springValue`: Apply spring smoothing to source values.

## Render Effects

- `styleEffect`: Bind values to style properties.
- `attrEffect`: Bind values to element attributes.
- `propEffect`: Bind values to object properties.
- `svgEffect`: SVG-specific value bindings.

## Integration and Guides

- `css`: Generate/author Motion-driven CSS animation behavior.
- `squarespace`: Use Motion inside Squarespace custom code.
- `webflow`: Use Motion in Webflow embed/custom code.
- `wordpress`: Use Motion in WordPress themes/blocks.
- `faqs`: Common setup and behavior questions.
- `gsap vs motion`: Capability comparison guidance.
- `improvements to WAAPI DX`: Why Motion improves animation ergonomics.
- `migrate from GSAP to Motion`: Migration strategy and API mapping.
- `performance`: Performance principles and diagnostics.
- `upgrade guide`: Breaking changes and migration notes.
- `studio install`: Motion Studio setup.

## Official Docs Coverage (Provided)

- [Quick start](https://motion.dev/docs/quick-start)
- [Animate](https://motion.dev/docs/animate)
- [Scroll](https://motion.dev/docs/scroll)
- [Animate view](https://motion.dev/docs/animate-view)
- [Layout animations](https://motion.dev/docs/layout-animations)
- [Easing functions](https://motion.dev/docs/easing-functions)
- [Hover](https://motion.dev/docs/hover)
- [In view](https://motion.dev/docs/inview)
- [Press](https://motion.dev/docs/press)
- [Resize](https://motion.dev/docs/resize)
- [Delay](https://motion.dev/docs/delay)
- [Frame](https://motion.dev/docs/frame)
- [Mix](https://motion.dev/docs/mix)
- [Split text](https://motion.dev/docs/split-text)
- [Spring](https://motion.dev/docs/spring)
- [Stagger](https://motion.dev/docs/stagger)
- [Transform](https://motion.dev/docs/transform)
- [Wrap](https://motion.dev/docs/wrap)
- [Motion value](https://motion.dev/docs/motion-value)
- [Map value](https://motion.dev/docs/map-value)
- [Transform value](https://motion.dev/docs/transform-value)
- [Spring value](https://motion.dev/docs/spring-value)
- [Attr effect](https://motion.dev/docs/attr-effect)
- [Prop effect](https://motion.dev/docs/prop-effect)
- [Style effect](https://motion.dev/docs/style-effect)
- [SVG effect](https://motion.dev/docs/svg-effect)
- [CSS](https://motion.dev/docs/css)
- [Squarespace](https://motion.dev/docs/squarespace)
- [Webflow](https://motion.dev/docs/webflow)
- [WordPress](https://motion.dev/docs/wordpress)
- [FAQs](https://motion.dev/docs/faqs)
- [GSAP vs Motion](https://motion.dev/docs/gsap-vs-motion)
- [Improvements to WAAPI DX](https://motion.dev/docs/improvements-to-the-web-animations-api-dx)
- [Migrate from GSAP to Motion](https://motion.dev/docs/migrate-from-gsap-to-motion)
- [Performance](https://motion.dev/docs/performance)
- [Upgrade guide](https://motion.dev/docs/upgrade-guide)
- [Studio install](https://motion.dev/docs/studio-install)
