# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page website for Nollayks software consultancy. No build tools, bundlers, or package managers — pure HTML, CSS, and JavaScript deployed to GitHub Pages at `nollayks.com`.

## Development

Open `index.html` directly in a browser or use any static file server:

```bash
python3 -m http.server 8080
# or
npx serve .
```

There are no build, lint, or test commands.

## Architecture

All content lives in three files:

- **`index.html`** — Single-page layout with 7 sections: navbar, hero, services, expertise, why-us, contact, footer. All copy is inline.
- **`styles.css`** — CSS custom properties defined in `:root`, responsive grid layouts, scroll-reveal transitions, and breakpoints at 900px and 600px.
- **`script.js`** — Three behaviours: navbar scroll shadow, hamburger mobile menu, IntersectionObserver scroll-reveal, and async Formspree form submission.

## Design System

CSS custom properties (defined in `:root`):
- Background: `--bg: #0A0F1E`, Surface: `--surface: #111827`
- Accent: `--accent: #3B82F6`, Success: `--success: #10B981`, Amber: `--amber: #F59E0B`
- Font: Inter from Google Fonts (400/600/700)
- Note: navbar and footer use white backgrounds (`#ffffff`) — intentionally different from the dark page body.

## Scroll Reveal Pattern

Elements with class `reveal` start hidden (`opacity: 0, translateY(28px)`) and gain class `visible` when scrolled into view via IntersectionObserver in `script.js`. Add `reveal` to any new card or section element to animate it in.

## Deployment

Push to `main` branch → GitHub Pages auto-deploys. No CI/CD pipeline. The `CNAME` file sets the custom domain.

## Contact Form

Form submits to Formspree (`https://formspree.io/f/maqdzazq`). The JS in `script.js` intercepts submit, POSTs via `fetch`, and shows inline success/error state in `#formStatus`.
