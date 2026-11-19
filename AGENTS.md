# braickish.github.io

The Braickish homepage, served at https://braickish.github.io/ (GitHub Pages from `main`, repo root).

- One static page: `index.html` (inline CSS/JS, Google Fonts only) plus `favicon.svg`. No build step.
- Black-and-white styling. The page leads with a dictionary-style definition of "brackish" and ends with `hello@braickish.com`.
- The logo is an inline SVG: one `<text>` word drawn twice and clipped along a diagonal seam.
  - Left half is pen and ink: wobbly outlines, hatching, and cross-hatch shading on the lower part of the letters,
    plus a few ink spatters. The `ink-*` filters displace the shapes with `feTurbulence`, blur them slightly, then
    sharpen the alpha back up so edges pool and taper like ink. A small "line boil" re-seeds the noise; it's skipped
    for reduced motion.
  - Right half is crisp solid black with type-design guide lines.
  - The seam is draggable: drag anywhere on the logo, or focus the round grip (`role="slider"`) and use the arrow
    keys, Page Up/Down, Home or End. The script sets both clip polygons, `#seam` and the grip from one value, `c`.
    It defaults to 370 (through the "ai"), and a short sweep on load shows that it moves.
- To preview: open `index.html` in a browser. Screenshots: `npx playwright screenshot --channel chrome --wait-for-timeout=2500 file://$PWD/index.html out.png`.
