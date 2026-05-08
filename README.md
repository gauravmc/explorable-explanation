# Explorable

An [Agent Skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) that turns a long markdown document into a single-file HTML explorable explanation — scroll-snapped scenes, hand-written SVG, vanilla CSS/JS, no build step.

Hand it research, a project plan, a methodology writeup, a history piece, or a design exploration whose ideas are visual, temporal, spatial, causal, or comparative — i.e., where prose is forcing the reader to reconstruct structure that the machine could render directly. The skill walks through seven phases (plan → aesthetic direction → content structuring → copy → interaction design → build → review) and produces one self-contained `.html` file that runs identically in `file://`, Claude Artifacts, and on static hosting.

## What it covers

- Reading a source for the structure trapped inside its prose (temporal, spatial, causal, comparative, procedural, branching, taxonomic, evidentiary)
- Mapping source genres to default forms (research synthesis, methodology, repo retrospective, civics, investment thesis, architecture doc, tutorial)
- A copy discipline drawn from Zinsser's *On Writing Well* — full clutter catalog, walk-through voice, paragraph job test, before/after examples
- An anti-slop filter and source-genre starting patterns for visual direction
- Color-stable variables: each named quantity gets a color, reused across widgets, diagrams, and inline math
- 21 interactive primitives, each labelled with the claim it carries, plus a teaching test for separating thesis-carrying interactions from scaffolding
- Predict-then-reveal as the underused primitive (pretesting effect, Quantum Country, NYT *You Draw It*)
- Build rules: vanilla HTML/CSS/JS + hand-written SVG, single file, pinned CDN deps, accessible defaults, `prefers-reduced-motion`, no fake data, no invented citations
- A five-gate review and an optional fork review for higher-stakes pieces

## Installation

```bash
npx skills add gmchande/explorable-skills
```

Or install manually for Claude Code by cloning into `~/.claude/skills/`:

```bash
git clone https://github.com/gmchande/explorable-skills.git
cp -r explorable-skills/skills/explorable ~/.claude/skills/explorable
```

## Usage

Invoke directly:

```
/explorable <path-to-markdown-file>
```

Or describe what you want and the skill activates on its own:

> "Make this explorable"
> "Turn this research into an interactive"
> "Render this as a walkthrough"

The skill proposes a plan in plain language, calibrates voice with one sample paragraph, and confirms before building. Phase 6 is the build — one `.html` file, no build step.

## What's in the skill

- **SKILL.md** — phase scaffold, decision logic, hard rules. Loaded every invocation.
- **writing.md** — full Zinsser canon, walk-through voice, copy procedures (`sample`, `review`).
- **aesthetics.md** — source-genre starting patterns, anti-slop filter, color-stable variables.
- **primitives.md** — interactive primitives table, teaching test with worked examples, predict-then-reveal evidence, defaults.

## Lineage

This skill descends from Bret Victor's *Explorable Explanations* (2011), Nicky Case's playable essays at [explorabl.es](https://explorabl.es), Distill's *Communicating with Interactive Articles*, and the independent auteur tradition: Bartosz Ciechanowski ([ciechanow.ski](https://ciechanow.ski)), Sam Rose ([samwho.dev](https://samwho.dev)), Red Blob Games ([redblobgames.com](https://redblobgames.com)). The copy discipline is William Zinsser's *On Writing Well*. The single-file distribution shape and skill structure follow Jakub Krehel's [make-interfaces-feel-better](https://github.com/jakubkrehel/make-interfaces-feel-better).

## Companion essay

A walkthrough of the design decisions behind this skill is in progress. (Link forthcoming.)

## License

MIT — see [LICENSE.txt](LICENSE.txt).

## Author

Gaurav Chande — [github.com/gauravmc](https://github.com/gauravmc)
