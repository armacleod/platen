# Platen 1.0

A design system for sites and Svelte apps: the ledger and the void.

**Specimen:** [armacleod.github.io/quire](https://armacleod.github.io/quire)
**Spec:** [DESIGN.md](./DESIGN.md)

A sheet field for work, a void field for orientation. Every page uses both.
One signal hue (ember). Slate structures. Grotesk type set by width and weight.
Section-cut geometry. No shadows.

## Use it

```css
@import './tokens/tokens.css';
```

Copy `src/lib` into a Svelte project. Primitives: Button, Field, Panel,
Rule, Badge, Notice, Tabs, Dialog. See DESIGN.md.

## Stack

- Tokens: plain CSS custom properties, three tiers
- Components: Svelte 5
- Type: Archivo (800 display, normal width) + IBM Plex Mono
- Reference site: `index.html` (self-contained), deployed via GitHub Pages

## Themes

`data-theme="sheet"` (default) and `data-theme="void"` on `<html>`.
