# Motion JS Patterns

## 1) Staggered Reveal on Enter View

```js
import { animate, inView, stagger } from "motion"

inView(".feature-grid", () => {
  animate(
    ".feature-card",
    { opacity: [0, 1], y: [24, 0] },
    {
      duration: 0.45,
      easing: "ease-out",
      delay: stagger(0.08),
    }
  )
}, { margin: "0px 0px -15% 0px" })
```

Use when cards should reveal once as users scroll.

## 2) Scroll-Linked Progress Bar

```js
import { animate, scroll } from "motion"

const progressAnimation = animate(
  ".reading-progress",
  { scaleX: [0, 1] },
  { easing: "linear" }
)

scroll(progressAnimation)
```

Use when a single element should track global page progress.

## 3) Scroll-Linked Parallax Value Pipeline

```js
import { motionValue, scroll, mapValue, styleEffect } from "motion"

const progress = motionValue(0)
const parallaxY = mapValue(progress, [0, 1], [0, -180])

scroll((latest) => progress.set(latest))
styleEffect(".hero-layer", { y: parallaxY })
```

Use when multiple elements should derive motion from one scroll value.

## 4) Hover + Press Interaction

```js
import { animate, hover, press } from "motion"

const stopHover = hover(".cta", (element) => {
  animate(element, { scale: 1.04 }, { type: "spring", stiffness: 420, damping: 28 })
  return () => animate(element, { scale: 1 }, { duration: 0.15 })
})

const stopPress = press(".cta", (element) => {
  animate(element, { scale: 0.97 }, { duration: 0.08 })
  return () => animate(element, { scale: 1 }, { duration: 0.12 })
})

// Later during teardown:
// stopHover()
// stopPress()
```

Use when a control needs desktop hover and touch/mouse press feedback.

## 5) Delayed Sequence Without Timelines

```js
import { animate, delay } from "motion"

animate(".badge", { opacity: [0, 1], y: [10, 0] }, { duration: 0.3 })

delay(() => {
  animate(".headline", { opacity: [0, 1] }, { duration: 0.4 })
}, 0.12)
```

Use when you need simple temporal orchestration but not a full timeline.

## 6) Spring-Smoothed Pointer Follow

```js
import { motionValue, springValue, styleEffect } from "motion"

const x = motionValue(0)
const y = motionValue(0)
const sx = springValue(x, { stiffness: 320, damping: 30 })
const sy = springValue(y, { stiffness: 320, damping: 30 })

styleEffect(".cursor-dot", { x: sx, y: sy })

window.addEventListener("pointermove", (event) => {
  x.set(event.clientX)
  y.set(event.clientY)
})
```

Use when raw pointer movement feels too sharp and needs smoothing.
