# Contributing

Thanks for helping improve the Open Electricity docs. This repo holds the content for
**https://docs.openelectricity.org.au**, built with [Tangly](https://tangly.dev).

## Setup

```bash
bun install
bun run dev        # live preview at http://localhost:9411
```

## Editing a page

Pages are MDX files (`.mdx`) at the repo root and under `guides/`, `sdk/`, `howto/`,
`platform/`, `contribute/`, and `api-reference/`. Each page starts with frontmatter:

```mdx
---
title: Page title
description: One-line summary used for SEO and social cards.
---

Body content in Markdown / MDX.
```

You can use the full set of [Tangly components](https://tangly.dev) (callouts, cards,
tabs, steps, code groups, accordions, API blocks, and more) directly in the body.

## Adding a page

1. Create the `.mdx` file in the right folder.
2. Add its path (without extension) to `navigation` in `docs.json` so it appears in the
   sidebar. Pages not referenced in `docs.json` are reachable by URL but show as
   orphans in `bun run check`.
3. Reference images from `images/` using absolute paths (`/images/...`).

## Before you open a PR

```bash
bun run check      # validates docs.json, nav, links, and frontmatter (strict)
bun run build      # full production build; catches MDX and asset errors
```

Both must pass. `check` is also run in CI and gates deploys.

## Pull request flow

1. Branch from `main`, make your change, push, open a PR.
2. CI builds a **preview deployment** and comments the URL on the PR. Use it to review
   the rendered result.
3. Once approved and merged to `main`, the change **deploys automatically** to
   production (docs.openelectricity.org.au).

## Style

- Keep titles and descriptions concise; the description feeds SEO and social cards.
- Prefer short sentences and active voice.
- Link to source, dashboards, and the API reference where it helps the reader.

## Configuration and theming

Site-wide settings (navigation, theme, colors, logo, API reference source) live in
`docs.json`. See the [Tangly schema reference](https://tangly.dev) for every option.
Larger structural or theming changes are worth a quick issue first.
