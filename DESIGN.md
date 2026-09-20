# Quire — design specification

Version 0.2 · 2026-09-20

## Diagnosis (0.1)

Version 0.1 used uncoated cream, burnt sienna, and a book serif (Newsreader) as the product voice. That combination is the current default for “serious technology that wants to feel human”: Anthropic / Claude (ivory `#faf9f5`, clay `#c96442`–`#d97757`, proprietary serif), and a large set of 2024–2026 AI and editorial SaaS sites that copied it.

It is also a misreading of the source. Erik Nitsche’s General Dynamics work was Swiss modernism applied to a defense contractor: white or cool fields, jewel teal and primary pigment, small discrete type (Didot on posters, not a soft reading serif on every heading), geometry as diagram. Warmth came from printing and photography, not from a yellowed canvas and terracotta buttons.

0.2 throws out the salon palette and the serif-as-personality rule.

## Intent

Quire is a token system and a small set of Svelte primitives for sites and apps that should read as instruments: grid, hairline, one accent, no chrome.

It keeps Carbon’s method (named roles, 8px space, explicit states) and takes from mid-century aerospace reports only what survives without costume: pacing, line instead of shadow, diagram geometry used rarely.

## What this is not

- Not cream paper, clay/terracotta, oat, olive, or “warm gray.”
- Not a book serif for product UI.
- Not IBM Blue on Cool Gray 10.
- Not amber-on-charcoal “CRT night.”
- Not Inter, Geist, or system-ui as the brand face.
- Not marketing copy that performs taste.

## Principles

1. **Sheet, not glass.** Elevation is a 1px rule or a shift in canvas tone.
2. **One chromatic action.** Teal is accent and structure. Red is only danger. There is no second brand hue for buttons.
3. **One grotesque, one mono.** Headings are the UI face at a larger size. Mono is for figures and code.
4. **Geometry is a diagram.** Concentric ticks and orbits belong on empty states and covers. They are not card texture.
5. **Space is the hierarchy.** Related: 8–12px. Groups: 32–48px.
6. **States are tokens.** Hover, focus, active, selected, disabled are named. No hex in component files.
7. **Contrast.** Body on canvas ≥ 7:1. UI text ≥ 4.5:1. Focus ≥ 3:1 against its neighbor.

## Color

Cool uncoated stock, near-black ink, jewel teal.

| Name | Hex | Note |
|---|---|---|
| Canvas 0 | `#F3F4F2` | Page. Cool, slightly green-gray. Not ivory. |
| Canvas 1 | `#E6E8E5` | Recessed band, zebra |
| Ink 0 | `#16181A` | Text |
| Teal | `#0B6E73` | Accent, links, focus |
| Teal deep | `#08575B` | Hover |
| Teal wash | `#D4E6E6` | Subtle fill |
| Red | `#B31B1B` | Danger only |
| Night 0 | `#0E1112` | Night page |
| Night teal | `#5EB8BC` | Night accent (same hue, not amber) |

Role tokens live in `tokens/tokens.css`. `--struct` and `--accent` share a hue on purpose.

## Typography

IBM Plex Sans for display, heading, UI, and body. IBM Plex Mono for figures and code. Didot is allowed only on a printed cover; it is not shipped in the web tokens.

## Layout

8px scale. Page max `72rem`. Hairline rules, no shadow. Radius 0 on sheets, 2px on controls.

## Voice

Captions, not slogans.

## Anti-patterns

Cream/ivory canvases. Terracotta/clay/rust accents. Book serifs in product UI. Phosphor amber dark mode. IBM Blue 60. Inter/Geist. A second chromatic button color.
