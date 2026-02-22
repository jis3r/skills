# Migration from @lucide/svelte

## Basic Swap

From:

```svelte
<script>
  import { Bell } from '@lucide/svelte';
</script>
```

To:

```svelte
<script>
  import { Bell } from '@jis3r/icons';
</script>
```

## Add Animation Incrementally

1. Swap imports first with no behavior change.
2. Bind `animate` in places where interaction feedback helps.
3. Keep existing sizing and color tokens.

## Low-Risk Rollout Pattern

- Start in one feature/module.
- Verify visual parity and spacing.
- Add animation only to key actions (notifications, toggles, navigation cues).

## Regression Checklist

- Icon still communicates meaning when animation is off.
- No layout shift from icon container sizing.
- Contrast remains valid in light/dark themes.
- Motion remains subtle and does not loop unnecessarily.
