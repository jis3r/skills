# Quickstart

## 1) Install

```bash
npm i geist-svelte
```

Use `pnpm add geist-svelte` or `yarn add geist-svelte` if needed.

## 2) SvelteKit + Tailwind v4

Root layout:

```svelte
<!-- src/routes/+layout.svelte -->
<script lang="ts">
  import '../app.css';
  import 'geist-svelte/font/sans';
  import 'geist-svelte/font/mono';

  let { children } = $props();
</script>

{@render children()}
```

Global CSS:

```css
/* src/app.css */
@theme inline {
  --font-sans: var(--font-geist-sans);
  --font-mono: var(--font-geist-mono);
}
```

Use in markup:

```svelte
<h1 class="font-sans">Heading</h1>
<code class="font-mono">const x = 1</code>
```

## 3) SvelteKit + Tailwind v3

Keep the same root layout imports, then map fonts in `tailwind.config.js`:

```js
import { fontFamily } from 'tailwindcss/defaultTheme';

export default {
  theme: {
    extend: {
      fontFamily: {
        sans: ['var(--font-geist-sans)', ...fontFamily.sans],
        mono: ['var(--font-geist-mono)', ...fontFamily.mono],
      },
    },
  },
};
```

## 4) Svelte (Vite) without SvelteKit

Bootstrap imports in `src/main.ts`:

```ts
import 'geist-svelte/font/sans';
import 'geist-svelte/font/mono';
import './app.css';
```

Then in CSS:

```css
body {
  font-family: var(--font-geist-sans);
}
code,
pre {
  font-family: var(--font-geist-mono);
}
```

## 5) No Tailwind in SvelteKit

```svelte
<!-- src/routes/+layout.svelte -->
<script lang="ts">
  import { GeistSans } from 'geist-svelte/font/sans';
  import { GeistMono } from 'geist-svelte/font/mono';

  let { children } = $props();
</script>

{@render children()}

<style>
  :global(body) {
    font-family: var(--font-geist-sans);
  }

  :global(code, pre) {
    font-family: var(--font-geist-mono);
  }
</style>
```
