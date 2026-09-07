# Dinoroco Studios — company website

The public website for **Dinoroco Studios**, a Spanish software company
founded in 2022 that builds apps for iOS.

- **Live site:** <https://www.dinoroco.com>
- **Repo:** `Dinoroco-Studios/dinoroco-studios.github.io` (GitHub Pages, organisation site)
- **Stack:** [Jekyll](https://jekyllrb.com/) via the `github-pages` gem — static,
  no database, no analytics.

---

## What the site is

Deliberately minimal: a one-line landing page, a short About, and the legal
pages that the shipped apps link to. There is no blog, no portfolio and no
marketing catalog.

| Page | URL |
|---|---|
| Landing | `/` |
| About | `/about/` |
| Work Calendar — Privacy | `/work-calendar-privacy/` |
| Work Calendar — Terms | `/work-calendar-terms/` |
| Acerinox — Privacy | `/acerinox-privacy/` |
| Acerinox — Terms | `/acerinox-terms/` |

The two app privacy/terms pairs are linked from inside the apps themselves, so
they must keep their current URLs.

---

## Company facts

| | |
|---|---|
| Name | Dinoroco Studios |
| Founded | 2022 |
| Country | Spain |
| Contact | info@dinoroco.com |
| Domain | www.dinoroco.com |

These live in the `author:` block of [`_config.yml`](_config.yml) and feed the
navbar, footer and social links.

---

## Project structure

```
.
├── _config.yml           # Site + author config
├── CNAME                 # www.dinoroco.com
├── Gemfile               # github-pages gem
├── docs/pages/           # Every page lives here
│   ├── index.md          # Landing (renders _includes/landing.html)
│   ├── about.md          # About
│   ├── 404.html
│   ├── work-calendar-privacy.md / work-calendar-terms.md
│   └── acerinox-privacy.md / acerinox-terms.md
├── _includes/            # landing, navbar, footer, head, social, analytics
├── _layouts/             # default.html, page.html
├── _sass/                # portfolYOU-derived styles (base, navbar, footer, themes)
├── assets/               # style.scss, theme.js, logos, favicons
└── _site/                # Build output (committed, see note below)
```

---

## Local development

Requires Ruby (3.2+) and Bundler.

```bash
bundle install
bundle exec jekyll serve      # http://127.0.0.1:4000
bundle exec jekyll build      # output to _site/
```

### Notes

- **Dark mode** is handled by `assets/js/theme.js` with `_sass/_theme-dark.scss`.
- **Analytics are off** (`analytics.enabled: false` in `_config.yml`); nothing
  third-party is loaded.
- **`_site/` is committed** in this repo. GitHub Pages does not serve it — it
  runs its own Jekyll build from `main` — so it is a historical artefact rather
  than the deployed output. If you edit a page, rebuild before committing so the
  two do not drift, or drop the directory from version control.

---

## Deployment

Pushing to `main` triggers a GitHub Pages build automatically. In
**Settings → Pages** the custom domain is `www.dinoroco.com` with **Enforce
HTTPS** enabled.

**DNS** (at the registrar):

- `CNAME` · `www` → `dinoroco-studios.github.io`
- `A` · `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  (the apex redirects to `www`)

---

## License

MIT — see [LICENSE.md](LICENSE.md).

© 2026 Dinoroco Studios. All rights reserved.
