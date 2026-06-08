# Open Electricity Documentation

![logo](https://platform.openelectricity.org.au/oe_logo_full.png)

The OpenElectricity project (formerly OpenNEM) aims to make the wealth of public Australian energy data more accessible to a wider audience. Project homepage at [openelectricity.org.au](https://openelectricity.org.au).

This repo holds the source for the documentation, live at **https://docs.openelectricity.org.au**, built with [Tangly](https://tangly.dev) ([GitHub](https://github.com/tanglydocs/tangly)), a self-hosted, open-source docs framework that renders a Mintlify-style `docs.json` unmodified. Pages are MDX; navigation, theme, and the API reference are configured in `docs.json`.

## Quick start

Requires [bun](https://bun.sh) (Node 19+).

```bash
bun install
bun run dev        # http://localhost:9411 (override with PORT)
```

```bash
bun run build      # static build -> ./dist
bun run preview    # serve ./dist locally
bun run check      # tangly check --strict (config, nav, links, frontmatter)
```

## Layout

| Path | What |
|------|------|
| `docs.json` | Site config: nav, theme, colors, API reference. See the [Tangly docs](https://tangly.dev) for options. |
| `*.mdx`, `guides/`, `sdk/`, `howto/`, `platform/`, `contribute/` | Documentation pages |
| `api-reference/` | OpenAPI-driven API pages |
| `images/` | Static assets, served from `/images/...` |

## OpenAPI

API reference pages read the spec from `docs.json` (`api.openapi`). `TANGLY_OPENAPI_URL` overrides it at build time. Preview builds use the dev API (`https://api.oedev.org/openapi.json`); production uses the default in `docs.json`.

## Contributing

Edits and new pages are welcome. See **[CONTRIBUTING.md](./CONTRIBUTING.md)** for the full guide. In short:

1. Branch, edit or add an `.mdx` page, and wire it into `docs.json` navigation.
2. `bun run check` to validate; `bun run dev` to preview locally.
3. Open a PR. CI builds a **preview deployment** and comments the URL.
4. On merge to `main`, the site **deploys automatically** to production.

For component syntax, frontmatter, and config options, see the [Tangly documentation](https://tangly.dev).

## Deployment

Push-to-deploy via Cloudflare Pages (GitHub Actions):

- **Pull requests** -> `.github/workflows/preview.yml` builds a preview and comments the URL.
- **`main`** -> `.github/workflows/deploy.yml` builds and deploys to **docs.openelectricity.org.au**.

Deploys require `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` as repository secrets.

## License

[MIT](./LICENSE). Part of the [Open Electricity](https://openelectricity.org.au) project.
