# I/C Research — website

The front door for **I/C Research** (Intelligence per Compute): an AI research lab on adaptive computation, testing whether a model's own history can tell it when to run less.

> **Interim page.** The current copy is a stopgap from the v2 positioning while the new site is planned and designed.

The site is a single static page. There is no build step, framework, or package manager.

## Structure

```
index.html        The whole site: markup and CSS (in <style>), plus a small inline script for the theme toggle
favicon.svg, favicon.ico, favicon-16/32/48.png   I/C mark favicons; from the brand kit (ops/brand/icons)
apple-touch-icon.png, android-chrome-*.png, maskable-512.png, site.webmanifest   touch and app icons
robots.txt, sitemap.xml
assets/
  brand/          Logos (SVG) and share-preview images (PNG), copied from the brand kit (ops/brand)
  social/         icon-512.png
images/           Logo concept images and screenshots (reference only; excluded from deploys)
```

### Logo files

All in `assets/brand/`, copied from the brand kit in the ops repo (`ops/brand/logos`). The files already include the brand's clear space, so size them by height. They are outlined SVGs and need no fonts.

| File | Use |
|------|-----|
| `ic-research-horizontal-reverse.svg` / `-primary.svg` | Header logo: reverse on dark, primary on light |
| `ic-research-mark-reverse.svg` / `-primary.svg` | I/C mark alone, for small phones (header) |
| `ic-research-horizontal-tagline-reverse.svg` / `-primary.svg` | Footer logo, with the tagline (only at 240px wide or more) |

Each logo is two `<img>` elements (`.on-dark`, `.on-light`); CSS shows the one that matches the active theme. Don't recolour the files; follow the logo rules in `ops/brand/README.md`.

## Run it locally

Open `index.html` in a browser, or serve the folder so relative paths behave exactly as in production:

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000.

## Page sections

| Section | Anchor | Purpose |
|---------|--------|---------|
| Hero | `#top` | Headline, one-line description, current stage |
| The question | `#question` | Why full passes on familiar inputs are waste; the three routes |
| How we work | `#how` | Protocol-first principle, Intelligence per Compute |
| Research | `#research` | FANN, research directions, stages A to C |
| Contact | `#connect` | Writing, code, LinkedIn, X, email, founder |

## Common edits

**Status.** The hero note states the current stage. Dates and thresholds live in the protocol, not on the homepage, so the page doesn't go stale when a milestone moves.

**Contact email.** Search for `hello@intelligencepercompute.com`. It appears in the Contact section and the footer.

**Colors and spacing.** Design tokens are CSS custom properties on `:root` at the top of the `<style>` block (values from `ops/brand/colors/tokens.css`): background, foreground, muted, line, field, amber and teal (with text-safe variants that meet WCAG AA contrast), max width, and the fluid side gutter.

**Theme.** Dark is the default; light follows the visitor's OS setting (`prefers-color-scheme: light`). The toggle in the header saves a choice in `localStorage` (`ic-theme`) and sets `data-theme` on `<html>`, which overrides the OS setting. Theme values live in the `:root` blocks near the top of the `<style>` block.

**Fonts.** Loaded from Google Fonts: Playfair Display (headings), Inter (body), DM Mono (labels).

## Share previews

Link previews on WhatsApp, LinkedIn, Slack, X and others come from the Open Graph and Twitter tags in `<head>`: title, description, and `assets/brand/og-image-1200x630-dark.png`. Image URLs are absolute (`https://www.intelligencepercompute.com/...`), as the platforms require.

The images come from the brand kit (`ops/brand/social/web`, dark and light, 1200x630). To change the card, regenerate it in the ops repo with `python3 brand/build/build.py` and copy the file here. Use a new file name when the image changes, so platforms don't serve a cached copy.

Platforms cache previews. After deploying a new card, refresh it with LinkedIn's Post Inspector or Facebook's Sharing Debugger; WhatsApp updates on its own after a while.

## Responsive behavior

Tested from 320px to 1920px wide, plus phones in landscape.

- Spacing, gutters and headline sizes scale fluidly with `clamp()`.
- Below 680px: single column; the header shows the I/C mark, the "Break the claim" button and the theme toggle.
- The header nav drops links as space shrinks: "The question" below 900px, "Research" below 560px, "How we work" below 400px. The "Break the claim" button always stays.
- Touch devices get 44px minimum tap targets (including the theme toggle); hover effects apply only on devices that support hover.
- Safe-area insets are respected on notched phones.
- Motion (the hero entrance and frontier-curve draw) is disabled for visitors who prefer reduced motion.

## Deploying

The site deploys on Vercel from `main`. `index.html` at the repository root is the entry point. `.vercelignore` keeps `images/` (the logo concept files) out of the deploy; on another host, exclude that folder the same way.
