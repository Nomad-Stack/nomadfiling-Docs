# Nomadfiling Docs

Source repository for the Nomadfiling product documentation.

Nomadfiling is a web app that helps foreign-owned US LLCs prepare IRS filings such as Form 5472, Form 1120, partnership Form 1065, extensions, late-filing letters, and related PDFs. This repo does not contain the application itself. It contains the docs site content and navigation.

## What lives here

| Path | Purpose |
| --- | --- |
| `documentation.json` | Site config: product name, brand colors, and the full sidebar navigation per language |
| `en/` | English documentation (source language) |
| `de/` | German documentation (same folder and file names as `en/`) |

Each language folder mirrors the other. Keep file names, folder names, and MDX structure aligned so the nav can point at `en/...` and `de/...` with the same relative paths.

## Languages

`documentation.json` currently defines two languages:

- **English** → pages under `en/`
- **German** → pages under `de/`

Navigation titles are translated. Paths stay in English (for example `de/form-5472-1120`, not `de/formular-5472-1120`).

## Content map

Both `en/` and `de/` contain the same set of pages:

```
introduction.mdx
quickstart.mdx
features.mdx
dashboard.mdx
form-5472-1120.mdx
partnership-filing.mdx
form-7004-extension.mdx
late-filing-letter.mdx
ai-compliance-scanner.mdx
fax-service.mdx
integrations.mdx
changelog.mdx
getting-started/pricing.mdx
account/profile.mdx
account/payments.mdx
account/api-keys.mdx
help-center.mdx
help-center/faq/getting-started.mdx
help-center/troubleshooting/cannot-login.mdx
help-center/guides/first-filing.mdx
api-reference/openapi.yaml
api-reference/api/mcp-overview.mdx
api-reference/api/authentication.mdx
api-reference/api/mcp-tools.mdx
```

The docs cover:

- Getting started, pricing, and product features
- Filing guides (5472/1120, partnership, Form 7004, late filing letter)
- Dashboard, account, payments, and API keys
- Fax delivery and third-party integrations
- Help Center (FAQ, troubleshooting, first-filing guide)
- MCP / API reference plus OpenAPI spec
- Changelog

## How navigation works

Pages are only shown in the docs site if they are listed in `documentation.json`. Adding a new `.mdx` file is not enough; you also need a matching nav entry for each language, with:

- English: `"path": "en/<file-without-extension>"`
- German: `"path": "de/<same-file-without-extension>"`

OpenAPI endpoints are wired with:

```json
"openapi": "en/api-reference/openapi.yaml"
```

and the German equivalent under `de/`.

## Editing docs

- Write pages as MDX. Frontmatter `title` and `description` are required.
- Translate visible copy. Leave code, field names, form numbers, prices, app routes (`/login`, `/dashboard`, `/filing/:id`), and external URLs unchanged.
- Internal docs links in German pages should use the `/de/...` prefix. App routes stay unprefixed.

## Adding a language later

1. Copy `en/` to a new locale folder (for example `es/`) with the same file names.
2. Translate the MDX content 1:1.
3. Add a new `"language"` block in `documentation.json` with translated tab/group/page titles and paths like `es/introduction`.
