# drayker-theme

The Drayker documentation theme: one dark Jekyll layout so that every `*.drayker.org` documentation site reads as part of the same system as [drayker.org](https://drayker.org) and [drayker.com](https://drayker.com).

## Using it

In the `_config.yml` of the repository whose README is published by GitHub Pages:

```yaml
remote_theme: draykerdk/drayker-theme
plugins:
  - jekyll-remote-theme
  - jekyll-optional-front-matter

title: BSDK
description: Base Structure DK. The base structure proposed for the Dk kernel.

dk_kicker: Kernel component        # the small uppercase line above the title
dk_subdomain: bsdk.drayker.org     # shown beside the mark and in the footer bar
dk_repo: https://github.com/draykerdk/bsdk

defaults:
  - scope:
      path: ""
    values:
      layout: default
```

`title` and `description` become the page header, so a README does not need to repeat its own name as an `# H1`.

If the site is served from `docs/`, the `_config.yml` goes in `docs/` too.

## What it gives you

- The Drayker tokens: canvas `#08080A`, surface `#0C0C0F`, border `#18181E`, text `#EDECF0`, muted `#8585A0`, accent `#FF5500`, Archivo + JetBrains Mono, 1320px content width.
- A sticky header carrying the mark and a way back to the participation portal and the source repository.
- The complete official favicon chain on every generated Markdown page, served from the canonical portal assets.
- Markdown styling for headings, tables, code, blockquotes and lists, with tables scrolling inside their own container instead of pushing the page sideways.
- A shared footer pointing at the protocol, the knowledge base, the open functions and the volunteer flow.
- Visible focus states and `prefers-reduced-motion` respected.
- Little JavaScript: the shared mark engine (`https://drayker.org/drayker-mark.js`) and a short inline script that stops the mark from following the cursor under reduced motion. The page reads fully without either; the mark simply does not appear.
- Diagrams: a fenced ```` ```mermaid ```` block in a README is drawn as a diagram in the theme's colours. The library (Mermaid 11.4.1, from jsDelivr) is loaded only on pages that have such a block, with `securityLevel: 'strict'`. Without it the block stays readable as text.

The layout writes its own `<title>` and Open Graph tags rather than depending on `jekyll-seo-tag`, so it builds in a repository whose plugin list you have not touched.

## Changing it

`_layouts/default.html` is the whole theme, markup and tokens in one file, on purpose. Thirteen sites inherit it and a single file is what makes a change reviewable. If a token changes here it must change in `SITE_PATTERN.md` of [`draykerdk/drayker.org`](https://github.com/draykerdk/drayker.org) as well. That document is the source of truth for the pattern.

Code under MIT (see `LICENSE`), content under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
