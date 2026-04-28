---
name: explorable-aesthetics
description: Visual-direction reference for /explorable. Source-genre starting patterns, anti-slop filter, color-stable variables. Phase 2 reads this before generating any design.
---

# Aesthetics — visual direction reference

Phase 2 of /explorable reads this file before generating any design. SKILL.md
carries the principle ("the source's subject dictates the visual register");
this file carries the starting patterns, the banned defaults, and the color
discipline that does most of the work.

## Contents

- [Source-genre starting patterns](#source-genre-starting-patterns)
- [Anti-slop filter — banned defaults](#anti-slop-filter--banned-defaults)
- [Color-stable variables](#color-stable-variables)

---

## Source-genre starting patterns

A reader landing cold should be able to guess the topic from the visual
language alone. Each subject genre has an established register that readers
already know how to read. Use these as starting patterns, not menus to pick
from — the source can override.

- **Children's iPad app** → playful, generous, hand-drawn marks, warm
  palette, picture-book cadence
- **Scientific research synthesis** → archival, restrained, serif body,
  numbered figures, generous white space
- **Security post-mortem** → brutalist, monospace where it earns it, high
  contrast, no decorative warmth
- **Founder letter** → editorial, single-column, drop caps if the prose
  warrants, restrained color
- **Code archaeology / repo retrospective** → terminal-archive hybrid, mono
  accents, timestamp typography, log-style margins
- **Civics / history learning doc** → archival but alive, period-aware
  palette without pastiche, real sources visible
- **Investment thesis** → understated, precise, financial-press typography,
  no dashboard glam
- **Methodology / how-to** → diagrammatic, technical-manual restraint,
  numbered steps, callouts where they earn their place
- **Design exploration** → catalog-page logic, side-by-side, captions
  doing real work, type as evidence

The principle: read the source for what it's already telling you about its
visual world.

- **Subject genre.** Children's product, scientific research, founder essay,
  code archaeology, civics, design critique, financial memo, art history.
  Each has a register readers already know.
- **Named visual referents.** Colors ("Purple Crayon" → Harold's purple),
  objects, cultural references, era, brand identity. If the source names
  something visual, it's load-bearing — use it.
- **Tone.** Playful, austere, journalistic, intimate, technical. Match it.
- **Audience.** Who would naturally read this, and what media do they
  already consume? Design for that reader, not a generic "tasteful website."

The skill chooses the palette, fonts, and aesthetic moves; the list above
is a starting pattern, not a menu.

---

## Anti-slop filter — banned defaults

Apply before any design generation. Every one of these reads as AI slop.

**Fonts.** Inter, Roboto, Arial, Fraunces, Space Grotesk, system-ui as
automatic default. Pick something with character that fits the source's
register — distinctive display fonts, opinionated body fonts. A fourth
font earns its place only if the subject genuinely calls for a hand-written
accent.

**Color.** Default purple-blue SaaS palette, gradient backgrounds applied
out of habit, glassmorphism. Commit to a cohesive palette derived from the
source's subject — dominant colors with sharp accents beat timid, evenly-
distributed palettes.

**Decoration.** Emoji as decoration. Decorative icons that carry no
meaning. Auto-generated hero art with no teaching role. Margin asides that
don't add information not in the main text. Left-border Notion cards.

**Pattern matter.** Cookie consent modals, sign-in gates, fake CTAs — the
explorable is the artifact, not a marketing page.

**Copy.** Every section starting with "In today's…" or "It's important to
note…" — see [writing.md](writing.md) for the LLM-tic catalog.

**Font count.** Usually 2–3 fonts (display + body, plus mono if metadata is
present). A fourth earns its place only if the subject genuinely calls
for a hand-written accent.

---

## Color-stable variables

Each named quantity in the piece gets a color at first introduction. That
color is reused in every subsequent widget, in inline math, and as the
stroke color in diagrams.

This single discipline does most of the work of "looking like a real
explainer."

Implementation:

- Define color tokens as CSS custom properties at the top of the
  `<style>` block: `--color-x`, `--color-y`, `--color-z`.
- First introduction in prose uses the color as a `<span>` inline.
- Every subsequent reference — widget, diagram stroke, equation term —
  uses the same token.
- The reader learns the color-to-quantity mapping once and reads diagrams
  faster from then on.

Bret Victor's *Scrubbing Calculator* and Bartosz Ciechanowski's pieces
are the canonical examples. Color-stable variables are the difference
between "an explainer with charts" and "an explainer that teaches."
