# Quire

A design system for sites and Svelte apps that should feel like a mid-century aerospace annual report that learned tokens from IBM Carbon.

Carbon is systematic. The Nitsche-era General Dynamics reports were systematic *and* warm: paper, ink, orbital color, cinematic pacing, hairline rules. Quire keeps Carbon’s discipline (role-based tokens, an 8px spacing scale, explicit states) and drops the fluorescent blue, the gray-on-gray layering, and the clinical flatness.

**Not a Carbon fork.** Steal the *method*. Leave the IBM livery.

## Use it

```bash
# tokens only
@import '@your-path/tokens/tokens.css';

# or copy src/lib into a SvelteKit project
```

See [DESIGN.md](./DESIGN.md) for principles, palette, type, motion, and component contracts.

Open `preview.html` locally for a no-build specimen (Paper / Night toggle).

## Stack

- Tokens: plain CSS custom properties (no Sass required)
- Components: Svelte 5
- Type: [Newsreader](https://fonts.google.com/specimen/Newsreader) + [Source Sans 3](https://fonts.google.com/specimen/Source+Sans+3) + [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono)

## Themes

`data-theme="paper"` (default) and `data-theme="night"` on `<html>`.
