# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is the static website for **Forge Performance Co.** (teamfpco.com), hosted on GitHub Pages. The entire site is a single self-contained file: `index.html`.

## Architecture

- **`index.html`** — The entire website. All CSS is in a `<style>` block in `<head>`, all JavaScript is in a `<script>` block before `</body>`. There are no external stylesheets, build tools, frameworks, or bundlers.
- **`assets/`** — Static images: two logo variants (`primary_logo_transparent.png`, `alt_primary_logo_transparent.png`) and a founder headshot (`images/founder-headshot.jpeg`).
- **`CNAME`** — GitHub Pages custom domain: `teamfpco.com`.

## Development

No build step required. Open `index.html` directly in a browser, or use any local static file server:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Brand Design System

CSS custom properties are defined at the top of the `<style>` block under `DESIGN TOKENS — FORGE BRAND SYSTEM`:

- **Colors**: `--black`, `--forge`, `--steel`, `--slate`, `--copper` (accent), `--ember`, `--pearl` (light text)
- **Typography**: `--f-head` (Montserrat), `--f-body` (Inter)
- **Key accent color**: `--copper: #b46e3d` / `--ember: #d4895a`

Always use these CSS variables rather than hardcoding values.

## Deployment

Pushing to `main` on GitHub automatically deploys via GitHub Pages. No CI pipeline exists.
