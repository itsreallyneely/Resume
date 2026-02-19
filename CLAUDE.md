# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static HTML/CSS resume website for Kellen Neely. There is no build process, no JavaScript framework, and no package manager — changes are visible immediately by opening files in a browser.

## Previewing

Open HTML files directly in a browser, or serve them with any static file server:
```
python -m http.server 8080
```
Then visit `http://localhost:8080`.

To preview print layout, use browser print preview (Ctrl+P / Cmd+P). The `@media print` styles and `@page` rules in `styles.css` are critical for the paper output.

## Architecture

**Two resume variants share one stylesheet:**
- `index.html` — General-purpose resume
- `harper_tailored.html` — Version tailored for a specific employer/role (same structure, different summary/competencies wording)
- `styles.css` — Shared by both HTML files; controls all layout, typography, and color

**CSS design decisions:**
- All colors and font sizes are defined as CSS custom properties in `:root` (top of `styles.css`) — edit these to retheme
- `body::before` and `body::after` pseudo-elements display decorative SVG backgrounds (airplane, computer head) only on screen; both are hidden via `display: none` in `@media print`
- Print styles use `@page { size: letter; margin: 0.4in 0.8in; }` and `break-inside: avoid` on entries to prevent awkward page breaks
- Responsive breakpoint at 600px collapses grids to single-column and hides separator pipes

**SVG assets:**
- `United_Airlines_Boeing_777-200_Meulemans.svg` — airplane shown bottom-left as background decoration
- `colored_computerhead.svg` — computer head shown bottom-right as background decoration
- `resume-graphic.svg` — custom hand-drawn Inkscape SVG (currently unattached/in development)
- Untracked: `777_no_paint.svg`, `painted_forklift.svg` — SVG variants being worked on in the current branch

**Notebook:**
- `Notebook.ipynb` — The "Cancer in America by County" data science project referenced on the resume; linked from `index.html` to its GitHub URL

## Branching convention

Feature branches follow the pattern `feature-<topic>` (e.g., `feature-plane-svg`, `feature-color-changes`) and are merged into `main`.
