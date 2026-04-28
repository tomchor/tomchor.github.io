# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Personal academic website for Tomás Chor (geophysical fluid dynamicist). Built with Jekyll using a locally-vendored and customized [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme (v4.26.2). Deployed via GitHub Pages.

## Build & Serve

```bash
bundle install          # install gems (first time / after Gemfile changes)
bundle exec jekyll serve   # local dev server at http://localhost:4000 (live reload)
bundle exec jekyll build   # build to _site/
```

Requires Ruby. The Gemfile points to the local gemspec, so the theme is resolved from this repo, not from a remote gem.

## Architecture

**Content lives in two places:**

- `index.md` — homepage ("About me")
- `_pages/` — top-level site pages: research, publications, personal projects, field work, contact. Each page sets its own `permalink` in front matter.

**Navigation** is defined in `_data/navigation.yml` (maps to Research, Personal projects, Publications, Field work).

**Theme customization:**
- The theme is `remote_theme: mmistakes/minimal-mistakes` with skin `dark`.
- `_includes/`, `_layouts/`, `_sass/minimal-mistakes/` contain vendored + customized Minimal Mistakes files — edits here override the remote theme.
- `_includes/pubpage.html` and `_includes/pubpage.md` render the publications bibliography with CSL citation styles (`_includes/bvp.csl`, `_includes/els-modified.csl`).
- `assets/css/main.scss` imports the theme SCSS; no custom overrides beyond skin selection.

**Static assets:** `assets/images/`, `assets/pdf/` (publication PDFs), `assets/animations/` (research page videos).

## Key Conventions

- Publications are maintained as plain markdown in `_pages/publications.md` (not generated from data files). Each entry includes a DOI link and a link to a locally-hosted PDF in `assets/pdf/`.
- Pages use the `single` layout with `classes: wide` and `author_profile: true` by default (set in `_config.yml` defaults).
- The banner image `/assets/images/vortart/banner_vorticity.png` is shared across all pages via front matter `header.image`.
