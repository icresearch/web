# I/C Research — website

The front door for **I/C Research** (Intelligence per Compute): an AI research lab on adaptive computation, testing whether a model's own history can tell it when to run less.

> **Interim page.** The current copy is a stopgap from the v2 positioning while the new site is planned and designed.

The site is a single static page. There is no build step, framework, or package manager.

## Structure

```
index.html        The whole site: markup and CSS (in <style>), no scripts
assets/
  logo/           Logo files, outlined SVGs that need no fonts; icon-dark.svg is the favicon
images/           Logo concept images and screenshots (reference only, not used by the page)
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

## Responsive behavior

Tested from 320px to 1920px wide, plus phones in landscape.

- Spacing, gutters and headline sizes scale fluidly with `clamp()`.
- Below 680px: single column; the header shows the I/C mark and the "Break the claim" button.
- The header nav drops links as space shrinks: "The question" below 900px, "Research" below 560px, "How we work" below 400px. The "Break the claim" button always stays.
- Touch devices get 44px minimum tap targets; hover effects apply only on devices that support hover.
- Safe-area insets are respected on notched phones.
- Motion (the hero entrance and frontier-curve draw) is disabled for visitors who prefer reduced motion.

## Deploying

Any static host works (GitHub Pages, Netlify, Vercel, Cloudflare Pages, S3). Publish the repository root; `index.html` is the entry point. Exclude `images/` from the deploy if you want to keep the concept files private — the page doesn't use them.
