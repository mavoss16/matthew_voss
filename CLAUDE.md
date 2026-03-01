# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Quarto blog** (matthew_voss) — a static website built with [Quarto](https://quarto.org/) and rendered to HTML. The blog contains political commentary posts by Matthew Voss. It is configured as an R project (`mjv_blog.Rproj`) but posts are plain Markdown (`.qmd` files) with no R code execution.

## Build & Render Commands

```bash
# Render the entire site
quarto render

# Preview the site locally with live reload
quarto preview

# Render a single post
quarto render posts/<post-folder>/index.qmd
```

The rendered output goes to `docs/` (configured in `_quarto.yml` as `output-dir: docs`), which is what GitHub Pages serves. The `_site/` directory is a legacy/mirror copy.

## Project Structure

- `_quarto.yml` — Site-level config: theme (cosmo + brand), output dir (`docs/`), navbar settings
- `posts/` — All blog posts, each in its own dated subfolder (e.g., `posts/20251026/index.qmd`)
- `posts/_metadata.yml` — Applied to all posts: `freeze: true` (no code re-execution), banner-style title blocks
- `templates/index.qmd` — Template for new posts
- `docs/` — Rendered site output (committed to git for GitHub Pages)
- `styles.css` — Custom CSS overrides

## Post Format & Conventions

Each post lives in `posts/<YYYYMMDD>/index.qmd` with this YAML front matter:

```yaml
---
title: "Post Title"
author: "Matthew Voss"
date: "YYYY-MM-DD"
categories: [Authoritarianism, Corruption, Immigration]
editor:
  markdown:
    wrap: sentence
---
```

- `wrap: sentence` — Markdown is wrapped at sentence boundaries (not word-wrapped)
- Categories used: `Authoritarianism`, `Corruption`, `Immigration` (and others)
- Posts use standard Markdown headers (`##`, `####`) to organize topics
- External citations are inline links: `([Source](URL))`
- `freeze: true` is set globally — computational output is frozen and never re-run

## Deployment

The `docs/` directory is committed to git and served via GitHub Pages from the `master` branch. After rendering, commit the updated `docs/` contents along with any new/changed `.qmd` files.
