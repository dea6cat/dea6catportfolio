# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A two-page static portfolio website for Alexander Montolio. There is **no build system, no package manager, no tests, and no backend** — it is plain HTML/CSS/JS served as static files (deployed via GitHub Pages). The global Dart/Flutter instructions do **not** apply to this repo.

It is a monochrome developer-portfolio, skinned in the visual identity of the **A2** app (the headline project): no chromatic accent, a geometric-grotesk face with wide letter-spacing on labels, and a `[ bracket ]` motif. The bright "gallery" main page gives way to A2's own **pure-black** page — "color enters only as product."

- **`index.html`** — the portfolio: sticky nav, centered hero (oversized "Mobile Developer" title + "System Engineer" role line + Download-CV button + socials), skills chips, "What I do" services, "My work" project cards (A2 + 2B, with status badges), and a "Let's talk" contact close. Light-gallery by default with a monochrome dark theme.
- **`a2.html`** — A2's dedicated page in its own committed pure-black world: the reticle, the ELIZA note, the "Inside A2" capability grid, and a back-link to `index.html`.

## Working with the code

- **Preview:** Open `index.html` in a browser, or serve the directory (`python3 -m http.server`). Navigate to A2 via the nav or the A2 card.
- Each page carries its content as semantic `<section>` blocks and a trailing inline `<script>` (no jQuery) running three IIFEs: **code-rain**, **i18n**, and **scroll-reveal** (`IntersectionObserver`). All animation honors `prefers-reduced-motion`.
- **The A2 reticle** is an inline SVG (a HUD ring cluster + the `[ Λ ]2` fragment mark, geometry ported from `a2_flutter`'s `_FragmentMarkPainter`). Rings idly spin at different rates around the **always-fully-drawn** mark with a faint pulsing core — there is deliberately **no stroke-by-stroke draw-on**. It appears large on `a2.html` and beside the hero content is not used on the main page.
- **Matrix code-rain (`#rain`)** is a fixed full-viewport `<canvas>` behind the content (`z-index:0`; content is `z-index:1`). Falling Dart/Python glyphs, drawn once per row so they stay legible, with a **glowing head** and a real-time **1.5s glyph lifetime**; columns get a random depth `scale` driving size/speed/brightness for a 3D-parallax feel. Colors are read from the CSS tokens each theme change, so it stays theme-aware. Off under reduced motion. Opaque section/footer backgrounds mask it; transparent bands let it show through.
- **Bilingual (auto):** copy is tagged with `data-i18n` / `data-i18n-html` keys and translated from an in-script `dict` (`en`/`es`). The language is picked from `navigator.languages` (starts-with `es` → Spanish, else English) — **no manual toggle**. English is the no-JS fallback baked into the markup.

## Styling

- No build step. `index.html` links **`assets/css/a2.css`** (light-gallery + dark theme); `a2.html` links **`assets/css/a2-page.css`** (the pure-black world). Design tokens are CSS custom properties in `:root` at the top of each file — including `@media (prefers-color-scheme)` and `:root[data-theme]` overrides in `a2.css`.
- The `[ bracket ]` label is the signature device — apply the `.kicker` class (it wraps content in brackets via `::before`/`::after`).
- Fonts: **Inter** loads from Google Fonts; the CSS stack leads with the system geometric-grotesk (`SF Pro Display`), so Apple devices use SF Pro and everything else falls back to Inter. Icons are **inline SVG** — there is no icon font.

## Conventions

- Elevation is by background-value / hairline border only — **never add `box-shadow`** (matches A2's flat aesthetic).
- Keep the palette monochrome; A2 carries no accent color.
- **The CV** lives at `assets/CV_Alexander_Montolio.pdf`; the "Download CV" buttons carry the `.cv-link` class and a `download` attribute, wired to that path by the CV IIFE.
- Cross-page and external links are plain relative/absolute URLs in the anchor tags.
