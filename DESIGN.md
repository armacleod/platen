# Platen 1.0 — design specification

Version 1.0 · 2026-09-20 · Rebuilt from principles. Supersedes 0.1–0.6.

## Thesis

Platen is the ledger and the void.

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
2. **Ember acts; red warns.** Ember is the only action color. Signal red
   appears solely on destructive controls in hover and active states — never
   at rest, never as decoration. No two solid buttons share a hue family.
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
   system may drop below 4.5:1. Void grounds are explicitly scoped with a
   nested data-theme (or fixed values) so a page-theme switch cannot silently
   recolor them; components inside a scoped ground read that ground's tokens.

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

Space is a token. Alignment is a rule. Parent containers own gaps.
Children do not add margins in compositions.

Scale: 8px base. `--s-01` 2 through `--s-12` 96. Page max 76rem,
gutter 16px, page margin 32px (16px mobile). Related items sit
8–12px apart (`--s-03`, `--s-04`). Groups sit 24–32px apart
(`--s-06`, `--s-07`). Sections sit 64–96px apart (`--s-10`, `--s-12`).

### Spacing ownership

- The parent sets `gap`. Children set `margin: 0`.
- Never combine parent `gap` with child bottom margins in the same axis.
  Double spacing drifts baselines and breaks the grid.
- Type styles carry reading margins (`p`, `h1–h3`). Reset to `margin: 0`
  when type is used as a label inside a component (field label, caption,
  badge text). The component gap then owns the rhythm.

### Stack and row

Use two compositions only.

- **Stack**: vertical `display: flex; flex-direction: column`. Owns
  label-to-input (`--s-02`), input-to-help (`--s-02`), and
  group spacing (`--s-05` to `--s-07`).
- **Row (cluster)**: horizontal `display: flex; flex-wrap: wrap;
  gap: var(--s-04)`. Wrap is required. Pick alignment by content:

| Row content | `align-items` | Why |
|---|---|---|
| Single-line controls (buttons, badges of one size) | `center` | Shared center line reads as one toolbar |
| Mixed-size controls shown as a ramp | `flex-end` | Shared bottom line proves the size steps |
| Form fields with labels, hints, or errors | `flex-start` | Shared top line; help text extends down without lifting inputs |
| Cards, notices, panels with different copy lengths | `stretch` | Equal height; inner content starts at the top |

Default to `flex-start` when unsure. `center` is only for rows
where every item is one line and the same height. Never use `center`
to align multi-line cards. Never use `flex-end` to align fields:
the taller field (with help or error) pulls its input out of line.

### Form rows

Tether to the top line.

- Row uses `align-items: flex-start`.
- Each field is a stack: label, input, then help or error. Help and
  error occupy the same slot below the input so swapping them does
  not move the input.
- Error uses a 2px border with `box-sizing: border-box` at the same
  outer `height` as rest, so invalid does not shift the row.
- Reserve the help slot only when rows must not move at all
  (dense tables, dialogs). Otherwise let help extend the field down.

### Card rows

Tether to the top line and stretch to equal height.

- Row uses `align-items: stretch`.
- Each card uses `min-width: 16rem; flex: 1` so wrapping keeps
  a readable measure.
- Inside the card, content starts at the top (`align-items: start`
  or default block flow). Anchor bars (`Notice`) span full height.
- Do not vertically center card bodies. Centering leaves both the
  top and bottom edges floating, so no edge proves alignment.

### Grid

Grid: 12 columns, Swiss asymmetric placement. Media spans fields.
Gutter is `--gutter` (16px). A visible grid overlay is part of the
specimen to prove alignment. Grid children align to `start` unless
a hero explicitly centers one band.

### Type in compositions

Kickers, badges, and captions use `margin: 0` inside fields, notices,
and panels. The specimen resets `.field .kicker` and `.notice strong`
spacing for this reason. Body copy keeps its reading margins outside
compositions only.

Radius: 0 for sheets and tables, 2px for inputs and buttons,
999px for badges only. Bars: 8px strong rule as anchor, 1px hairlines for tables.

## Motion

`--t-fast` 120ms, `--t-mid` 220ms, `--t-slow` 400ms.
`--ease-out` cubic-bezier(0.22, 1, 0.36, 1). Panels fade with an 8px rise.
No bounce, no spring. `prefers-reduced-motion` keeps opacity only.

## Mark and diagram

The Platen section-mark: a 32-unit square, ink hairline border, internal
cross at thirds, one ember quadrant. Drawn as SVG in the specimen and as
`mark.svg`. Diagram vocabulary: crosshairs, section-cuts, contour ticks,
fragment bars, dotted leaders. No orbits, no radar sweeps, no glow.

## Components

Every component reads tokens only. Sizes sm/md/lg where applicable.
Minimum target 24px; buttons ship 28/40/48px.

- **Button**: primary (ember fill), secondary (strong-rule outline),
  ghost (accent text), danger (inverse-field rest, signal-red hover and
  active; cold at rest so it cannot read as primary, armed on contact).
  Destructive actions use destructive verbs.
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
