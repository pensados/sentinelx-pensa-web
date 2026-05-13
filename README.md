# sentinelx-pensa-web

Landing page for **SentinelX legacy** — the older, self-hosted
SentinelX MCP that runs at [sentinelx.pensa.ar](https://sentinelx.pensa.ar)
and predates [SentinelX Cloud](https://sentinelx.app). Kept online as
a backup / reference deployment.

Served from `/var/www/sentinelx.pensa.ar/` on the production host
(`orion`). nginx routes:

- `https://sentinelx.pensa.ar/` → this static content
- `https://sentinelx.pensa.ar/mcp` → proxied to the legacy MCP
  server (not in this repo)

## Layout

```
.
├── index.html       The landing page
├── og-image.png     OpenGraph preview card (used in social shares)
└── .gitignore
```

## Deploy workflow

Files in this repo ARE the live website — the working tree IS
`/var/www/sentinelx.pensa.ar/`. There is no separate deploy step:
editing here changes what nginx serves immediately.

To pull changes onto the running server:

```bash
ssh orion
cd /var/www/sentinelx.pensa.ar
git pull
```

nginx picks up the new content on the next request. No restart needed.

## Relationship to SentinelX Cloud

This is the **legacy** site. The actively-marketed product lives at:

- Code:    https://github.com/pensados/sentinelx-cloud-core
- Site:    https://sentinelx.app  (repo: pensados/sentinelx-app-web)
- Hub:     https://mcp.sentinelx.app

The legacy `sentinelx.pensa.ar/mcp` server still works for users
who installed it before the Cloud version existed. Both are kept
running so existing setups don't break.

## License

Apache License 2.0 — see [LICENSE](./LICENSE).

Copyright 2026 Carlos Javier Torres Pensa
Pensa Software® — https://sentinelx.app
