# Quire — design specification

Version 0.1 · 2026-09-20

## Intent

Quire is for product UIs and websites that need to be *legible as instruments* without looking like a hospital kiosk.

It takes two sources and refuses to average them into mush:

| From Carbon | From vintage aerospace reports |
|---|---|
| Role-based color tokens | Warm paper and ink, not cool gray |
| 8px spacing scale | Hairline rules instead of drop shadows |
| Explicit hover / focus / disabled | Abstract geometry used sparingly |
| Layered surfaces with named roles | Cinematic page pacing, generous air |
| Productive vs editorial type | Didot-adjacent display; not Plex everywhere |
| Accessibility as a constraint | Swiss printing: color with a job |

Carbon’s sterility comes from a single accent (IBM Blue 60), a gray-only architecture, zero radius as ideology, and type that never leaves Plex. Quire keeps the token *roles* and changes the *values*.

## Principles

1. **Paper before chrome.** Surfaces are sheets, not glass. Elevation is a rule or a shift in paper tone, not a shadow stack.
2. **One signal color.** Amber-oxide is the only action color. Teal-orbit is structural (charts, rules, diagrams), never a second button.
3. **Type has two jobs.** Newsreader speaks (titles, pull quotes, report covers). Source Sans 3 works (labels, body, controls). Mono is for values.
4. **Geometry is citation, not decoration.** Orbits, grids, and crystalline fragments appear in hero moments and empty states. They do not texture every card.
5. **Pacing over density.** Prefer one more unit of space to one more divider. Reports turned pages; screens should feel like they could.
6. **States are visible.** Hover, focus, active, selected, disabled each have a token. Do not invent one-off hex in a component.
7. **Contrast is non-negotiable.** Body text on paper ≥ 7:1. UI text ≥ 4.5:1. Focus ring ≥ 3:1 against adjacent surface.

## Color

Role tokens, not raw palette in components.

### Palette (reference)

| Name | Hex | Use |
|---|---|---|
| Paper 0 | `#f6efe2` | Page |
| Paper 1 | `#efe6d4` | Recessed / zebra |
| Paper 2 | `#e4d8c2` | Rules, chips |
| Ink 0 | `#1c1814` | Primary text |
| Ink 1 | `#4a433a` | Secondary text |
| Ink 2 | `#7a7166` | Tertiary, placeholders |
| Oxide | `#c45c1a` | Primary action, links |
| Oxide deep | `#9a4310` | Action pressed |
| Oxide mist | `#f3d9c4` | Action subtle fill |
| Orbit | `#2f5f63` | Diagrams, selected chrome |
| Orbit mist | `#d5e2e0` | Selected wash |
| Signal | `#9b2f2a` | Danger |
| Signal mist | `#f0d4d1` | Danger wash |
| Good | `#2f6b45` | Success |
| Night 0 | `#161410` | Night page |
| Night 1 | `#221e18` | Night surface |
| Phosphor | `#e8a04a` | Night accent (amber CRT) |

Oxide is burnt-sienna, not startup orange and not IBM blue. It sits next to paper the way a printed spot color sat next to uncoated stock.

### Role tokens

See `tokens/tokens.css`. Do not use palette names in components.

| Token | Paper | Night | Role |
|---|---|---|---|
| `--bg` | Paper 0 | Night 0 | Page |
| `--bg-subtle` | Paper 1 | Night 1 | Recessed band, table stripe |
| `--bg-inverse` | Ink 0 | Paper 0 | Inverse blocks |
| `--fg` | Ink 0 | `#f3ebe0` | Body / titles |
| `--fg-muted` | Ink 1 | `#c4b8a6` | Secondary |
| `--fg-subtle` | Ink 2 | `#8a7f70` | Meta, captions |
| `--fg-inverse` | Paper 0 | Ink 0 | Text on inverse |
| `--accent` | Oxide | Phosphor | Primary action, links |
| `--accent-hover` | Oxide deep | `#f0b56a` | Hover |
| `--accent-muted` | Oxide mist | `#3a2a18` | Subtle accent fill |
| `--struct` | Orbit | `#7aa3a6` | Rules that are “instrument” |
| `--struct-muted` | Orbit mist | `#243436` | Selected / chart wash |
| `--danger` | Signal | `#e07068` | Destructive |
| `--border` | `#d4c7b0` | `#3a342c` | Default hairline |
| `--border-strong` | Ink 0 | `#f3ebe0` | Emphasis rule |
| `--focus` | Oxide | Phosphor | Focus ring |
| `--overlay` | `rgba(28,24,20,.48)` | `rgba(0,0,0,.64)` | Modal veil |

### Gradients

Allowed, and this is where Quire parts from Carbon.

- **Atmosphere** — page heroes and report covers only: `var(--grad-atmosphere)`, a long paper→orbit-mist wash. Never behind body copy.
- **Scope** — empty states, loading, diagrams: a radial fade that suggests a radar bloom, not a CSS-tutorial sunset.
- **No mesh, no aurora, no three-stop rainbow.** Two stops. Low contrast. Printed, not rendered.

```css
--grad-atmosphere: linear-gradient(165deg, var(--bg) 0%, var(--struct-muted) 100%);
--grad-scope: radial-gradient(120% 80% at 80% 0%, var(--accent-muted), transparent 55%);
```

## Typography

| Role | Family | Notes |
|---|---|---|
| Display / editorial | Newsreader | Optical size via `font-optical-sizing: auto`. Weight 400–600. Slight negative tracking at ≥36px. |
| UI / body | Source Sans 3 | 400 body, 600 labels and buttons. Never light (300) for UI chrome. |
| Data / code | IBM Plex Mono | The one Carbon artifact kept on purpose. Tabular figures for numbers. |

Scale (1rem = 16px):

| Token | Size / line / weight / tracking | Use |
|---|---|---|
| `--type-display` | clamp(2.5rem, 4vw + 1rem, 4.25rem) / 1.1 / 500 / -0.02em | Cover titles |
| `--type-title` | 2rem / 1.2 / 500 / -0.015em | Page titles |
| `--type-heading` | 1.5rem / 1.25 / 500 | Section |
| `--type-subhead` | 1.125rem / 1.35 / 600 | Card titles, group |
| `--type-body` | 1.0625rem / 1.55 / 400 | Reading |
| `--type-ui` | 0.9375rem / 1.4 / 400 | Controls, nav |
| `--type-label` | 0.75rem / 1.3 / 600 / 0.06em | Uppercase meta, form labels |
| `--type-mono` | 0.8125rem / 1.45 / 400 | Values, code |

Labels are small and letterspaced. All-caps only for kicker lines of 1–4 words (`ATMOSPHERE`, `FISCAL 1968`). Do not all-caps paragraphs.

Measure: body 60–70ch.

## Layout & space

8px base, Carbon-like numbering so the muscle memory transfers.

| Token | px |
|---|---|
| `--s-01` | 2 |
| `--s-02` | 4 |
| `--s-03` | 8 |
| `--s-04` | 12 |
| `--s-05` | 16 |
| `--s-06` | 24 |
| `--s-07` | 32 |
| `--s-08` | 40 |
| `--s-09` | 48 |
| `--s-10` | 64 |
| `--s-11` | 80 |
| `--s-12` | 96 |

Page grid: 12 columns, gutter `--s-05`, max content `72rem`, page margin `--s-07` (mobile `--s-05`).

**Related things sit `--s-03`–`--s-04` apart. Groups sit `--s-07`–`--s-09` apart.** That is the whole layout system.

Radius: `--r-0: 0` (sheets, tables), `--r-1: 2px` (inputs, buttons). No pill radius except true chips.

## Line, not shadow

```css
--rule: 1px solid var(--border);
--rule-strong: 1px solid var(--border-strong);
--shadow: none;
```

If a floating panel must leave the page, use a 1px strong rule plus `--overlay` behind it. Do not stack box-shadows.

## Motion

| Token | Value |
|---|---|
| `--ease-out` | `cubic-bezier(0.22, 1, 0.36, 1)` |
| `--ease-in` | `cubic-bezier(0.64, 0, 0.78, 0)` |
| `--t-fast` | 120ms |
| `--t-mid` | 220ms |
| `--t-slow` | 400ms |

Use `--t-mid` + `--ease-out` for panels and fades. No bounce. No spring. Page transitions may fade + 8px rise.

`prefers-reduced-motion: reduce` zeroes translation and keeps opacity only.

## Iconography & diagram

- Stroke icons, 1.5px, 24px grid, square caps.
- Diagrams may use orbit circles, concentric ticks, and 30° crystalline shards — Nitsche citation, not illustration soup.
- Photography: documentary, slightly warm, full-bleed with a thin ink rule. No stock handshakes.

## Components (contracts)

Every component reads tokens only.

### Button

- `primary` — accent fill, inverse text, 2px radius, height 40px (`--s-08`).
- `ghost` — transparent, accent text, hairline on hover.
- `danger` — danger fill.
- Disabled: 40% opacity, no pointer events.

### Field

- Hairline box, paper-1 fill, label above in `--type-label`.
- Focus: 2px `--focus` ring offset 2px. No glow.
- Error: danger rule + caption.

### Panel (the “sheet”)

- Paper background, 1px `--border`, padding `--s-06`.
- Optional kicker label + Newsreader title.
- No shadow. Optional atmosphere wash via `--grad-atmosphere`.

### Rule

- Horizontal hairline. `strong` uses `--border-strong`.
- Optional label sitting on the line, paper knockout — a report running head.

### Table

- Row height 44–48px. Zebra `--bg-subtle`. Header `--type-label`.
- Numeric columns: Plex Mono, right aligned, tabular nums.

### Link

- Accent color, underline offset 3px, thickness 1px. Hover: underline thickness 2px, no second hue.

## Content voice

Write like a caption in *Dynamic America*: concrete nouns, no growth-hacking. “Backlog, $1.7 billion.” not “Unlocking next-gen synergies.”

## Anti-patterns

- IBM Blue, or any electric primary on paper.
- Gray-100 developer dark mode with neon focus.
- 16px radius cards and 32px pills.
- Inter / Roboto / system-ui as the brand face.
- Mesh gradients, glassmorphism, hero video.
- Putting Newsreader on buttons.
- Putting Source Sans on a 72px cover title.

## File map

```
DESIGN.md              this document
tokens/tokens.css      source of truth for implementation
tokens/tokens.json     same values, machine-readable
src/app.css            reset + element defaults
src/lib/*.svelte       primitives
preview.html           no-build specimen
```
