# braickish.github.io

The Braickish homepage, served at https://braickish.github.io/ (GitHub Pages from `main`, repo root).

- One static page: `index.html` (inline CSS/JS, Google Fonts only) plus `favicon.svg`. No build step.
- Black-and-white styling. The page leads with a dictionary-style definition of "brackish" and has two senses: the dictionary meaning, then
  "(also br·ai·ck·ish)", where AI and human currents mix. It ends with `hello@braickish.com`.
- The logo is an inline SVG: one `<text>` word drawn twice and clipped along a diagonal seam.
  - Left half is charcoal, modelled on the bottom-left "P" in `braickish/reference-images/handwritten-letters.jpg`.
    The user tried a pen-and-ink version and then a scribble (the second lost the letter shapes) before choosing this.
    `buildCharcoal()` rasterizes the word to a canvas mask, then lays overlapping horizontal swipes row by row across
    each letter. Each swipe has its own opacity (pressure), slight tilt, tapered ragged ends, and the odd longer drag
    past the edge. The `#charcoal` filter adds a little fray, a soft falloff and horizontal paper tooth. Everything is
    seeded and static; keep motion out of the letters (the user found the old line boil gimmicky).
    To tune it: row spacing and `half` (swipe width), the overshoot amounts on `x0`/`x1`, the opacity `a`, and the tooth matrix.
  - Right half is crisp solid black with type-design guide lines.
  - The seam is draggable: drag anywhere on the logo, or focus the round grip (`role="slider"`) and use the arrow
    keys, Page Up/Down, Home or End. The script sets both clip polygons, `#seam` and the grip from one value, `c`.
    It defaults to 370 (through the "ai"), and a short sweep on load shows that it moves.
- To preview: open `index.html` in a browser. Screenshots: `npx playwright screenshot --channel chrome --wait-for-timeout=2500 file://$PWD/index.html out.png`.
