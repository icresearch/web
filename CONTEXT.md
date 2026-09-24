# I/C Research — Landing Page: Design Context

Paste this into the Claude Design console as the brief for the `ic-research-web` landing page.

---

## 1. One-line summary

**I/C Research** ("Intelligence Per Compute") is a research lab that pays for itself by cutting other people's GPU bills — while researching how to make AI compute go further. This site is the lab's front door: brand + a feed of its research output.

## 2. Naming note (important, get this right)

- **Current name:** I/C Research — stylized as **I/C Research**, meaning **"Intelligence Per Compute."**
- **Former name:** Efficio AI. The rename is recent (Sep 2026); any older internal docs still say "Efficio AI" — treat that as historical, not current brand.
- **Publication brand stays separate and unchanged:** **The Efficient Frontier** (theefficientfrontier.ai) is the lab's existing long-form research publication (Next.js + Tailwind + Contentlayer blog, author Kailash Ahirwar). It is not being renamed and this new site does not replace it — this new site is the parent/lab site that the publication sits under and links to.

## 3. What the lab actually does

**Sells (funds the lab):** Paid, fixed-fee engagements — roughly **4 weeks** — that cut a client's training or inference GPU bill at an agreed quality bar, using whatever combination of quantization, distillation, pruning, GPU utilization, and training/serving-stack changes actually moves the number in that window. Client keeps optimized weights/recipes under licence; **IP stays with I/C Research**. No hourly billing, no dashboard, no agent product, no UI-as-the-product.

**Buyer / ICP:** Teams that **self-host** models (training or inference), have a **real GPU bill**, and have **no dedicated optimization team**. Not API-only stacks, not teams with a large in-house perf team, not toy spend.

**Researches (the thesis, not the pitch):** **FANN** — Familiarity-Aware Neural Networks: allocate compute in inverse proportion to *path-level* familiarity in a model's processing (skip work instead of caching a full-price answer). This is a longer-horizon research bet, explored in parallel using real workload shape earned from paid engagements. It should appear on the site as a research thread/teaser, not as the commercial pitch.

**Explicitly not:** an agentic product, a platform, a dashboard, or anything whose value is a UI.

## 4. Positioning vs. the market

Sits in the efficiency/optimization layer for AI infrastructure — closest historical analogs (OctoML, Deci, Neural Magic, MosaicML) were acquired because efficiency is strategic infra, not a standalone category. Not a hosted inference API (Together, Fireworks) and not GPU orchestration (Run:ai). The wedge is a **measurable 2–5× cost reduction**, proven with paid design partners before any platform ambitions.

## 5. Voice and tone

- Direct, technical, numbers-first. Written by and for engineers who own a GPU bill.
- No hype language ("revolutionary," "game-changing"). Claims are backed by a quality-vs-cost table, not adjectives.
- Confident but plain: short declarative sentences, real numbers (2–5×, ~4 weeks), explicit about what the lab does *not* do.
- Research and commercial voices are distinct: the offer page is a sales page in disguise as documentation; the research feed reads like a lab notebook.

## 6. Existing visual-identity cues (from marketing assets, no dedicated site theme yet)

There is no locked web design system yet — this is a fresh brand and Claude Design should help establish one. But two internal visual-language docs (originally written for generated marketing graphics) point at a consistent aesthetic worth carrying into the web design:

- **Palette:** cool white canvas/background; **display navy** for headline type; one accent family only — **periwinkle/violet** — for kickers, links, underlines, numerals, icon strokes; very pale lilac washes for nested surfaces. No neon, no gold, no extra accent hues, no gradient mesh.
- **Type:** geometric grotesque sans (Inter/Satoshi character). Four-role hierarchy: extra-bold tight-tracking display, a lighter "deck" subhead, a small accent-colored kicker, and micro/caption text. A short thick accent underline under display headlines for emphasis (not a highlighter bar).
- **Surfaces:** large-radius rounded white cards/boards with soft cool shadows, hairline (often dotted) connectors, generous airy padding, low density — leftover whitespace is intentional, not a gap to fill.
- **Mood:** quiet, precise SaaS/lab product — confident and airy, not playful-sketch, not cinematic dark-tech, not a dense dashboard. No photos of people, no hand lettering, no logos/watermarks baked into imagery.

Treat this as a strong starting palette/type direction, not a locked spec — Claude Design should propose an actual web design system (light/dark mode, component states, spacing scale) consistent with this mood.

## 7. Site goal: hybrid brand + research feed

This is **not** a pure marketing landing page and **not** a pure blog. It needs to do two jobs on one page (and a few supporting pages):

1. **Brand/company home:** explain what I/C Research is, what it sells, who it's for, and how to start a conversation (design-partner engagement).
2. **Research feed:** surface the lab's research output — pulling in / linking out to posts from The Efficient Frontier, plus shorter research notes/threads that may live natively on this site (FANN teasers, quantization notes, etc.).

## 8. Proposed page structure (starting point, not final)

- **Header/nav:** I/C Research wordmark · Approach · Research · About · Contact/CTA
- **Hero:** name + meaning ("Intelligence Per Compute"), one-line mission, primary CTA ("Talk to us about your GPU bill") + secondary CTA (read the research)
- **What we do (offer):** the 4-week paid-engagement model, the method list (quantization/distillation/pruning/utilization), "you keep the outcome, we keep the IP" framing — adapted from the one-pager
- **Who it's for:** self-hosting teams with a real GPU bill and no dedicated optimization group (explicit "not for" list builds trust)
- **Research thesis teaser:** FANN in one paragraph + "why this is research, not the pitch" framing, linking to deeper material
- **Research feed:** latest 3–6 posts, pulled from The Efficient Frontier (and/or native short-form notes), each with title/date/one-line summary, linking out to theefficientfrontier.ai
- **Positioning/credibility:** short comparison to the acquired-efficiency-company landscape (OctoML, Deci, Neural Magic, MosaicML) framed as "why this layer matters," not a features table
- **CTA band:** "20 minutes with whoever owns the GPU invoice" — the actual ask from the one-pager
- **Footer:** links to The Efficient Frontier, contact, socials

## 9. Tech constraints for the design

- Build target: **Next.js (latest)** + **Tailwind CSS (latest)**, deployed as a standalone site in `ic-research-web` (separate codebase from the existing publication).
- Should support light/dark mode (the sibling publication site does).
- Design should be componentized cleanly enough to translate directly into Tailwind utility classes / a small design-token set (colors, spacing, radii, type scale) — avoid one-off bespoke shapes that are hard to rebuild in code (e.g. the trapezoid slab motif from the marketing docs is fine for social graphics, likely too illustrative for site chrome).
- No dependency on the marketing image-generation motifs (trapezoid stacks, landscape vignettes) as literal UI — those were for static social graphics, not web components.

## 10. Source material available (for whoever writes final copy)

- `efficio-hq/knowledge/one-pager.md` — the commercial offer, verbatim sales copy to adapt
- `efficio-hq/knowledge/positioning.md` — what we sell vs. what we research, in one page
- `efficio-hq/knowledge/glossary.md` — terminology used consistently in outreach
- `efficio-hq/knowledge/papers-latest.md` — current research reading (compression/on-device), good source for research-feed teaser content
- `efficio-ai/README.md` / `ABOUT-EFFICIO-AI.md` — fuller company narrative (pre-rename name, same substance)
- `efficio-ai/company/research-thesis-and-wedge.md` — deeper research-strategy background (note: superseded in parts by the current Sep–Dec 2026 plan, which centers on quantization + FANN rather than the earlier diffusion-blocks wedge)
- `efficio-ai-publication/` — the live Efficient Frontier codebase (Next.js 15, Tailwind 4, Contentlayer2), useful as a technical/content-model reference, not a visual template to copy
