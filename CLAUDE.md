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
- Logo: none. The header shows the site title as a Georgia-serif wordmark (no icon).
  (A narwhal logo via `theme.icon.logo` was removed at the user's request.)
- Favicon: [docs/assets/images/favicon.png](docs/assets/images/favicon.png) — the
  narwhal in white on a `#C24A22` background (512×512). Still in use.

### Icons — Font Awesome Pro 7
The site uses Font Awesome **Pro 7.0.1** icons (commercial licence — keep in mind for
public hosting). The Pro web package lives **outside the repo** on the user's machine
at `~/Desktop/fontawesome-pro-7.0.1-web/` and is the source for regenerating glyphs.

Two distinct mechanisms are in play:

1. **Icons in the theme UI (logo, palette toggle)** — custom SVG icon set in
   [overrides/.icons/fontawesome-regular/](overrides/.icons/fontawesome-regular/),
   enabled via `theme.custom_dir: overrides`. Current icons: `brightness`
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

## Design system

Official source: **https://app.openreferral.io/design-system** (public; a
shadcn/ui + Tailwind app — semantic tokens are HSL triplets, plus a named brand
palette Terra/Night/Honey). Applied to the theme in
[docs/assets/stylesheets/openreferral.css](docs/assets/stylesheets/openreferral.css),
which overrides Material's `--md-*` custom properties per scheme.

- **Colours** — mapped onto Material via `extra_css`, scoped to
  `[data-md-color-scheme="default"]` (light) and `"slate"` (dark). Palette entries in
  [mkdocs.yml](mkdocs.yml) are `primary: custom` / `accent: custom` so Material ships no
  built-in colour CSS. Key mappings: primary/header/links → terracotta `hsl(14 74% 45%)`
  (terra-600, ≈ `#C8471E` — this is the canonical brand colour; the favicon's `#C24A22`
  is a near-identical earlier value, fine to leave); accent (hover/focus) → honey
  (honey-600 in light for contrast, honey-500 in dark); bg → paper (light) / night-800
  (dark); text → slate / 92%-white. The header is terracotta in both light and dark
  modes.
- **Fonts** — `theme.font: false` (opts out of Google Fonts; both faces are system
  fonts). `h1`/display and the header wordmark use **Georgia serif**; everything else
  uses the **Calibri, -apple-system, system-ui, "Segoe UI"** stack, set via
  `--md-text-font`. `--md-code-font` is a system monospace stack (the DS has no code
  font). On macOS/Linux Calibri falls back to the system UI font — expected, matches the
  DS's own stack.

Not yet applied from the DS (out of the colours+fonts scope): remapping admonition hues
to the DS semantic tokens, buttons/badges/cards styling.
