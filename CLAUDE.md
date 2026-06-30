# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static portfolio website for Alexander Montolio. There is **no build system, no package manager, no tests, and no backend** — it is plain HTML/CSS/JS served as static files (deployed via GitHub Pages). The global Dart/Flutter instructions do **not** apply to this repo.

The page was redesigned in an Apple-product-page style, skinned in the visual identity of the **A2** app (the portfolio's headline project): monochrome (no chromatic accent), a monospace utility face with wide letter-spacing, and a `[ bracket ]` motif. The bright "gallery" sections give way to A2's pure-black showcase — "color enters only as product."

## Working with the code

- **Preview:** Open `index.html` directly in a browser, or serve the directory (e.g. `python3 -m http.server`).
- **Page content** lives entirely in `index.html` as semantic `<section>` blocks: `.nav`, `.hero`, `.showcase` (the black A2 zone), `.band` capability/roadmap sections, `.footer`. One small inline `<script>` IIFE (no jQuery) does scroll-reveal via `IntersectionObserver`, honoring `prefers-reduced-motion`.
- **The A2 reticle (`.reticle`)** is an inline SVG (a HUD ring cluster + the `[ Λ ]2` fragment mark, geometry ported from `a2_flutter`'s `_FragmentMarkPainter`) that morphs rings → logo → rings on its own continuous ~9s loop (pure time-based CSS, no JS/scroll), so every visitor sees it. The morph is a collapse-and-fade between two layers: `.r-reticle` (rings, which also idly spin) collapses inward while `.r-logo` (the **always-fully-drawn** mark) fades in and holds. There is deliberately **no stroke-by-stroke draw-on** — that proved fragile and could be caught mid-draw, so the mark is only ever shown complete. Reduced motion holds the static logo.

## Styling

- The active stylesheet is the **hand-authored `assets/css/apple.css`** — there is no build step. All design tokens (color, type, spacing, radii, motion) are CSS custom properties in `:root` at the top of that file; edit those to retheme.
- The `[ bracket ]` label is the signature device — apply the `.kicker` class (it wraps content in brackets via `::before`/`::after`).
- Font Awesome (`assets/css/fontawesome-all.min.css` + `assets/webfonts/`) is kept only for the footer icons. Inter + JetBrains Mono load from Google Fonts, falling back to the system SF Pro / SF Mono stack.
- **Legacy (unused):** the old HTML5 UP "Story" template — `assets/css/main.css`, `assets/sass/`, and `assets/js/*.min.js` — is **no longer referenced** by `index.html`. Don't edit it expecting changes to show.

## Conventions

- Elevation is by background-value only — **never add `box-shadow`** (matches both the Apple reference and A2's flat aesthetic).
- Keep the palette monochrome; A2 carries no accent color.
- External downloads/links are hardcoded URLs in `index.html` anchor tags.
