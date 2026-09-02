---
name: anti-slop
description: >
  Detect, rewrite, and ingest AI-slop. One maintained spec that consolidates and
  replaces avoid-ai-writing, humanizer, and stop-slop. Use when drafting,
  editing, or reviewing any text to remove AI tells; when the user pastes text
  marked "slop:" to memorialize a new pattern; or when asked to "de-slop",
  "remove AI-isms", "clean up AI writing", or "audit for AI tells". Also fires
  on technically clean but voiceless prose that needs a stance. This is the
  general AI-slop floor. On a byline with a personal voice spec, it pairs with
  that voice overlay through the protect-list seam, so it never flattens a
  writer's real signatures.
version: 0.2.0
license: MIT
metadata:
  replaces: [avoid-ai-writing, humanizer, stop-slop]
  status: stable
---

# anti-slop

One owned, maintained skill for removing AI writing patterns, and for ingesting
new ones as the models change. The rule lists are commodity; every skill in
this category ships the same 80%. The moat is the machinery around them: the
learning loops, the eval gate, and the voice-spec seam. The living corpus
(`references/living-corpus.md`) is that machinery's output: dated tells caught
in the wild, tagged with the generative mechanism.

This file alone runs the common pass. `references/` is escalation (the full
tables and profiles) and maintenance (loops, inbox, corpus); load those only
when the task needs them.

## How this fits together

- **This skill is the general floor.** Universal AI tells. Reusable across every
  project and surface.
- **Your voice spec is the personal overlay.** Your signatures and the protect
  list (what this skill must NOT strip from your byline). The voice spec is
  canonical for the protect list; this skill points at it, never restates it. See
  `references/protect-list.md` for the seam. To build your own voice spec from
  your writing, use the companion onboarding flow (`voice-dna-builder`).
- **Predecessors and sources are retired into this skill.** What folded in
  from where: `CREDITS.md`.

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

**rewrite and detect always end with the completeness verifier** (see below): a
fresh-context subagent whose only job is to confirm the pass caught everything
it was supposed to catch. Not skippable. ingest does not need it.

## The spine

1. **Minimum effective edit.** Fix the tell, leave strong human sentences
   alone, cut in proportion to the actual slop. A clean draft gets a light
   pass, and "this text is fine" is a valid verdict. Over-editing human prose
   is the same failure as slop, pointed the other way.
2. **Structure is the #1 detection signal**, above vocabulary. Uniform sentence
   and paragraph length reads as AI even with every flagged word removed. Vary
   rhythm first, swap words second.
3. **Tiered vocabulary, not blanket bans.** Tier 1 always-replace, Tier 2 flag
   in clusters, Tier 3 flag by density. Full tables in `references/patterns.md`.
   Blunt "never" rules stacked deep recreate the over-polishing failure they are
   meant to fix.
4. **The portability test.** If a sentence could move unchanged to another
   person, company, or product, it says nothing about this one. Cut it or make
   it specific.
5. **Context profiles** adjust strictness: linkedin, blog, technical-blog,
   investor-email, docs, casual. Matrix in `references/patterns.md`. Auto-detect
   from content cues if none is passed.
6. **The protect-list seam.** On a byline with a voice spec, load
   `references/protect-list.md` first; if `references/protect-list.local.md`
   exists it replaces the template, and it is gitignored so a filled-in list
   never leaves the machine (canonical: your voice spec). Never strip a
   protected signature. If a flag collides with one, surface it and do not
   auto-edit. With no voice spec (someone else's draft, an unowned byline), build
   a throwaway one: before editing, note the core point and 3-5 voice signals in
   the draft itself (vocabulary, humor, cadence, pet phrases) and preserve them
   through the rewrite. De-slopped text that lost its author is still a failure.
7. **Honesty, both modes.** Detect mode names patterns, never authors: a named
   pattern is checkable evidence, an authorship claim is a guess, so never
   declare a text AI-written. Rewrite mode never invents: no fact, name,
   number, date, or quote that isn't in the source. A needed specific comes
   from the source or the user, or the sentence ships plain.
8. **Sterile is also slop.** Voiceless, stanceless, evenly balanced prose is as
   machine-tellable as delve. On genres that carry a byline (opinion, blog,
   personal, marketing), the draft needs a position and a pulse: react to
   facts, vary rhythm, let some mess in. Stance content comes from the voice
   spec's stance layer; with no spec, sharpen the positions already in the
   draft, never fabricate new ones. A pulse comes from a position, never from
   flourish; mannered prose (see `references/patterns.md`) is the wrong fix
   for sterility. Technical reference and encyclopedic text are exempt: neutral
   is the correct human voice there.
9. **Self-reference escape hatch.** When writing ABOUT slop (this file, examples,
   quoted bad writing), do not flag the quoted patterns. Only flag the author's
   own prose.

## Seams (rewrite mode)

AI slop shows most at the seams: how paragraphs and thoughts connect. Banning
transitions backfires (the metronome moves; see displacement in the corpus).
Instead:

- Vary the shape of the connection, not just the word: a fragment, a question,
  a flat statement, a callback. Two boundaries leaning on the same move means
  break one.
- The best transition is often none. Start the next thought.
- Never manufacture connective tissue where the thought connects fine; a
  transition bolted onto every seam is itself an AI habit. Rare or showy
  transitions are their own tell; fit beats novelty.
- On a byline, bias toward that voice's natural transitions (protect list).
- Flagship pieces only: a separate seam review by a fresh-eyes agent that did
  not write the draft. Not worth the cost on a tweet.

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
- Sentence could ship unchanged in someone else's post? Portability fail: cut
  it or make it specific.
- Opinion-genre piece with no position anywhere? A flag, not a virtue.
- Reads like clean TTS with no rhythm? It is too uniform. Add disfluency.
- Metaphor standing in for a statement ("a dial worth turning", "earns its
  keep")? Say what you mean. When a literal phrase is available, use it.
- Sentences run long and paragraphs rarely break? Density is a tell on its
  own. Break the sentence at its second clause, the paragraph at its second
  idea.

## The gate (before delivery)

Two questions, answered honestly, every time:

1. "What makes this still obviously AI-generated?" Whatever you name, fix.
   "Nothing" is a valid answer, and on an already-clean draft it is the right
   one (spine rule 1). Naming a tell you cannot point at in the text fails the
   gate the same way missing a real one does; the question hunts for tells, it
   does not require a quota.
2. "Does the rewrite state any fact, name, number, date, or quote that isn't
   in the source?" A fabrication is a defect even when it sounds more human.

Then, on a byline with a voice spec: walk that spec's runtime self-review
checklist and the protect list. If question 1 keeps finding the same class of
tell across passes, stop patching and regenerate from a tighter brief.

## Completeness verifier (mandatory before returning any rewrite or detect)

The pass above grades its own homework. A pass that missed a tell can't flag the
tell it missed. So before returning, launch a fresh-context subagent with the
Agent tool (`general-purpose`) whose sole job is to confirm this pass caught
everything it was supposed to. This is not the flagship-only fresh-eyes seam
review above; that one hunts seam monotony on long-form. This one runs on every
rewrite and detect, short or long, and its scope is narrow: did anything slip
through?

The verifier does NOT rewrite, does NOT add new stylistic opinions, does NOT
second-guess a protected signature that was correctly left alone, and does NOT
re-litigate judgment calls. It re-scans and reports misses, nothing else.

Give the subagent:
- the ORIGINAL text (pre-edit), and the cleaned/flagged output plus the list of
  what this pass changed or flagged,
- the rule set to check against: `references/patterns.md` (Tier 1/2/3 vocab,
  false agency, binary-contrast variants) and, on a byline with a voice spec,
  the protect list plus that spec's runtime checklist,
- the active context profile, so it holds the same strictness bar.

Brief it to walk the original independently and surface only tells this pass
FAILED to catch or fix: any em dash (glyph or `--`) beyond what the active
profile allows (zero on a byline whose voice spec bans it), any "not X, it's Y" /
binary-contrast variant (FATAL on a byline whose spec bans it), copula
avoidance, false agency, significance inflation, three-in-a-row uniform sentence
length, synonym cycling, mannered prose (metaphor standing in for a literal
statement) and dense unbroken paragraphs, chatbot artifacts / sycophancy /
validation tails / cutoff disclaimers, and any Tier 1 vocab left standing. It must also flag
over-correction: a real signature or intended fragment the pass wrongly stripped.

Required return: a list of misses only, most-severe first, each with the exact
quoted span and the rule it violates; empty list if the pass was clean. No
praise, no restating what was already caught. Then fold any confirmed misses
back into the output before returning it.

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
- **Scout** (same file): monthly. last30days sweep for tells the wild is
  already mocking and for new anti-slop techniques worth absorbing, plus the
  Wikipedia signs-of-AI-writing page. Its cleanest finds ship as a drafted PR
  (weekly-loop.md, step 6); merging is filing.
- **Aging** (same file): quarterly. Re-test corpus entries against current
  models; propose retiring what no longer fires.

## References

- `references/patterns.md`: the deduped rule library (the floor) and the
  context-profile matrix.
- `references/living-corpus.md`: dated tells caught in the wild, with mechanism
  tags. The moat.
- `references/ingestion.md`: the curation flow for memorializing new slop.
- `references/protect-list.md`: the seam to a personal voice spec; signatures the
  floor must not strip. Ships as a fill-in template; a filled-in
  `references/protect-list.local.md` overrides it and stays gitignored.
- `onboarding/taste-interview.md`: the stance-layer interview; builds the
  judgment half of a voice spec (companion to `voice-dna-builder`).
- `onboarding/voice-sources.md`: the corpus discovery manifest; finds the
  voice evidence already on the machine, with per-source consent and
  register tagging. Runs before the interview.
- `references/harvest.md`: the shipped-diff harvest loop.
- `references/weekly-loop.md`: the scheduled self-play / scout / aging round.
- `references/candidates.md`: the inbox of proposed rules awaiting the gate.
- `evals/`: the regression gate; slop fixtures, a local-only golden set, and
  committed run reports (`evals/reports/`).

## Credits and license

anti-slop consolidates prior open work: avoid-ai-writing (Conor Bronsdon),
humanizer (Wikipedia "Signs of AI writing" lineage), stop-slop (Hardik Pandya),
no-ai-slop (Peter Yang), unslop (@poteto), and soundshuman (aashaexo). Who
contributed what, plus the CC BY-SA share-alike note for the Wikipedia-lineage
material, lives in `CREDITS.md`. anti-slop's own text is MIT; see `LICENSE`.
