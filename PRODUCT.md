# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Standalone Next.js (latest) + Tailwind CSS (latest) web app, in this repo (`ic-research-web`), separate codebase from the sibling publication. Must support light/dark mode. Confirmed by the user during init (locked as stated in the original brief).

## Users

Primary: engineers/teams who **self-host** models (training or inference), carry a **real GPU bill**, and have **no dedicated optimization team**. Not API-only stacks, not teams with a large in-house performance team, not toy spend. The buyer is whoever owns the GPU invoice.

Secondary: researchers/labs/faculty interested in the FANN research thesis (a distinct, non-commercial audience — collab/red-team/co-author interest, not a sales lead).

## Product Purpose

**I/C Research** ("Intelligence Per Compute") is a research lab that pays for itself by cutting other people's GPU bills, while researching how to make AI compute go further. This site is the lab's front door: brand/company home plus a feed of its research output. It is not a pure marketing landing page and not a pure blog — it does both jobs on one page plus a few supporting pages.

Success = a self-hosting team with a real GPU bill understands the offer and starts a conversation (design-partner engagement), and the research thesis (FANN) reads as credible, ongoing lab work rather than a pitch.

## Positioning

Sits in the efficiency/optimization layer for AI infrastructure — closest historical analogs (OctoML, Deci, Neural Magic, MosaicML) were acquired because efficiency is strategic infra, not a standalone category. Not a hosted inference API (Together, Fireworks) and not GPU orchestration (Run:ai). The wedge: a **measurable 2–5× cost reduction**, proven with paid design partners before any platform ambitions. Explicitly not an agentic product, a platform, a dashboard, or anything whose value is a UI.

## Operating Context

**Commercial engagement model:** paid, fixed-fee engagements (~4 weeks) that cut a client's training or inference GPU bill at an agreed quality bar, using whatever combination of quantization, distillation, pruning, GPU utilization, and training/serving-stack changes moves the number in that window. Client keeps optimized weights/recipes under licence; IP stays with I/C Research. No hourly billing, no dashboard, no agent product.

**Research thread (not the pitch):** FANN — Familiarity-Aware Neural Networks — allocates compute in inverse proportion to path-level familiarity in a model's processing (skip work instead of caching a full-price answer). A longer-horizon research bet explored in parallel using real workload shape earned from paid engagements. Appears on the site as a research thread/teaser, not the commercial pitch.

**Sibling publication:** The Efficient Frontier (theefficientfrontier.ai) is the lab's existing long-form research publication (Next.js 15 + Tailwind 4 + Contentlayer2, author Kailash Ahirwar), not being renamed, not replaced by this site — this site is the parent/lab site that the publication sits under and links to.

**Research feed integration:** undecided whether posts from The Efficient Frontier are live-fetched (RSS/API) or manually curated for v1 — build the feed UI against placeholder/representative data now; the data-source decision comes later. Native short-form research notes (FANN teasers, quantization notes) may also live directly on this site.

**Copy source material** (for whoever writes final copy, paths relative to the sibling `codebase/` directory):
- `efficio-hq/knowledge/one-pager.md` — commercial offer, verbatim sales copy to adapt
- `efficio-hq/knowledge/positioning.md` — what we sell vs. what we research
- `efficio-hq/knowledge/glossary.md` — terminology used consistently in outreach
- `efficio-hq/knowledge/papers-latest.md` — current research reading, source for research-feed teaser content
- `efficio-ai/README.md`, `efficio-ai/ABOUT-EFFICIO-AI.md` — fuller company narrative (pre-rename name "Efficio AI," same substance)
- `efficio-ai/company/research-thesis-and-wedge.md` — deeper research-strategy background (superseded in parts by the current Sep–Dec 2026 plan, which centers on quantization + FANN rather than the earlier diffusion-blocks wedge)
- `efficio-ai-publication/` — the live Efficient Frontier codebase, a technical/content-model reference, not a visual template to copy

## Capabilities and Constraints

- No dependency on the marketing image-generation motifs (trapezoid stacks, landscape vignettes) as literal UI components — those were built for static social graphics, not web chrome.
- Design/components should be clean enough to translate directly into Tailwind utility classes / a small design-token set (colors, spacing, radii, type scale) — avoid one-off bespoke shapes that are hard to rebuild in code.
- Research feed data source (live-fetch vs. static/curated) is an explicitly open decision (see Operating Context).

## Brand Commitments

- **Current name:** I/C Research, stylized **I/C Research**, meaning "Intelligence Per Compute."
- **Former name:** Efficio AI. The rename is recent (Sep 2026); older internal docs saying "Efficio AI" are historical, not current brand.
- **The Efficient Frontier** (theefficientfrontier.ai) is a separate, unchanged publication brand this site links to as a sibling, not a property this site absorbs or restyles.
- **Voice:** direct, technical, numbers-first — written by and for engineers who own a GPU bill. No hype language ("revolutionary," "game-changing"); claims are backed by a quality-vs-cost table, not adjectives. Confident but plain: short declarative sentences, real numbers (2–5×, ~4 weeks), explicit about what the lab does *not* do. The offer/commercial pages read like a sales page in disguise as documentation; the research feed reads like a lab notebook — these are distinct voices.

## Evidence on Hand

- One-pager, positioning doc, glossary, and current-reading notes exist in `efficio-hq/knowledge/` (see Operating Context for paths) — real source copy to adapt, not to be treated as absent.
- No customer testimonials, case studies, or public benchmark numbers exist yet on hand for this site; do not fabricate them. The "measurable 2–5×" figure is a positioning claim from source docs, not a citable case study — do not attribute it to a named client without confirmation.
- No dedicated web visual-identity system exists yet; two internal visual-language docs written for generated marketing graphics exist as directional (not locked) references — visual-world decisions belong to `new-work`, not this file.

## Product Principles

- The commercial offer and the research thesis are two distinct voices on one site — never blur the sales page into the lab notebook, or vice versa.
- Every claim is numbers-first and falsifiable (2–5×, ~4 weeks); no unearned superlatives.
- The site is the lab's front door, not a product UI — nothing here should read as "the product is a dashboard/app."
- Brand separation is a hard constraint: The Efficient Frontier keeps its own identity; this site is the parent that links out to it, never a reskin of it.
- IP and outcome framing ("you keep the outcome, we keep the IP") is core positioning language to preserve, not a detail to soften.

## Accessibility & Inclusion

Target WCAG 2.1 AA (confirmed by the user during init): sufficient color contrast, full keyboard navigation, semantic structure. Treat as a baseline constraint on the palette/type system established later, not an afterthought pass.
