---
name: moving-icons
description: Integrate and use the Moving Icons library (`@jis3r/icons`) in Svelte 5/SvelteKit apps. Use when users ask for animated (Lucide-style) icons in Svelte, mention `@jis3r/icons` or moving icons, icon import/usage patterns, hover-controlled animation with the `animate` prop, icon selection, theming, sizing, or migration from `@lucide/svelte` to animated icons.
---

# Moving Icons

This skill helps to integrate animated icons into Svelte/SvelteKit apps and consume `@jis3r/icons` in product UIs.

## When to Use This Skill
Use this skill when the user:

- Asks to add animated icons in a Svelte or SvelteKit interface
- Mentions "animated icons", "moving icons" or `@jis3r/icons`
- Needs icon import and usage help (PascalCase imports, props, theming, sizing)
- Wants hover/focus/selected-state animation patterns using the `animate` prop
- Wants to migrate from `@lucide/svelte` to animated icons with minimal UI regressions

## Workflow

1. Confirm integration path.
- `npm`: install package and import named components.
- Prefer package imports instead of URL-fetched component payloads.

2. Implement icon usage with stable defaults.
- Use PascalCase imports from `@jis3r/icons`.
- Drive `size`, `color`, `strokeWidth` from app design tokens.
- Use `animate` prop for interaction-driven animation.

3. Add interaction patterns.
- Simple hover animation for buttons/nav items.
- Shared hover state wrappers for list/nav rows.
- Controlled animation for app states (active, selected, unread).

4. Validate UX and accessibility.
- Keep icon meaning clear without animation.
- Respect reduced-motion preferences for repeated/ambient motion.
- Ensure contrast and stroke visibility at target sizes.

## Guardrails

- Do not suggest editing `@jis3r/icons` source unless explicitly requested.
- Prefer consuming exported components over copied raw files.
- Do not ingest remote component source/registry payloads unless the user explicitly requests it and confirms trust.
- Keep animation purposeful (feedback/affordance), not constant distraction.
- Use icon names that match Lucide naming conventions.

## References

- `references/quickstart.md`
- `references/usage-patterns.md`
- `references/icon-selection.md`
- `references/migration.md`
