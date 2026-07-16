# CLAUDE.md — project notes for Claude

Documentation site for Open Referral. MkDocs Material, hosted on Cloudflare Pages.
Every push to `main` auto-deploys to https://docs.openreferral.io (~1–2 min). See
[README.md](README.md) and [DEMO.md](DEMO.md) for setup/authoring.

## Local preview

```bash
source .venv/bin/activate && mkdocs serve   # http://127.0.0.1:8000
mkdocs build --strict                       # verify before committing
```

## Branding & theming

Brand colour (orange): **`#C24A22`**.

### Logo & favicon
- Logo: `theme.icon.logo: fontawesome-regular/narwhal` in [mkdocs.yml](mkdocs.yml).
  It is an inline SVG icon, so it inherits the header colour automatically.
- Favicon: [docs/assets/images/favicon.png](docs/assets/images/favicon.png) — the
  narwhal in white on a `#C24A22` background (512×512).

### Icons — Font Awesome Pro 7
The site uses Font Awesome **Pro 7.0.1** icons (commercial licence — keep in mind for
public hosting). The Pro web package lives **outside the repo** on the user's machine
at `~/Desktop/fontawesome-pro-7.0.1-web/` and is the source for regenerating glyphs.

Two distinct mechanisms are in play:

1. **Icons in the theme UI (logo, palette toggle)** — custom SVG icon set in
   [overrides/.icons/fontawesome-regular/](overrides/.icons/fontawesome-regular/),
   enabled via `theme.custom_dir: overrides`. Current icons: `narwhal`, `brightness`
   (light-mode sun), `moon` (dark-mode), `hand-wave`.
   - The bundled free FA set (`fontawesome/regular|solid|brands`) only covers free-tier
     icons, so Pro-only glyphs (narwhal, brightness, hand-wave) had to be extracted.

2. **Icons in Markdown content** — via `:fontawesome-...:` shortcodes. The theme bundles
   free-tier SVGs; our custom set is also searchable because `overrides/.icons` is
   registered under `pymdownx.emoji` → `options.custom_icons` in [mkdocs.yml](mkdocs.yml).

Font-content usage (`.far` / `.fa-regular` CSS classes) is wired via
[docs/assets/fontawesome/css/regular.min.css](docs/assets/fontawesome/css/regular.min.css)
+ `fa-regular-400.woff2`, loaded through `extra_css`.

### Extracting a Pro glyph to an SVG icon
FA Pro webfonts are **CFF** (not glyf), so use `SVGPathPen`, and flip the Y axis (fonts
are Y-up, SVG is Y-down). `ascender = 448`, `unitsPerEm = 512` for these fonts.

```python
from fontTools.ttLib import TTFont
from fontTools.pens.svgPathPen import SVGPathPen
from fontTools.pens.transformPen import TransformPen

font = TTFont("~/Desktop/fontawesome-pro-7.0.1-web/webfonts/fa-regular-400.woff2")
gs, cmap, asc = font.getGlyphSet(), font.getBestCmap(), font["hhea"].ascender
g = gs[cmap[0xF6FE]]                       # codepoint from css/all.css (.fa-<name> --fa)
pen = SVGPathPen(gs)
g.draw(TransformPen(pen, (1, 0, 0, -1, 0, asc)))
svg = f'<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 {int(g.width)} 512"><path d="{pen.getCommands()}"/></svg>'
```

**Header sizing gotcha:** extracted glyphs fill 100% of their viewBox, but Material's
own header icons only fill ~73%. Without a margin, custom header icons look oversized.
Pad the `viewBox` (path untouched), e.g. `viewBox="-80 -80 672 672"`. This was applied
to `brightness.svg` / `moon.svg`.

## TODO — next session: apply the design system

Official design system: **https://app.openreferral.io/design-system**

Apply **colours** and **fonts** from it to the MkDocs Material theme:
- Colours: replace the `indigo` primary/accent palette in [mkdocs.yml](mkdocs.yml) with
  the design-system palette (light + dark schemes). Brand orange is `#C24A22`; use
  `extra_css` custom properties (`--md-primary-fg-color`, `--md-accent-fg-color`, etc.)
  for exact values the built-in palettes can't express.
- Fonts: override `--md-text-font` / `--md-code-font` (theme `font:` key or `extra_css`)
  with the design-system typefaces.
