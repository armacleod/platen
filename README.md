# Quire

Token system and Svelte primitives. Two fields (void, sheet) and three signals (beacon, flare, abort). Clusters instead of card layers.

Void is the default operating field. Sheet is print and daylight.

Not a Carbon recolor. Not cream-and-serif.

**Spec:** [DESIGN.md](./DESIGN.md)  
**Specimen:** [index.html](./index.html)

```css
@import './tokens/tokens.css';
```

```html
<html data-field="void">
```

Copy `src/lib` into a SvelteKit project. Version 0.3.
