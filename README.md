# harshankarthikeyan.com

Static site, served by GitHub Pages from the `main` branch of this repo.

## Nothing in here is hand-edited

Every file except this README, `CNAME` and `.git*` is **generated**. Editing them
directly gets your work overwritten on the next build.

The source lives one level up in the workspace:

| What | Where |
|---|---|
| The generator | `site_engine/` |
| Page copy (home, about, consulting, 404) | `site_engine/content/*.md` |
| Site config: nav, footer, base URL | `site_engine/content/site.json` |
| The stylesheet | `site_engine/theme/style.css` |
| Posts | `journal/<YYMMDD>-<slug>/source.md` |

## Build

From the workspace root. No venv and no dependencies; Python 3.11+ stdlib only.

```sh
python3 -m site_engine check     # every gate, exits non-zero on failure
python3 -m site_engine build     # writes this directory
python3 -m site_engine serve     # http://localhost:8080
```

## Deploy

```sh
git add -A && git commit -m "Update site" && git push
```

Live about 30 seconds later.

## DNS

Registrar: Namecheap. Under **Advanced DNS**, delete the default parking `CNAME`
and the `URL Redirect Record`, then:

| Type | Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | harshan-jpg.github.io. |

`CNAME` in this repo holds the custom domain. **Do not delete it** — and note
that changing the custom domain in the GitHub Pages UI rewrites this file.
