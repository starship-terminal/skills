# Skills brand kit

Mark 2-1. Kit folder: `skills/kit/`. Marks are letter-free; only the lockups and banners carry the name.

## Palette

| Role | HEX | RGB |
|---|---|---|
| Background | #1C1B1F | 28 27 31 |
| Cream | #EBCAA7 | 235 202 167 |
| Orange | #B84A13 | 184 74 19 |
| Orange | #DB5915 | 219 89 21 |
| Cream | #F2E0CC | 242 224 204 |
| Cream | #D9B48E | 217 180 142 |
| Orange | #ED6B1C | 237 107 28 |
| Mono cream / charcoal / black / white | #F2E0CC / #1C1B1F / #000000 / #FFFFFF | 242 224 204 / 28 27 31 / 0 0 0 / 255 255 255 |

The vector master has 6 colour layer(s). This is above the 2 to 3 colour house guideline because the faceted artwork depends on its shaded tones; the actual colours are kept exactly (no posterising). Use the mono set where a strict 2 to 3 colour limit applies.

## Typeface

Geist Mono (Google Fonts, SIL OFL 1.1): SemiBold for the name in lockups and banners, Regular for text and captions. A clean monospace that ties back to the family and to SKILL.md files; the most technical choice. Names are outlined in every SVG/PDF; install the TTFs in `fonts/` for new text. Licence: `fonts/OFL.txt`.

## Rules

- Clear space: x = 0.25 x mark height (tight bounding box) on all sides.
- Minimum size: 24 px tall (digital) / 8 mm (print). Below that use `png/favicon-16.png`.
- Do: use the supplied files; keep clear space; cream marks go on dark or mid backgrounds, use the light version (or mono charcoal) on light.
- Don't: stretch or skew, recolour, add shadows/glow/gradients, or place on busy backgrounds.

## Files

### `png/`
Raster set (avatars, logos, mark-transparent, favicons + .ico, apple-touch/PWA icons, maskable, social preview mark-only)

`apple-touch-icon-180.png`, `avatar-1024.png`, `avatar-500.png`, `favicon-16.png`, `favicon-32.png`, `favicon-48.png`, `favicon.ico`, `icon-192.png`, `icon-512.png`, `logo-rounded-160.png`, `logo-rounded.png`, `logo-square-2048.png`, `logo-square.png`, `mark-transparent-2048.png`, `mark-transparent.png`, `maskable-512.png`, `social-preview-1280x640.png`

### `svg/`
Vector masters: full colour on background, full colour transparent, one-colour versions. Palette-exact, one filled path per colour layer

`mark-color-on-bg.svg`, `mark-color.svg`, `mark-mono-black.svg`, `mark-mono-charcoal.svg`, `mark-mono-cream.svg`, `mark-mono-white.svg`

### `pdf/`
Vector PDFs generated from the SVGs

`mark-color-on-bg.pdf`, `mark-color.pdf`, `mark-mono-black.pdf`, `mark-mono-charcoal.pdf`, `mark-mono-cream.pdf`, `mark-mono-white.pdf`

### `mono/`
One-colour marks (cream #F2E0CC, charcoal #1C1B1F, black, white) as SVG and transparent PNG, with knockouts so the silhouette reads

`mono-black.png`, `mono-black.svg`, `mono-charcoal.png`, `mono-charcoal.svg`, `mono-cream.png`, `mono-cream.svg`, `mono-white.png`, `mono-white.svg`

### `lockups/`
Mark + name (set in the mark typeface, outlined). Horizontal and stacked x dark / light / transparent (for dark use) / transparent-onlight, as SVG, PDF and PNG

`skills-horizontal-dark.pdf`, `skills-horizontal-dark.png`, `skills-horizontal-dark.svg`, `skills-horizontal-light.pdf`, `skills-horizontal-light.png`, `skills-horizontal-light.svg`, `skills-horizontal-transparent-onlight.pdf`, `skills-horizontal-transparent-onlight.png`, `skills-horizontal-transparent-onlight.svg`, `skills-horizontal-transparent.pdf`, `skills-horizontal-transparent.png`, `skills-horizontal-transparent.svg`, `skills-stacked-dark.pdf`, `skills-stacked-dark.png`, `skills-stacked-dark.svg`, `skills-stacked-light.pdf`, `skills-stacked-light.png`, `skills-stacked-light.svg`, `skills-stacked-transparent-onlight.pdf`, `skills-stacked-transparent-onlight.png`, `skills-stacked-transparent-onlight.svg`, `skills-stacked-transparent.pdf`, `skills-stacked-transparent.png`, `skills-stacked-transparent.svg`

### `banners/`
README banner 1280x320 and social preview with name 1280x640, both on dark

`banner-readme-1280x320.png`, `banner-readme-1280x320.svg`, `social-preview-name-1280x640.png`, `social-preview-name-1280x640.svg`

### `fonts/`
Static TTFs for the mark's typeface (name and body weights) and the SIL OFL licence

`GeistMono-Regular.ttf`, `GeistMono-SemiBold.ttf`, `OFL.txt`

`brand-sheet.pdf`: one-page brand sheet (versions, palette, typeface, clear space, minimum size, dos and don'ts). `brand.md`: this file.

## Vector fidelity

SVG (rendered at 1024) vs the flat-palette raster: 0.0013% of pixels differ by more than 40/255 away from colour edges (0.366% including the 1 px edge antialiasing); mean abs diff 0.28/255. Node counts: colour 1766, mono 389.
