# braickish.github.io

The Braickish homepage, served at https://braickish.github.io/ (GitHub Pages from `main`, repo root).

- One static page: `index.html` (inline CSS/JS, Google Fonts only) plus `favicon.svg`. No build step.
- Black-and-white styling. The page leads with a dictionary-style definition of "brackish" and ends with `hello@braickish.com`.
- The logo is an inline SVG: one `<text>` word drawn twice and clipped along a diagonal. The left half is
  "hand-drawn" (hatched fill + wobbly outlines via `feTurbulence`/`feDisplacementMap`, with a small "line boil"
  animation that is skipped for reduced motion). The right half is crisp and solid, with type-design guide lines.
  The seam runs through the "ai" in the middle of the word. To move it, change both clip polygons and `#seam`.
- To preview: open `index.html` in a browser. Screenshots: `npx playwright screenshot --channel chrome file://$PWD/index.html out.png`.
