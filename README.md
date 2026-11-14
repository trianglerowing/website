# Triangle Rowing Club website

Source for the Triangle Rowing Club website, a nonprofit youth rowing club in Raleigh, NC. While under construction it is served at https://dev.trianglerowing.org; trianglerowing.org stays on SportsEngine until launch.

Why it is built this way (Hugo, the Sveltia CMS browser editor, GitHub, a Hetzner server) and what must not break (SportsEngine registration, payments, rosters and logins): [docs/decisions/0001-platform-and-hosting.md](docs/decisions/0001-platform-and-hosting.md).

## Editing content

Volunteers edit at `/admin` in a browser. No local setup is needed for that.

## Building locally

The site uses one pinned Hugo version, recorded in `.hugo-version`. Use exactly that version, the **extended** edition, from https://github.com/gohugoio/hugo/releases.

```
hugo server        # preview at http://localhost:1313, rebuilds on save
hugo --minify      # production build into public/
```

There is no npm, no theme module and no other build dependency, on purpose: they are what makes small sites stop building after a year untouched.

## Layout

| Path | What it holds |
|---|---|
| `content/pages/` | Every page; folder layout is the URL layout (`programs/high-school/_index.md` → `/programs/high-school/`) |
| `content/news/` | News posts |
| `data/settings.yaml` | Registration links and open/closed switches, donation link, season name |
| `data/glossary.yaml` | Rowing terms |
| `data/coaches/`, `data/sponsors/` | One file per coach or sponsor |
| `layouts/` | Page templates; `_shortcodes/` holds the blocks editors insert |
| `assets/css/main.css` | Brand colors and fonts, set once at the top |
| `static/admin/` | Editor configuration |
| `docs/` | Decisions and research |

## Building blocks for page text

| Block | Example |
|---|---|
| Registration button | `{{</* register program="sneak-peek-week" */>}}` |
| Donate button | `{{</* donate */>}}` |
| Upcoming events | `{{</* calendar feed="high-school" limit="10" */>}}` |
| YouTube video | `{{</* video id="VIDEO_ID" title="What it shows" */>}}` |
| Embedded page | `{{</* embed src="https://..." title="What it shows" height="600" */>}}` |

All of them are shown on `/style-guide/`.
