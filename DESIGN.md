# Quire — design specification

Version 0.5 · 2026-09-20

## Brief

Print ancestry. Void as distance. Dual-use tension. No costume.

## Rejected streets

| Version | Collision |
|---|---|
| 0.1 | Anthropic: cream, clay, book serif |
| 0.2 | Carbon: teal, Plex, layer stack |
| 0.3 | Blockstream: void, cyan, gold, orbits |
| 0.4 | S&P Global: paper, process red, offset slabs |

## Model

**Plate is the page.** Iron blue — press ink, hydrodynamics plate — is the default field.

**Paper is type and wells.** White sits on the plate. A paper well is a document, not the chrome.

**No brand chroma.** Keys are paper-on-ink or hairline. Charts may use a lighter cut of the same ink. No red, no cyan, no gold as identity.

**Mark is a section cut.** One isobar. Not rings. Not Mondrian slabs.

**Clusters, not layers.** Hairline frame, legend, silence.

## Color

### Plate (default · `data-field="plate"`)

| Token | Hex |
|---|---|
| `--plate` | `#182436` |
| `--plate-lift` | `#223044` |
| `--paper` | `#E7EBF0` |
| `--meta` | `#8A96A4` |
| `--rule` | `#3A4A5C` |
| `--plot` | `#C5D0DC` |

`--accent` maps to `--paper`. Inverse text on a live key is `--plate`.

### Sheet well (`data-field="sheet"`)

Paper field `#E7EBF0`, plate text `#182436`, hairline `#C3CAD2`. Same rule: no second hue.

## Type

Source Sans 3. Source Code Pro for figures. Sentence case. No condensed all-caps hero.

## Space

8px series. Radius 0 on clusters; 2px on keys and fields.

## Motion

120ms hover. No sweep.

## Geometry

Allowed: a single isobar, parallel section ticks, a truncated curve.

Forbidden: concentric rings, Venn, offset rectangles, starfield, red slabs.

## Components

**Key, live** — paper fill, plate text.
**Key, quiet** — hairline paper.
**Key, halt** — hairline, meta text.
**Well** — paper inset on the plate.
**Cluster** — hairline, legend.

## Anti-patterns

Cream, clay, process red, IBM Blue, cyan-on-black, gold lamps. Plex, Inter, Rigid Square, Geist, Orbitron. Book serifs in product UI. Card elevation. Slogans.
