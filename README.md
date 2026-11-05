# thedataguyz.com

Static website for **The Data Guyz** — data advisory, cloud strategy, AI adoption and insights & analytics.

| File | Page |
|---|---|
| `index.html` | Home — marquee hero, logo walls, six-foundation journey, Exhibits 01–04 |
| `Services.html` | Capabilities — the four pillars |
| `Solutions.html` | Our IP — accelerators (Noviq, Noviq Shift) and foundations |
| `Offers.html` | Offer catalogue — 7 packages plus entry offers |
| `Industries.html` | Industries and verticals |
| `UseCases.html` | Use-case library (36 entries, filterable) |
| `CaseStudies.html` | Case studies |
| `About.html` | About and contact |
| `founder.jpg` | Founder portrait |

## Stack

Plain static HTML — no build step, no framework, no dependencies. Fonts load from Google Fonts;
everything else is inline. Two pages carry a small vanilla-JS block at the end of the file:
the hero marquee on `index.html` and the domain filter on `UseCases.html`.

## Running locally

    python3 -m http.server 8000

## Publishing on GitHub Pages

Settings → Pages → Deploy from a branch → `main` / root. `.nojekyll` is included.

## Before launch

- Swap the typographic client tiles on `index.html` for real client logo files, where permission allows
- Swap the inline SVG partner and certification glyphs for the official badge artwork
- Replace the inline SVG wordmark with the real logo file
- Fill the `[YOUR PRICE]`, `[BOOKING LINK]` and `[YOUR PHONE NUMBER]` placeholders
- Wire the contact form on `About.html` to a real enquiry handler and add the privacy notice
- Verify the third-party statistics cited on `index.html` (Gartner, ADAPT, S&P Global) are still current
