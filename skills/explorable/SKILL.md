---
name: explorable
version: 0.2.0
description: Turns a long markdown document into a single-file HTML explorable — scroll-snapped scenes, hand-written SVG, interactive widgets where the source has structure trapped inside the prose. One file, no build step, vanilla CSS/JS/SVG. Use when the user says "make this explorable", "/explorable", "turn this into an interactive", "render this research", or has a long markdown doc whose ideas are visual, temporal, spatial, causal, or comparative. Descends from Bret Victor's Explorable Explanations, Nicky Case, Distill, Ciechanowski, Sam Rose, Red Blob Games.
license: Complete terms in LICENSE.txt
allowed-tools:
  - Read
  - Write
  - Bash
  - Agent
---

# /explorable — turn markdown into a single-file interactive

## Thesis

A wall of text is often a diagram, map, model, or simulation that hasn't
been rendered yet.

> Don't make the reader reconstruct what the machine can render.

If the source's argument is visual, temporal, spatial, causal, comparative,
procedural, or branching, prose alone is a tax. Render the structure
directly. If none of that applies, the source probably doesn't want this
skill.

The user opted in by invoking `/explorable`. Treat that as license to build
something explorable, unless the source would make exploration dishonest,
wasteful, or silly.

## What this does

Reads a long markdown doc and produces one self-contained `.html` file:
hand-written SVG, interactive widgets where the source has kinetic
structure, deliberate aesthetic, voice tuned to the source. No build step.
Runs identically in `file://`, Claude Artifacts, and on static hosting.

## Files in this skill

This skill is self-contained. Four files, all in this directory:

- **SKILL.md** (this file) — phase scaffold, decision logic, hard rules. Loaded every invocation.
- **writing.md** — full Zinsser canon, walk-through voice, copy procedures (`sample`, `review`). Read before Phase 1.5 and Phase 4.
- **aesthetics.md** — source-genre starting patterns, anti-slop filter, color-stable variables. Read before Phase 2.
- **primitives.md** — interactive primitives table, teaching test with worked examples, predict-then-reveal evidence, defaults. Read before Phase 5.

Pointers below are imperative ("**read X**"). Treat them as instructions, not suggestions.

## Genre is the ceiling

The input's genre caps the output's interactive density. A founder letter
won't become *Parable of the Polygons* by adding sliders. A research
synthesis won't become Ciechanowski's *Mechanical Watch* in one pass.
Name this honestly instead of overselling.

The realistic agent ceiling for one-shot output is **Sam Rose / Red Blob
Games quality**: color-stable palette, hand-written SVG, prose that earns
its place, widgets where the source genuinely calls for them. Aim for that.
Ciechanowski's auteur level is unattainable in one pass.

The source dictates how many widgets, not a target range — see the
Density section below.

---

## Writing standard (applies throughout)

Every phase that produces text — body prose, figure captions, scene
transitions, button labels, error messages — follows Zinsser's four
principles: clarity, simplicity, brevity, humanity. The governing test
for every sentence: **is this sentence doing new work?** If not, cut it.

The three LLM-tics most likely to leak into agent-generated copy:

- **Hedges** — "a bit", "sort of", "arguably", "perhaps". Either claim or cut the sentence.
- **Throat-clearing openers** — "It's interesting to note that…", "At this point in time…". Cut the opener; start with the sentence.
- **Passive voice when actor is known** — "was deleted by Jorge" → "Jorge deleted".

Preserve voice, specifics (dates, names, hashes, quotes, numbers),
deliberate fragments, and the source author's distinctive rhythm. Make it
easier to read without making it dumber.

**writing.md holds the full canon.** Read it before Phase 1.5 and before Phase 4.

---

## Phase 1 — Plan the piece, confirm in one line

Read the source completely. Find the structure trapped inside the prose:
temporal, spatial, causal, comparative, procedural, branching, taxonomic,
evidentiary. Most pieces have one dominant shape and one or two secondary.

Then propose the plan to the user — plain language, one screen, no jargon.

*A Phase 1 proposal might read:*

> Reading this as a research synthesis with a temporal arc (3 phases of
> the Purple Crayon experiment) and a comparative core (three parallel
> agent runs).
>
> Building a chaptered walkthrough — sketch gallery, 3-up comparison
> scrubber, scope explorer for the MVP cuts. About 6 scenes, 4 interactive
> moments.
>
> Look and feel: warm picture-book colors on cream paper, hand-drawn marks.
>
> Say "go" or change anything.

### Default modes by source

Pick the form first. The agent's first job is to map the source genre to a
default form, then confirm.

| Source | Default form |
|---|---|
| Research synthesis | Visual case study with thesis-carrying interactive |
| Product / project plan | Scope explorer + comparison scrubber |
| Methodology / how-to | Step-through walkthrough or sticky figure |
| Commit history / repo analysis | Chronological case study |
| History / civics | Timeline + map + predict-then-reveal |
| Design exploration | Side-by-side comparison gallery + principles overlay |
| Investment thesis / financial memo | Scenario model with visible assumptions |
| Architecture doc | SVG system diagram + flow walkthrough |
| Tutorial / learning material | Step-through + predict-then-reveal + (Orbit handoff if retention) |

This table is a starting point, not a rule. The source can override — for
example, a research synthesis whose argument is fundamentally spatial (not
temporal) wants a map-and-atlas form, not the default visual case study.
Follow the source.

### Check the prose-to-interactive ratio before proposing

While reading, count: how much of the spine is prose, and how much is
candidate interactives? Two stable shapes:

- 70–95% prose with interactive moments threaded through (retrofit)
- 5–30% prose, interactives carrying the spine (compose)

The 40–60% middle is unstable — prose feels like connective tissue and
widgets feel undersupported. If your read of the source lands clearly in
that middle, name it in the proposal:

> "This source's argument lives mostly in its kinetic structure — prose
> is mostly connecting widgets. Want me to keep the prose and let the
> widgets carry the weight, or rewrite as a shorter interactive-first
> piece?"

If it's borderline, default to retrofit and proceed without asking.

### When to actually ask the user

Ask only when the answer would change the artifact materially:

- Genre is genuinely ambiguous between two very different shapes
- The source has emotional content (mental health, conflict, loss) — confirm
  before transforming at all
- The source supplies code/data and the agent needs to know whether to re-run

Otherwise: propose, let the user redirect in one line, move on.

### Hide internal vocabulary from the user

Words to keep inside the skill, never in user-facing output: "kinetic
potential", "thesis-carrying", "Mode A/B/C", "density budget",
"anti-slop filter".

Translation table:

| Internal | What to say to the user |
|---|---|
| Mode A retrofit | "keep your writing, add interactive moments where they earn their place" |
| Mode B compose | "rewrite as a shorter, interactive-first piece" |
| Mode C re-typeset | "clean typographic layout, no interactivity" — only when interaction would be silly |
| thesis-carrying interactive | "this one carries the argument — you can't say it in prose" |
| scaffolding interactive | "this one makes the piece easier to navigate" |
| density budget | "N interactive moments" |
| five-gate review | "a few checks before we ship" |

---

## Phase 1.5 — Voice calibration

Generate one sample paragraph at the target tone. Show it with a one-line
frame:

> "Voice sample. Say 'go' or name a shift (warmer / colder / more Zinsser /
> less clinical / more playful / less playful)."

**Run the writing.md `sample` procedure on the first paragraph of the source.**

Skip this step for quick internal artifacts under 1500 words.

---

## Phase 2 — Aesthetic direction

The artifact's design takes its cues from what the source is *about*.
A children's iPad app gets a different visual language than a security
post-mortem. Don't impose a house style — read the source for what
genre, mood, and visual world it belongs to, and design into that.

### Read the source for visual cues

Before generating any design from scratch, scan the source for what it's
already telling you about its visual world:

- **Subject genre.** Is this children's product, scientific research,
  founder essay, code archaeology, civics, design critique, financial
  memo, art history? Each has an established visual register that readers
  already know how to read.
- **Named visual referents.** Colors ("Purple Crayon" → Harold's purple),
  objects, cultural references, era, brand identity. If the source names
  something visual, it's load-bearing — use it.
- **Tone.** Playful, austere, journalistic, intimate, technical? Match it.
- **Audience.** Who would naturally read this, and what media do they
  already consume? Design for that reader, not a generic "tasteful website."

The principle: a reader landing cold should be able to guess the topic
from the visual language alone.

**Read aesthetics.md before generating any design.** It carries the
source-genre starting patterns, the anti-slop filter (banned defaults),
and the color-stable-variables discipline that does most of the work of
"looking like a real explainer."

---

## Phase 3 — Content structuring

1. **Extract the thesis sentence.** Promote it to typographic status —
   pull-quote, cold open, or dedicated scene. Never buried in body prose.
2. **Identify the arc.** However many acts/phases/eras the source has.
   If the source has phases, an explicit "Acts" scene is first-class output.
3. **Map scenes.** If sections vary wildly in weight, consolidate the thin
   ones, split the heavy ones.
4. **Extract the vivid moments** — dates, names, hashes, quotes, specific
   scenes. Whatever the source gives you.

---

## Phase 4 — Copy

Write the full draft of body copy and figure captions before touching
visuals. Copy is the skeleton; visuals and interactions are muscles. Three
passes, in order:

1. **Draft.** Section by section, following the scene map from Phase 3.
   No widgets yet — write what each scene says. Body prose, headings, figure
   captions, scene transitions.
2. **Ground the vocabulary.** For each domain term, is it grounded on
   first use? See the walk-through voice section in writing.md. Cutting
   can't add missing context, so do this before the Zinsser pass.
3. **Zinsser pass.** **Run the writing.md `review` procedure on the full draft.**
   Apply the rewrites before Phase 5.

---

## Phase 5 — Interaction design

For each candidate interactive, label it **thesis-carrying** or
**scaffolding**.

- **Thesis-carrying**: the reader cannot be argued the same thing in prose
  alone. The interaction IS the argument.
- **Scaffolding**: useful navigation or detail, but not load-bearing.

At least 1 thesis-carrying interactive for the output to be called an
explorable. Below that, label the output "document with interactives."

### Teaching test

For each interaction, fill in the blanks:

> "The reader changes ___ to understand ___."

If the sentence sounds weak, cut the interaction. Static typography beats
dead motion.

Exception: when the thesis is about causality, responsiveness, or
transformation, interaction is mandatory — you can't argue responsiveness
typographically.

**Read primitives.md before designing interactions.** It carries the full
primitives table (21 patterns and the claim each carries), worked examples
of the teaching test, the predict-then-reveal evidence, and the defaults
every widget must respect (auto-preview, reset, pause,
`prefers-reduced-motion`, single-variable default, accordion behavior,
motion-as-explanation).

---

## Phase 6 — Build

Single HTML file. Inline `<style>` and `<script>`. Hand-written SVG.
Vanilla JS. Canvas + `requestAnimationFrame` for sims. Pinned CDN deps
only when the source genuinely needs them.

### Hard rules

- One file. Inline `<style>` and `<script>`. Pinned CDN deps via
  `https://cdn.jsdelivr.net/npm/...@version/+esm` only.
- `<meta name="viewport" content="width=device-width,initial-scale=1">`
- `text-wrap: balance` on headlines, `pretty` on body
- `font-variant-numeric: tabular-nums` on changing numbers
- IntersectionObserver for scroll triggers (Scrollama only when ≥3 sticky
  scenes earn it)
- Arrow keys / Space-Shift-Space for scene paging. Add j/k only for
  developer-audience explorables.
- Stack on <700px viewports. Touch targets ≥44px. No hover-only meaning.
- `prefers-reduced-motion` disables ambient motion, pauses thesis motion.
- Color contrast ≥ AA. Visible focus states.
- Total weight target <500KB excluding generated imagery (soft cap 1MB).
- Runs identically in: `file://`, Claude Artifacts iframe, static hosting.
- Disclosed playing time at the top.
- Per-section 10-second rule: first interaction lands within 10 seconds of
  the reader arriving at that section.

### Tech policy

Default: vanilla HTML/CSS/JS + hand-written SVG. Reach for a library only
when the source genuinely calls for it — Canvas for continuous simulation,
a charting library when prose can't carry the data, a map library when
geography matters. Pinned CDN imports via
`https://cdn.jsdelivr.net/npm/...@version/+esm` only. No build steps, no
framework setup.

### Image-generation rule

Generated raster only when:
- The subject's *appearance* is the explanandum (historical scene, fashion,
  architecture, a specific design, a product), OR
- The imagery is decorative cover/divider, explicitly labeled.

Always hand-write SVG for propositional content: anatomy, circuits, data
flows, equations, geometry, system diagrams. Generated diagrams hide
errors behind aesthetic competence. The Frontiers Cell Dev Biol rat-anatomy
retraction is the parable.

### No-fake-data rule

Either user-supplied data, formulas the reader can read inline, or omit
the chart. **No invented numbers. No invented citations.** No "trust = 0.7"
fake precision. No "what if SG&A were 15% lower" with nothing behind it.

For model-backed widgets:
- Show variables and their default values
- Show formulas (or include a "show formulas" toggle)
- Show what the model omits ("what this does not model")
- Label illustrative simulations as illustrative
- No forecast voice unless the source supports it

---

## Phase 7 — Review

### Five-gate review

| Gate | What it checks | Automated? |
|---|---|---|
| 1. Static | Syntax, var refs, tag balance | Yes |
| 2. Visual | Layout at 1440 and 640, no clipping | Partial |
| 3. Design | Aesthetic deliberate, not default | No — user |
| 4. Copy | Each paragraph teaches | No — user or writing.md `review` |
| 5. Arc | Narrative arc visible to a first-time reader | No — user |

Plus three honesty checks (always run):
- No invented numbers, citations, or causal relationships
- Every model-backed widget shows assumptions and omissions
- Voice preserves the source's distinctive phrases (don't smooth into
  LLM-default tone)

Surface gates 3–5 to the user with an explicit checklist. Don't
self-approve.

### Fork review (optional, for higher-stakes pieces)

For longer or higher-stakes pieces (public blog posts, portfolio work,
things the user will share widely), spawn a separate sub-agent
(staff-designer role) for an independent taste pass before shipping. The
builder doesn't self-verify on taste.

The review surfaces: copy that doesn't teach, asides that don't add
information, scenes that mis-weight the arc, interactions that are
scaffolding masquerading as thesis.

Skip for quick single-source explorables — the five-gate review is enough.

---

## Refusal and downshift

When refusing, name what *would* work in the same message. No bare
refusals.

| Source | Offer instead |
|---|---|
| Legal, contracts, regulatory text, formal specs, API references | Better typography + search + index. Exact wording is the product. |
| Memorials, eulogies, apologies | Don't transform. Suggest reading the original. Register-mismatch. |
| <500 words | Single-page layout or card. |
| Opinion-only, no quantifiable claims | Re-typeset, or suggest reading the original. |
| Messy / contradictory / transcript-like | Suggest the user distill it down first; offer to continue once they have. |
| API docs (Docusaurus exists) | Decline; point at standard docs tooling. |
| Reference / lookup tables | Decline; search indexes do this better. |
| Personal essay where voice is the value | Typographic essay only; no widgets. |

---

## Density

The source dictates density. Count the kinetic claims, count the structures
that would read faster as widgets, build the ones that survive the teaching
test.

The bimodal-middle check happens in Phase 1, before any building. By the
time you're here, the form is already chosen.

**Label honestly.** If the finished piece has zero thesis-carrying
interactives (all scaffolding), call it "document with interactives," not
"explorable."

### Minimum viable floor

Jason Davies's *Map Projection Transitions*: 12 words of prose, one
`<select>`, one pause button, one SVG that morphs on change. When the input
is a compact visual object with no surrounding argument, emit at the floor.
A clean 12-word piece beats a bloated prose shell.

---

## Voice for this skill

Execution mode. The skill builds, doesn't discuss.

Right: "Reading this as a research synthesis with a temporal arc. Building
a chaptered walkthrough with a 3-up comparison scrubber. Voice sample
coming next."

Wrong: "Great, let me start by reading the source. Phase 1: I'll identify
the structure. I see this is a research synthesis with a temporal arc. Now
moving to Phase 1.5 — voice calibration..."

---

## References

- Bret Victor, *Explorable Explanations* (2011) — north star, not product spec
- Nicky Case, explorabl.es — guided play, do/show/tell
- Distill, *Communicating with Interactive Articles* — affordances taxonomy
  and the warning ("not everything needs to be interactive")
- Bartosz Ciechanowski, ciechanow.ski — auteur ceiling
- Sam Rose, samwho.dev — realistic agent ceiling
- Red Blob Games, redblobgames.com — incremental interactivity
- Andy Matuschak + Michael Nielsen, *Quantum Country* — predict-then-reveal as the load-bearing primitive
- Jakub Krehel, *Details that make interfaces feel better* — essay+skill pair
- William Zinsser, *On Writing Well* — copy rubric
