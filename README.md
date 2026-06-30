# Alexander Montolio — Portfolio

A single-page static portfolio. Plain HTML and one hand-written CSS file — no build step, no framework, no dependencies to install. Deployed as static files (GitHub Pages).

The page is composed as an Apple-style "gallery" — enormous type on an off-white canvas, depth by background value rather than shadow, a single rationed action — skinned in the visual identity of **A2**, the headline project: an AI agent being reimagined. A2's section is the app's own pure-black world, monochrome and monospace, anchored by the `[ Λ ]2` fragment mark that morphs out of an animated HUD reticle on a continuous loop.

## Structure

- `index.html` — all page content, plus a small inline scroll-reveal script (no jQuery).
- `assets/css/a2.css` — the entire stylesheet; design tokens live in `:root` at the top.

## Notes

- **Fonts:** Inter, JetBrains Mono, and Rajdhani (the `2` numeral) from Google Fonts, falling back to the system SF Pro / SF Mono stack.
- **Icons:** inline SVG (no icon font).
- The `[ Λ ]2` mark and HUD reticle are recreated as SVG from the A2 app's fragment-mark painter.

## Credits

Design and build: [dea6cat](https://github.com/dea6cat).
