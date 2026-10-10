# I/C Research — website

The front door for **I/C Research** (Intelligence per Compute): an AI research lab on adaptive computation, testing whether a model's own history can tell it when to run less.

> **Interim page.** The current copy is a stopgap from the v2 positioning while the new site is planned and designed.

The site is a single static page. There is no build step, framework, or package manager.

## Structure

```
index.html        The whole site: markup and CSS (in <style>), no scripts
favicon.ico       16/32/48px favicon for browsers and crawlers that skip SVG icons
apple-touch-icon.png  180px icon for iOS home screens and some link previews
robots.txt, sitemap.xml
assets/
  logo/           Logo files, outlined SVGs that need no fonts; icon-dark.svg is the favicon
  social/         Share-preview card (og-card.png, 1200x630) and its HTML source; icon-512.png
images/           Logo concept images and screenshots (reference only; excluded from deploys)
```

### Logo files

| File | Use |
|------|-----|
| `ic-research-horizontal.svg` | Primary lockup (I/C · RESEARCH · Intelligence per Compute), light backgrounds |
| `ic-research-horizontal-light.svg` | Same, for dark backgrounds |
| `ic-research-mark.svg` | I/C mark alone, light backgrounds |
| `ic-research-mark-light.svg` | I/C mark alone, dark backgrounds |
| `icon-dark.svg` | Grid icon on an ink tile: favicon, social avatar, app icon |
| `ic-research-grid-horizontal.svg` | Grid icon + I/C RESEARCH wordmark, an alternate lockup |
| `ic-research-lockup.svg`, `ic-research-lockup-compact.svg` | Earlier stacked versions, kept as alternates |

The letterforms are EB Garamond ExtraBold (I/C) and Montserrat (RESEARCH, tagline), converted to outlines. Both fonts are under the SIL Open Font License. The page embeds the same logo inline in `index.html`, so it doesn't load these files.

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
| Contact | `#connect` | Writing, code, email, founder |

## Common edits

**Status.** The hero note states the current stage. Dates and thresholds live in the protocol, not on the homepage, so the page doesn't go stale when a milestone moves.

**Contact email.** Search for `hello@intelligencepercompute.com`. It appears in the Contact section and the footer.

**Colors and spacing.** Design tokens are CSS custom properties on `:root` at the top of the `<style>` block: ink, paper, field, amber and teal (with `-text` variants that meet WCAG AA contrast for small text), max width, and the fluid side gutter.

**Fonts.** Loaded from Google Fonts: Playfair Display (headings), Inter (body), DM Mono (labels).

## Share previews

Link previews on WhatsApp, LinkedIn, Slack, X and others come from the Open Graph and Twitter tags in `<head>`: title, description, and `assets/social/og-card.png`. Image URLs are absolute (`https://www.intelligencepercompute.com/...`), as the platforms require.

To change the card, edit `assets/social/og-card.html` and re-render it with Chrome:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars --force-device-scale-factor=1 --window-size=1200,630 --virtual-time-budget=8000 --screenshot="$PWD/assets/social/og-card.png" "file://$PWD/assets/social/og-card.html"
```

Platforms cache previews. After deploying a new card, refresh it with LinkedIn's Post Inspector or Facebook's Sharing Debugger; WhatsApp updates on its own after a while.

## Responsive behavior

Tested from 320px to 1920px wide, plus phones in landscape.

- Spacing, gutters and headline sizes scale fluidly with `clamp()`.
- Below 680px: single column; the header shows the I/C mark and the "Break the claim" button.
- The header nav drops links as space shrinks: "The question" below 900px, "Research" below 560px, "How we work" below 400px. The "Break the claim" button always stays.
- Touch devices get 44px minimum tap targets; hover effects apply only on devices that support hover.
- Safe-area insets are respected on notched phones.
- Motion (the hero entrance and frontier-curve draw) is disabled for visitors who prefer reduced motion.

## Deploying

The site deploys on Vercel from `main`. `index.html` at the repository root is the entry point. `.vercelignore` keeps `images/` (the logo concept files) out of the deploy; on another host, exclude that folder the same way.
