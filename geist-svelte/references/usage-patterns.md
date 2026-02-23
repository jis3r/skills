# Usage Patterns

## Import styles

Use side-effect imports when you only need variables:

```ts
import 'geist-svelte/font/sans';
import 'geist-svelte/font/mono';
```

Use named imports when you need metadata:

```ts
import { GeistSans } from 'geist-svelte/font/sans';

GeistSans.variable; // '--font-geist-sans'
GeistSans.style.fontFamily;
```

## Pixel fonts

Import once:

```ts
import 'geist-svelte/font/pixel';
```

Available variables:

- `--font-geist-pixel-square`
- `--font-geist-pixel-grid`
- `--font-geist-pixel-circle`
- `--font-geist-pixel-triangle`
- `--font-geist-pixel-line`

Tailwind v4 mapping example:

```css
@theme inline {
  --font-pixel-square: var(--font-geist-pixel-square);
  --font-pixel-grid: var(--font-geist-pixel-grid);
  --font-pixel-circle: var(--font-geist-pixel-circle);
  --font-pixel-triangle: var(--font-geist-pixel-triangle);
  --font-pixel-line: var(--font-geist-pixel-line);
}
```

## Non-variable fallback usage

Use only when compatibility requires static files:

```ts
import { GeistSansNonVariable } from 'geist-svelte/font/sans-non-variable';
import { GeistMonoNonVariable } from 'geist-svelte/font/mono-non-variable';
```

## Migration from manual font setup

1. Remove custom `@font-face` blocks for Geist assets.
2. Add root imports from `geist-svelte/font/*`.
3. Replace hardcoded stacks with `var(--font-geist-sans)` / `var(--font-geist-mono)`.
4. For Tailwind, map variables in `@theme` (v4) or `theme.extend.fontFamily` (v3).

## Svelte 4 layout recipe

```svelte
<!-- src/routes/+layout.svelte -->
<script lang="ts">
  import '../app.css';
  import 'geist-svelte/font/sans';
  import 'geist-svelte/font/mono';
  export let data;
</script>

<slot />
```
