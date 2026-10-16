# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A static personal resume site (Nicolas Bretécher). Plain HTML + CSS: no build step, package manager, linter, or tests.

- `index.html`: portfolio (home) page with the `projects` section
- `blog.html`: blog; posts are `<article class="card">` entries
- `about.html`: "About me" page: `about` (job title, location, contact links), `experience`, `education`, `skills` sections
- `styles.css`: all styling, shared by all pages, including the `@font-face` declarations for the self-hosted Quicksand font in `fonts/`
- `images/profile.jpg`: profile picture shown in the header

Every page starts with the same `<header>` with the profile picture, name, and a `<nav>` linking Portfolio / Blog / About me. It is copied by hand into each page, so edit all three together.

## Guiding principles

Keep it simple. These are deliberate choices; don't change them without being asked.

- Use vanilla HTML, CSS, and JavaScript wherever possible.
- Avoid libraries and frameworks. Add one only when there's no reasonable vanilla alternative.
- No build tools, bundlers, transpilers, or `package.json`. Files are served as-is.
- No over-abstraction: no templating systems or component layers. Write the markup directly in each page, even when it repeats.
- No tests.

## Previewing

Open `index.html` directly in a browser, or serve the directory so relative paths resolve as they would when hosted:

```sh
python3 -m http.server 8000
```

## Conventions

- Asset paths are relative (`styles.css`, `fonts/...`, `images/...`). Keep them relative; the "fix asset paths" commit switched to this.
- Each experience/education entry is an `<article class="card">` with an `<h3>` title (`Role — Company`) and a `<p class="card-subtitle">` for dates, contract type, and location. Skills are `<span class="badge">` items grouped into `<p>` rows (frontend / backend & data / tooling).
- Content mixes French and English (dates and many descriptions are in French, LinkedIn-style e.g. `sept. 2025 - Present · CDI`). Match the language of neighboring entries.
- Headings (`h2`, `h3`) use Quicksand; body text uses the system sans-serif stack. Accent color is `#1a73e8`.
