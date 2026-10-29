# BioInterpreter AI - Landing Page

The landing page for [biointerpreter.ai](https://biointerpreter.ai). It shows a field of about 2,600 light
particles that form, one after another, seven layers of biological data. At the end the particles
gather into a "tame AI" that interprets them all.

## Files

```
bia/
├── index.html      # Current landing page (v2): HTML, CSS and JavaScript in one file
├── index-v1.html   # First version of the page (kept for reference)
├── CNAME           # Custom domain for GitHub Pages
└── README.md
```

The page has no external dependencies, build step or framework. Open `index.html` in a browser to
view it locally.

## What the page shows

The particles change shape every ~9 seconds, cycling through:

| # | Layer          | Structure drawn                                                    |
|---|----------------|--------------------------------------------------------------------|
| 1 | Genome         | DNA double helix with base pairs and 5′/3′ ends                    |
| 2 | Transcriptome  | Transfer RNA cloverleaf (acceptor stem, D-arm, anticodon, TΨC-arm) |
| 3 | Proteome       | Folded protein: α-helices around a twisted β-sheet                 |
| 4 | Metabolome     | Metabolic network with flux flowing along its edges                |
| 5 | Cell           | Membrane, nucleus, mitochondria, endoplasmic reticulum, vesicles   |
| 6 | Species        | Circular tree of life with nine model organisms, rooted at LUCA    |
| 7 | Interpretation | A bright core held inside rotating rings (the tame AI)             |

Around the structure:

- **Orbiting text ring**: content changes with the layer (DNA bases, RNA bases, amino acids,
  chemical formulas, cell types, species names).
- **Light scan**: a beam sweeps each new structure, carried over from v1.
- **Interpretation stream**: a console that types what the AI is "reading" in each layer.
- **Ticker**: omics types, species and molecule classes.

Visitors can click a layer in the list, or use the left/right arrow keys, to jump to it. Moving the
mouse tilts the view and pushes nearby particles away.

## How it works

- All drawing happens on one `<canvas>` using the 2D API, with a simple 3D projection.
- Each layer is built from weighted pieces (curves, blobs, shells). Particles are spread across the
  pieces in proportion to their weight.
- A seeded random number generator makes the structures identical on every visit.
- Moving between layers, each particle eases from its current position to its new one while
  spiralling around the vertical axis.

## Accessibility

- With "reduce motion" turned on in the operating system, the page shows a still image and the full
  text, with no animation.
- The canvas is hidden from screen readers, and a text description of the animation is provided instead.

## Browser support

Tested in Chrome (desktop and phone-sized screens). It uses only standard features (canvas 2D, CSS
grid, `backdrop-filter`), so recent Safari, Firefox and Edge should work, but they have not been
tested yet.

## License

© biodavidjm
