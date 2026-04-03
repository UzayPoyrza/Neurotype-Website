# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Neurotype is a static marketing website for a meditation app (neurotypeapp.com). It is a landing page with a waitlist signup form, plus legal/policy pages and an OAuth redirect handler for the companion mobile app. There is no build step, no framework, and no package.json — everything is plain HTML/CSS/JS served as static files.

## Deployment

- Hosted on **Vercel** (project: `neurotype-website`)
- Pushing to `main` triggers automatic deployment
- Routing and headers configured in `vercel.json`
- Domain: `neurotypeapp.com`

## Architecture

```
public/              ← Vercel serves this directory as the site root
  index.html         ← Main landing page (single-file: all CSS + JS inline)
  oauth-redirect.html← OAuth callback → deep link bridge for mobile app
  privacy-policy.html
  terms-of-service.html
  consumer-health-data-privacy-policy.html
  robots.txt / sitemap.xml
  icons/             ← Logo variants, favicons
vercel.json          ← Rewrites, security headers, cache rules
```

### Key design decisions

- **Single-file landing page**: `index.html` contains all styles in a `<style>` block and all JS in a `<script>` block at the end. There are no external CSS/JS files. When editing, be aware the file is large (~1500 lines).
- **No build system**: Edit files directly; changes are live on deploy.
- **Waitlist form** submits directly to Supabase REST API (anon key is in `index.html`). The table is `waitlist` in the Supabase project.
- **OAuth redirect** (`oauth-redirect.html`) extracts `id_token` from URL params/hash and redirects to `neurotype://oauth-callback` deep link for the mobile app.

### Design system (CSS custom properties in index.html)

- Primary accent: `--accent: #2A9D8F` (teal)
- Fonts: `Instrument Serif` for h1, `Plus Jakarta Sans` for body/headings
- Dark sections use `--bg-dark: #0C1117`; light sections use `--bg-system: #FFFFFF`
- Scroll-reveal animations via `.reveal` class + IntersectionObserver in JS

## Local Development

No install or build needed. Open `public/index.html` in a browser, or:

```bash
# Quick local server (any of these work)
npx serve public
python3 -m http.server -d public
```

To test Vercel-specific routing (rewrites, headers), use:
```bash
npx vercel dev
```
