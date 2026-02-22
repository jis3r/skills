# Usage Patterns

## 1) Button Hover Feedback

```svelte
<script>
  import { Bell } from '@jis3r/icons';
  let hovered = $state(false);
</script>

<button
  onmouseenter={() => (hovered = true)}
  onmouseleave={() => (hovered = false)}
  class="inline-flex items-center gap-2"
>
  <Bell size={16} animate={hovered} />
  <span>Notifications</span>
</button>
```

## 2) Reusable Hover Wrapper

```svelte
<!-- HoverableItem.svelte -->
<script>
  let { children, class: className = '' } = $props();
  let isHovered = $state(false);
</script>

<div
  class={className}
  onmouseenter={() => (isHovered = true)}
  onmouseleave={() => (isHovered = false)}
>
  {@render children(isHovered)}
</div>
```

```svelte
<script>
  import HoverableItem from './HoverableItem.svelte';
  import { Home } from '@jis3r/icons';
</script>

<HoverableItem class="flex items-center gap-2 rounded p-2">
  {#snippet children(isHovered)}
    <Home size={16} animate={isHovered} />
    <span>Home</span>
  {/snippet}
</HoverableItem>
```

## 3) Selected State Instead of Hover

```svelte
<script>
  import { Check } from '@jis3r/icons';
  let selected = $state(false);
</script>

<button onclick={() => (selected = !selected)}>
  <Check size={16} animate={selected} />
</button>
```

## 4) Design Token Driven Styling

```svelte
<script>
  import { Activity } from '@jis3r/icons';
</script>

<Activity
  size={20}
  color="var(--color-fg-muted)"
  strokeWidth={1.8}
  class="shrink-0"
/>
```
