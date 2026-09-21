# Quire 1.0 — design specification

Version 1.0 · 2026-09-20 · Rebuilt from principles. Supersedes 0.1–0.6.

## Thesis

Quire is the ledger and the void.

- The **sheet** is a neutral document field for reading and work.
- The **void** is a near-black instrument field for orientation, figures, and covers.
- Every page uses both. Optimism and threat share the frame: the sheet states
  plain facts, the void holds what is still unresolved.

This is the break from 0.1–0.6. No warm cream and clay book-serif edition.
No gray-and-blue Carbon copy. No cyan lamp, gold companion, or orbit marks.
No off-white and process-red slabs. No amber CRT night.

## Principles

1. **Two fields, one page.** Sheet grounds work. Void grounds orientation.
   A page without void has no tension. A page without sheet has no record.
2. **One signal hue.** Ember acts. Slate structures. Nothing else competes.
3. **Type is grotesk, set by weight.** Archivo Black speaks
   on covers at normal width. Archivo works in UI. Plex Mono counts values. No book serif.
4. **The mark is a section-cut, not an orbit.** A quartered square with one
   ember quadrant and a registration cross. Target, drawing, and record.
5. **Line before shadow.** Elevation is a rule or a tone shift. No shadows.
6. **States are tokens.** Hover, active, selected, disabled, and focus each
   read a token. No one-off hex in components.
7. **Contrast is a constraint.** Body ink on sheet 16:1. Ember text variants
   pass 4.5:1 minimum. Focus rings pass 3:1 against adjacent grounds.
   Danger behaves like an e-stop: always solid, always legible; hover moves
   toward alarm (brighter), never toward wash. No hover state anywhere in the
   system may drop below 4.5:1. Void grounds carry explicit values, never
   page-theme variables, so a theme switch cannot silently recolor them.

## Color

Primitives are reference only. Components use semantic roles.

| Primitive | Hex | Job |
|---|---|---|
| Paper | `#f2f1ec` | Sheet ground (neutral, not cream) |
| Paper deep | `#e7e4d9` | Recessed bands, zebra |
| Ink | `#131316` | Text, strong rules |
| Void | `#0b0d10` | Instrument ground |
| Void raised | `#14181d` | Raised void surfaces |
| Ember fill | `#b93305` | Primary fill on sheet |
| Ember deep | `#9a2b00` | Text and links on sheet |
| Ember bright | `#e8440a` | Graphics on sheet (3:1 uses only) |
| Ember void | `#ff6b2c` | Action on void |
| Ember wash | `#f6d9cb` | Subtle ember field on sheet |
| Slate | `#3a4a5a` | Technical linework, secondary text structures |
| Slate mist | `#dde3e9` | Structural wash |
| Crimson | `#a6192e` | Danger on sheet |
| Pine | `#1e6b45` | Success on sheet |

Roles (see `tokens/tokens.css`): `--bg`, `--bg-subtle`, `--bg-raised`,
`--bg-inverse`, `--fg`, `--fg-muted`, `--fg-subtle`, `--fg-inverse`,
`--fg-on-fill`, `--accent`, `--accent-fill`, `--accent-hover`,
`--accent-active`, `--accent-muted`, `--struct`, `--struct-muted`,
`--danger`, `--success`, `--border`, `--border-strong`, `--focus`, `--overlay`.

Measured pairs: sheet ink 16.4:1, ember deep 6.8:1, primary fill with white
5.9:1, void text 16.8:1, void ember 6.9:1, void fill with ink 6.5:1.

### Gradients

Two are allowed. Both are printing moves, not rendering moves.

- `--grad-fountain`: split-fountain sheet-to-slate-mist band for hero bands only.
- `--grad-void-bloom`: faint ember bloom on void grounds only.
- Two stops. Low contrast. Never behind body copy.

## Typography

| Role | Face | Notes |
|---|---|---|
| Cover and title | Archivo 800, normal width | Tight, −0.02em, sentence case |
| UI and body | Archivo 400/600 | Left aligned, ragged right |
| Values | IBM Plex Mono 400/500 | Tabular figures, uppercase labels |

Scale: display clamp(2.75rem, 5vw + 1rem, 4.75rem)/1.02, title 2rem/1.1,
heading 1.375rem/1.2, subhead 1.0625rem/1.35, body 1.0625rem/1.6,
UI 0.9375rem/1.45, label 0.75rem/1.3 tracked +0.06–0.1em, mono 0.8125rem/1.5.
Body measure 60–68ch. Kickers are 1–4 words uppercase. Never all-caps paragraphs.

## Layout and space

8px base. `--s-01` 2 through `--s-12` 96. Page max 76rem, gutter 16px,
page margin 32px (16px mobile). Related items sit 8–12px apart.
Groups sit 32–48px apart. Sections sit 64–96px apart.

Grid: 12 columns, Swiss asymmetric placement. Media spans fields.
A visible grid overlay is part of the specimen to prove alignment.

Radius: 0 for sheets and tables, 2px for inputs and buttons,
999px for badges only. Bars: 8px strong rule as anchor, 1px hairlines for tables.

## Motion

`--t-fast` 120ms, `--t-mid` 220ms, `--t-slow` 400ms.
`--ease-out` cubic-bezier(0.22, 1, 0.36, 1). Panels fade with an 8px rise.
No bounce, no spring. `prefers-reduced-motion` keeps opacity only.

## Mark and diagram

The Quire section-mark: a 32-unit square, ink hairline border, internal
cross at thirds, one ember quadrant. Drawn as SVG in the specimen and as
`mark.svg`. Diagram vocabulary: crosshairs, section-cuts, contour ticks,
fragment bars, dotted leaders. No orbits, no radar sweeps, no glow.

## Components

Every component reads tokens only. Sizes sm/md/lg where applicable.
Minimum target 24px; buttons ship 28/40/48px.

- **Button**: primary (ember fill), secondary (strong-rule outline),
  ghost (accent text), danger (solid deep-crimson fill, darker and cooler than
  ember so the two never read alike; hover jumps to vivid signal red,
  active drops to near-black maroon). Explicit hover and active tokens.
- **Field**: raised fill, hairline, label above, 2px focus ring offset 2px,
  2px danger rule with caption on error.
- **Badge**: uppercase mono-adjacent label, full radius, four tones.
- **Notice**: 4px anchor bar with info, danger, and success tones.
- **Panel**: sheet with hairline; void variant with ember bloom allowed.
- **Rule**: hairline or strong; optional running-head label.
- **Tabs**: strong underline for the section, ember underline for selection.
- **Dialog**: void veil, sheet with strong rule. No shadow.
- **Table**: 44–48px rows, zebra subtle, label header, mono numerals right.

## Voice

Plain and timeless. Concrete nouns. Verb-first actions.
Empty states state the fact and the next step. No puns, no awe.

## File map

```
DESIGN.md            this document
tokens/tokens.css    source of truth
tokens/tokens.json   machine-readable roles plus measured contrast
src/app.css          reset and element defaults
src/lib/*.svelte     Button Field Panel Rule Badge Notice Tabs Dialog
index.html           self-contained specimen, deployed via Pages
```
