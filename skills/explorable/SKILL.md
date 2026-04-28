---
name: explorable
description: |
  Turns a long markdown document (research, plan, methodology, technical
  writeup, history, design exploration) into a single-file HTML
  explorable — scroll-snapped scenes, hand-written SVG, interactive
  widgets where the source has structure trapped inside the prose. One
  file, no build step, vanilla CSS/JS/SVG.

  Use this skill when the user says "make this explorable", "/explorable",
  "turn this into an interactive", "render this research", "build a
  walkthrough", "visualize this", or has a long markdown doc whose ideas
  are visual, temporal, spatial, causal, or comparative — i.e., where
  prose is forcing the reader to reconstruct structure that the machine
  could render directly.

  Descends from Bret Victor's Explorable Explanations (2011), Nicky Case's
  playable essays at explorabl.es, Distill, and the independent auteur
  tradition (Ciechanowski, Sam Rose, Red Blob Games).
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

## Genre is the ceiling

The input's genre caps the output's interactive density. A founder letter
won't become *Parable of the Polygons* by adding sliders. A research
synthesis won't become Ciechanowski's *Mechanical Watch* in one pass.
Name this honestly instead of overselling.

The realistic agent ceiling for one-shot output is **Sam Rose / Red Blob
Games quality**: vivid palette, hand-written SVG, prose that earns its
place, widgets where the source genuinely calls for them. Aim for that.
Ciechanowski's auteur level is unattainable in one pass.

The source dictates how many widgets, not a target range — see the
Density section below.

---

## Writing standard (applies throughout)

Every phase that produces text follows Zinsser's four principles —
clarity, simplicity, brevity, humanity. The governing test for every
sentence: is it doing new work? If not, cut it.

### Walk-through voice

An explorable walks the reader through. Ground domain vocabulary on
first use — an example, a plain gloss, a concrete scene.

**Bad:** "Commit archaeology is the systematic analysis of version-control
history."

**Better:** "A git log tells you what changed. Commit archaeology asks the
better question: what was the story of the work?"

Diagnostic: hand the draft to someone who hasn't read the source. If a
paragraph assumes a term you haven't grounded, ground it.

### Cut on sight

| Pattern | Replace with |
|---|---|
| Hedges: "a bit", "sort of", "arguably", "perhaps" | Either claim or cut the sentence |
| Throat-clearing: "It's interesting to note...", "At this point in time..." | The sentence after it |
| "utilize" | "use" |
| "implement" | "build" / "do" / "ship" |
| "leverage" (unless it means actual financial leverage) | name the thing being used |
| "facilitate" | use the more specific verb (help, speed, enable, host) |
| Vague evaluative adjectives: "robust", "comprehensive", "seamless" | name the actual quality (strength, scope, where the seams are) or cut |
| "made a decision to" | "decided" |
| "the implementation of X" | "X" |
| Passive when actor is known: "was deleted by Jorge" | "Jorge deleted" |
| LLM-tics: "as we'll see", "let's dive in", "buckle up", "in today's rapidly evolving landscape", "a nuanced understanding of" | cut. If cutting breaks flow, rewrite the surrounding sentence to remove the need for the tic — don't just snip. |

Preserve: voice, specifics (dates, names, hashes, quotes, numbers),
deliberate fragments, the source author's rhythm and vivid details.
Make it easier to read without making it dumber.

If `/zinsser` is available, invoke `/zinsser review` on the full draft for
a rigorous sentence-level pass after Phase 4. Otherwise apply the table
above inline.

### Paragraph job test

Each paragraph does at least one of: orient the reader, explain a claim,
ground an abstraction, introduce an interaction, interpret what changed,
surface an assumption, create momentum, preserve a vivid detail. If it
does none, cut it.

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

If `/zinsser` is available, invoke `/zinsser sample` on the first paragraph
of the source. Otherwise generate inline.

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

*Some starting patterns:*

- Children's iPad app → playful, generous, hand-drawn marks, warm
  palette, picture-book cadence
- Scientific research synthesis → archival, restrained, serif body,
  numbered figures, generous white space
- Security post-mortem → brutalist, monospace where it earns it, high
  contrast, no decorative warmth
- Founder letter → editorial, single-column, drop caps if the prose
  warrants, restrained color
- Code archaeology / repo retrospective → terminal-archive hybrid, mono
  accents, timestamp typography, log-style margins
- Civics / history learning doc → archival but alive, period-aware
  palette without pastiche, real sources visible
- Investment thesis → understated, precise, financial-press typography,
  no dashboard glam

The principle: a reader landing cold should be able to guess the topic
from the visual language alone. The skill chooses the palette, fonts, and
aesthetic moves; the example block is a starting pattern, not a menu to
pick from.

### Anti-slop filter (apply before any design generation)

Banned defaults — every one of these reads as AI slop:

- Fonts: Inter, Roboto, Arial, Fraunces, Space Grotesk, system-ui as
  automatic default
- Gradient backgrounds, glassmorphism, default purple-blue SaaS palette
- Emoji as decoration
- Left-border Notion cards
- Margin asides that don't add information not in the main text
- Cookie consent modals, sign-in gates, fake CTAs
- Decorative icons that carry no meaning
- Auto-generated hero art with no teaching role
- Every section starting with "In today's…" or "It's important to note…"

Usually 2–3 fonts (display + body, plus mono if metadata is present). A
fourth earns its place if the subject genuinely calls for a hand-written
accent.

### Color-stable variables

Each named quantity in the piece gets a color at first introduction. That
color is reused in every subsequent widget, in inline math, and as the
stroke color in diagrams.

This single discipline does most of the work of "looking like a real
explainer."

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
   first use? See Walk-through voice above. Cutting can't add missing
   context, so do this before Zinsser.
3. **Zinsser pass.** Invoke `/zinsser review` on the full draft. Apply the
   rewrites before Phase 5. Fall back to the cut-on-sight table above if
   the skill isn't available.

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

### Primitives

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

Prefer fewer primitives used well over a buffet used badly. The source
dictates the count, not a target range — see Density.

**Predict-then-reveal** has strong empirical support in the learning
sciences (the pretesting effect; Quantum Country's spaced-repetition
prompts; the NYT *You Draw It* line). Reach for it whenever the source
has a counter-intuitive claim. It's underused.

### Interactive defaults

- Auto-preview on first scroll-in, cancelable on user click. Duration fits
  the widget (toggle ~1s, scene redraw ~3s, slow simulation longer).
- Reset button on sandbox widgets that can reach broken states.
- Pause on auto-animating elements.
- `prefers-reduced-motion` respected — ambient motion off, thesis-carrying
  motion paused-by-default.
- One variable → one output by default. Multi-variable widgets keep presets
  so the reader has a way in.
- Accordions default one item open. All-closed reads as decoration —
  the reader has no visible action on arrival.
- When motion is the explanation, animate. Otherwise don't. A sweep
  through valid model states is teaching. A morph between images is
  decoration.

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

### Lean into the medium

HTML, vanilla CSS, vanilla JS, hand-written SVG are the strengths of this
stack. Use them. A purposeful SVG scene, a CSS-only transition, a short
script that redraws a figure — first-class teaching tools, not fallbacks.

Bret Victor's *Scrubbing Calculator*, Nicky Case's *Polygons*, Jez Swanson's
*Fourier*, Ciechanowski's *Mechanical Watch*, Red Blob's *A**, Sam Rose's
*Load Balancing* — all hand-built. None used production illustration
assets. Craft in the markup is the aesthetic.

---

## Phase 7 — Review

### Five-gate review

| Gate | What it checks | Automated? |
|---|---|---|
| 1. Static | Syntax, var refs, tag balance | Yes |
| 2. Visual | Layout at 1440 and 640, no clipping | Partial |
| 3. Design | Aesthetic deliberate, not default | No — user |
| 4. Copy | Each paragraph teaches | No — user or `/zinsser` |
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
- Jakub Krehel, *Details that make interfaces feel better* — essay+skill pair
- William Zinsser, *On Writing Well* — copy rubric
