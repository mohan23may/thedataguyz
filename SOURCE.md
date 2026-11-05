# The Data Guyz — website source

Two things live in this folder.

```
thedataguyz-v4/
├─ index.html, Services.html, …      ← the built static site (deploy this)
├─ founder.jpg, .nojekyll
├─ README.md, PUSH.md
└─ source/
   ├─ build.py                        ← converter: canvas source → static site
   └─ project/
      ├─ canvas.json                  ← board layout / index
      └─ *.dc.html                    ← 11 page sources
```

## What the source files are

`project/*.dc.html` are Design-canvas artboards. Each is a normal HTML page wrapped in
`<x-dc>` with a `<helmet>` block for fonts and base CSS, plus a small `<script type="text/x-dc">`
block at the end holding preview dimensions. Two pages carry interactive state in that script:

- `Main.dc.html` — the rotating marquee hero (5 slides, 7s autoplay)
- `UseCases.dc.html` — the domain filter over the use-case library

`canvas.json` is the index: board positions, sizes, titles and reading order on the canvas.

## The 11 pages

| Source | Built as | What it is |
|---|---|---|
| `Main.dc.html` | `index.html` | Home — marquee hero, journey, four pillars, exhibits |
| `Services.dc.html` | `Services.html` | Capabilities — 4 pillars, 2 cross-pillar practices, Delivery exhibits |
| `Offers.dc.html` | `Offers.html` | Fixed-scope offer ladder |
| `Noviq.dc.html` | `Noviq.html` | Noviq / Noviq Shift product and delivery IP |
| `Modernisation.dc.html` | `Modernisation.html` | Big Data Platform Modernisation partner offering |
| `Agents.dc.html` | `Agents.html` | AI agents — knowledge engine + insight agent patterns |
| `Industries.dc.html` | `Industries.html` | Industries served |
| `Accountants.dc.html` | `Accountants.html` | AI for accountants and finance teams |
| `UseCases.dc.html` | `UseCases.html` | Filterable use-case library |
| `CaseStudies.dc.html` | `CaseStudies.html` | Delivered engagements |
| `About.dc.html` | `About.html` | About and contact |

## Rebuilding

`build.py` strips the canvas wrapper, lifts `<helmet>` into `<head>`, rewrites every
`X.dc.html` link to `X.html` (and `Main.dc.html` → `index.html`), swaps the founder
image reference for the local `founder.jpg`, and re-implements the marquee and the
use-case filter as plain vanilla JS. It exits non-zero if any template placeholder
survives into the output.

It needs Python 3 only — no packages.

```
python3 build.py
```

Edit the paths at the top of `build.py` (`BASE`) to point at wherever you put this folder.

## Editing

Two ways, and they do not sync automatically:

1. **In the canvas artifact** — visual editing, then re-export the `project/` files and
   re-run `build.py`.
2. **In these files directly** — edit the `.dc.html` source, re-run `build.py`, deploy
   the output. The built `.html` files are generated; don't hand-edit them or the next
   build overwrites your changes.

## Conventions worth keeping

- Inline styles throughout — that is what the canvas properties panel edits.
- No root-level pixel widths; `max-width` containers and
  `repeat(auto-fit, minmax(min(Npx, 100%), 1fr))` grids so pages stay fluid.
- Fonts: Plus Jakarta Sans (display), Inter (body), JetBrains Mono (micro-labels).
- Palette: navy `#0E1730` ground, primary blue `#1D4ED8`, page ground `#F6F8FC`,
  cyan `#5FD4E4` on dark. Pillar accents: blue `#1D4ED8`, teal `#0E6B7A`, amber `#9A4A08`.
- 8px card radius, 6px flow boxes, 999px pills.
- Diagrams are built from separate flex/grid elements joined by small chevron SVGs,
  never one large `<svg>` — so they reflow and stay editable.

## Deploying

See `PUSH.md` for the GitHub Pages steps. `.nojekyll` is required so GitHub serves the
files as-is.
