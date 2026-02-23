# Troubleshooting

## Fonts do not apply

Check all three:

1. Root imports exist (`import 'geist-svelte/font/sans'` etc.).
2. Global CSS is loaded (for SvelteKit: `import '../app.css'` in `+layout.svelte`).
3. Variables are mapped correctly for Tailwind (`@theme` or `tailwind.config`).

## Tailwind class works but still default font

Variable names are likely mismatched. Use exact names:

- `--font-geist-sans`
- `--font-geist-mono`
- `--font-geist-pixel-square`
- `--font-geist-pixel-grid`
- `--font-geist-pixel-circle`
- `--font-geist-pixel-triangle`
- `--font-geist-pixel-line`

## Linter says imports are unused

Use side-effect imports when you only need registration:

```ts
import 'geist-svelte/font/sans';
```

If metadata is needed, use the imported object values in code.

## CSP or deployment font loading issues

Bundled `.woff2` files are served from your app's asset origin. Ensure `font-src` allows your own asset origin/CDN domain.

## SvelteKit route-level import causes inconsistent behavior

Move imports to root `src/routes/+layout.svelte`, not individual pages/components.

## Non-variable variant confusion

Default recommendation is variable fonts (`sans`, `mono`). Use `sans-non-variable` and `mono-non-variable` only when a legacy compatibility requirement is explicit.
