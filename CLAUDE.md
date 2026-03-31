# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Personal portfolio/resume website hosted on GitHub Pages at https://nhavronskyi.github.io/. Jekyll-based static site with no build pipeline — files are served directly.

## Development

No build step required. To preview locally with Jekyll:
```bash
bundle exec jekyll serve
```

The site is deployed automatically by GitHub Pages on push to `main`.

## Architecture

- **`index.html`** — Root redirect (meta refresh) to `/pages/home`
- **`_layouts/default.html`** — Master Jekyll layout; loads Bootstrap 5.3.3, Font Awesome 6.4.0, and `/assets/css/style.css`
- **`pages/home/index.html`** — Landing page (two-column: profile left, about right)
- **`pages/resume/index.html`** — Full CV/resume page
- **`pages/404/index.html`** — Placeholder maintenance page (also serves as portfolio stub)
- **`assets/css/`** — One CSS file per page (`style.css` global, `landing.css`, `resume.css`, `404.css`)

Each page uses Jekyll front matter to select the `default` layout and set its title. CSS is page-scoped — edits to `resume.css` only affect the resume page.

## Key Details

- **PDF resume** is referenced as `/Nazar_Havronskyi.pdf` from the resume page's download button. The file in the repo root must match that name.
- **Years of experience** on the home page is calculated dynamically in JS from a hardcoded start date of March 2024.
- **Email copy button** on the home page switches icons (copy → checkmark → copy) via `copyTextFromElement()`.
- Bootstrap grid handles responsive layout; a media query in `resume.css` handles ≤600px screens.
