---
name: anti-slop
description: >
  Detect, rewrite, and ingest AI-slop. One maintained spec that consolidates and
  replaces avoid-ai-writing, humanizer, and stop-slop. Use when drafting,
  editing, or reviewing any text to remove AI tells; when the user pastes text
  marked "slop:" to memorialize a new pattern; or when asked to "de-slop",
  "remove AI-isms", "clean up AI writing", or "audit for AI tells". This is the
  general AI-slop floor. On a byline with a personal voice spec, it pairs with
  that voice overlay through the protect-list seam, so it never flattens a
  writer's real signatures.
version: 0.1.0
license: MIT
metadata:
  replaces: [avoid-ai-writing, humanizer, stop-slop]
  status: stable
---

# anti-slop

One owned, maintained skill for removing AI writing patterns, and for ingesting
new ones as the models change. The rule lists are commodity. The living corpus
(`references/living-corpus.md`) is the moat: dated tells caught in the wild, each
tagged with the mechanism that produces it.

## How this fits together

- **This skill is the general floor.** Universal AI tells. Reusable across every
  project and surface.
- **Your voice spec is the personal overlay.** Your signatures and the protect
  list (what this skill must NOT strip from your byline). The voice spec is
  canonical for the protect list; this skill points at it, never restates it. See
  `references/protect-list.md` for the seam. To build your own voice spec from
  your writing, use the companion onboarding flow (`voice-dna-builder`).
- **The three old skills are retired here.** Their unique parts fold in:
  avoid-ai's tiered vocabulary, context profiles, and severity tiers;
  humanizer's content-pattern catalog and adversarial self-audit; stop-slop's
  false-agency rule and scoring rubric.

## Modes

**rewrite** (default): flag every AI-ism, return a clean version, show a diff of
what changed.

**detect**: flag only, grouped by severity (P0/P1/P2). No rewriting. For
published text, someone else's writing, or a quick scan. Trigger on "detect",
"flag only", "audit only", "scan", "what AI patterns are in this".

**ingest**: the curation flow. The user pastes slop (marked `slop:` or "this is
slop"), or I catch my own. The skill dissects it, names the generative
mechanism, writes a tiered rule plus a replacement, checks it against the
protect list, dedups, and files it into the living corpus. Full flow:
`references/ingestion.md`.

## The spine

1. **Structure is the #1 detection signal**, above vocabulary. Uniform sentence
   and paragraph length reads as AI even with every flagged word removed. Vary
   rhythm first, swap words second.
2. **Tiered vocabulary, not blanket bans.** Tier 1 always-replace, Tier 2 flag
   in clusters, Tier 3 flag by density. Full tables in `references/patterns.md`.
   Blunt "never" rules stacked deep recreate the over-polishing failure they are
   meant to fix.
3. **Context profiles** adjust strictness: linkedin, blog, technical-blog,
   investor-email, docs, casual. Matrix in `references/patterns.md`. Auto-detect
   from content cues if none is passed.
4. **The protect-list seam.** On a byline with a voice spec, load
   `references/protect-list.md` (canonical: your voice spec) first. Never strip a
   protected signature. If a flag collides with one, surface it and do not
   auto-edit. With no voice spec (someone else's draft, an unowned byline), build
   a throwaway one: before editing, note the core point and 3-5 voice signals in
   the draft itself (vocabulary, humor, cadence, pet phrases) and preserve them
   through the rewrite. De-slopped text that lost its author is still a failure.
5. **Self-reference escape hatch.** When writing ABOUT slop (this file, examples,
   quoted bad writing), do not flag the quoted patterns. Only flag the author's
   own prose.

## Transition iteration (rewrite mode)

AI slop shows most at the seams: how paragraphs and thoughts connect. Banning
specific transitions (the old blocklist approach) is subtractive and backfires.
Kill "Moreover" and the model collapses to a different small set, or drops
connective tissue entirely, and you get a new uniformity. So transitions get
iterated, not banned. Same mental model as iterating on a feature in code: do
not ship the first pass.

The target is variety plus voice-fit, not rarity. A deliberately rare or showy
transition is its own tell. Vary toward the byline's own transition vocabulary
(from the protect list and voice samples), and remember the best transition is
often none: just start the next thought.

### The procedure (run on every rewrite)

1. **Draft pass.** Write or rewrite normally.
2. **Seam pass.** Walk each paragraph boundary and each major thought-shift. At
   each one, generate 2-3 candidate openers and always include "no transition,
   start the thought directly" as a candidate. Choose by fit to the voice and the
   argument, not by novelty. State a one-word reason. Emitting the candidates is
   the forcing function; it is what stops this from collapsing to a single pass.
3. **Monotony pass.** Read the whole piece end to end for transition repetition.
   If two boundaries lean on the same move (two "and then"s, two Wh-openers, two
   appositive asides), break one. Vary the shape of the connection, not just the
   word: a short fragment, a question, a flat statement, a callback to an earlier
   line.

### Candidate-artifact format (seam pass)

For each boundary, before committing:

```
[seam after "...last few words of prior paragraph"]
  a) <candidate opener>
  b) <a structurally different candidate>
  c) no transition: <how the next line reads cold>
  -> chose (x): <one-word reason: fit / rhythm / voice / cut>
```

In rewrite mode this is internal scaffolding; do not ship it in the final text.
In detect mode, surface it so the writer sees the seams and the choices.

### Guards

- Do not manufacture a transition where the thought connects fine on its own.
  Bolting connective tissue onto every seam is itself an AI habit.
- Do not reach for rare transitions to seem human. Fit is the goal, not novelty.
- On a byline with a protect list, bias the candidate set toward that voice's
  natural transitions, never away from them.

### Optional escalation: fresh-eyes pass

For flagship pieces (a published blog post, a long-form essay), run a separate
transition review after the inline passes. An agent that did not write the draft
catches seam-monotony the author is blind to, the same way you miss your own
typos. Reserve it for high-value work; it is not worth the cost on a tweet.

## Quick checks

Before delivering prose, run the pass:

- Em dash anywhere (the Unicode glyph or the -- substitute), including headings? Remove it.
- "Not X, it's Y" or any binary-contrast variant? State Y directly. (FATAL on a
  byline whose voice spec bans it: zero, not "max one".)
- Copula avoidance ("serves as", "boasts", "features")? Default to is/has.
- Inanimate thing doing a human verb ("the data tells us", "the decision
  emerges")? Name the actor. (See `references/patterns.md`, false agency.)
- Three consecutive sentences match length? Break one. Tricolon reflex? Use two
  or four.
- Synonym cycling within a paragraph? Repeat the right word instead.
- Significance inflation on a routine event ("marking a pivotal moment")? Cut it.
- Chatbot artifacts, sycophancy, cutoff disclaimers? Strip entirely.
- Reads like clean TTS with no rhythm? It is too uniform. Add disfluency.

Then, on a byline with a voice spec: walk that spec's runtime self-review
checklist and the protect list.

## Scoring

Rate 1-10 on each. Below 35/50, revise.

| Dimension | Question |
|-----------|----------|
| Directness | Statements, or announcements about what comes next? |
| Rhythm | Varied, or metronomic? |
| Trust | Respects the reader's intelligence? |
| Authenticity | Sounds like a person wrote it? |
| Density | Anything cuttable without losing meaning? |

## Maintenance

This skill is alive on purpose. The third-party skills it replaces went stale in
months because their update trigger was a maintainer's schedule. The trigger
here is "I spotted a tell," which is cheap and high-signal. When the user pastes
slop, run the ingest flow and grow `references/living-corpus.md`. Tells age:
the delve/tapestry era is already burned. Re-tier or retire entries as the
models change.

### Size budget (the anti-ratchet rule)

The rule set has a hard ceiling, because a list I cannot hold in attention is a
list I will not follow, and over-constraint breeds displacement tells. Budget:
`patterns.md` holds at most ~40 mechanism-level rules; the living corpus at
most ~30 live entries. At budget, filing something new requires merging it into
an existing mechanism or retiring an entry in the same commit. Fold, don't
append: a new tell is usually an example of a mechanism already on the books,
not a new rule. Three banned phrases with one cause are one rule with three
examples.

## Learning loops

Beyond the manual triggers, four automated read-paths feed
`references/candidates.md` (the inbox). All of them propose; only the writer
files. The gate at filing time is the ingestion six-step plus the eval suite
(`evals/`): a proposed rule must still catch the slop fixtures and must flag
nothing in the golden set of real human prose.

- **Harvest** (`references/harvest.md`): diff the skill's output against what
  actually shipped. Human edits are labeled examples: missed tell or flattened
  voice.
- **Self-play** (`references/weekly-loop.md`): weekly. Generate with the skill
  on, detect with fresh-eyes agents that never read it. Catches displacement
  tells our own rules create.
- **Scout** (same file): weekly. last30days sweep plus the Wikipedia
  signs-of-AI-writing page, for tells the wild is already mocking.
- **Aging** (same file): quarterly. Re-test corpus entries against current
  models; propose retiring what no longer fires.

## References

- `references/patterns.md`: the deduped rule library (the floor) and the
  context-profile matrix.
- `references/living-corpus.md`: dated tells caught in the wild, with mechanism
  tags. The moat.
- `references/ingestion.md`: the curation flow for memorializing new slop.
- `references/protect-list.md`: the seam to a personal voice spec; signatures the
  floor must not strip. Ships as a fill-in template.
- `references/harvest.md`: the shipped-diff harvest loop.
- `references/weekly-loop.md`: the scheduled self-play / scout / aging round.
- `references/candidates.md`: the inbox of proposed rules awaiting the gate.
- `evals/`: the regression gate; slop fixtures plus a local-only golden set.

## Credits and license

anti-slop is a consolidation of prior open work. It would not exist without:

- **avoid-ai-writing** by Conor Bronsdon (MIT). Source of the tiered vocabulary
  (Tier 1/2/3), the context profiles, and the severity tiers. Its vocabulary
  tiering was itself adapted from `brandonwise/humanizer`.
- **humanizer** (MIT), based on Wikipedia's "Signs of AI writing" page,
  maintained by WikiProject AI Cleanup (content under CC BY-SA 4.0). Source of
  the content-pattern catalog and the adversarial self-audit step.
- **stop-slop** by Hardik Pandya, hvpandya.com (MIT). Source of the false-agency
  rule, the binary-contrast variant table, and the 5-dimension scoring rubric.
- **no-ai-slop** by Peter Yang (MIT). Source of the faux-insight-setup,
  colon-reveal, and fake-profound-kicker patterns, and the throwaway
  voice-signal step for drafts without a voice spec.

License: MIT for anti-slop's own text. Examples ported from the humanizer /
Wikipedia lineage are rewritten in our own words; the underlying Wikipedia
material is CC BY-SA 4.0. See `CREDITS.md` and `LICENSE` for full attribution and
the share-alike note.
