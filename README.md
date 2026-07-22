# verk.foltopia.com

Fredriks samlade verk. A single-page home for finished work: books, essays,
papers, software. Built with [Zola](https://www.getzola.org), deployed to
GitHub Pages. No JS, system fonts, one stylesheet.

## Layout

```
config.toml              site config, section list, footer links
content/_index.md        the "about" paragraph at the top of the page
content/<section>/*.md   one file per work
templates/               index.html (front page), page.html (hosted works)
static/style.css         the entire design
static/CNAME             custom domain for GitHub Pages
```

## Adding a work

Create one markdown file in the right section directory:

```toml
+++
title = "Title of the work"
date = 2026-09-01          # omit while unfinished
weight = 10                # ordering within the section, lower = higher
[extra]
gloss = "One-line English gloss."   # optional
lang = "sv"                          # sv / en
meta = "essä"                        # venue, type, "repo", etc.
status = "in progress"               # optional, overrides year display
external_url = "https://..."         # link out instead of hosting
+++

Body text here only if the work is hosted on the site itself.
```

Works with an `external_url` link out (papers with DOIs, repos, the book's
landing page). Works with body text get their own page under
`/<section>/<slug>/`. Push to `main` and the Action rebuilds the site.

## Local preview

```
zola serve
```

Single binary, no other dependencies. https://www.getzola.org/documentation/getting-started/installation/

## One-time setup

1. Create the GitHub repo (public) and push this content to `main`.
2. Repo → Settings → Pages → Source: **GitHub Actions**.
3. DNS: add a CNAME record
   `verk.foltopia.com → <username>.github.io`
   The apex record is untouched; VPN resolution on foltopia.com is unaffected.
4. Repo → Settings → Pages → Custom domain: `verk.foltopia.com`,
   wait for the check, then enable **Enforce HTTPS**.

The `static/CNAME` file keeps the custom domain pinned across deploys.

## Placeholders to replace

- Footer/contact links in `config.toml` (`[extra.elsewhere]`)
- DDT `external_url` in `content/books/dusty-drawer-test.md`
- SPAM DOI in `content/papers/spam-innovsail.md`
- The essay body in `content/essays/moraliska-cirklar.md`
