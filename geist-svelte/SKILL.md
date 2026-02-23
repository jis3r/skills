---
name: geist-svelte
description: Integrate Geist fonts in Svelte 4/5 and SvelteKit projects using `geist-svelte`. Use when users ask for Geist Sans, Geist Mono, or Geist Pixel variants, need setup with Tailwind v4 or v3, want CSS variable usage without Tailwind, need import/config troubleshooting, or want migration from manual `@font-face` setup to package-based Geist fonts.
---

# Geist Svelte

Use this skill for integrating Geist fonts into Svelte and SvelteKit apps. Focus on app integration patterns, not library maintenance.

## When to Use This Skill
Use this skill when the user:

- Asks to add Geist fonts in a Svelte or SvelteKit project.
- Mentions Geist Sans, Geist Mono, or Geist Pixel variants.
- Needs help importing `geist-svelte/font/*` in root app/layout files.
- Wants Tailwind v4 (`@theme`) or Tailwind v3 (`theme.extend.fontFamily`) setup for Geist variables.
- Wants to apply Geist fonts without Tailwind using `var(--font-geist-*)`.
- Needs troubleshooting for fonts not loading or not applying.
- Wants to migrate from manual/local `@font-face` Geist setup to `geist-svelte`.

## Workflow

1. Identify runtime and styling path.
- SvelteKit or Svelte (Vite).
- Tailwind v4, Tailwind v3, or no Tailwind.
- Decide whether the user needs Sans/Mono only or Pixel variants too.

2. Install and import fonts at app entry/root.
- Install with package manager: `pnpm add geist-svelte` (or `npm i` / `yarn add`).
- Import font modules as side effects in the root layout/bootstrap file.
- Keep imports in root entry so CSS variables are registered globally.

3. Map variables to the app styling system.
- Tailwind v4: map in `@theme inline` in global CSS.
- Tailwind v3: map in `theme.extend.fontFamily`.
- No Tailwind: use `var(--font-geist-*)` in global CSS rules.

4. Apply fonts intentionally.
- Use `font-sans`/`font-mono` (Tailwind) or explicit CSS `font-family`.
- For Pixel, use specific variables (`--font-geist-pixel-*`) for display-only UI text.
- Use named imports only when metadata (`.variable`, `.style.fontFamily`) is needed.

5. Troubleshoot quickly.
- Verify root side-effect imports exist and load before UI render.
- Verify Tailwind theme mapping matches the CSS variable names.
- If lint flags unused imports, use side-effect import style (`import 'geist-svelte/font/sans'`).

## Guardrails

- Do not suggest editing `node_modules` or `geist-svelte` package internals.
- Do not use remote/CDN runtime imports for fonts when package imports are available.
- Keep import paths to documented exports only:
  - `geist-svelte/font/sans`
  - `geist-svelte/font/mono`
  - `geist-svelte/font/pixel`
  - `geist-svelte/font/sans-non-variable`
  - `geist-svelte/font/mono-non-variable`
- Prefer variable fonts first; use non-variable variants only for compatibility constraints.

## References

- `references/quickstart.md`
- `references/usage-patterns.md`
- `references/troubleshooting.md`
