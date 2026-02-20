# Motion JS Performance and Accessibility

## Performance Defaults

1. Prefer `transform` and `opacity` before animating layout-heavy properties.
2. Use `motion/mini` when the task only needs straightforward keyframe animation.
3. Keep one source value and derive other values via `mapValue` / `transformValue`.
4. Use CSS for static states and let Motion handle only dynamic state.
5. Avoid per-frame DOM reads inside update loops unless required.

## Frame Loop Guidance

Use `frame` only for custom read/update/render control that cannot be expressed with `animate` or `scroll`.

- Read layout in read phase.
- Mutate values/styles in update/render phases.
- Cancel frame jobs when component/page scope tears down.

## Cleanup Rules

Always retain cleanup functions returned by Motion helpers and call them when tearing down:

- `scroll(...)`
- `inView(...)`
- `hover(...)`
- `press(...)`
- `resize(...)`

Also stop running animations (`animation.stop()`) when animation scope is no longer valid.

## Reduced Motion

Respect user preferences for motion reduction.

```js
const prefersReduced = window.matchMedia("(prefers-reduced-motion: reduce)").matches

animate(
  ".panel",
  { opacity: [0, 1], y: prefersReduced ? [0, 0] : [24, 0] },
  { duration: prefersReduced ? 0.01 : 0.4 }
)
```

For large transitions, provide non-motion alternatives (instant state, subtle fade only, or no parallax).

## Debug Checklist

- Animation never runs: confirm selector matches live elements.
- Stutter on scroll: reduce animated elements and avoid layout-triggering properties.
- Gesture feels inconsistent: validate both pointer and keyboard/touch pathways.
- Repeated triggers: use one-time logic or explicit guard flags for enter-only reveals.
