# Quickstart

Requires Svelte 5.

## Install via npm

```bash
npm i @jis3r/icons
```

```svelte
<script>
  import { Activity, Bell } from '@jis3r/icons';
</script>

<Activity size={20} />
<Bell size={20} color="var(--color-primary)" />
```

Install and consume via npm exports by default. Avoid URL-based component ingestion unless explicitly approved.

```bash
npm i @jis3r/icons
```

## Core Props

- `size` (number, default `24`)
- `color` (string, default `'currentColor'`)
- `strokeWidth` (number, default `2`)
- `class` (string)
- `animate` (boolean, default `false`)

## Immediate Rule of Thumb

- For static icon display: omit `animate`.
- For interaction feedback: bind `animate` to hover/focus/selected state.
