# @ambystech/ui

Shared Astro components, design tokens and brand assets for Ambystech websites
(corporate, open source, decks). Source-only: there is no build step, each site's
Astro compiles the `.astro` files.

## Install

```sh
npm i github:ambystechcom/ambystech-ui#v0.2.0
```

Requires `astro >= 7` and Tailwind CSS 4 in the consuming site.

## Use

```css
/* src/styles/global.css */
@import "tailwindcss";
@import "@ambystech/ui/theme.css";
/* Tailwind v4 does not scan node_modules: let it see the package's classes. */
@source "../../node_modules/@ambystech/ui/src";
```

```astro
---
import SiteHeader from '@ambystech/ui/components/SiteHeader.astro';
import SiteFooter from '@ambystech/ui/components/SiteFooter.astro';
import CTABand from '@ambystech/ui/components/CTABand.astro';
import Icon from '@ambystech/ui/components/Icon.astro';
---
<SiteHeader label="Open Source" links={[{ label: 'Projects', href: '/#projects' }]}>
  <a slot="actions" href="https://github.com/ambystechcom" class="btn-outline">GitHub</a>
</SiteHeader>
```

## What is in it

| Path | What |
| --- | --- |
| `theme.css` | `@theme` tokens (colors, shadows, font) and utilities: `.container-site`, `.btn-cta`, `.btn-dark`, `.btn-outline`, `.text-gradient`, `.card-hover`, `.tag`, `.section-eyebrow`, `.section-title`, `.section-pad` |
| `components/Icon.astro` | Font Awesome Free icons by the site's names (`<Icon name="arrowRight" />`) |
| `components/CTABand.astro` | Gradient call-to-action band; all copy via props |
| `components/SiteHeader.astro` | Sticky header shell. Slots: `utility`, `nav`, `actions`, `mobile`, `toggle` |
| `components/SiteFooter.astro` | Light footer shell. Slots: `brand`, default (columns), `contact`, `bottom` |
| `assets/brand/*` | Lockup and symbol PNGs |

The package contains **no translations and no site data**. Pass already-translated
strings and links as props or slots, so the same components render in English,
Spanish or any other language.

## Rules

- Tokens in `theme.css` are the source of truth; keep `DESIGN.md` and the Ambystech
  Design System artifact in sync with them.
- Before adding a component to a site, check whether it already exists here.
- Changing a shared class name or selector (`#site-header`, `[data-scrolled]`,
  `.nav-trigger`, `.nav-line`) is a breaking change: bump the major version.

## Releasing

```sh
git tag v0.2.0 && git push --tags
# then in each site
npm i github:ambystechcom/ambystech-ui#v0.2.0
```

See `NOTICE.md` for icon and brand-asset terms.
