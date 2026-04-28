---
name: explorable-primitives
description: Interactive-primitives reference for /explorable. Full primitive table, the teaching test, predict-then-reveal evidence, and the defaults every interactive widget must respect. Phase 5 reads this before designing interactions.
---

# Primitives — interactive design reference

Phase 5 of /explorable reads this file before designing any interaction.
SKILL.md carries the framing — thesis-carrying vs scaffolding, the teaching
test, the rule that at least one thesis-carrying interactive is required to
call the output an explorable. This file carries the primitives table, the
worked teaching examples, the predict-then-reveal evidence, and the
defaults.

## Contents

- [The primitives table](#the-primitives-table)
- [The teaching test, with worked examples](#the-teaching-test-with-worked-examples)
- [Predict-then-reveal — why it's underused](#predict-then-reveal--why-its-underused)
- [Interactive defaults](#interactive-defaults)

---

## The primitives table

Each primitive carries a particular kind of claim. Reach for the one whose
claim matches what the source argues.

| Primitive | Claim it carries |
|---|---|
| Inline scrubbable number | "If x changes, y follows" — quantitative prose |
| Slider + reactive view | Continuous parameter sweep |
| Step-through / paginated | Argument unfolds in stages |
| Click-to-act | Discrete choice has a consequence |
| Drag-to-position | Spatial relation matters |
| Drag-to-target | Reach a state |
| Drawable canvas | The reader's input becomes the example |
| Auto-running simulation | The system's behavior IS the teaching |
| Comparison scrubber | Before/after differs here |
| Layer toggle | Hidden structure can be revealed |
| Timeline scrubber | Time changes structure |
| Map pan / zoom / filter | Geography or distribution matters |
| Branching path | Choices have consequences |
| Sort / filter / search | A corpus has patterns |
| Annotated artifact | Read this object with guidance |
| ⭐ **Predict-then-reveal** | Counter-intuitive result; commit before reveal |
| Mnemonic card | Retention required (hand off to Orbit if user goal = remember) |
| Exploded diagram | A system has parts |
| Flow simulator | Things move through a process |
| Trade-off frontier | Competing constraints |
| Hover / tap for detail | Overview first, dig in |

---

## The teaching test, with worked examples

For each interaction, fill in the blanks:

> "The reader changes ___ to understand ___."

If the sentence sounds weak, cut the interaction. Static typography beats
dead motion.

**Strong examples:**

- "The reader changes the **infection rate** to understand **why curve flattening matters**." (Nicky Case, *Polygons*-style)
- "The reader changes the **friend's bias threshold** to understand **how segregation emerges from mild preferences**." (Nicky Case, *Parable of the Polygons*)
- "The reader changes the **time of day** to understand **how the watch's escapement releases energy**." (Ciechanowski, *Mechanical Watch*)
- "The reader **predicts** then **reveals** to understand **how surprising the actual data is**." (NYT, *You Draw It*)

**Weak examples — cut these:**

- "The reader changes the **chart color** to understand **the data**." (Color isn't the teaching.)
- "The reader **clicks a button** to understand **the next paragraph**." (That's a page break, not an interaction.)
- "The reader **hovers over a word** to understand **what the word means**." (That's a glossary; do it as a glossary.)

**Exception clause:** when the thesis is about causality, responsiveness,
or transformation, interaction is mandatory — you can't argue
responsiveness typographically. In those cases the test still applies, but
"static beats dead motion" is overridden by "the medium IS the argument."

---

## Predict-then-reveal — why it's underused

Predict-then-reveal has strong empirical support in the learning sciences.
The reader is asked to commit to a prediction, then sees the actual answer.
The act of committing — even silently — produces a measurable improvement
in retention compared to passive reading.

Three lineages:

- **The pretesting effect.** Cognitive psychology research (Kornell, Hays
  & Bjork, and others) shows that attempting to retrieve an answer before
  being told it improves later memory for that answer, even when the
  initial attempt is wrong.
- **Quantum Country.** Andy Matuschak and Michael Nielsen built a
  quantum-computing primer with embedded spaced-repetition prompts. The
  primer doesn't just show you content — it asks you to recall it. The
  retention gains are the headline result.
- **NYT *You Draw It*.** A reader is shown the start of a chart and asked
  to draw what they expect happens next. The reveal of the actual data
  lands harder *because* the reader has committed.

**When to reach for it.** Whenever the source has a counter-intuitive
claim — a number people guess wrong, a trend that reverses, a result that
surprised the author. The interaction makes the surprise legible.

**Implementation patterns:**

- Click-to-reveal a hidden value after the reader commits a guess.
- Drawable canvas: reader sketches their prediction, the actual line
  overlays.
- Slider: reader sets where they think the value is, the true value
  appears as a marker.

The pattern is underused because it requires the writer to identify
what's surprising. That's the work.

---

## Interactive defaults

Every interactive widget in an /explorable output respects these defaults
unless the source genuinely calls for an override.

### Auto-preview on first scroll-in

When a widget enters the viewport, run a short preview animation so the
reader sees the affordance without needing to click. Cancel the preview
on user interaction.

Duration fits the widget:

- Toggle / single-state change: ~1 second
- Scene redraw / parameter sweep: ~3 seconds
- Slow simulation: longer, with a pause control visible

### Reset button on sandbox widgets

If the widget can reach a broken or confusing state through user input, a
reset button is mandatory. The reader should never get stuck.

### Pause on auto-animating elements

Anything that animates without user input must have a pause control.
Visible, not hidden behind a hover. Respect the reader's attention.

### `prefers-reduced-motion`

- Ambient motion (decorative loops, parallax, idle drift): off.
- Thesis-carrying motion: paused-by-default with a play control. The
  motion is part of the argument, so the reader still has access — but
  on their terms.

### One variable → one output by default

Multi-variable widgets are the exception, not the default. When a widget
takes multiple inputs, ship presets so the reader has a way in. A blank
slider rack with no starting state is a tax on the reader.

### Accordions default one item open

All-closed accordions read as decoration — the reader has no visible
action on arrival, no visible content, no signal that the section
contains anything. Default to one item open.

### Motion as explanation, not decoration

When motion IS the explanation, animate. Otherwise don't.

- A sweep through valid model states is teaching.
- A morph between images is decoration.
- A graph redrawing as a slider moves is teaching.
- A logo that rotates on page load is decoration.

The bar: if removing the motion removes information, keep it. If removing
the motion makes the page calmer without losing meaning, cut it.
