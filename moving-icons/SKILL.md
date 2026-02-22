---
name: moving-icons
description: Integrate and use the Moving Icons library (`@jis3r/icons`) in Svelte 5/SvelteKit apps. Use when users ask for animated (Lucide-style) icons in Svelte, mention movingicons.dev or `@jis3r/icons`, need installation (npm or shadcn-svelte registry), icon import/usage patterns, hover-controlled animation with the `animate` prop, icon selection, theming, sizing, or migration from `@lucide/svelte` to animated icons.
---

# Moving Icons

This skill helps to integrate animated icons into Svelte/SvelteKit apps and consume `@jis3r/icons` in product UIs.

## When to Use This Skill
Use this skill when the user:

- Asks to add animated icons in a Svelte or SvelteKit interface
- Mentions `@jis3r/icons`, movingicons.dev, or "moving icons"
- Needs install/setup help via npm or shadcn-svelte registry commands
- Needs icon import and usage help (PascalCase imports, props, theming, sizing)
- Wants hover/focus/selected-state animation patterns using the `animate` prop
- Wants to migrate from `@lucide/svelte` to animated icons with minimal UI regressions

## Workflow

1. Confirm integration path.
- `npm`: install package and import named components.
- `shadcn-svelte registry`: add single icons as local component files.
- direct copy: paste component source from movingicons.dev if needed.

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
- Keep animation purposeful (feedback/affordance), not constant distraction.
- Use icon names that match Lucide naming conventions.

## References

- `references/quickstart.md`
- `references/usage-patterns.md`
- `references/icon-selection.md`
- `references/migration.md`
