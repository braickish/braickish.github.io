# braickish.github.io

The Braickish homepage, served at https://braickish.github.io/ (GitHub Pages from `main`, repo root).

- One static page: `index.html` (inline CSS/JS, Google Fonts only) plus `favicon.svg`. No build step.
- Black-and-white styling. The page leads with a dictionary-style definition of "brackish" and has two senses: the dictionary meaning, then
  "(also br·ai·ck·ish)", where AI and human currents mix. It ends with `hello@braickish.com`.
- The logo is an inline SVG: one `<text>` word drawn twice and clipped along a diagonal seam.
  - Left half is a dense pen scribble with no outline, modelled on the middle "P" in
    `braickish/reference-images/handwritten-letters.jpg`. `buildScribble()` in the script rasterizes the word to a
    canvas mask, then a simulated pen wanders in loops inside it and hairpins back at the edges. Short strokes restart
    in the least-inked cells. It is seeded, so the result is static and identical on every load (no animation; the user
    found the line boil gimmicky). Pen weights are split across `#scrib-a/b/c`, with a light static `#ink` filter.
    To tune the look, edit `budget` (density), `n` (stroke length), the `om` curvature limits (loop size) and `LOOK`.
  - Right half is crisp solid black with type-design guide lines.
  - The seam is draggable: drag anywhere on the logo, or focus the round grip (`role="slider"`) and use the arrow
    keys, Page Up/Down, Home or End. The script sets both clip polygons, `#seam` and the grip from one value, `c`.
    It defaults to 370 (through the "ai"), and a short sweep on load shows that it moves.
- To preview: open `index.html` in a browser. Screenshots: `npx playwright screenshot --channel chrome --wait-for-timeout=2500 file://$PWD/index.html out.png`.
