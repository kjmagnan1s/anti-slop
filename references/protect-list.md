# Protect-list seam (template)

The floor (this skill) strips general AI tells. The overlay (your voice spec)
defines what must survive on a given byline. This file is the seam between them.

This ships as a **template**. The categories below are the ones that most often
collide with a real writer's voice. Fill each one in from your own writing, or
let the `voice-dna-builder` onboarding flow generate it for you. Delete the
placeholder examples once you have replaced them; an unfilled template protects
nothing.

To keep a filled-in list out of a public clone, write it to
`references/protect-list.local.md` instead. That file is gitignored, and when it
exists the skill loads it in place of this template.

## The mechanism (general)

anti-slop is reusable across contexts. Each context supplies its own protect list:

- **Your byline** → your personal voice spec is canonical. The list below is the
  operational mirror for when that spec is not loaded.
- **A specific project** → that project's in-repo voice doc / CLAUDE.md.
- **No named context** → no protect list; apply the floor at full strength.

Rule: before flagging or filing on a byline that has a protect list, load it
first. Never strip a protected signature. If a floor flag collides with a
protected item, surface the collision and do not auto-edit.

### Where the list lives in a prose voice spec

A voice spec is often a prose document, not a config file. When it is, the
protect list is the section whose heading starts with `protect:`, matched
without case, and the list is that section's top-level bullets. One signature
per bullet, with a quoted example from the writer's own samples. No separate
machine block is required, and none should be added: the section a person
writes by hand is the contract.

### A remove-pattern beats a protected signature

A voice spec may also carry a `## Patterns to remove, not protect` section.
That section wins. A pattern named there is a tell on this byline even when it
reads like a signature, and even when the `protect:` list names it too. Apply
the floor to it and say in the report that the two sections named the same
pattern.

Carry those patterns into the mirror below, under `Calibration gap to enforce`.
A mirror that copies the protect half and leaves the remove half behind
protects the exact patterns the byline asked you to strip, on every pass that
runs without the spec.

### An empty protect list is a finding, not a default

Say so before editing. A missing or empty protect list on a named byline is a
setup failure, and the symptom is invisible: the floor runs at full strength,
the flags all look correct, and the writer's real moves come out flattened
with nothing in the report to show it. Report which spec was read and that it
carried no protect section, then either get the section written or run in
detect mode only. Never treat "no protected items" as a clean state. The
floor at full strength is correct for an unowned byline and wrong for an
owned one.

## How to fill this in

For each category, list the specific words, phrases, or moves that are genuinely
*yours* and that a generic de-slop pass would wrongly flatten. Be concrete: quote
the exact phrase. Anything you cannot point to in your own writing samples is not
a signature yet; leave it out. Keep the list short and real. A bloated protect
list defeats the floor.

## Operational mirror (canonical: your voice spec)

These are floor flags that are actually *your* signatures. Do not strip them from
your byline. This is a cache; your voice spec wins on any conflict. Fill every
`<...>` from your own writing samples.

- **Reveal verb / framing tic**: the phrase you habitually reach for right before
  stating a finding. A generic pass cuts these as throat-clearing; if it is a real
  tic of yours, keep it.
  - `<your reveal verb / lead-in phrase>`
- **Intensifier verdict**: your go-to moderate judgment phrase, positive or
  negative. The floor would kill the adverb inside it. Keep yours.
  - `<your verdict phrase>`
- **Hedge-then-commit words**: the softeners you use to set up a hard claim, where
  the hedge front-loads a flag you then plant firmly. Keep them when they front a
  hard claim.
  - `<your hedge words>`
- **Closers**: your move at the end of a piece (a question that hands the reader
  the ball, a directive, a sign-off). The floor would restructure question-style
  openers; protect these as closers.
  - `<your closers>`
- **Fragment beats**: deliberate sentence fragments and short/long stacking you use
  for rhythm. The floor would flag dramatic fragmentation. Keep the deliberate ones.
  - `<your fragment-beat examples>`
- **Conjunction openers**: `And` / `But` / `So` at the start of a sentence or
  paragraph, if you use them on purpose. Keep.
- **Comma splices for rhythm** (occasional, deliberate): keep if they are part of
  your cadence.
- **First-person density**: if you write heavily in first person on purpose, record
  your baseline (count the "I"s per 1,000 words in your samples) so the floor does
  not strip it for a "professional" tone.
  - `<your first-person baseline, if any>`
- **Word repetition over synonym-cycling**: if you deliberately repeat the right
  word instead of reaching for a synonym, keep it.
- **Profanity as a verdict word** (if applicable): the surgical, after-a-setup use
  you allow yourself, with a ceiling. Keep that; never add filler swearing.
  - `<your profanity rule, or "none">`
- **Signature phrases**: the recurring phrases that are distinctly yours: idioms,
  coined terms, pet metaphors. Keep where they fit.
  - `<your signature phrases>`

## Calibration gap to enforce

Where your voice spec is stricter than the floor, the spec wins. Common example:
the floor allows "max one" binary-contrast ("not X, it's Y") per piece, but a
voice spec may ban it at zero (FATAL). Enforce the stricter setting. List any such
gaps here so the floor does not silently relax them.

- `<your stricter-than-floor rules, e.g. "binary contrast: zero, not max one">`
- `<each pattern from the spec's "Patterns to remove, not protect" section, or
  "none">`
