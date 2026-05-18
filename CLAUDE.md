# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A plain HTML/CSS personal landing page for [andrej.zelnik.sk](https://andrej.zelnik.sk). No build step, no framework, no dependencies — just `index.html` and `style.css` served directly via GitHub Pages.

## Deployment

Pushing to `master` triggers `.github/workflows/deploy.yml`, which uploads the repo root to GitHub Pages. The custom domain is set by `CNAME`. There is no local build command — open `index.html` directly in a browser to preview.

To enable deployment on a fresh fork, go to **Settings → Pages → Source** and select **GitHub Actions**.

## Structure

- `index.html` — the entire page; content and social links live here
- `style.css` — all styles; fluid type scale via `font-size` at three breakpoints (default 95%, ≥800px 100%, ≥1400px 115%)
- `svg/` — social icon SVGs referenced as `<img src="/svg/*.svg">` in `index.html`
- `favicon.ico`, `favicon-{16,32}x32.png` — favicons; regenerate at [favicon.io](https://favicon.io/favicon-generator/) (settings: text "a", Fugaz One, size 125, white on black rounded)

## Accent colour

The purple dot after the heading (`h1 .dot`) uses `#9013fe`. This is the only brand colour.
