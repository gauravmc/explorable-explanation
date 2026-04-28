# Writing — copy procedures for /explorable

Every phase of /explorable that produces text — body prose, figure captions,
scene transitions, button labels, error messages — runs through the standard
in this file. SKILL.md carries the four principles and the governing test;
this file carries the full canon, the procedures, and the worked examples.

## Contents

- [Walk-through voice](#walk-through-voice)
- [The paragraph job test](#the-paragraph-job-test)
- [The four principles](#the-four-principles)
- [The clutter catalog](#the-clutter-catalog)
- [Before / after — the shape of the move](#before--after--the-shape-of-the-move)
- [The `sample` procedure (Phase 1.5)](#the-sample-procedure-phase-15)
- [The `review` procedure (Phase 4)](#the-review-procedure-phase-4)
- [Voice preservation — the one limit](#voice-preservation--the-one-limit)

---

## Walk-through voice

An explorable walks the reader through. Ground domain vocabulary on first
use — an example, a plain gloss, a concrete scene.

**Bad:** "Commit archaeology is the systematic analysis of version-control
history."

**Better:** "A git log tells you what changed. Commit archaeology asks the
better question: what was the story of the work?"

Diagnostic: hand the draft to someone who hasn't read the source. If a
paragraph assumes a term you haven't grounded, ground it.

---

## The paragraph job test

Each paragraph does at least one of: orient the reader, explain a claim,
ground an abstraction, introduce an interaction, interpret what changed,
surface an assumption, create momentum, preserve a vivid detail. If it does
none, cut it.

---

## The four principles

From William Zinsser, *On Writing Well*.

- **Clarity.** One thought per sentence. The reader should not have to
  re-read.
- **Simplicity.** Short word over long word. Plain construction over ornate.
- **Brevity.** Every word serves a function. When in doubt, cut.
- **Humanity.** The writer's voice stays on the page. Voice is not a
  decoration — it's the thing that makes prose feel written by a person.

The governing test for every sentence: **is this sentence doing new work?**

Three diagnostic questions to ask against any draft:

1. *What am I trying to say?*
2. *Have I said it?*
3. *Is it clear to someone encountering the subject for the first time?*

If a sentence (or word, or phrase) isn't earning its place in clarity,
brevity, active force, or voice — cut it.

> "The secret of good writing is to strip every sentence to its cleanest
> components." — Zinsser

---

## The clutter catalog

Cut on sight. The categories below are ordered roughly by how often they
show up in agent-generated copy.

### Hedges and qualifiers

Words that inflate without adding meaning:

> a bit, a little, sort of, kind of, rather, quite, very, too, pretty much,
> in a sense, arguably, somewhat, perhaps, possibly

Right: "The pipeline is fast."
Wrong: "The pipeline is rather fast, in a sense."

### Throat-clearing openers

Phrases that delay the point:

> "It is interesting to note that…"
> "I might add that…"
> "It should be pointed out that…"
> "At this point in time…"
> "What I want to say is…"
> "Needless to say…"

Cut the opener. Start with the sentence.

### Inflated phrases — one-word replacements

| Bloated | Tight |
|---|---|
| at the present time | now |
| in the event that | if |
| due to the fact that | because |
| with the possible exception of | except |
| experiencing difficulty | having trouble |
| prior to | before |
| subsequent to | after |
| in order to | to |
| the reason why is because | because |
| a majority of | most |

### Inflated words — one-syllable replacements

| Bloated | Tight |
|---|---|
| assistance | help |
| numerous | many |
| facilitate | ease |
| individual | person (or: man, woman, name) |
| remainder | rest |
| initial | first |
| implement | do (or: build, ship) |
| sufficient | enough |
| attempt | try |
| referred to as | called |
| additional | more |
| commence | start |
| terminate | end |
| prioritize | put first |
| finalize | finish |
| utilize | use |
| leverage (unless actual financial leverage) | name the thing being used |

### Concept nouns (nominalizations)

A verb dressed as a noun. Unpack it.

| Bloated | Tight |
|---|---|
| the establishment of | established |
| the implementation of | built (or: did) |
| the consideration of | considered |
| made the decision to | decided to |
| gave an explanation | explained |
| reached an agreement | agreed |

### Passive voice (when the actor is known)

Right: "Jorge deleted the AI module."
Wrong: "The AI module was deleted by Jorge."

Passive is defensible when the actor is unknown, unimportant, or the
sentence's focus is the object ("The vase was broken"). Otherwise, active.

### Adverbs that duplicate the verb

> effortlessly easy → easy
> totally flabbergasted → flabbergasted
> quickly sprinted → sprinted
> loudly shouted → shouted

If the verb already carries the meaning, the adverb is clutter.

### Adjectives that decorate without working

> the blue sky (if "sky" is enough) → sky
> a yellow daffodil → a daffodil
> a brief summary → a summary

Keep adjectives that distinguish, characterize, or clarify. Cut ones that
exist to pad.

### Vague evaluative adjectives

Words that feel descriptive but don't describe anything specific:

> robust, comprehensive, seamless, holistic, scalable, intuitive,
> cutting-edge, world-class, best-in-class

Replace with the actual quality (strength, scope, where the seams are) or
cut.

### Jargon and euphemism

Business, government, and academic language that hides meaning:

> leverage, synergy, utilize, impact (as verb), incentivize, pivot,
> stakeholder, touch base, circle back, take this offline, at the end of
> the day, deep dive

Find the plain-English word and use it.

### LLM-tics — kill on sight

Phrases that mark prose as model-generated:

> "as we'll see", "let's dive in", "buckle up", "in today's rapidly
> evolving landscape", "a nuanced understanding of", "it's worth noting
> that", "I'll walk you through", "let me explain", "in the realm of"

Cut. If cutting breaks the flow, rewrite the surrounding sentence to
remove the need for the tic — don't just snip.

---

## Before / after — the shape of the move

These are faithful to Zinsser's own edits.

**Example 1 — throat-clearing + inflation**

> Wrong: "It is interesting to note that the patient was experiencing
> considerable pain at this point in time."
> Right: "The patient hurt."

**Example 2 — concept noun + passive**

> Wrong: "The implementation of the new system was completed by the team."
> Right: "The team built the new system."

**Example 3 — inflated diction**

> Wrong: "Subsequent to the initial meeting, we reached an agreement to
> commence the project."
> Right: "After the first meeting, we agreed to start."

**Example 4 — hedged claim**

> Wrong: "The approach is arguably somewhat faster than the alternative,
> in a sense."
> Right: "The approach is faster."

**Example 5 — passive where active works**

> Wrong: "A decision was made that the feature would be deprioritized."
> Right: "We deprioritized the feature."

---

## The `sample` procedure (Phase 1.5)

Take the first paragraph of the source. Rewrite it at the target tone
calibrated for the explorable being built. Show the rewrite to the user
with this frame:

> "Voice sample. Say 'go' or name a shift (warmer / colder / more Zinsser /
> less clinical / more playful / less playful)."

The sample is calibration, not commitment. The user's response sets the
voice for the rest of the build.

Skip this step for quick internal artifacts under 1500 words.

---

## The `review` procedure (Phase 4)

After Phase 4's draft and grounding passes, run the full Zinsser pass on
the body copy and figure captions before Phase 5.

Process, in order:

1. **Read the draft top-to-bottom once** without editing. Note where the
   prose drags.
2. **Pass for hedges and throat-clearing.** These compound — every
   hedge survived means more clutter survives elsewhere. Cut first.
3. **Pass for inflated phrases, words, and concept nouns.** Use the
   tables above as the substitution list.
4. **Pass for passive voice where the actor is known.** Flip to active.
5. **Pass for adverbs that duplicate the verb and decorative adjectives.**
6. **Pass for jargon and LLM-tics.**
7. **Final read.** Each paragraph passes the [paragraph job test](#the-paragraph-job-test).

Return a short changelog naming the biggest cuts:

> *"Cut throat-clearing in ¶1; active voice in ¶3; replaced 'utilize' with
> 'use' throughout; tightened the conclusion."*

Apply the rewrites before Phase 5. The agent does not self-approve copy —
the user reviews the rewrite + changelog and confirms before the build
phase begins.

---

## Voice preservation — the one limit

Clutter removal is not voice removal. Zinsser's fourth principle is
humanity — the writer's voice stays on the page.

Preserve:

- Deliberate fragment sentences that carry rhythm.
- Colloquialisms, contractions, idioms the author chose.
- Mannered constructions that are the author's signature (short staccato
  beats, long serpentine Sebald-ic sentences, rhetorical questions).
- Named references, insider terms for an insider audience.
- Specifics: dates, names, hashes, quotes, numbers, vivid scenes.

The test: **would removing this change what the author sounds like?** If
yes, leave it alone.

Sharpening clarity within the author's voice is the job. Creating or
imposing a voice is a different job and not part of this procedure.
