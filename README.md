# 10keyz.com

Static site for 10Keyz (Martijn Tennekes): guitar lessons, live music and apps.
Plain HTML and CSS, no build step, no JavaScript, no cookies. Served from this
repo by GitHub Pages (`CNAME` = `10keyz.com`). `spicemap.10keyz.com` lives in
a separate repo.

## Preview locally

Links are root-relative (`/lessons/`), so open the site through a local server
rather than by double-clicking `index.html`:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Structure

| English                    | Dutch                         |
| -------------------------- | ----------------------------- |
| `/`                        | `/nl/`                        |
| `/lessons/`                | `/nl/lessen/`                 |
| `/live/`                   | `/nl/live/`                   |
| `/apps/`                   | `/nl/apps/`                   |
| `/apps/spicemap/support/`  | `/nl/apps/spicemap/support/`  |
| `/about/`                  | `/nl/over/`                   |
| `/contact/`                | `/nl/contact/`                |
| `/privacy/`                | `/nl/privacy/`                |
| `/terms/`                  | `/nl/voorwaarden/`            |

Every page has `hreflang` links to its counterpart and an `EN | NL` switch.
All styles are in `css/style.css`; accent colours are SpiceMap's pitch-class
palette (`--pc1` … `--pc11`).

The navigation (`<!-- NAV -->` … `<!-- /NAV -->`) and the footer with the
business details are identical on every page of the same language. When you
change one, change them all (find and replace across the repo).

## Hiding a page (phased launch)

Each activity is tagged in the navigation and on the home page with a comment:
`phase:lessons`, `phase:live`, `phase:apps`. Every tagged line is self-contained,
so hiding an activity means deleting those lines. For example, to hide Live music
everywhere:

```sh
grep -rl --include='*.html' 'phase:live' . | xargs sed -i '' '/phase:live/d'
```

The page itself (`/live/`, `/nl/live/`) stays reachable by direct URL; delete
or move those folders too if it should not be online at all.

## Placeholders

Anything not decided yet is marked `[TODO: …]` and highlighted in yellow:

```sh
grep -rn 'TODO' --include='*.html' .
```

## Not published

`_archive/` (old v2 site, content source only), `README.md` and the brief are
excluded in `_config.yml`.
