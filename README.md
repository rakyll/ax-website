# AX website

Hugo site for [AX](https://github.com/google/ax). The theme is self-contained in
`layouts/` and `assets/css/main.css`; there are no external theme dependencies
and no JavaScript.

## Develop

```bash
hugo server          # http://localhost:1313
hugo --gc --minify   # production build into public/
```

Requires Hugo extended 0.106 or newer.

## Layout

| Path | Purpose |
|---|---|
| `config.toml` | Site config, menu, doc groups (`params.docGroups`), GitHub URL |
| `content/docs/*.md` | Documentation pages, ported from the AX repo's `docs/` and README |
| `layouts/index.html` | Landing page |
| `layouts/docs/` | Docs section with sidebar, table of contents, prev/next |
| `assets/css/main.css` | Styles. Palette comes from the axolotl mascot |
| `static/axolotl*.svg` | Logo files copied from the AX repo |

## Palette

| Token | Hex | Source |
|---|---|---|
| Pink | `#F15B85` | Gills |
| Soft pink | `#FFAAC0` | Face |
| Blush | `#F77FA3` | Cheeks |
| Plum | `#432B41` | Eyes and mouth; used for text and code blocks |
| Cream | `#FFF4F7` | Mono logo in dark mode; used for tinted backgrounds |

Dark mode follows `prefers-color-scheme` and inverts to plum backgrounds with
cream text.

## Adding a doc page

Create `content/docs/<slug>.md` with front matter:

```yaml
---
title: Page title
description: One sentence shown on cards and under the heading.
weight: 45           # ordering within the sidebar
group: Guides        # one of params.docGroups in config.toml
---
```

Link between pages with `{{</* relref "slug" */>}}`.

## Deploying

`baseURL` is `/` so the site works at any origin. Set it to the real domain
in `config.toml` before publishing so canonical and Open Graph URLs are absolute.
