# Icon Selection

## Naming Model

The library follows Lucide-style names:

- file name: kebab-case (`alarm-clock`, `arrow-right`)
- import name: PascalCase (`AlarmClock`, `ArrowRight`)

## Practical Selection Process

1. Start with semantic intent (alert, success, navigation, data, settings).
2. Search your project's available `@jis3r/icons` exports by name/category intent.
3. Test at real UI sizes (16, 20, 24) with your stroke width.
4. Keep one icon style per feature area for consistency.

## Common UI Mapping

- Alerts: `Bell`, `CircleAlert`, `BadgeAlert`
- Confirmations: `Check`, `CircleCheck`, `BadgeCheck`
- Navigation: `ArrowRight`, `ChevronRight`, `Home`
- Settings/admin: `Cog`, `SlidersHorizontal`, `ShieldCheck`
- Data: `ChartBar`, `ChartPie`, `Gauge`

## Consistency Rules

- Avoid mixing multiple near-synonyms in the same UI surface.
- Keep stroke width aligned across siblings.
- Use animation sparingly for focus/feedback, not all icons at once.
