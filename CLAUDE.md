# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A [Quarto](https://quarto.org) website (`project: type: website` in `_quarto.yml`) published as `franciscoletelier.github.io` via GitHub Pages. It is a personal site with a landing page (`index.qmd`), an about page (`about.qmd`), and an article gallery (`posts.qmd`) linking to individual posts in `posts/`.

**GitHub Pages serves `docs/` directly** — there is no CI build step. Every change to `.qmd` source files must be rendered locally with `quarto render` and the resulting `docs/` output committed alongside the source. The `docs/` directory is the published site; keep it in sync with the source.

## Quick Start

First time? Set up your environment:

```bash
# 1. Verify Quarto is installed
quarto --version

# 2. Create and activate Python virtual environment
python3 -m venv .venv
source .venv/bin/activate

# 3. Install Python dependencies
pip install -r requirements.txt

# 4. Verify Jupyter setup
quarto check jupyter
```

Then you're ready to develop. See **Commands** below for rendering and preview workflows.

## Commands

```bash
# Render the whole site (updates docs/) — run after any change to a .qmd file
quarto render

# Render a single post while iterating (faster than full render)
quarto render posts/<name>.qmd

# Live-preview with auto-reload while writing
quarto preview

# After pulling changes: clean cache if renders fail unexpectedly
rm -rf .quarto/
```

### Python environment (needed for posts with executable Python code)

Some posts (e.g. `posts/rutas-maritimas-chile.qmd`) are real Quarto documents with `{python}` code cells executed via the Jupyter engine. Dependencies live in a project-local virtualenv because macOS's Homebrew Python is externally managed.

**Always activate the venv before rendering:**

```bash
source .venv/bin/activate && quarto render posts/<name>.qmd
```

This ensures Quarto's Jupyter engine finds the right Python interpreter and installed packages.

`.venv/` is gitignored. `requirements.txt` is the source of truth for Python deps — edit it (then re-run `pip install -r requirements.txt`) when a post needs a new package.

## Architecture: two kinds of posts

Posts in `posts/` follow one of two patterns — check which one before editing:

1. **Hand-authored standalone HTML** (e.g. `posts/coincidencias.html`): plain HTML with Tailwind CDN, Chart.js, KaTeX, etc. These bypass Quarto rendering entirely — they're copied as-is into `docs/posts/` via the `resources: [posts/*.html]` entry in `_quarto.yml`. They do **not** inherit the site's navbar/footer/theme, so they hand-roll their own back-navigation bar (`<a href="../index.html">Volver al sitio</a>` / `<a href="../posts.html">Artículos</a>`).

2. **Real Quarto documents** (`.qmd`, e.g. `posts/rutas-maritimas-chile.qmd`): executable Python notebooks rendered by Quarto's Jupyter engine into `docs/posts/<name>.html`. These automatically inherit the site's navbar, footer, and `cosmo` theme from `_quarto.yml` — no manual navigation markup needed. They typically use `execute: freeze: auto` in the front matter so Quarto reuses cached execution results (stored in `_freeze/`, which **is** committed to version control) instead of re-running Python/OR-Tools on every full-site render — this matters because there's no CI, so `_freeze/` is what lets the site be rebuilt without reinstalling the Python environment.

When adding a new post: decide up front which pattern it needs. If it's meant to show live-executed Python/data-analysis code, use the `.qmd` + Jupyter pattern and follow the structure of `posts/rutas-maritimas-chile.qmd` (front matter with `code-fold: true`, `df-print: paged`, `freeze: auto`).

## Adding a post to the gallery

`posts.qmd` lists posts as `.post-card` divs inside a `.posts-grid` container. Duplicate an existing card (title as a markdown link to `posts/<name>.html`, a `.post-card-tag`, description, `.post-card-meta` line, and a `.post-card-link`) — there's a placeholder "Próximamente" card at the end showing the pattern to copy. Link to the **rendered** `.html` output, not the `.qmd` source.

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `quarto render` fails with "Jupyter not found" or "Python not found" | Activate the venv: `source .venv/bin/activate` before running `quarto render` |
| Python code cells don't execute / `.py` imports fail | Same as above — the venv must be active so Quarto's Jupyter engine finds the right Python |
| `quarto render` produces unexpected output or caches stale results | Delete the cache: `rm -rf .quarto/` and try again |
| Single post renders but full-site `quarto render` fails | The full render stops at the first error. Check the error message, fix that one post, and re-run |

## Styling

`styles.css` holds all custom CSS on top of Quarto's `cosmo` Bootstrap theme (configured in `_quarto.yml`: `format.html.theme: cosmo`, custom font Inter via Google Fonts, FontAwesome icons). The site is light-themed only — there is no dark-mode toggle.
