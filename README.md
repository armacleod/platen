# Quire

A design system for sites and Svelte apps that should feel like a mid-century aerospace annual report that learned tokens from IBM Carbon.

**Specimen:** [armacleod.github.io/quire](https://armacleod.github.io/quire)

Carbon is systematic. The Nitsche-era General Dynamics reports were systematic *and* warm: paper, ink, orbital color, cinematic pacing, hairline rules. Quire keeps Carbon’s discipline (role-based tokens, an 8px spacing scale, explicit states) and drops the fluorescent blue, the gray-on-gray layering, and the clinical flatness.

**Not a Carbon fork.** Steal the *method*. Leave the IBM livery.

## Use it

```css
@import './tokens/tokens.css';
```

Or copy `src/lib` into a SvelteKit project. See [DESIGN.md](./DESIGN.md).

## Stack

- Tokens: plain CSS custom properties
- Components: Svelte 5
- Type: Newsreader + Source Sans 3 + IBM Plex Mono
- Reference site: `index.html` (self-contained), deployed via GitHub Pages

## Themes

`data-theme="paper"` (default) and `data-theme="night"` on `<html>`.
