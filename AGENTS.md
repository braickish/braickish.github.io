# braickish.github.io

The Braickish homepage, served at https://braickish.github.io/ (GitHub Pages from `main`, repo root).

- One static page: `index.html` (inline CSS/JS, Google Fonts only) plus `favicon.svg`. No build step.
- Black-and-white styling. The page leads with a dictionary-style definition of "brackish" and has two senses: the dictionary meaning, then
  "(also br·ai·ck·ish)", a disquieting mix of human and AI work. A subtle tagline inside the logo SVG, tucked under
  the word and right-aligned to the end of the "h", reads "where interesting things tend to grow". It is clipped to the computer-drawn side, so swiping toward
  hand-drawn wipes it away and reveals a black-and-white 🌱 (the emoji run through the `#mono` filter) at the far right Use the user's wording exactly. It ends with `hello@braickish.com`.
- The logo is an inline SVG: one `<text>` word drawn twice and clipped along a diagonal seam.
  - Left half is a charcoal/watercolour wash, matched to the bottom-left "P" in
    `braickish/reference-images/handwritten-letters.jpg` by tuning a single P side by side with the reference first.
    Earlier tries (pen and ink, scribble, generated swipes, pure SVG filters) didn't feel hand-made enough.
    `paintCharcoal()` paints it pixel by pixel into a canvas, which is shown as the `#charcoal` `<image>`:
    letter mask (slightly wobbled) -> soft vertical edge -> horizontal box blurs with a per-row threshold. Each row
    either reaches past the edge (a feathered finger) or nibbles into it, so stems stay whole. A finger reaches at most 2.4 units past the outline
    (`maxReach`) and at most about a fifth of any gap (`maxShare`); edges nibble in at most about 1.8 units, so letters never bleed into each other. Each letter is painted as
    its own drawing (own noise offsets, stroke tilt, height offset and pressure; fingers in a gap belong to the letter
    they grew from), so brush rows never line up across the word. Then the tone:
    brush-row bands, broad wash patches, short broken pale streaks, wet-edge pooling, mottling and grain.
    It is seeded and static (keep motion out of the letters) and takes about 60-90 ms once on load.
    Resolution follows the logo's on-screen size times the device pixel ratio.
  - Right half is crisp solid black with type-design guide lines.
  - The seam is draggable: drag anywhere on the logo, or focus the round grip (`role="slider"`) and use the arrow
    keys, Page Up/Down, Home or End. The script sets both clip polygons, `#seam` and the grip from one value, `c`.
    It defaults to 370 (through the "ai"), and a short sweep on load shows that it moves.
- To preview: open `index.html` in a browser. Screenshots: `npx playwright screenshot --channel chrome --wait-for-timeout=2500 file://$PWD/index.html out.png`.
