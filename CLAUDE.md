# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A [Quarto](https://quarto.org) website (`project: type: website` in `_quarto.yml`) published as `franciscoletelier.github.io` via GitHub Pages. It is a personal site with a landing page (`index.qmd`), an about page (`about.qmd`), and an article gallery (`posts.qmd`) linking to individual posts in `posts/`.

**GitHub Pages serves `docs/` directly** — there is no CI build step. Every change to `.qmd` source files must be rendered locally and the resulting `docs/` output committed alongside the source.

## Commands

```bash
# Render the whole site (updates docs/) — run after any change to a .qmd file
quarto render

# Render a single post while iterating
quarto render posts/<name>.qmd

# Live-preview with auto-reload while writing
quarto preview
```

### Python environment (needed for posts with executable Python code)

Some posts (e.g. `posts/rutas-maritimas-chile.qmd`) are real Quarto documents with `{python}` code cells executed via the Jupyter engine, not static HTML. macOS's Homebrew Python is externally managed, so dependencies live in a project-local virtualenv:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# Always activate the venv before rendering any post with Python code cells,
# so Quarto's Jupyter engine picks up the right interpreter/kernel:
source .venv/bin/activate && quarto render posts/<name>.qmd

# Sanity-check that Quarto can find Jupyter/the venv's Python:
quarto check jupyter
```

`.venv/` is gitignored. `requirements.txt` is the source of truth for Python deps — update it (not just `pip install`) when a post needs a new package.

## Architecture: two kinds of posts

Posts in `posts/` follow one of two patterns — check which one before editing:

1. **Hand-authored standalone HTML** (e.g. `posts/coincidencias.html`): plain HTML with Tailwind CDN, Chart.js, KaTeX, etc. These bypass Quarto rendering entirely — they're copied as-is into `docs/posts/` via the `resources: [posts/*.html]` entry in `_quarto.yml`. They do **not** inherit the site's navbar/footer/theme, so they hand-roll their own back-navigation bar (`<a href="../index.html">Volver al sitio</a>` / `<a href="../posts.html">Artículos</a>`).

2. **Real Quarto documents** (`.qmd`, e.g. `posts/rutas-maritimas-chile.qmd`): executable Python notebooks rendered by Quarto's Jupyter engine into `docs/posts/<name>.html`. These automatically inherit the site's navbar, footer, and `cosmo` theme from `_quarto.yml` — no manual navigation markup needed. They typically use `execute: freeze: auto` in the front matter so Quarto reuses cached execution results (stored in `_freeze/`, which **is** committed to version control) instead of re-running Python/OR-Tools on every full-site render — this matters because there's no CI, so `_freeze/` is what lets the site be rebuilt without reinstalling the Python environment.

When adding a new post: decide up front which pattern it needs. If it's meant to show live-executed Python/data-analysis code, use the `.qmd` + Jupyter pattern and follow the structure of `posts/rutas-maritimas-chile.qmd` (front matter with `code-fold: true`, `df-print: paged`, `freeze: auto`).

## Adding a post to the gallery

`posts.qmd` lists posts as `.post-card` divs inside a `.posts-grid` container. Duplicate an existing card (title as a markdown link to `posts/<name>.html`, a `.post-card-tag`, description, `.post-card-meta` line, and a `.post-card-link`) — there's a placeholder "Próximamente" card at the end showing the pattern to copy. Link to the **rendered** `.html` output, not the `.qmd` source.

## Styling

`styles.css` holds all custom CSS on top of Quarto's `cosmo` Bootstrap theme (configured in `_quarto.yml`: `format.html.theme: cosmo`, custom font Inter via Google Fonts, FontAwesome icons). The site is light-themed only — there is no dark-mode toggle.
