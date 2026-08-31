# Candidates inbox

Proposed rules waiting for the writer's gate. The learning loops (harvest,
self-play, scout, aging; see `references/harvest.md` and
`references/weekly-loop.md`) write here. Nothing moves from this file into
`living-corpus.md`, `patterns.md`, or the protect list without approval, the
ingestion six-step, and the eval gate.

## Entry format

```
### <short-name> [status: proposed | approved | rejected | filed]

- Found: YYYY-MM-DD  |  Loop: harvest | self-play | scout | aging
- Evidence: "<the quoted span, or the diff hunk>"
- Source: <ledger file / detector round / URL>
- Proposed rule: <one-line directive + suggested tier>
- Mechanism guess: <ingestion taxonomy tag>
```

Aging proposals use the same block with `Proposed rule:` replaced by
`Proposed change: retire | re-tier <entry> because <evidence>`.

## How to process the inbox

Reply with the entry name plus `ok` (file it), `edit: <change>`, or `no`
(mark rejected, keep the entry as a record so the same candidate is not
re-proposed next round). Rejected entries are dedup targets too.

---

## Inbox

## Round 2026-07-22 (bootstrap round, run manually)

Scout: 103 last30days items (Reddit, X, TikTok, YouTube, GitHub, web;
2026-06-22 to 2026-07-22), Wikipedia signs-of-AI-writing (48 signs), Algorithmic
Bridge and Olivia Cal catalogs. 11 candidates survived dedup; 16 near-miss
groups deduped as already covered. Self-play entries open the section; the 11
scout entries follow them.

Self-play: 4 samples written with the skill fully applied; 8 fresh-eyes
detectors (isolated headless runs, no repo access) judged all 4 AI-written on
structural grounds despite clean vocabulary. 69 raw flags, ~24 distinct tells,
7 survivors after dedup; 5 of 7 tagged displacement (tells our own rules
created). Two generation-side misses also logged at the end of this section:
existing rules that failed at write time, not new patterns.

### punchline-terminal-paragraphs [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "Every paragraph ends on a crafted zinger... One button is voice; a
  button per paragraph is a generation pattern." The most-cited tell of the
  round: flagged by 8/8 detectors across all 4 samples.
- Source: self-play round 1 detector reports (scratchpad selfplay-round1/)
- Proposed rule: Flag when 3+ consecutive paragraphs land a crafted closer;
  let some paragraphs end on a plain fact or trail off. Also check the paired
  shape (hook opener, body, stinger). Suggested Tier 2.
- Mechanism guess: displacement (vary-rhythm rule + generic-conclusions ban +
  sound-like-a-person pressure; "human" gets performed as one punchline per
  seam)

### closed-loop-narrative-economy [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "Every setup detail gets a tidy payoff... Humans leave loose
  threads; here nothing is introduced that isn't cashed in." Flagged on 4 of 4
  samples with narrative content.
- Source: self-play round 1 detector reports
- Proposed rule: In anecdote/narrative prose, do not cash in every planted
  detail; a digression that goes nowhere reads human. Flag when every
  introduced detail pays off and the ending bow-ties a planted callback.
  Context-dependent: fine in a short hook, a tell in essay/anecdote registers.
- Mechanism guess: displacement (the Density scoring dimension and cut-filler
  rules select against exactly the loose threads that mark human recollection)

### metered-specificity [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "Roughly one concrete number per paragraph, metering out
  authenticity at a steady rate... no awkward number like $4.25, no 'I think
  it was'."
- Source: self-play round 1 detector reports
- Proposed rule: Clump specifics where the memory or argument actually lives
  and let other paragraphs go without. Evenly spaced specificity tokens and
  perfectly reconciling arithmetic are tells. Suggested Tier 2.
- Mechanism guess: displacement (vagueness/weasel bans demand specifics; the
  model satisfies the quota at a uniform rate instead of where memory clusters)

### periodic-long-short-alternation [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "Varied sentence lengths, but the variation itself is metronomic...
  fragments used only for punch, never from sloppiness."
- Source: self-play round 1 detector reports
- Proposed rule: Check second-order rhythm after applying vary-rhythm: if short
  fragments recur on a fixed cycle, break the cycle; run a stretch with no
  fragments, or land one mid-paragraph on a non-joke. Suggested Tier 2. Sibling
  of the anti-em-dash displacement corpus entry.
- Mechanism guess: displacement (the "three matching sentences? break one"
  check executed as a schedule rather than as noise)

### strategic-de-contraction [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "The text contracts everywhere except in the deadpan beats... the
  formal verb landing exactly where the emphasis goes, twice, reads like
  deliberate comedic engineering rather than typing."
- Source: self-play round 1 detector reports (casual sample)
- Proposed rule: In casual registers, keep contraction behavior consistent;
  uncontracted forms placed only on punchlines are a tell. One emphatic
  de-contraction is a real human move; a pattern of them is not. Suggested
  Tier 3, casual/linkedin profiles.
- Mechanism guess: pretraining-register (formal forms surface under emphasis),
  amplified by sound-human pressure

### rhetorical-figure-flourish [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "'Total cost came to $912 and one Saturday.' Zeugma... a cute
  rhetorical figure that humanized AI output reaches for constantly; real DIY
  recaps almost never do." Also chiastic reveals and withheld-name punchlines.
- Source: self-play round 1 detector reports
- Proposed rule: Cap performed literary figures (zeugma, chiasmus/word-flip
  reveals, withheld-name reveals) at roughly one per piece in plain-prose
  registers. Suggested Tier 2.
- Mechanism guess: displacement (vocabulary tables scrub word-level style, so
  the sound-like-a-person target routes style into syntactic figures)

### universalized-maxim-closer [status: proposed]

- Found: 2026-07-22  |  Loop: self-play
- Evidence: "'I no longer trust any job that can't prove it ran today.' Ending
  a postmortem on a personally-earned general principle is the stock AI
  essay-closer."
- Source: self-play round 1 detector reports (technical-blog sample)
- Proposed rule: Merge as a variant into fake-profound kicker: closing by
  universalizing the incident into a life-rule/maxim is the same inflation
  without the metaphor. End on the last concrete point. Suggested Tier 2.
- Mechanism guess: instruction-tuning (essay-arc training rewards
  lesson-shaped endings; the metaphor ban leaves the maxim shape as the
  surviving exit)

### quietly-becoming [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: "The new super obvious AI slop post giveaway that makes me roll my
  eyes is, 'This thing is *quietly* becoming this thing' in the opening
  sentence. AI sure loves quietly for some reason"
- Source: https://x.com/Trikeri_Omni/status/2077566360981516357
- Proposed rule: Flag "quietly" as a stealth-hype adverb ("X is quietly becoming
  Y", "quietly shipped", "quietly powering"). State the change plainly or cut.
  Suggested Tier 1; publicly mocked, burns fast.
- Mechanism guess: reward-tuning (manufactured insider-scoop framing)

### let-that-sink-in [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: "Hallmarks of AI-written slop include 'poignant' reminders of its
  own importance ('let that sink in'); repetition; very short sentences set on
  one line; platitudes; and a formulaic structure."
- Source: https://x.com/BTRadford/status/2079344331245465762
- Proposed rule: Flag emphasis commands that instruct the reader to feel the
  weight ("let that sink in", "read that again", "sit with that"). Sibling of
  the fake-profound kicker. Suggested Tier 1 phrase list.
- Mechanism guess: reward-tuning (engagement-bait significance inflation)

### subtext-vacuum [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: "I wonder if one of the tells of AI writing is that it makes
  explicit things that people would normally just leave implicit"; Algorithmic
  Bridge sign IX: explicit explanation of everything leaves nothing for readers
  to discover.
- Source: https://x.com/m_ashcroft/status/2079122520372895780 (also
  https://www.thealgorithmicbridge.com/p/10-signs-of-ai-writing-that-99-of)
- Proposed rule: Flag prose that narrates its own communicative intent or
  explains what should stay implicit (announcing the goal of each paragraph,
  explaining the joke, naming the theme after showing it). Trust the reader.
  Suggested content pattern, Tier 2.
- Mechanism guess: reward-tuning (helpfulness training rewards explicitness)

### horizontal-rule-addiction [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Wikipedia sign: thematic breaks before headings (horizontal rules
  inserted before section headers).
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: Flag decorative `---` dividers between sections, especially
  preceding a heading that already provides the break. One per document at
  most. Suggested formatting pattern, Tier 2.
- Mechanism guess: instruction-tuning (chat-response sectioning carried into
  prose)

### machine-reference-artifacts [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Wikipedia signs: ChatGPT "oaicite", Gemini "[cite: 1]", Grok
  "grok_card", DeepSeek dagger symbols, and utm_source=chatgpt.com query
  params on shared links.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: Strip machine citation residue: oaicite/turn0search markers,
  [cite: N], grok_card, stray daggers, and chatbot utm_source params on links.
  Suggested P0 credibility killer, chatbot-artifact family.
- Mechanism guess: tooling artifact (copy-paste from chat UI; possible new
  taxonomy tag)

### markdown-residue [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Wikipedia sign: markdown syntax surviving on surfaces that do not
  render it (asterisk bold, ### headers in emails, DMs, plain-text posts).
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: On non-markdown surfaces (email, social captions, DMs, form
  fields), flag literal **asterisks**, ### headers, and backticks as
  paste-from-chatbot residue. Suggested P0.
- Mechanism guess: tooling artifact

### placeholder-residue [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Wikipedia sign: phrasal templates and placeholder text ("This
  section would speculate...").
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: Flag unfilled scaffolding: bracketed placeholders ([Company],
  [insert detail]), conditional meta-text ("this section would..."), and
  instructions-to-self left in output. Suggested P0 credibility killer.
- Mechanism guess: tooling artifact

### ai-native-pitch-vocab [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: "AI slop giveaways in a pitch deck: 'AI native' 'Intelligence
  layer' 'Operating system for ____' 'It's not ___. It's ____'"
- Source: https://x.com/dangaron/status/2078192747333529934
- Proposed rule: In marketing/pitch/investor contexts, flag category-abstraction
  vocab: "AI-native", "intelligence layer", "operating system for X", "copilot
  for X". Name what the product does instead. Context-dependent
  (investor-email/marketing), Tier 1 there.
- Mechanism guess: pretraining-register (2024-26 startup-copy saturation)

### treadmill-paragraphs [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Algorithmic Bridge sign VII: AI hovers over similar ideas without
  advancing, "lots of motion, no displacement".
- Source: https://www.thealgorithmicbridge.com/p/10-signs-of-ai-writing-that-99-of
- Proposed rule: Flag consecutive paragraphs that restate one idea in fresh
  wording without adding a fact, example, or consequence. The idea-level sibling
  of synonym cycling. Delete-test: if a paragraph can go with nothing lost, it
  goes. Suggested structure pattern, Tier 2.
- Mechanism guess: repetition-penalty (length optimized over information)

### rather-than-variant [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Wikipedia negative-parallelism variant: "X rather than Y" as a
  reversed construction; our binary-contrast table lacks this shape.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: Extend the binary-contrast family with "X rather than Y" /
  "focuses on X rather than Y" when used as a reflexive frame rather than a
  real comparison. Edit to the patterns.md binary-contrast table, same tier.
- Mechanism guess: displacement (crackdown on "not X, it's Y" pushes the same
  reversal into softer syntax)

### emoji-bullets [status: proposed]

- Found: 2026-07-22  |  Loop: scout
- Evidence: Wikipedia sign: emoji as decorative dividers or list markers; our
  rule covers headers only.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: Widen the emoji rule from headers to formatting generally:
  emoji bullet markers, checkmark lists, dividers. Edit to the patterns.md
  style section; linkedin keeps its 1-2 end-of-line allowance.
- Mechanism guess: pretraining-register (LinkedIn-corpus style bleed)

### Round notes: generation-side misses (not candidates)

1. A tailing-negation binary contrast ("before you turn the thing on, not
   after") shipped despite the FATAL family being on the books. Rule exists;
   application missed it.
2. A conscious reroute around the faux-insight ban ("Nobody warned us about
   the GPS stamps") was still caught as the identical template slot. Rewording
   a banned phrase does not vacate the slot; the fix is structural.

## Round 2026-07-23 (aging observation, logged manually)

### em-dash-retier [status: proposed]

- Found: 2026-07-23  |  Loop: aging (Kevin's observation)
- Evidence: Kevin's read is that current models emit em dashes noticeably less
  than the 2024-25 era, so the pattern may no longer deserve headline
  preferential treatment relative to binary contrast and the colon reveal.
- Source: Kevin, in-session 2026-07-23
- Proposed change: gather frequency evidence in the next self-play and aging
  passes; if confirmed, re-tier the em dash corpus entry down from headline
  status while keeping it flagged. Note the seam: the zero-em-dash rule on
  Kevin's byline comes from his voice spec and stands regardless of model
  frequency; only the floor's tiering would change.
- Mechanism guess: n/a (aging; models moved)

## Round 2026-07-28 (weekly loop)

Harvest: 1 ledger entry (`2026-07-23-trimhero-gate-qt.md`, tweet). Fetch-back
FAILED: WebFetch on x.com returned HTTP 402, and the Grok Build fallback was not
run (the shell invocation required an approval that was not granted in this
session). Classification proceeded from the ledger's own ship-time record of the
posted text, which capture path 1 had already stored; no published text was
reconstructed from memory. Ledger entry retained rather than pruned, because
fetch-back was never confirmed. 3 candidates (2 missed-tell, 1 protect-list).

Self-play: 4 samples (linkedin, blog, technical-blog, casual), skill fully
applied, no voice spec loaded. 8 fresh-eyes detectors, tool-free and given only
the sample text. Verdicts: 7 of 8 called AI (confidence 60-80%); the casual
sample split, one detector calling it human at 95%. ~86 raw flags, ~28 distinct
tells, 10 survivors after dedup plus 3 fold-only proposals. 5 of 10 tagged
displacement. Not one detector flagged a vocabulary tell as decisive; every
decisive flag was structural, and three detectors independently named the
pattern "surface cleaned, skeleton untouched."

Scout: last30days FAILED to execute (skill returned an error on two attempts);
fell back to WebSearch plus a direct fetch of the Wikipedia signs page (58 signs
enumerated). 3 candidates plus 4 fold-only proposals; the rest deduped against
the 2026-07-22 batch.

Aging: SKIPPED. Not the first run of the quarter. Q3 2026 opened with the
2026-07-22 bootstrap round and the 2026-07-23 aging observation. One evidence
entry is logged below against the open `em-dash-retier` proposal.

### unnamed-attributor-social [status: proposed]

- Found: 2026-07-28  |  Loop: harvest
- Evidence: draft read "The security review found my gate was a sentence in a
  markdown file"; Kevin shipped "@claudeai's security review found..."
- Source: harvest/2026-07-23-trimhero-gate-qt.md
- Proposed rule: When the actor behind a finding, quote, or decision is a
  nameable person, org, or handle, name them in the sentence. The floor already
  bans vague attributions ("experts believe"); the miss here was a *known* actor
  flattened into a definite noun phrase ("the security review"). Extend the
  vague-attributions rule to cover the case where the source is known and the
  writer generalized it anyway. Suggested edit to patterns.md content pattern 5,
  same tier.
- Mechanism guess: instruction-tuning (neutral-register default strips
  identifying handles)

### fix-and-cta-close [status: proposed]

- Found: 2026-07-28  |  Loop: harvest
- Evidence: Kevin cut the delivered draft's entire closer, "Fixed it in code
  this morning" plus "If a skill you install can edit your settings, check its
  gate is more than a sentence." The posted version ends on the vulnerability.
- Source: harvest/2026-07-23-trimhero-gate-qt.md
- Proposed rule: Do not resolve-and-advise at the end of a post about a problem.
  Reassuring the reader that it is fixed, then converting the incident into a
  reader instruction, is the same exit-shape as the fake-profound kicker and the
  universalized maxim: three doors out of one room. Merge all three into one
  mechanism rule (end on the last concrete finding) with three example shapes.
  Suggested Tier 2. This is the fold the size budget asks for.
- Mechanism guess: instruction-tuning (helpfulness training wants every
  narrative to terminate in resolution plus actionable takeaway)

### lineage-credit-signature [status: proposed]

- Found: 2026-07-28  |  Loop: harvest
- Evidence: Kevin added "based on @mattpocockuk's work on Claude's system prompt
  bloat" to a draft that credited no one, and personalized "@claudeai" into the
  sentence body.
- Source: harvest/2026-07-23-trimhero-gate-qt.md
- Proposed rule: Protect-list candidate, not a floor rule. Kevin names his
  lineage and personalizes @-mentions into the prose rather than appending them.
  Belongs in his voice spec, not in patterns.md. Route to voice-dna.md rather
  than filing here.
- Mechanism guess: n/a (flattened voice)

### actorless-scene [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: "I went to the July meeting. About ninety people were there, most of
  them angry about the sinkhole." Detector B2 led with it: "the narrator claims
  to have physically attended a meeting with ninety angry people in it and comes
  back with zero sensory observation, zero quotation, zero name." B1 called it
  "synthetic first person." C1 and C2 flagged the sibling in the technical
  sample: "No first person anywhere... Agency belongs entirely to subsystems."
  Flagged on 3 of 4 samples by 4 detectors.
- Source: self-play round 2 detector reports (samples B, C)
- Proposed rule: If the prose claims presence at an event, it must contain at
  least one thing only a present person could supply: a named person, a quoted
  line, an observed particular, or a dead end the writer actually hit. A scene
  rendered as headcount plus aggregate emotion is attendance asserted, not
  remembered. The strongest single new finding of the round. Suggested Tier 2,
  narrative and incident registers. Sibling of the existing false-agency rule:
  false agency removes the actor from a sentence, this removes them from a room.
- Mechanism guess: pretraining-register (summary-of-an-event is far more common
  in training data than witness-of-an-event)

### canonical-detail [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: A1 on "our setup script had been broken on Apple silicon": "the
  detail is doing authenticity work while being the least surprising possible
  instance of its category... it has the texture of something retrieved," set
  against "whoever had the lightest sprint that week," which "has the texture of
  something observed." C1 and C2 both flagged "on a Tuesday" as
  precision-as-texture; D2 flagged "his wife made coffee" the same way.
- Source: self-play round 2 detector reports (all 4 samples)
- Proposed rule: Test concrete details for retrieved-vs-observed, not for
  presence. A detail that is the category's most canonical example (Apple
  silicon for a dev-setup break, "a Tuesday" for an unremarkable weekday) reads
  generated even though it is specific. Prefer the slightly wrong, slightly
  useless particular. Suggested Tier 2. Note for the writer: this resolves an
  apparent contradiction in the inbox. `closed-loop-narrative-economy` says
  leave loose threads; detectors this round flagged *both* the pay-off-everything
  pattern and the planted-unused-detail pattern. The reconcilable rule is not
  about whether a detail pays off, it is about whether it reads observed. Fold
  both into one mechanism when filing.
- Mechanism guess: pretraining-register (sampling toward the modal instance of a
  category is what specificity-under-pressure produces)

### paragraph-opener-monotony [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: A1: "Five of six paragraphs open subject-first with a declarative...
  No paragraph starts mid-thought, with a conjunction, with a fragment, or with
  a subordinate clause." C1 counted six sentences opening on a definite
  determiner plus subject: "Human prose staggers its entry points; this
  marches." C2 and B2 flagged the same shape independently.
- Source: self-play round 2 detector reports (samples A, B, C)
- Proposed rule: Second-order check on the transition-iteration procedure. After
  the seam pass, audit paragraph and sentence *entry points*, not just
  transitions: if nearly every unit opens subject-first with a definite article,
  the connective tissue was cut uniformly rather than varied. Vary the entry
  point (subordinate clause, conjunction, fragment, mid-thought) even where no
  transition word is wanted. Suggested Tier 2.
- Mechanism guess: displacement (SKILL.md's "the best transition is often none"
  guard, applied everywhere, produces blocks that abut without touching; A1
  named this explicitly as "a taught de-slop behavior, over-applied")

### matched-antithesis-pairs [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: "On paper it was a mentor. In practice it was whoever had the
  lightest sprint that week." A1: "the negate-then-correct frame in its most
  respectable clothes... Both clauses share the identical 'it was' hinge, which
  is the giveaway that they were generated as a pair." Same detector flagged
  "Sometimes that is an afternoon. Once it was most of a week." A2 called it
  "the de-slopped descendant of 'it wasn't X, it was Y'."
- Source: self-play round 2 detector reports (sample A)
- Proposed rule: Extend the binary-contrast family to the non-negated symmetric
  pair: two adjacent sentences in matched syntactic frames sharing a hinge verb
  (on paper / in practice, sometimes / once, in theory / in the room). Dropping
  the word "not" does not vacate the slot. Edit to the patterns.md
  binary-contrast table, same FATAL tier on bylines that ban the family. Sibling
  of the already-proposed `rather-than-variant`; file them together.
- Mechanism guess: displacement (the FATAL crackdown on explicit negation pushes
  the identical reversal into paired declaratives)

### scheduled-humility-beat [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: A2 on "On 90-day attrition I have no read yet": "it arrives exactly
  where a well-built draft would place a credibility concession, second-to-last,
  right before the CTA, which is itself a template slot." A1: "the most
  predictable possible next sentence after 'dropped from 11 days to 4'." B1 and
  B2 flagged the blog sibling, "including me until this year": "the humility beat
  that AI reliably installs to purchase credibility right before the
  conclusion." 4 detectors, 2 samples.
- Source: self-play round 2 detector reports (samples A, B)
- Proposed rule: Flag self-implicating humility placed immediately after the
  strongest claim and immediately before the close. The move is real; the slot
  is the tell. If the caveat belongs, put it where the doubt actually arose, or
  earlier than the payoff. Distinct from the concession-reflex corpus entry,
  which is about manufactured balance mid-argument; this is about position.
  Suggested Tier 2.
- Mechanism guess: displacement (bans on generic conclusions and sycophancy
  leave calibrated-humility as the surviving pre-close move, so it hardens into
  a slot)

### contraction-register-mismatch [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: A1: "Zero contractions in an otherwise conversational register...
  Full expansion across six paragraphs is not a stylistic accident; it's the
  single strongest tell in the piece." A2 and D2 flagged the same; D2 caught the
  inverse in the casual sample, "uncontracted forms in a text that elsewhere
  does contract... the inconsistency is the giveaway."
- Source: self-play round 2 detector reports (samples A, D)
- Proposed rule: Supersedes and absorbs the open `strategic-de-contraction`
  candidate, which covered only de-contraction on punchlines. The general rule:
  contraction rate must match the register and stay internally consistent. Zero
  contractions in conversational prose is a tell; so is contracting everywhere
  except two emphatic beats. File one rule, retire the narrower one in the same
  commit. Suggested Tier 2, casual and linkedin profiles.
- Mechanism guess: pretraining-register (assistant-formal default survives the
  instruction to sound plain, because "plain" is read as "unornamented" rather
  than "spoken")

### fronted-cleft-syntax [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: "The managers finding the rot is the part I did not plan for." A1:
  "It's a constructed sentence, not a spoken one. The natural version is 'I
  didn't plan for the managers finding the rot.' The inversion exists to put
  'rot' early for punch." A2 flagged the same span as "assembled to front the
  surprise." B2 on "What would have changed the outcome is someone reading the
  February agenda": "counterfactual-as-thesis, phrased as a cleft for emphasis."
- Source: self-play round 2 detector reports (samples A, B)
- Proposed rule: Flag gerund-nominal subjects and it-/wh- clefts used to front
  the punch word ("The X doing Y is the part that...", "What would have changed
  it is..."). Rewrite in speech order. Related to the existing Wh- opener rule,
  which covers openers only; this covers the whole-sentence inversion. Fold into
  that rule rather than adding a new one. Suggested Tier 2.
- Mechanism guess: displacement (with punchy vocabulary and em dashes both
  banned, emphasis routes into word order)

### clean-mechanics-in-casual [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: D2: "All-lowercase, zero typos, perfect apostrophes across five
  paragraphs. People who type in lowercase are optimizing for speed and drop
  apostrophes, double a word, fumble a number... Performed casualness with
  copyedited mechanics." Corroborated inversely by D1, the one human verdict of
  the round, which cited *inconsistent* terminal punctuation and mixed numeral
  styles as its strongest human signals.
- Source: self-play round 2 detector reports (sample D)
- Proposed rule: In casual registers, informality must be inconsistent to read
  as real. Uniform lowercase with perfect apostrophes and normalized number
  formatting is performed, not typed. Do not manufacture typos, but do not
  normalize away the drift either: mixed numeral conventions and inconsistent
  terminal punctuation are protected texture. Suggested Tier 2, casual profile
  only. This one has real risk of being gamed into fake sloppiness; tier
  carefully or reject.
- Mechanism guess: displacement (the informal-register instruction is applied as
  a uniform transform, and uniformity is the thing being detected)

### locally-plausible-globally-incoherent [status: proposed]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: C1 found a real causal inversion in the technical sample: stale
  statistics would make the planner *underestimate*, so the row estimate could
  not have moved from 12,000 to 3.2 million if ANALYZE never ran. "Every
  sentence is locally plausible, the causal chain sounds tidy, and it does not
  survive being held in mind all at once." C1 and C2 also both flagged the
  histogram-vs-MCV claim as "wrong at the level a model gets wrong."
- Source: self-play round 2 detector reports (sample C)
- Proposed rule: Detect-mode check, not a rewrite rule. On any explanatory or
  incident text, read the causal chain end to end in one pass and check
  direction of effect, not just plausibility per sentence. Fluent-but-inverted
  causation is a detection signal distinct from style. Note the honest limit:
  this is a factual-accuracy check wearing a slop-detector coat, and it may
  belong in a different skill. Flagging for the writer to decide scope.
- Mechanism guess: n/a (generation coherence, not a style tell)

### lone-flourish [status: proposed, recommend reject unless it recurs]

- Found: 2026-07-28  |  Loop: self-play
- Evidence: A1 on "the rot": "the one decorative noun in an otherwise concrete
  piece, and it sticks out." B1 on "photogenic": "the isolated single sparkle in
  otherwise flat diction reads like a model spending its one allotted vivid
  word." Contested: B1 simultaneously listed "photogenic" as "the strongest
  human signal in the piece," and B2 agreed with the human reading.
- Source: self-play round 2 detector reports (samples A, B)
- Proposed rule: Possible Tier 3 density check: exactly one figurative word in
  otherwise flat diction. Evidence is contradictory within a single detector's
  own report, which is usually a sign the pattern is not real. Logging it so the
  next round can confirm or kill it rather than rediscovering it. Recommend
  reject on one round of contested evidence.
- Mechanism guess: displacement (vocabulary scrubbing leaves a single surviving
  stylistic gesture) — speculative

### anglo-weight-words [status: proposed]

- Found: 2026-07-28  |  Loop: scout
- Evidence: A May 2026 catalog of new giveaway signs lists quietly, shift,
  matters, shape, land, actually, real, earn, the work, hold, pull, compound,
  signal, built different, with example collocations ("this matters because",
  "decisions compound", "send the signal", "do the work", "the pull of", "any
  sentence where a point lands").
- Source: https://www.forbes.com/sites/jodiecook/2026/05/21/15-new-giveaway-signs-of-ai-writing-may-2026-update/
  (corroborated for "quietly" by the already-open `quietly-becoming` candidate,
  sourced independently from X in the 2026-07-22 round, and by a cross-model
  Reddit report cited in the same coverage)
- Proposed rule: One mechanism rule, not fourteen entries. Our Tier tables are
  entirely Latinate hype vocabulary (delve, robust, leverage); this is the
  opposite register, short Anglo-Saxon verbs and nouns used as abstract weight
  words with no referent. Test: if the sentence still parses when the word is
  deleted, and no concrete thing is named, it is doing weight and not work.
  Suggested Tier 2 (flag in clusters), with the listed collocations as examples.
  "Quietly" stays Tier 1 on its own evidence.
- Mechanism guess: displacement (the Latinate-hype crackdown is industry-wide;
  the register moved down, not away)

### cluster-threshold [status: proposed]

- Found: 2026-07-28  |  Loop: scout
- Evidence: Current coverage converges on the same methodological point: no
  single word, phrase, or punctuation mark proves AI authorship, and what gives
  slop away is pile-up, three or four patterns landing in one short passage.
  Independently corroborated by this round's own detectors, none of which rested
  a verdict on a single flag.
- Source: WebSearch summaries of https://www.tweeks.io/blog/what-is-ai-slop and
  https://slopdetector.org/slop/what-is-ai-slop (summary only; neither page was
  fetched directly, so treat the wording as paraphrase)
- Proposed rule: Add a density gate to the severity tiers in patterns.md: report
  P1 and P2 flags with a per-passage count, and escalate on clustering (3+ in a
  short passage) rather than on any single hit. Makes the existing Tier 2
  "flag in clusters" logic explicit at the triage layer instead of only the
  vocabulary layer. Methodology edit, no new tier.
- Mechanism guess: n/a (detection calibration)

### register-discontinuity [status: proposed]

- Found: 2026-07-28  |  Loop: scout
- Evidence: Wikipedia sign, "pronounced writing style shift": an abrupt change
  in tone, vocabulary, or approach within a single document. Not covered by
  patterns.md, which only evaluates a document against a single profile.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: In detect mode on a document (not a short post), check for
  register discontinuity between sections: one stretch markedly more polished,
  more hedged, or more Latinate than its neighbors. The seam between human and
  generated text is a stronger signal than either side alone. Detect-mode
  addition. Suggested P1.
- Mechanism guess: tooling artifact (partial-document generation)

### Fold-only proposals (no new rule; merge into an existing one)

- **Number texture** → fold into the open `metered-specificity` candidate. That
  entry covers distribution; detectors this round flagged *texture*. C1: "Real
  incident numbers are uglier (0.019, 8.3s, 41.7M)." C2 noted the arithmetic was
  engineered to close (3M into 40M is exactly the "under 8%" the story needs) and
  flagged "about 12,000 to 3.2 million" as a hedge welded to one-decimal
  precision. Add both as examples; do not file separately.
- **Invisible-heading copula** → fold into the open `subtext-vacuum` candidate.
  "The cause was a bulk import." / "The durable fix was..." C2: "outline-shaped
  prose with the outline still visible." Paragraphs that open by labeling their
  own function are the prose form of narrating communicative intent.
- **Hedged emotion labels** → fold into patterns.md content pattern 13
  (emotional flatline). "feeling something I would describe as smug", "what I
  can only describe as". Both D detectors flagged it. Same mechanism as claiming
  the feeling instead of earning it; add as a variant, not a new rule.
- **Payoff-promise hooks** → fold into patterns.md faux-insight setups. "Here's
  the kicker", "The best part?", "But here's the thing", "Here's the part most
  people miss", "Here's the breakdown." Publicly mocked ("no one says 'here's
  the kicker'... Everyone can tell I didn't write that",
  https://www.threads.com/@itslaurawall/post/DDxFsRIABXW), so Tier 1 within that
  rule. Distinguished from the existing entries only by position: these fire
  mid-piece rather than as an opener.
- **Structural over-formatting** → three Wikipedia signs, one existing rule.
  Widen patterns.md "excessive bullet lists" to list-and-table over-structuring
  (tables where prose belongs), and add heading-level skipping (H1 to H3) and
  section headers on a fixed cadence regardless of content. All formatting,
  same mechanism.

### em-dash-retier-evidence [status: proposed]

- Found: 2026-07-28  |  Loop: self-play (evidence for the open 2026-07-23 entry)
- Evidence: Across 4 samples written with the skill on, zero em dashes appeared,
  which is what the rule is for and therefore says nothing about model baseline
  frequency. The useful finding is the inverse: 3 of 8 detectors named em-dash
  *absence* as the first thing they checked and read it as evidence of a
  de-slopping pass. B2: "Surface hygiene is excellent... which is exactly the
  signature of AI text that has been passed through a de-slopping filter."
- Source: self-play round 2 detector reports (all samples)
- Proposed change: re-tier `em-dash` on the evidence that its diagnostic value
  has inverted, not merely faded. It no longer separates human from AI text; it
  separates unedited AI text from edited text of either origin. That is an
  argument for tiering it down from headline status, and it is a different
  argument than the one in the 2026-07-23 entry. A proper aging pass with
  rule-off generation is still needed to measure baseline frequency; this round
  cannot supply it. Next quarterly aging pass should generate with the em-dash
  rule explicitly disabled.
- Mechanism guess: n/a (aging; the ecosystem moved, not just the models)

### Round notes: generation-side misses (not candidates)

1. A binary contrast shipped again, in the technical sample: "Those statistics
   were not stale in the sense of being old. They were wrong about one value in
   a skewed column." Two detectors named it as the single most reliable AI
   fingerprint. Second consecutive round in which the FATAL family survived
   generation while being on the books. The rule is not the problem; two rounds
   of the same miss means the check needs to run as a discrete pass over the
   finished draft, not as an item in a list.
2. The technical sample contained a real causal inversion (see
   `locally-plausible-globally-incoherent`). Recording it as a miss, not as a
   pattern: the sample was wrong on the facts, and no rule in the skill would
   have caught it.
3. Detectors converged on a summary the skill should take seriously: the
   vocabulary layer is clean and the skeleton is not. Every decisive flag this
   round was structural. SKILL.md already ranks structure above vocabulary; the
   rule set does not yet reflect that ratio, and most of this round's survivors
   are structural.

## Round 2026-08-04 (weekly loop)

Harvest: 1 ledger entry (`2026-07-23-trimhero-gate-qt.md`, tweet). Fetch-back
FAILED for the second consecutive round. WebFetch on x.com returned HTTP 402
again (re-confirmed today), and the documented Grok Build fallback could not run:
the shell invocation required an approval that was not granted in this session.
No published text was retrieved and none was reconstructed. The ledger entry is
retained, not pruned, because fetch-back has still never been confirmed. No new
harvest candidates: the entry's ship-time record was already classified in the
2026-07-28 round, and re-reading the same record would only duplicate
`unnamed-attributor-social`, `fix-and-cta-close`, and `lineage-credit-signature`.
Note for the writer: two rounds blocked on the same approval means the fetch-back
path is effectively dead in a headless run. Either the Grok invocation gets a
standing allow, or `harvest.md` should demote fetch-back below the paste
fallback.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), skill fully
applied, no voice spec loaded. Topics were changed from the previous round to
avoid re-testing the same registers. Samples were held in-session rather than
written to a scratch file, because writes outside the repo were not permitted;
every span quoted below is reproduced verbatim from the sample text. 8 fresh-eyes
detectors, tool-free, given only the sample text and the weekly-loop prompt.
Verdicts: 6 of 8 called AI (70-80% confidence), 1 unsure leaning AI (60%), 1
human (88%, the casual sample). ~92 raw flags, ~30 distinct tells, 6 survivors
after dedup, plus 1 consolidation proposal and 6 fold-only proposals. 2 of 6
survivors tagged displacement, and the consolidation proposal is entirely
displacement-driven. As in the previous round, no detector rested a verdict on a
vocabulary tell.

Scout: last30days FAILED to execute for the third consecutive round (the skill
returned an error on invocation); fell back to WebSearch plus direct fetches.
Wikipedia signs-of-AI-writing re-fetched (59 signs enumerated, up from 58). The
round's highest-value find is The Economist's corpus study, which supplies the
quantitative em-dash evidence the two open aging entries asked for and could not
produce. Direct fetches of the Fast Company and Dataconomy write-ups both
returned HTTP 403, so the study's findings below are sourced from search-result
summaries and should be treated as paraphrase until the primary is read. 2
candidates plus 4 fold-only proposals; the rest deduped against the 2026-07-22
and 2026-07-28 batches.

Aging: SKIPPED. Not the first run of the quarter. Q3 2026 opened with the
2026-07-22 bootstrap round. One evidence entry is logged below against the open
`em-dash-retier` and `em-dash-retier-evidence` proposals.

### flat-syntactic-spine [status: proposed]

- Found: 2026-08-04  |  Loop: self-play + scout (cross-loop corroboration)
- Evidence: B1 on the blog sample: "No 'but,' no 'because,' no 'so,' no
  'however,' no semicolon, no dash, no parenthetical. Nearly all coordination is
  carried by 'and'... An essay whose whole engine is a reversal contains zero
  adversative conjunctions." B2 independently on the same sample: "'and' carries
  almost every join... Six coordinations, essentially no subordination variety.
  Flat syntactic spine under varied sentence lengths," and separately
  "Punctuation palette is period and comma only. No dash, semicolon, colon,
  parenthesis, or question mark in 21 sentences. That is not restraint, that is a
  rule being followed." Independently corroborated at corpus scale by The
  Economist, which found LLMs "used fewer commas, semicolons and parentheses than
  humans, and often produced long sentences while overusing the word 'and'," and
  concluded that "the clearest signs of AI-written text are verbosity and light
  use of punctuation."
- Source: self-play round 3 detector reports (sample B); The Economist corpus
  study (55,940 sentences / 1.2M words; its own articles plus NYT, Washington
  Post, and novels 1950-2022, against ChatGPT, Claude, Gemini, Grok), as reported
  by https://www.fastcompany.com/91584243/how-to-identify-ai-generated-writing-viral-report-has-surprising-new-clues-economist
  and https://dataconomy.com/2026/08/04/how-to-spot-ai-writing/ (both 403 on
  direct fetch; summaries only)
- Proposed rule: The headline candidate of the round, and the only one this
  quarter confirmed by two independent loops. Our rules vary sentence *length*
  and say nothing about sentence *architecture*, so the model satisfies them with
  a metronome-free surface over a uniform spine. Add a spine check to the
  monotony pass: count the joins. If coordination is carried almost entirely by
  "and", if no adversative ("but", "though", "except") or causal ("because",
  "since", "so") conjunction appears in a piece that argues a reversal, or if the
  punctuation palette is period-and-comma only across 15+ sentences, the rhythm
  was varied and the syntax was not. Suggested Tier 2, escalating to Tier 1 on
  long-form. Note the seam this opens: it is in direct tension with the em dash
  rule and the hedging rules, which both push toward a thinner punctuation
  palette. That tension is the point, and the writer should resolve it
  deliberately rather than let the two rules fight at runtime.
- Mechanism guess: displacement (the em-dash ban, the "vary rhythm" rule, and the
  cut-filler pressure all operate on length and on single marks; nothing in the
  skill asks what holds a sentence together, so the model economizes there)

### named-entity-vacuum [status: proposed]

- Found: 2026-08-04  |  Loop: self-play
- Evidence: The most widely flagged tell of the round: 5 detectors, 4 samples,
  and named the single strongest AI signal by two of them. A2 on the linkedin
  sample: "the specificity profile, quantities everywhere, proper nouns nowhere...
  Models generate texture through *counts* because a count is unfalsifiable in a
  way an invented product name is not. That asymmetry (numerically dense,
  nominally empty) is the tell." B1 on the blog sample: "All specificity is
  numeric or calendrical. There are no other proper nouns and no sensory detail
  whatsoever... An object kept daily for six years, described without a single
  physical property." B2, same sample: "it is never a Moleskine, a Hobonichi, a
  bullet journal... Systematic brand-avoidance is a strong generative
  fingerprint." C2 gave the most general form, on the technical sample:
  "Everything is one notch above concrete. 'a local-time constructor', not `new
  Date(y, m, d)`. No language, no framework, no test name, no assertion text, no
  date, no ticket, no colleague. The abstraction level is *uniformly* one step
  up." D2 noted the missing appliance brand and model number in a forum post that
  would normally lead with them.
- Source: self-play round 3 detector reports (samples A, B, C, D)
- Proposed rule: Distinct from the two open specificity candidates and it
  resolves both. `metered-specificity` covers the *rate* of specifics;
  `canonical-detail` covers whether a detail reads retrieved or observed; this
  covers the *kind*. Numbers, dates, and counts are cheap to generate because
  nothing can check them; named entities are expensive because they can be wrong.
  So generated prose comes out numerically dense and nominally empty, sitting
  uniformly one notch above the concreteness a participant would actually use.
  Test: count the proper nouns and the physical properties. If a piece is full of
  quantities and contains no brand, tool, product, place, person, or sensory
  property, the specificity is simulated. Where a real name cannot ship
  (anonymized employer, private client), say so, or use the physical detail
  instead of the count. Suggested Tier 2, escalating on narrative and incident
  registers. Anonymization is a genuine confound and this rule must not force
  invented names; flag the vacuum, do not fill it with fabrication.
- Mechanism guess: uncertainty-conditioning (a fabricated proper noun is a
  checkable error and training penalizes it; a fabricated count is not, so
  "be specific" resolves toward the safe half of specificity)

### performed-refusal [status: proposed]

- Found: 2026-08-04  |  Loop: self-play
- Evidence: Both blog detectors named it their top tell, independently. B2:
  "'There is a productivity argument I could make here about systems versus
  habits. I do not have one.' The densest tell in the piece. A person who has no
  productivity argument does not name the genre in order to decline it.
  Announcing the cliché you are refusing is what a model does when told to avoid
  neat lessons. It performs the refusal rather than simply not doing it." B1:
  "this is *the* signature humanization gambit of the current era: refusing the
  takeaway as the takeaway," and caught that the sentence does not survive
  scrutiny: "if you could make the argument, you have one... The sentence was
  optimized for the beat, not the referent." B2 also flagged the sibling shape,
  "What actually happened is that...", as "self-supplied setup, self-supplied
  knockdown."
- Source: self-play round 3 detector reports (sample B)
- Proposed rule: A pure displacement tell and the cleanest example the loop has
  produced. Do not name the conclusion you are declining to draw. Staging a
  cliché in order to refuse it is the same slot as drawing it, one move later,
  and it reads worse because the refusal has to be performed. Covers "There is a
  [X] argument I could make here. I do not have one", "I could tell you [tidy
  lesson], but", "This is where I am supposed to say", and the self-supplied
  setup-then-correction ("What actually happened is..."). If there is no lesson,
  write the last fact and stop. Suggested Tier 2. Flag for the writer: this rule
  and the open `scheduled-humility-beat` are both about a *slot* rather than a
  move, and they should probably be filed as one mechanism with two positions.
- Mechanism guess: displacement (the bans on generic conclusions,
  universalized-maxim closers, and fake-profound kickers remove the exit but not
  the expectation of one, so the model narrates the exit it is not taking)

### one-job-per-paragraph [status: proposed]

- Found: 2026-08-04  |  Loop: self-play + scout
- Evidence: 4 detectors, 3 samples, converging on a reconstructible beat outline.
  A1: "Rigid before/after scaffolding... That is a five-beat outline, and you can
  reconstruct it from the text." A2: "Five paragraphs, five template beats, no
  spill. Problem, new mechanism, third-party proof, metric plus reframe, risk
  plus humility. No paragraph does two jobs, none bleeds into the next, none
  digresses. Paragraph mass is banded tight at 31-49 words." D2 on the casual
  sample: "Paragraph architecture is a clean five-part essay... No paragraph does
  two jobs, no job is split across two paragraphs. Nothing is out of order,
  nothing is remembered late." D1, the one human verdict of the round, listed the
  same thing as the leading reason for its 12% of doubt. Scout corroboration: the
  LinkedIn Hook-Point-Action template is described as instantly recognizable to
  readers, and a May 2026 slop taxonomy lists "rigid outline structure" as its
  own category.
- Source: self-play round 3 detector reports (samples A, B, C, D);
  https://writewithai.substack.com/p/the-linkedin-hook-point-action-method and
  https://momenticmarketing.com/blog/avoid-ai-slop (item 18)
- Proposed rule: Distinct from `closed-loop-narrative-economy`, which is about
  details paying off; this is about *labor allocation*. When every paragraph
  discharges exactly one function and no function spans two paragraphs, the piece
  is an outline that got sentences. Test: try to reconstruct the outline from the
  finished text. If it comes back cleanly in one pass, the paragraphing is
  template-shaped. Fix by making one paragraph do two jobs, or splitting one job
  across a break, or remembering something late. Suggested Tier 2, blog and
  linkedin profiles hardest. Note the tension with ordinary good structure: this
  cannot be tiered so high that it punishes clear writing, which is why it is a
  reconstruct-test rather than a ban.
- Mechanism guess: instruction-tuning (plan-then-write and the outline-shaped
  training corpus both make the paragraph the unit of one idea; nothing in the
  skill asks whether the seams fall where the thinking actually turned)

### discourse-vocabulary-bleed [status: proposed]

- Found: 2026-08-04  |  Loop: self-play
- Evidence: Both linkedin detectors flagged the same two words, independently and
  with the same diagnosis. A1: "'confidently wrong', stock phrasing lifted
  straight from AI-safety discourse." A2: "register slip. 'Confidently wrong' is
  imported from how people talk about hallucinating LLMs, applied here to a
  spreadsheet export. The vocabulary of the discourse leaking into the anecdote."
  C1 flagged the technical-register sibling: "leaves the trap in place for
  whoever comes next" and "reintroduce the ambiguity" as diction from a register
  the surrounding prose is not written in.
- Source: self-play round 3 detector reports (samples A, C)
- Proposed rule: A new mechanism, not a new word list, and the only survivor this
  round that predicts rather than catalogs. The model's own discourse community
  has a vocabulary (confidently wrong, failure mode, load-bearing, surface area,
  guardrails, ground truth, alignment, context window, footgun, the happy path),
  and that vocabulary leaks into domains where nobody talks that way. It reads as
  register mismatch to anyone outside the community and as invisible to anyone
  inside it, which is why it survives self-review. Test: would a nonprofit
  program manager, a plumber, or a parent use this phrase about this subject? If
  the phrase belongs to AI, startup, or rationalist shop-talk and the subject
  does not, replace it. Suggested Tier 2. Distinct from the open
  `ai-native-pitch-vocab` candidate, which covers marketing copy pitching AI
  products; this covers the vocabulary bleeding into writing about anything else.
- Mechanism guess: pretraining-register (recency-weighted and heavily
  overrepresented in the fine-tuning and RLHF corpora relative to its share of
  ordinary English)

### citation-integrity [status: proposed]

- Found: 2026-08-04  |  Loop: scout
- Evidence: Seven Wikipedia signs form one uncovered cluster: broken external
  links, invalid DOIs and ISBNs, DOIs that resolve to unrelated articles, book
  citations with no page numbers or URLs, unconventional reference use, and named
  references declared but never used. `patterns.md` has no link-or-source
  integrity rule anywhere; the open `machine-reference-artifacts` candidate covers
  only pasted chat residue (oaicite, [cite: N], utm_source), not whether the
  citation points at anything real.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Proposed rule: Detect-mode addition, not a rewrite rule. On any text carrying
  links, citations, studies, or statistics, resolve them before shipping: a link
  that 404s, a DOI that lands somewhere else, a study cited without an author or
  year, or a statistic with no traceable source is a P0 credibility killer on
  outbound work. Same scope caveat the writer flagged on
  `locally-plausible-globally-incoherent`: this is a verification check wearing a
  slop-detector coat, and it may belong in a different skill. It is proposed here
  because the two share a mechanism and because an unresolvable citation is the
  single most expensive tell to ship on Kevin's byline. Flagging for the writer
  to decide scope; if it lands anywhere, it lands in detect mode.
- Mechanism guess: tooling artifact / hallucination (citation-shaped tokens are
  cheap to generate and the surrounding prose gives no signal that they were
  never resolved)

### Consolidation proposal: second-order uniformity (one rule, four checks)

- Found: 2026-08-04  |  Loop: self-play
- Evidence: Four open candidates and one new finding all describe the same thing,
  and this round's detectors flagged all four shapes in a single set of samples.
  (1) Terminal beat: "Every single paragraph closes on a punch... this is a
  drumbeat" (D2), 5-for-5 in three separate samples (A1, B1, D2), and C2 on the
  technical sample: "Not one paragraph trails off, runs long, or dumps a stray
  detail at the end." (2) Entry point: "Every paragraph opens subject-first,
  declarative, no connective. Seam monotony at the highest structural level"
  (B1). (3) Sentence cycle: "Burstiness is present but scheduled... The variance
  is decorative; the seams are metronomic" (B2); "short/long alternation in every
  paragraph, never two long sentences adjacent, never an unruly run. Real prose
  clumps. This alternates on schedule" (C1). (4) NEW, paragraph-internal contour:
  "Four of five paragraphs open with a short declarative and immediately expand
  into a long one... Raw sentence length varies well, but the *shape* repeats.
  That's monotony one level up from where slop detectors usually look" (A2);
  "Paragraphs 1, 3, and 4 are each exactly two sentences, and each is built the
  same way: short setup, longer elaboration" (C1).
- Source: self-play round 3 detector reports (all 4 samples); open candidates
  `punchline-terminal-paragraphs`, `paragraph-opener-monotony`,
  `periodic-long-short-alternation`, plus the new contour finding
- Proposed change: File these as ONE mechanism rule with four checks rather than
  four rules. The mechanism is identical in every case: the vary-rhythm
  instruction gets executed as a *schedule* instead of as noise, so the variation
  itself becomes the regularity. One rule, four things to audit after the seam
  pass, each on the piece as a whole rather than sentence by sentence: terminal
  beats, entry points, the sentence-length cycle, and the paragraph-internal
  contour. Suggested Tier 2. This is the fold the size budget asks for and it is
  the largest one available in the inbox: four proposals collapse to one, and the
  merged rule is easier to run than any of the four alone because it is a single
  end-to-end pass. Recommend filing this before any of the six new candidates
  above.
- Mechanism guess: displacement (SKILL.md's "three consecutive sentences match
  length? Break one" and "vary rhythm first" are both applied as procedures, and
  a procedure applied uniformly produces uniformity one level up)

### Fold-only proposals (no new rule; merge into an existing one)

- **Comparative demotion** -> add to the `patterns.md` binary-contrast table. "I
  care less about the hours than about what filled them." A1: "The reframe pivot:
  state the obvious metric, then demote it for the deeper one. Same family as
  'the real story isn't X, it's Y'." A2, independently: "The negate-and-pivot
  move, grammatically smoothed. Under it is 'It's not about the hours, it's about
  what filled them'." File alongside the open `rather-than-variant` and
  `matched-antithesis-pairs`; all three are the FATAL family with the negation
  dissolved into comparative or parallel syntax.
- **Anonymous validator** -> fold into the open `unnamed-attributor-social`
  candidate as its anecdote-register shape. A1: "an unnamed third party arrives
  to deliver the thesis in reported speech. No name, no context, no friction, and
  she is never mentioned again." A2 named the mechanism: "A flawless testimonial,
  paraphrased rather than quoted. Models paraphrase praise because a quote is a
  specific artifact to invent." That mechanism is the same one behind
  `named-entity-vacuum` above; file them so they cross-reference.
- **Labeled-takeaway seam** -> fold into `patterns.md` faux-insight setups as the
  understated variant. D1 and D2 both flagged "the annoying part is" as the
  strongest slop tell in an otherwise human-reading sample; D1: "the writer
  announces the moral compartment before delivering it. Cousin of 'the thing is'
  / 'here's the kicker'." The same shape appeared unprompted in a second sample
  ("which is the part I dislike", flagged by C1 and C2), so it is not
  register-specific. Existing entries cover the loud version ("Here's what nobody
  tells you"); this is the quiet one, and it survives precisely because it sounds
  modest.
- **Vapid openers** -> add to the `patterns.md` template / slot-fill table. "In
  today's rapidly evolving [anything]" is the most-cited AI opener in current
  coverage and does not appear anywhere in our rule library, which is a
  straightforward gap rather than a new finding. Same slot: "In an era of", "As
  the world becomes increasingly", "We live in a time where".
- **Verb inflation** -> frame the existing Tier tables with their mechanism and
  patch one gap. Current coverage lists the words (leverage, delve, utilize)
  without naming the move, which is that a plain verb gets swapped for a heavier
  one: use to leverage, make to craft, look into to delve, build to architect,
  help to empower. "Craft / crafted / crafting" is missing from both tiers and is
  now among the most-cited examples; add it to Tier 2.
- **"I hope this finds you well"** -> add to `patterns.md` chatbot artifacts,
  investor-email and outreach profiles. Our list has "I hope this helps" but not
  the email opener, which is now the single most publicly mocked AI tell in cold
  outreach. Same family, same fix: strip it.

### em-dash-retier-evidence-2 [status: proposed]

- Found: 2026-08-04  |  Loop: scout (evidence for the open 2026-07-23 and
  2026-07-28 aging entries)
- Evidence: The Economist compared 55,940 sentences and 1.2 million words of its
  own articles, New York Times and Washington Post writing, and novels published
  1950-2022 against ChatGPT, Claude, Gemini, and Grok generating the same
  articles. Reported findings: em dashes are no longer a reliable marker of AI
  writing; of the models tested **only Claude used em dashes more often than
  human writers**; ChatGPT now uses them less than any other model and less than
  humans do; and the clearest current signs are verbosity and light punctuation.
- Source: The Economist corpus study as reported by
  https://www.fastcompany.com/91584243/how-to-identify-ai-generated-writing-viral-report-has-surprising-new-clues-economist
  and https://dataconomy.com/2026/08/04/how-to-spot-ai-writing/. Both 403'd on
  direct fetch; findings are from search-result summaries and the primary should
  be read before filing.
- Proposed change: This is the population-level evidence both open aging entries
  asked for, and it argues **against** retiring the rule in this skill, which is
  the opposite of what those entries anticipated. The em dash has stopped being a
  reliable marker *of AI in general* while remaining a live signature *of Claude
  specifically*, and anti-slop runs on Claude. Recommend: keep the em-dash rule at
  full strength as a generation-side rule (it governs our own output, where the
  base rate is still elevated), and tier it DOWN as a detection-side signal (in
  detect mode on someone else's text, a lone em dash is now close to no evidence,
  and its absence is weak evidence of an editing pass, per the 2026-07-28 entry).
  That split resolves all three entries at once and is a smaller change than the
  retirement the earlier entries proposed. A rule-off generation pass is still
  the missing piece and remains queued for the Q4 aging round.
- Mechanism guess: n/a (aging; the population moved and the model-specific base
  rate did not)

### Round notes: generation-side misses and inbox state

1. The FATAL binary-contrast family survived generation for the **third**
   consecutive round, in two samples, in two new disguises: comparative demotion
   ("I care less about the hours than about what filled them") and always/never
   antithesis ("always on the same assertion, never on my machine"). C1 and C2
   both independently named a matched pair as among the strongest tells in the
   technical sample. The 2026-07-28 round already concluded that this check needs
   to run as a discrete pass over the finished draft rather than as a line item.
   Three rounds is enough evidence; that change should be made before the next
   loop, or the loop will keep reporting it.
2. The technical sample was **wrong again**, more comprehensively than last time.
   C1 and C2 independently reconstructed the timezone logic and found it
   inverted: on a UTC runner a local-time constructor and a UTC-derived label
   resolve to the same instant, so the described failure belongs to the laptop,
   not to CI, and the proposed `TZ=UTC` fix is a no-op on the machine that
   supposedly failed. Both also found that the stated failure rate ("about once a
   week") cannot be produced by the stated trigger (a six-hour window on one day
   a month), and both flagged the DST error (America/Chicago is UTC-5 for most of
   the year, so the band is five hours, not six). C2's framing is the useful one:
   "the numbers were generated for texture, not derived from the mechanism." This
   is the second consecutive round in which the technical sample was factually
   incoherent, which upgrades the open `locally-plausible-globally-incoherent`
   candidate from a one-round observation to a reproducible generation failure,
   and sharpens it: the check is not only causal direction but whether the
   quantitative claims survive being derived from the stated mechanism.
3. The one human verdict of the round (D1, 88% on the casual sample) again rested
   its call on mechanical imperfection: missing commas, a dropped subject, a
   hedged "maybe four seconds", an odd service-call number, and tangled syntax
   carrying real confusion. D2 read the *same* sample as 60% AI and cited "every
   apostrophe is correct and every comma is placed properly, with zero typos" as
   a stacking signal. Second consecutive round of inverse corroboration for the
   open `clean-mechanics-in-casual` candidate, from a fresh detector pair. That
   candidate carries a real gaming risk and should be tiered carefully, but the
   evidence for it is now two-for-two.
4. **Inbox state, and the reason it matters.** This round takes the inbox to
   roughly 40 open proposals across three rounds with zero filings. The size
   budget is ~40 rules in `patterns.md` and ~30 live corpus entries, so the
   inbox is now approximately the size of the entire rule set it feeds. That is
   not a backlog, it is a design problem: the loop is doing its job and the gate
   is the bottleneck, and an inbox this size will produce duplicate proposals
   because no round can hold all of it in attention. Two things would fix it, and
   the writer owns both. First, file the consolidation proposal above, which
   retires four entries for one. Second, consider a triage session that rejects
   in bulk rather than filing in bulk; rejected entries are dedup targets and
   cost nothing to keep, and a "no" is as valuable to the next round as a "yes".
   Until then, the loop is accumulating faster than the rule set can absorb,
   which is exactly the ratchet the size budget exists to prevent.

## Round 2026-08-11 (weekly loop)

Harvest: 1 ledger entry (`2026-07-23-trimhero-gate-qt.md`, tweet). Fetch-back
FAILED for the third consecutive round and the fourth time overall. WebFetch on
x.com returned HTTP 402 again (re-confirmed 2026-08-11), and the documented Grok
Build fallback could not run: the shell invocation was refused for want of an
approval this session could not grant. No published text was retrieved and none
was reconstructed. The ledger entry is retained, not pruned. No new harvest
candidates; the entry's ship-time record was classified in the 2026-07-28 round
and re-reading it would only duplicate `unnamed-attributor-social`,
`fix-and-cta-close`, and `lineage-credit-signature`. The 2026-08-04 note stands
and hardens: fetch-back is dead in a headless run. Either the Grok invocation
gets a standing allow in the repo's settings, or `harvest.md` should demote
fetch-back below the paste fallback and stop budgeting a step for it.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), skill fully
applied, no voice spec loaded. Topics changed again from the previous round.
Writes outside the repo were refused, so samples were held in-session rather than
saved to a scratch file; every span quoted below is verbatim from the sample
text. 8 fresh-eyes detectors, tool-free, given only the sample text. **The
verdict distribution inverted this round**: 3 of 8 called AI (65-72%), 1 unsure
leaning AI (60%), and 4 called human at 85-92%. Prior rounds ran 7-of-8 and
6-of-8 AI. ~88 raw flags, ~30 distinct tells, 3 survivors after dedup, plus 1
consolidation proposal and 3 fold-only proposals. Read the inversion with the
contamination caveat in round note 1 before treating it as progress.

Scout: last30days FAILED to execute for the fourth consecutive round (the skill
errored on invocation). Fell back to WebSearch plus direct fetches. Wikipedia
signs-of-AI-writing re-fetched: 59 signs, unchanged in count from 2026-08-04, with
two artifact families not in our coverage (Perplexity `attached_file`, unclassified
`:::writing`). The round's highest-value find is the Wired-sourced report on
writers deliberately performing human tells, which bears directly on what this
loop keeps proposing. A measured em-dash dataset also surfaced and closes out the
three open aging entries. 2 candidates, 1 fold-only, 1 evidence entry; the rest
deduped against the three prior batches.

Aging: SKIPPED. Not the first run of the quarter. Q3 2026 opened with the
2026-07-22 bootstrap round. The Q4 round is queued and now owes two specific
things: a rule-off generation pass for em-dash baseline frequency, and a re-test
of whether the humanization moves in round note 4 still read as human.

### uniform-hedge-per-number [status: proposed]

- Found: 2026-08-11  |  Loop: self-play
- Evidence: C2 named it the single strongest tell in the technical sample:
  "'**about** 90 seconds,' '**roughly** 3,400,' '**around** 900 requests,'
  '**about** 400ms,' '**roughly** 14,000'... Six numeric claims, six
  approximators, one each, never repeated in the same form. Real postmortems mix
  registers: some numbers come off a dashboard exact ('3,412 connection
  attempts'), some are eyeballed, some are stated flat with no hedge at all.
  Perfectly calibrated uncertainty distributed evenly across every figure is a
  model performing epistemic care, not a person reporting what their graphs
  said." C1 caught the inverse in the same sample: "'a great deal longer' is the
  one place the writer had a number available and didn't give one... The
  specificity budget runs out exactly where the causal argument needs support
  most."
- Source: self-play round 4 detector reports (sample C)
- Proposed rule: Distinct from the three open specificity candidates, which cover
  the rate (`metered-specificity`), the texture (`canonical-detail`), and the kind
  (`named-entity-vacuum`) of specifics. This one covers the *confidence marking*.
  A person's numbers carry uneven epistemic status because they came from
  different places: one off a dashboard, one from memory, one guessed. Uniform
  hedging flattens that, and the flatness is legible. Test: count the
  approximators. One per number, with the approximator rotated to avoid
  repetition, is a generated distribution. Some numbers should be exact and
  unhedged, and the hedge should be absent where the writer actually knew.
  Additional check from C1: if the piece hedges everywhere and then goes vague at
  exactly the load-bearing claim, the hedging is decoration and the vagueness is
  the real signal. Suggested Tier 2, escalating on incident and technical
  registers. File alongside the three specificity candidates as one family.
- Mechanism guess: displacement (the excessive-hedging ban and the be-specific
  pressure resolve into "hedge each number exactly once," and the synonym-cycling
  rule then rotates the approximator, which is what produces the giveaway
  regularity)

### monotonic-recall-order [status: proposed]

- Found: 2026-08-11  |  Loop: self-play
- Evidence: D2 on the casual sample: "every seam advances the clock by one step.
  There is no doubling back, no 'oh also,' no reordering of memory. The timeline
  is monotonic. People narrate repairs out of order because that's how it comes
  back to them." Inversely corroborated by two detectors reading the *same*
  structural feature where it was absent: D1 named the out-of-order tail its
  fourth-strongest human signal, "the last two paragraphs are afterthoughts
  stapled on after the advice paragraph, the natural closer... The out-of-order
  tail is a person remembering things." A1 on the linkedin sample listed
  paragraph asymmetry and the missing establishing shot as its lead human
  evidence.
- Source: self-play round 4 detector reports (samples A, D)
- Proposed rule: Narrative order should not equal chronological order. Recalled
  events arrive out of sequence: something gets remembered late, an aside
  interrupts, a fact from step two shows up after step four because that is when
  the writer thought of it. Prose whose timeline advances one step per seam with
  no backtracking was planned, not remembered. Distinct from
  `one-job-per-paragraph` (labor allocation) and `closed-loop-narrative-economy`
  (whether details pay off); this is about sequence. Test: is there anything in
  the piece that arrives later than it happened? Suggested Tier 2, narrative and
  incident registers. Guard: this must not license artificial scrambling, which
  would read worse than the monotone. One genuine late arrival is the target.
- Mechanism guess: displacement (plan-then-write produces an ordered outline, and
  every structural rule in the skill operates within that order rather than on it)

### reply-shaped-registers [status: proposed]

- Found: 2026-08-11  |  Loop: self-play
- Evidence: D2 led its AI verdict with genre shape rather than prose: "The
  five-paragraph arc is too complete. Purchase, symptom and diagnosis, fix,
  lesson, follow-up. That is a story, not a post. Real forum writing is a fragment
  of a conversation: it replies to someone, asks something, trails off, or comes
  back edited. This has no thread context, no question, no addressee, and no loose
  ends. It resolves." The same detector flagged the advice line as "an extractable
  lesson, delivered in generalized second person, placed exactly where a takeaway
  goes," and read "anyway" as "doing the work of a transition word while
  pretending to be a shrug."
- Source: self-play round 4 detector reports (sample D)
- Proposed rule: Casual and social surfaces are conversational turns, not
  standalone compositions. A forum post, a reply, a group-chat message, or a
  comment usually answers something, addresses someone, asks a question back, or
  stops without resolving. Generating a complete self-contained arc on a surface
  where nobody writes complete self-contained arcs is a genre error that survives
  every prose-level check. This is the first candidate the loop has produced that
  operates above the paragraph. Suggested Tier 2 in the casual profile, and worth
  a line in the context-profile matrix rather than the pattern list, since the
  correction is profile-specific. Related to the open `fix-and-cta-close` and
  `universalized-maxim-closer`: on a reply surface, having an ending at all is
  part of the tell.
- Mechanism guess: instruction-tuning (a prompt asking for a post produces a
  document, because documents are what the assistant format emits, and the
  register instruction only changes the diction inside it)

### Consolidation proposal: single-axis humanization (one rule, absorbs three)

- Found: 2026-08-11  |  Loop: self-play
- Evidence: Three open candidates and two new findings describe one failure. D2 on
  the casual sample gave the clearest statement: "Lowercase 'i' throughout, no
  capitalized sentence starts... But underneath it: zero typos, zero autocorrect
  artifacts, zero self-correction, correct apostrophes, correct comma placement...
  Casing is the *only* register that was lowered. Genuine casual typing degrades
  on several axes at once; this degrades on exactly one, uniformly, which reads as
  a style filter applied over clean prose." C1 and C2 found the same shape in a
  different register and a different axis, independently: C2, "'Our pricing
  endpoint **fell over**' is the single piece of engineer-slang in the piece,
  placed in sentence one where it does maximum work. Three sentences later: 'Under
  900 copies of itself it takes **a great deal longer**.' No engineer who says
  'fell over' says 'a great deal longer'... That collision of registers is the
  seam where the humanizing pass got bolted onto formal underlying prose." C1:
  "Register seam. The piece opens with 'fell over' and then reaches for 'a great
  deal longer,' which is stiff and formal. Two different voices, three paragraphs
  apart."
- Source: self-play round 4 detector reports (samples C, D); open candidates
  `clean-mechanics-in-casual`, `strategic-de-contraction`, `lone-flourish`
- Proposed change: File as ONE rule and retire three. The mechanism is identical
  in all five observations: a humanization instruction gets applied as a single
  uniform transform on one dimension while every other dimension keeps the
  assistant default. Lowercase but perfect punctuation. One slang verb over formal
  syntax. One figurative word in flat diction. Contractions everywhere except the
  punchlines. The tell is never the informality; it is that the informality has
  exactly one axis and no variance on it. Check: name the axis the piece is being
  informal on, then ask what the other axes are doing. If they are all clean, the
  register is a filter. Suggested Tier 2, casual and linkedin profiles hardest.
  This absorbs `clean-mechanics-in-casual` (mechanics axis),
  `strategic-de-contraction` (contraction axis, already superseded once by
  `contraction-register-mismatch`), and `lone-flourish` (diction axis, previously
  recommended for rejection on contested single-round evidence; it survives as an
  instance of a mechanism even though it fails as a rule of its own). Three
  retirements for one filing, which is the largest fold available after the
  2026-08-04 second-order-uniformity proposal. Recommend filing both before any
  new candidate.
- Mechanism guess: displacement (register instructions are executed as
  find-and-replace on the most legible surface feature, and uniformity on that
  feature is what gets detected)

### counterculture-signature [status: proposed]

- Found: 2026-08-11  |  Loop: scout
- Evidence: Reporting on an "anti-AI literary counterculture," dated 2026-07-29 and
  citing Wired coverage from 2026-07-28. Writers are deliberately performing human
  authorship: avoiding em dashes and replacing them with parentheses, forcing
  sentence-length variance ("some 3-word hitters and some 50-word runs" against the
  LLM default 15-25), introducing intentional typos ("teh" for "the"), contracting
  heavily, and breaking the 3-5 sentence paragraph. A novelist quoted names the
  problem directly: "I'm building my defense on patterns that will be obsolete in
  six months." The list is close to a description of this skill's rewrite pass.
- Source: https://www.machinebrief.com/news/writers-anti-ai-literary-counterculture-typos-fewer-em-dashes-human-writing-july-2026
  (reporting on Wired, 2026-07-28; the Wired original was not fetched directly, so
  treat the specifics as secondary)
- Proposed rule: Not a pattern to flag in prose. A methodology entry for SKILL.md
  or the over-polishing warning, and the most consequential scout find the loop has
  made. The moves this skill prescribes are now a publicly catalogued performance
  of humanity, which means they are becoming detectable *as* a performance rather
  than reading as human. Round note 4 below is the internal evidence for the same
  thing. Two concrete consequences. First, the standing guidance in
  `clean-mechanics-in-casual` (do not manufacture typos) is now doubly correct, and
  the reason should be recorded: manufactured imperfection is a described
  convention, not a signature. Second, the skill's stated goal should be restated
  as removing tells rather than adding human markers, because the marker set has a
  half-life measured in months and the loop should not be in the business of
  chasing it. Suggested filing: a paragraph in the over-polishing warning, no new
  tier.
- Mechanism guess: n/a (ecosystem; the detection game moved)

### forced-parable [status: proposed]

- Found: 2026-08-11  |  Loop: scout
- Evidence: A 2026 catalog of the LinkedIn slop backlash names "forced parables,"
  small mundane events paired with oversized business takeaways, alongside the
  cadence "Short line. Then another. Building to a lesson." The same source names
  "It's not X, it's Y" as "the one people name first, every time," which is already
  our FATAL family.
- Source: https://www.hiration.com/blog/ai-slop-linkedin/ (corroborated by the
  October 2025 field guide at https://www.ignorance.ai/p/the-field-guide-to-ai-slop,
  which lists "unearned profundity transitions" and "generic, plausible but hollow
  analogies")
- Proposed rule: Whole-piece structure, distinct from the fake-profound kicker,
  which is a closing line. Here the entire piece exists to convert a small concrete
  incident into a disproportionate general lesson, and every detail is selected
  backward from the lesson. Test: strip the takeaway and ask whether the anecdote
  was worth telling. If it was not, the anecdote was manufactured as a delivery
  vehicle. Suggested Tier 2, linkedin profile hardest. File with the exit-shape
  merge already proposed in `fix-and-cta-close`: that entry covers three ways out
  of a piece, and this covers the case where the exit was the reason for the piece.
- Mechanism guess: reward-tuning (engagement-optimized social corpora, where the
  parable form outperforms the report form)

### Fold-only proposals (no new rule; merge into an existing one)

- **Inverse emotional flatline** -> fold into `patterns.md` content pattern 13.
  That entry covers *claiming* a feeling instead of earning it. D2 caught the other
  half: "He bought a broken freezer off a stranger who misrepresented it, lost the
  top layer of his food, and spent two weeks chasing it. There is no irritation, no
  jab at the seller, no mention of what thawed. Sentiment sits at neutral for the
  whole piece. This is the most common invisible failure in synthetic first-person:
  the events imply an emotion the text never carries." Same rule, opposite failure;
  add as a second variant so the check runs both directions.
- **Humor on a schedule** -> fold into the open 2026-08-04 consolidation proposal
  (second-order uniformity) as a fifth check. D2: "Two humor beats, both appended
  to the tail of a clause, both dry understatement, both self-deprecating in the
  same register. That is one comic device deployed twice on a schedule. Human posts
  are funnier in bursts or not at all." The mechanism is the one that proposal
  already names: a device distributed evenly instead of clustered. Device
  distribution joins terminal beats, entry points, the sentence cycle, and the
  paragraph contour.
- **Solution-name-without-mechanism** -> sharpens the open
  `locally-plausible-globally-incoherent` candidate; do not file separately. C1's
  strongest tell: the fix "names the right technique but omits the mechanism that
  would make it possible, serving a 'stale value' from a key that, by the
  document's own account, no longer exists... that gap is what it looks like when
  text is assembled from the shape of a correct answer rather than from the system
  it describes." C2 found the same gap independently. The candidate now has three
  distinct failure signatures across three rounds: inverted causal direction
  (2026-07-28), quantities not derivable from the stated mechanism (2026-08-04),
  and canonical-fix vocabulary without the mechanism that licenses it (this round).
- **Perplexity and unclassified markup** -> add to the open
  `machine-reference-artifacts` candidate. The Wikipedia page lists `attached_file`
  (Perplexity) and an unclassified `:::writing` marker alongside the oaicite,
  `[cite: 1]`, `grok_card`, and lenticular-bracket families already captured there.
  Same rule, two more examples.

### em-dash-retier-evidence-3 [status: proposed]

- Found: 2026-08-11  |  Loop: scout (evidence for the open 2026-07-23, 2026-07-28,
  and 2026-08-04 aging entries)
- Evidence: A measured dash-density dataset, reported per model against a human
  control: GPT-4.1 at 10.62 per 1,000 words, Claude Opus 4.6 at 9.09, DeepSeek V3
  at 6.95, Gemini 2.5 Pro at 3.53, Llama 3.1 at 0.00, against a stated human
  baseline of 3.23 and a pooled classic-literature figure of 6.43 across 702,939
  words (Twain 10.13, Melville 8.12, Thoreau 4.27, Dickens and Austen 3.47-5.33).
  The site's own conclusion: the em dash is "a weak signal, not a fingerprint,"
  with considerable human overlap, particularly among 19th-century novelists.
- Source: https://slopdetector.org/blog/em-dash-ai-tell-data, reporting Freeburg's
  2026 controlled study. Two caveats the writer should weigh: the publisher sells
  detection, so the framing is not disinterested, and the primary study was not
  read. The measured model is Opus 4.6, not the current generation, so the
  Claude-specific figure is a lower bound on staleness rather than a current rate.
- Proposed change: **Close all three open em-dash entries with the 2026-08-04
  split, now quantified.** Claude at 9.09 sits at roughly 2.8x the study's human
  control and above every model except GPT-4.1, which independently confirms The
  Economist's finding that Claude is the one model still elevated. That is the
  case for keeping the em-dash rule at full strength generation-side, since this
  skill governs Claude's own output. The overlap with human literary prose at
  6.43 pooled, and Twain at 10.13 exceeding every model measured, is the case for
  tiering it down detection-side, since a lone em dash in someone else's text is
  now close to no evidence. No further evidence gathering is needed on the
  population question; what remains for the Q4 aging round is only the rule-off
  generation pass to measure our own current base rate. Recommend the writer close
  `em-dash-retier`, `em-dash-retier-evidence`, and `em-dash-retier-evidence-2` in
  one commit with the split filing.
- Mechanism guess: n/a (aging; resolved)

### Round notes: methodology, misses, and inbox state

1. **The verdict inversion is confounded, and the confound is the loop's own
   design.** Four of eight detectors called these samples human, against 1 of 8 and
   1 of 8 in the two prior rounds. That looks like the floor improving. It is not
   evidence of that. The generating context for this round held the full inbox,
   roughly 45 open candidates, before a word was written, so the samples were
   written against findings the skill has not filed and does not contain. The round
   measures the inbox, not the floor. This is a defect in `weekly-loop.md` step 1:
   it says to apply "this skill in full" while the generating session has
   necessarily just read `candidates.md` to do the dedup. The fix is an ordering
   change, and it should be made before the next run: generate the samples FIRST,
   in a subagent that has read only `SKILL.md`, `patterns.md`, and
   `living-corpus.md`, then read the inbox to dedup. Until that lands, treat
   cross-round verdict comparisons as unusable.
2. **The FATAL binary-contrast family survived generation for the fourth
   consecutive round.** C1 and C2 both flagged "Redis was healthy the whole time.
   Postgres was not:" and C1 named it explicitly: "negate-then-correct, the
   antithetical pair where a clean negative sets up the reveal. It's the single
   most recognizable LLM rhythm after the em dash, just wearing a colon instead."
   That is also a hit on the `anti-em-dash displacement` corpus entry, which
   predicted exactly this migration into colons. Four rounds. The 2026-07-28 round
   proposed the fix (run the check as a discrete pass over the finished draft), the
   2026-08-04 round repeated it, and it has not been made. The loop will keep
   reporting this every week until it is.
3. **The technical sample was wrong for the third consecutive round**, and the
   errors were again found independently by both detectors on that sample. C1 and
   C2 each caught that 900 requests per second across a 400ms window is 360
   requests and not 900; each caught that a value cannot be served stale from a key
   the piece says expired; each caught that a 240-connection peak against a pool
   sized for 200 contradicts the severity framing it is offered to resolve. C2's
   summary is the durable one: "The piece performs measurement everywhere and does
   measurement nowhere." Three-for-three across three different topics means this
   is not sample variance. Two things follow. The narrower one is the sharpening
   folded into `locally-plausible-globally-incoherent` above. The broader one is a
   question for the writer that the loop cannot answer: the self-play step keeps
   producing factually incoherent technical prose, and no rule in this skill
   addresses it, so either the check belongs here or the samples should stop being
   incident writeups.
4. **The humanization moves this loop keeps proposing are now being flagged as
   tells, by the same detector pool, in the same round.** D1 named the garage-light
   aside its single strongest human signal: "an unresolved, unflattering,
   load-bearing-in-no-way detail." D2 read the identical span as "manufactured
   incidental texture: irrelevant, mildly embarrassing, memorable. It is what
   'sounds authentic' looks like when it is being aimed at." Same sentence,
   opposite verdicts, from readers given the same prompt. The pattern repeats
   across the round: A1 and B1 cited the refused conclusion and the withheld
   explanation as decisive human evidence, while A2 read the same distribution of
   authenticity markers as "a checklist distributed evenly, not memory recalled
   unevenly." Combined with the `counterculture-signature` find above, this is the
   loop reporting its own limit. Every humanizing move it proposes has a
   detectable-as-performance twin, and the difference between them is whether the
   detail was actually observed, which no rule can supply. The writer should weigh
   this before filing any further candidate whose instruction is "add a human
   marker" rather than "remove a machine one." `canonical-detail` already carries
   the right formulation; the rest of the inbox does not.
5. **Inbox state.** This round adds 5 candidates, 1 consolidation, 4 fold-only
   proposals, and 1 evidence entry, taking the inbox past 45 open proposals across
   four rounds with zero filings. The 2026-08-04 note called this a design problem
   and it has not changed. Two consolidations are now queued that retire seven
   entries between them, and one aging thread is ready to close three. The cheapest
   next action for the writer is not triage of the whole inbox: it is filing the
   two consolidations and closing the em-dash thread, which alone would take the
   inbox down by ten entries and would resolve the only threads with evidence from
   three or four independent rounds. Round note 1 is the second cheapest, and it is
   the one that makes the next round's data trustworthy.

## Round 2026-08-18 (weekly loop)

Harvest: 1 ledger entry (`2026-07-23-trimhero-gate-qt.md`, tweet). Fetch-back
FAILED for the fourth consecutive round. WebFetch on x.com returned HTTP 402
again (re-confirmed 2026-08-18). The documented Grok Build fallback was
**attempted for the first time this round** rather than skipped: the binary is
present at `~/.grok/bin/grok`, and two invocations were refused for want of a
permission this session could not grant. That narrows the diagnosis the previous
three rounds could not: the fallback is not missing, it is not allowlisted. No
published text was retrieved and none was reconstructed. Ledger entry retained,
not pruned. No new harvest candidates; the entry was classified in the 2026-07-28
round and re-reading it would only duplicate `unnamed-attributor-social`,
`fix-and-cta-close`, and `lineage-credit-signature`. The fix is now one line: add
`/Users/kevinmagnan/.grok/bin/grok` to the repo's allowed Bash commands, or
demote fetch-back below the paste fallback in `harvest.md` and stop budgeting a
step for it.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), fresh topics.
**The 2026-08-11 round-note-1 methodology fix was applied this round**: each
sample was written by an isolated subagent instructed to read only `SKILL.md`,
`patterns.md`, and `living-corpus.md`, and explicitly forbidden to open
`candidates.md`. This is the first round whose samples measure the floor rather
than the inbox. 8 fresh-eyes detectors, tool-free, given only the sample text.
Verdicts: 3 of 8 called AI (68-78%), 5 called human (60-93%). ~59 raw flags, ~22
distinct tells, 3 survivors after dedup plus 6 fold-only proposals. Read round
note 1 before comparing this round's verdict split to any prior round, and round
note 2 before reading the technical sample's result at all.

Scout: last30days FAILED to execute for the fifth consecutive round (the skill
errored on invocation). Fell back to WebSearch plus direct fetches. Wikipedia
signs-of-AI-writing re-fetched: **61 signs, up from 59**, and the page now
carries an explicit "historical indicators" section retiring four tells, which is
a finding about method rather than about prose. A direct fetch of
slopdetector.org's threshold table succeeded and supplies measured numbers for
rules we already carry unquantified. 2 candidates, 3 fold-only proposals; the
rest deduped against the four prior batches.

Aging: SKIPPED. Not the first run of the quarter. Q3 2026 opened with the
2026-07-22 bootstrap round. The Q4 round is queued and owes three things: the
rule-off generation pass for em-dash baseline frequency, a re-test of whether the
humanization moves still read as human, and a decision on the retirement-marking
proposal filed below.

### isolated-turn-paragraph [status: proposed]

- Found: 2026-08-18  |  Loop: self-play
- Evidence: Both blog detectors named the same span, independently, and both read
  it as architecture rather than memory. B1 on "Somewhere in week seven I noticed
  I had drifted past the painted line without deciding to": "One sentence, its own
  paragraph, load-bearing, callback to the opening image. That's an architectural
  decision, not a memory surfacing." B2, same span: "Isolating the emotional turn
  in its own short paragraph is a very common AI rhythm trick to signal 'this is
  the moment' - competent, but formulaic."
- Source: self-play round 5 detector reports (sample B)
- Proposed rule: Distinct from the open second-order-uniformity consolidation,
  which audits contour across the whole piece, and from the existing dramatic
  fragmentation rule, which is about sentence shape. This is one specific slot: a
  single-sentence paragraph placed at the narrative pivot, carrying the
  realization, usually with a callback to the opening image. The isolation is
  doing the emphasis work that the em dash and the punchy vocabulary used to do.
  Test: if the piece has exactly one one-sentence paragraph and it is the turn,
  the paragraphing was staged. Put the realization inside the paragraph that
  earned it, or put a one-sentence paragraph somewhere that is not the turn.
  Suggested Tier 3, blog and linkedin profiles. Tiered low deliberately: the
  one-sentence paragraph is also a real and common human move, and the tell is the
  coincidence of isolation with the pivot, not the isolation itself.
- Mechanism guess: displacement (with em dashes, colon reveals, and punchy
  diction all banned, emphasis routes into whitespace, which no rule in the skill
  currently examines)

### unsolicited-validation [status: proposed]

- Found: 2026-08-18  |  Loop: scout
- Evidence: "AI writing tools frequently switch into unsolicited validation with
  phrases like 'You're not imagining it,' 'You're not alone,' or 'You're not
  broken.' These reassurances make sense in a therapy context but feel bizarre in
  a business article about pricing strategies or a LinkedIn post about
  productivity." Reported as observed across multiple LLMs by Reddit users. Not
  present anywhere in `patterns.md` and not in the inbox after four rounds, which
  makes it a straightforward coverage gap rather than a subtle finding.
- Source: https://www.forbes.com/sites/jodiecook/2026/02/03/the-15-new-giveaway-signs-of-ai-generated-content-in-february-2026/
  (via WebSearch summary; the Forbes page was not fetched directly, so treat the
  quoted phrasing as paraphrase). The same catalog family supplied the already-open
  `anglo-weight-words` candidate from its May 2026 update.
- Proposed rule: Flag second-person reassurance addressed to the reader's
  emotional state when nobody asked: "You're not imagining it", "You're not
  alone", "You're not broken", "It's okay to feel", "That frustration is valid".
  Cut entirely; the content should inform or argue, not console. Suggested Tier 1
  phrase family under communication/filler patterns, sibling of sycophancy, which
  covers flattery aimed at the interlocutor while this covers comfort aimed at the
  reader. Note the seam with the existing `patterns.md` sycophancy entry: they are
  the same mechanism pointed at two different targets and could file as one rule
  with two lists.
- Mechanism guess: reward-tuning (RLHF rewards emotional attunement in dialogue,
  and the register survives into prose where there is no interlocutor to attune to)

### explicit-retirement-marking [status: proposed]

- Found: 2026-08-18  |  Loop: scout (methodology, for the aging step)
- Evidence: The Wikipedia signs page has grown to 61 signs and now separates a
  "historical indicators" group that is explicitly aged out rather than deleted:
  didactic disclaimers, standalone section summaries, prompt refusal, and abrupt
  mid-sentence cutoffs, each scoped to roughly November 2022 through 2024. The
  page keeps them visible and dated instead of removing them.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing (fetched
  2026-08-18; 61 signs, up from 59 on 2026-08-11 and 58 on 2026-08-04)
- Proposed change: Adopt the same convention in `living-corpus.md`. Step 4 of
  `weekly-loop.md` says to "propose retire or re-tier" but does not say what
  retirement looks like on disk, and a deleted entry loses the thing the corpus
  exists to record, which is how fast a tell rose and fell. Proposal: retirement
  moves an entry to a dated "retired" section with the evidence that killed it,
  rather than removing it. Two concrete benefits. It keeps retired tells as dedup
  targets, the same argument the inbox already makes for keeping rejected
  candidates. And it makes the aging pass cheap to audit, because the corpus then
  carries its own history instead of requiring a git archaeology run. Costs one
  heading in `living-corpus.md` and one sentence in `weekly-loop.md` step 4. This
  is the first entry the loop has proposed against the aging step's own
  machinery rather than against a tell.
- Mechanism guess: n/a (methodology)

### Fold-only proposals (no new rule; merge into an existing one)

- **Measured thresholds for existing structural rules** -> fold into the open
  2026-08-04 `cluster-threshold` candidate, which proposed a density gate and had
  no numbers to put in it. A threshold table fetched directly this round supplies
  them: burstiness, defined as standard deviation of sentence length divided by
  mean, with a human range of 0.6-1.2, AI output at 0.2-0.4, and a flag below 0.4;
  transition-word stacking at more than half of paragraphs opening on a formal
  connector; rule-of-three at more than one polished triplet per 200 words; the
  "not just X, it's Y" contrast tic at three or more per article; style words at 3
  per 500 words when clustered. Our `patterns.md` sentence-uniformity rule is our
  single most important structural check and currently ships with a read-aloud
  test and no number. Caveat the writer should weigh: the publisher sells
  detection, so the framing is not disinterested, and the underlying studies were
  not read. Source: https://slopdetector.org/blog/signs-of-ai-writing
- **The restatement test** -> fold into the open `treadmill-paragraphs` candidate
  as its measurable form. Same source names it the most reliable single sign and
  the hardest to fake: after reading, try to name one concrete fact per paragraph,
  a name, number, date, or trade-off. More than half the paragraphs failing is the
  threshold. `treadmill-paragraphs` currently proposes a delete-test, which asks
  whether a paragraph can go; this asks what it deposited, which is the same check
  run forward instead of backward and is easier to apply.
- **Clean-ratio metric pairs** -> fold into the 2026-08-04 "number texture"
  proposal, which already sits under `metered-specificity`. A1 on "eleven hours
  instead of the forty we used to spend": "'Eleven' and 'forty' are the kind of
  numbers that feel specific but are actually a clean ~4x. Compare a real one:
  'somewhere around twelve, thirteen hours.'" Second round in which a detector
  independently caught arithmetic engineered to resolve; the 2026-08-04 instance
  was "3M into 40M is exactly the 'under 8%' the story needs." Add before/after
  metric pairs that reduce to a round multiple as a named example.
- **The still-flawed-but-changed closer** -> fold into the open `fix-and-cta-close`
  exit-shape merge as a fourth door. B1 named it the default resolution shape and
  quoted the mechanism: "'But I go on Tuesdays and Thursdays at 6 a.m., **and** the
  woman who does the water aerobics... **and** I can swim the length of the pool.'
  Three and-clauses escalating to the emotional payoff, preceded by a concessive
  'I'm still slow.'" That entry already proposes merging three exits into one
  mechanism rule; this is the narrative register's version, and it is the one that
  survives a ban on maxims and CTAs because it looks like honesty.
- **False connective entailment** -> sharpens the open
  `locally-plausible-globally-incoherent` candidate; do not file separately. C1 on
  "no write endpoints were cacheable, so nobody could act as anybody else": "the
  reason nobody could impersonate anyone is that no session tokens leaked, which
  was already stated... so the 'so' welds two facts into one conclusion they don't
  jointly support. This is the kind of confident-connector overreach LLMs make."
  Both facts are true and the connector between them is not earned. That is a
  fourth signature for that candidate, and the cheapest to check: audit every
  "so", "which means", and "because" and ask whether the left side actually
  entails the right. Prior signatures were inverted causal direction (2026-07-28),
  quantities not derivable from the mechanism (2026-08-04), and canonical-fix
  vocabulary without the licensing mechanism (2026-08-11).
- **Collaborative-communication register** -> add to `patterns.md` chatbot
  artifacts. Wikipedia sign 43, "we should consider" and other direct-to-reader
  collaborative phrasing carried out of a chat turn into standalone prose. Our
  chatbot-artifact list covers the openers and closers ("I hope this helps",
  "Feel free to reach out") but not the deliberative first-person-plural that
  appears mid-document. Same family, one more example.

### Round notes: methodology, misses, and inbox state

1. **The verdict inversion survived the methodology fix, which changes what it
   means.** The 2026-08-11 round called its 4-of-8 human split confounded, because
   the generating context had read the full inbox before writing. That fix was
   applied this round: four isolated subagents, corpus files only, `candidates.md`
   withheld. The result was 5 of 8 human, 3 of 8 AI. So the effect was not the
   contamination artifact the previous round suspected, and the honest reading is
   that the floor as currently written now clears roughly half of a fresh-eyes
   detector pool on its own. That is the first clean measurement the loop has
   produced, and it is one data point. Two caveats before anyone treats it as a
   trend. The detector pool is not fixed across rounds, so verdict rates carry
   detector variance as well as sample variance. And a rising human-verdict rate
   is exactly what `counterculture-signature` predicts would decay fastest, since
   the moves being rewarded are now publicly catalogued. Keep the isolated-generator
   protocol; it should be written into `weekly-loop.md` step 1 rather than
   re-derived each round.
2. **The technical sample was factually coherent this round, and the result is
   confounded by a protocol deviation this loop introduced.** The three prior
   rounds each produced a technically incoherent incident writeup, and the
   2026-08-11 notes asked the writer whether that belonged in this skill at all.
   This round the generator prompt for the technical sample carried an extra
   instruction not given to the other three: that every quantitative claim must
   follow from the described mechanism, with the arithmetic and causal direction
   checked before finishing. Both detectors then independently verified the piece
   and found it sound. C1 checked the request-to-account ratio, the per-POP victim
   bound, and the mapping of each fix to its failure mode, and concluded "the
   failure of AI-generated incident writeups is usually here... This one survives
   all three checks." C2 independently confirmed the causal ordering of the
   stripped `Vary` header. That is a useful finding, but it is not evidence the
   floor improved: it is evidence that an explicit coherence instruction fixes a
   failure the floor does not address, which is closer to an argument for filing
   the check than against it. Recording the deviation plainly because the loop's
   value depends on its samples being comparable, and this one was not. Next round
   should either give all four samples the instruction or none.
3. **The FATAL binary-contrast family survived generation for the fifth
   consecutive round.** A1 led its verdict with "were reconstructed, not recorded"
   in the very first sentence and called it "the single most reliable LLM tell",
   then caught the same move four sentences later in "So we rebuilt it. Not with
   software." A2 independently counted four instances in one 250-word post. B1
   found the narrative-costume version in the blog sample: "'That's a tidy story.
   The truer version is...' - the negate-then-correct move in narrative costume."
   The 2026-07-28 round proposed the fix (run the check as a discrete pass over
   the finished draft rather than as a line item), 2026-08-04 repeated it,
   2026-08-11 repeated it. It has not been made. Five rounds, four of them with
   the family appearing in the opening sentence of a sample. This is now the
   longest-running unactioned finding in the inbox and it will appear again next
   week.
4. **Same-span disagreement recurred with a fresh detector pair, for the second
   consecutive round.** On the casual sample, D1 named "came home from work, still
   full, lid up, raccoon situation" among its strongest human signals:
   "Predicate-dropped asyndeton... Models do not drop predicates like this; they
   resolve every clause." D2 read the identical span as manufactured: "build a
   normal sentence, then bolt on a punchy noun-phrase fragment for 'voice'. It
   reads like a writer imitating casualness rather than being casual." Same
   sentence, opposite verdicts, same prompt. The 2026-08-11 round found this on
   the garage-light aside and drew the conclusion the loop should keep: every
   humanizing move has a detectable-as-performance twin, and what separates them
   is whether the detail was observed, which no rule can supply. Two rounds of
   independent reproduction moves that from an observation to a constraint on what
   this skill can file. It is the strongest argument in the inbox for
   `counterculture-signature` and against any future candidate whose instruction
   is "add a human marker."
5. **Inbox state.** This round adds 3 candidates and 6 fold-only proposals,
   taking the inbox to roughly 50 open proposals across five rounds with zero
   filings. Nothing has changed since the 2026-08-04 and 2026-08-11 notes except
   the size. The cheapest actions remain the same three and they are now cheaper,
   because this round supplied evidence for two of them: file the
   second-order-uniformity consolidation (retires four entries for one), file the
   single-axis-humanization consolidation (retires three for one), and close the
   em-dash thread with the 2026-08-04 generation-side/detection-side split, which
   `em-dash-retier-evidence-3` already quantified and this round did not
   contradict. Those three actions take the inbox down by ten and resolve every
   thread with three or more rounds of evidence behind it. Round note 3 is the
   only item that is not a filing decision, and it is the one the loop has now
   reported five times.

## Round 2026-08-25 (weekly loop)

Harvest: 1 ledger entry (`2026-07-23-trimhero-gate-qt.md`, tweet). Fetch-back
FAILED for the sixth consecutive round, and the failure mode changed: WebFetch on
x.com returned **HTTP 403, not the 402 of the previous five rounds**. The Grok
Build fallback was attempted again, and the 2026-08-18 diagnosis was wrong in a
way worth correcting. The blocker is not a command allowlist. This session's
shell is confined to the repo working directory, so both `ls ~/.grok/bin` and a
direct invocation of the binary were refused by the sandbox before any allowlist
question arose. Adding a Bash permission would not fix it; the fix is either
adding `/Users/kevinmagnan/.grok` to the session's allowed directories or
demoting fetch-back below the paste fallback in `harvest.md`. No published text
was retrieved and none was reconstructed. Ledger entry retained, not pruned. No
new harvest candidates: the entry was classified in the 2026-07-28 round from the
capture-path-1 record, and re-reading it would only duplicate
`unnamed-attributor-social`, `fix-and-cta-close`, and `lineage-credit-signature`.
Note for the writer: a successful fetch-back would now only confirm a
classification the loop already holds, so the cost of leaving this broken is
close to zero, and the honest options are to widen the sandbox scope or to stop
budgeting a weekly step for it.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), fresh topics. The
isolated-generator protocol was applied again: four subagents, each reading only
`SKILL.md`, `patterns.md`, and `living-corpus.md`, explicitly forbidden to open
`candidates.md`. Samples are saved this round at `harvest/.selfplay-2026-08-25/`
(gitignored, dot-prefixed so no `harvest/*.md` glob picks them up); prior rounds
left their samples unrecoverable. 8 fresh-eyes detectors, tool-free, given only
the sample text. Verdicts: **7 of 8 called AI** (70-88%), 1 called human (82%).
~115 raw flags, ~30 distinct tells, 3 survivors after dedup plus 4 fold-only
proposals and one amendment to an open consolidation. Read round note 1 before
comparing this round's verdict split to any prior round: this loop introduced a
protocol deviation.

Scout: last30days FAILED to execute for the sixth consecutive round (the skill
errored on invocation). Fell back to WebSearch plus direct fetches. Two direct
fetches succeeded and supplied the strongest external evidence the loop has
collected: a 61,608-text controlled corpus with per-feature AI-versus-human rates,
and a 2026-08-03 Forbes Tech Council piece. The Wikipedia signs page was
re-fetched; its sign count is not comparable across rounds and previous rounds
reported that delta wrongly (round note 5). 2 candidates, 2 fold-only proposals.

Aging: SKIPPED. Not the first run of the quarter; Q3 2026 opened with the
2026-07-22 bootstrap round. One aging-shaped proposal is filed below anyway,
because its evidence is external rather than generated: Wikipedia has moved
elegant variation into its historical-indicators section, which is an aging
signal against a live `patterns.md` rule and needs no generation pass to act on.
The Q4 round still owes the three things listed on 2026-08-18.

### single-use-character [status: proposed]

- Found: 2026-08-25  |  Loop: self-play
- Evidence: Flagged on 3 of 4 samples by 4 detectors, independently. A2 on the
  linkedin mentor: "'Dee has dispatched our Ohio lanes for nineteen years' is a
  character card, not a colleague. No surname, no flaw, no annoyance. The wise
  nineteen-year veteran is an archetype." B1 on the blog sample: "Characters exist
  only as function. The grandfather is never named. The father-in-law appears
  solely to deliver the line the next sentence needs to refute, then vanishes. No
  one has an independent existence." B2, same sample, independently: "the
  father-in-law exists for exactly one sentence, purely as rung one of the
  ladder." D2 on the casual sample: "The wife exists for exactly one line, has no
  name, no characterization, and never returns, purely to license the emotional
  turn."
- Source: self-play round 6 detector reports (samples A, B, D)
- Proposed rule: Generalizes and absorbs the 2026-08-04 "anonymous validator"
  fold, which caught this shape only in its testimonial form. The general rule: a
  third party who appears in the prose must exist outside the function they
  discharge. Test: for each person named or referenced, ask what they do besides
  the one job, and whether anything about them would still be true if the job
  changed. Someone who arrives, delivers a line or a virtue, and never returns is
  a slot. Fix by giving them a second appearance, an irrelevant property, or a
  friction with the narrator, or by cutting them and stating the point directly,
  which is usually better than a synthetic colleague. Suggested Tier 2, narrative,
  anecdote, and incident registers. Distinct from `named-entity-vacuum`, which
  counts proper nouns and finds none, and from `actorless-scene`, which asks
  whether the writer was present: the people here are present and sometimes named,
  and they are still hollow. Corroborated externally this round by the StoryScope
  figure "no subplots 79% vs 57%": a piece with no subplot is a piece where nobody
  has a second reason to be there.
- Mechanism guess: instruction-tuning (plan-then-write allocates one character per
  narrative function, and the be-concrete pressure fills the slot with an
  archetype rather than deleting it)

### zero-residue-argument [status: proposed]

- Found: 2026-08-25  |  Loop: self-play
- Evidence: The only tell flagged on all 4 samples this round, by 4 detectors. C1
  gave the cleanest statement, on the technical sample: "why the versions differed
  (cordoned node pool), why nobody noticed (deploy tool reported green), why review
  missed it (config-map value read at boot... nobody would see it in a diff). Four
  objections, four answers, zero residue. No 'I still don't know why.' Incidents
  always leave one." D2 on the casual sample: "The reason stack is suspiciously
  complete. Paragraph 2 = money, paragraph 3 = circumstance, paragraph 4 =
  feeling. Practical, environmental, emotional, in that order, no overlap, no
  repetition, nothing omitted. Human self-justification circles and repeats
  itself; this is a well-formed outline." A1 caught the timing variant: "the cost
  admission is the best human signal in the piece, but it's defended in the very
  next sentence. Self-inoculation that fast reads as persuasive construction, not
  reporting." B2 caught the inverse, which is the sharpest form: the blog sample
  "hangs a lampshade on the wrong anomaly." It preempts the objection its genre
  expects ("He was a machinist, not a cook") and never notices the one its own
  details raise (waterstones stored in an oil-stiff rag).
- Source: self-play round 6 detector reports (all 4 samples)
- Proposed rule: File merged with the open `closed-loop-narrative-economy`
  candidate as one rule with two registers. That entry covers narrative detail,
  whether every planted thing pays off; this covers argument, whether every
  objection gets answered. Same mechanism, and merging them is what the size
  budget asks for. The rule: leave one thing unexplained, and let it be the thing
  you actually never worked out rather than a manufactured mystery. Test: after
  drafting, name the objection a hostile reader would raise that the piece does
  not answer. If there isn't one, the piece answered them all, and a text with no
  open questions was assembled rather than reported. Second check, from B2: the
  objections a piece preempts should be the ones its own details raise, not the
  ones its genre expects. Suggested Tier 2, escalating on incident and argument
  registers. Guard: this must not license vagueness or hedging as a substitute for
  a missing answer. One honest "I don't know why" beats four tidy causes.
- Mechanism guess: reward-tuning (helpfulness training penalizes leaving a
  reader's question unanswered, and the penalty applies to the imagined objection
  as well as the asked one)

### de-bulleted-list [status: proposed]

- Found: 2026-08-25  |  Loop: self-play
- Evidence: C2 on the technical sample: "'Two things let this happen.' The
  announce-the-enumeration seam. What follows is a two-item list flattened into a
  single compound sentence joined by 'and ... and', which is what list-avoidance
  looks like from the outside: the shape of a bulleted list with the bullets filed
  off." C1 independently named the same sentence "the enumerated-cause frame,
  dropped in as a section header disguised as a sentence. Then exactly two things
  arrive, in the same order they were introduced earlier, each with exactly one
  disposition (one has a PR, one needs a conversation). Real retrospectives produce
  three things, or two-and-a-half, or one thing plus a suspicion." A2 flagged the
  linkedin sibling, an unmarked list run into prose: "Safety, TMS navigation,
  customer tiers, a two-hour recording of me explaining detention policy."
- Source: self-play round 6 detector reports (samples A, C)
- Proposed rule: A displacement tell with a named parent. `patterns.md`
  "excessive bullet lists, convert bullet-heavy prose to paragraphs" produces it:
  the conversion strips the markers and leaves the structure, so the reader gets a
  list wearing paragraph clothes. Signature: an announcing sentence that states the
  count, then N items in introduction order, each carrying exactly one attribute,
  joined by "and". Test: can you re-bullet the paragraph without moving a word? If
  yes, it was never prose. Fix by cutting the count announcement, ordering by
  importance rather than by prior mention, letting one item carry more weight than
  another, or keeping the actual bullets, which are honest when the content really
  is list-like. Suggested Tier 2. Note the seam for the writer: this partly
  contradicts the 2026-08-04 "structural over-formatting" fold, which proposed
  widening the excessive-bullets rule. Widening the ban makes this tell more
  likely, not less. Resolve the two together; the resolution is probably that the
  rule should target bullets used for non-list content in both directions rather
  than bullets as such.
- Mechanism guess: displacement (a formatting ban applied as a surface transform,
  leaving intact the underlying structure that the formatting was reporting)

### body-language-cliche [status: proposed]

- Found: 2026-08-25  |  Loop: scout
- Evidence: A controlled corpus comparison reports this as the largest single
  per-feature gap in its results: AI "reaches for the body-language cliché... 81%
  vs 38%." Methodology as reported: 10,272 writing prompts, each written six ways,
  once by a human author and once each by Claude, GPT, Gemini, DeepSeek, and Kimi,
  for 61,608 texts, scored on "30-odd structural features."
- Source: the StoryScope study as reported by
  https://app.stationx.net/articles/ai-writing-patterns (fetched directly
  2026-08-25). The primary study was not read; treat the figures as secondary.
- Proposed rule: A straightforward coverage gap. `patterns.md` content pattern 13
  covers *claiming* the feeling ("what surprised me most"), and the 2026-08-11
  fold added the inverse, events that imply an emotion the text never carries.
  Neither covers the third and most common option: performing the feeling through
  a stock physical gesture. Her stomach dropped. He exhaled slowly. Something
  tightened in her chest. He ran a hand through his hair. Her jaw clenched. File
  as a third variant under the same content pattern rather than as a new rule, so
  the check runs in three directions. Suggested Tier 1 within that pattern for the
  listed gestures, Tier 2 for the shape. Scope caveat the writer should weigh: the
  corpus is fiction, and transfer to blog, linkedin, and incident registers is
  untested. It is the strongest number in the study and the least certain to apply
  to what Kevin actually writes.
- Mechanism guess: pretraining-register (the gesture set is a fiction-corpus
  convention, heavily overrepresented relative to how often people describe their
  own bodies in first-person nonfiction)

### elegant-variation-retired [status: proposed]

- Found: 2026-08-25  |  Loop: scout (aging proposal, filed outside the aging step)
- Evidence: Wikipedia's signs page has moved "Lexical diversity/elegant variation"
  into its "Historical indicators" section (13.6), alongside didactic disclaimers,
  section summaries, prompt refusal, abrupt cut-offs, and outdated access-date
  parameters. That page is maintained by WikiProject AI Cleanup and is the
  humanizer lineage's source, so a demotion there is pre-vetted the same way an
  addition is.
- Source: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing (fetched
  2026-08-25; the historical-indicators section was retrieved in full)
- Proposed change: re-tier or retire `patterns.md` content pattern 10, "Synonym
  cycling (elegant variation)". Two reasons to act without waiting for the Q4
  aging pass. The signal is external, so it needs no generation run to be
  credible, unlike the em-dash thread. And the rule is not free: the 2026-08-11
  `uniform-hedge-per-number` candidate names synonym cycling as an active *cause*
  of a displacement tell ("the synonym-cycling rule then rotates the approximator,
  which is what produces the giveaway regularity"). A rule that no longer catches
  its target while still generating pressure toward a new tell is the exact case
  the aging step exists for. Recommend re-tier to P2 rather than outright
  retirement, and if the 2026-08-18 `explicit-retirement-marking` proposal is
  adopted, this is the first entry to move into the dated retired section. This is
  the second aging-shaped proposal in the inbox with external evidence behind it;
  the first is the em-dash thread, which now carries three evidence entries and no
  decision.
- Mechanism guess: n/a (aging; the repetition-penalty behavior that produced it
  changed)

### Consolidation amendment: the clumping test (measurable form for second-order uniformity)

- Found: 2026-08-25  |  Loop: self-play
- Evidence: The dominant finding of the round, and the one thing every detector
  converged on. Five detectors across all four samples described the same
  measurement in five vocabularies. A1: detail is "metered, one or two anchors per
  beat, evenly." A2 on the hedges: "The hedges appear exactly twice and exactly
  where precision would be implausible. Real hedging is sloppier and lands in
  random places." B1: "Sentence-length variance is real but positionally
  scripted... Variety executed as a rule rather than as thought." C1: "That's the
  *taught* variance. Organic variance clumps: three long ones in a row, then a
  fragment." D2 gave the clearest statement: "Burstiness is evenly distributed,
  which defeats the purpose. Sentence length varies, but each paragraph contains
  exactly one short beat deployed against the long ones... Genuine variance clumps.
  This is variance on a schedule." D2 also caught it on the discourse markers: "One
  casual marker per act. 'So' to open, 'Also, look,' at the pivot, 'Anyway.' at the
  resolution. Staged spontaneity, placed at exactly the three structural joints."
- Source: self-play round 6 detector reports (all 4 samples); amends the open
  2026-08-04 second-order-uniformity consolidation and the 2026-08-11 "humor on a
  schedule" fold
- Proposed change: The open consolidation names five checks (terminal beats, entry
  points, the sentence cycle, the paragraph contour, device distribution) and
  describes all five qualitatively. This round supplies the single measurement that
  unifies them and makes the rule runnable: **count the device per structural unit
  and check whether the count is uniform**. If a humanizing device (a short
  sentence, a hedge, a concrete number, an informal marker, a joke, a
  self-deprecation) appears exactly once per paragraph or once per section, it was
  scheduled. Human deployment clumps: two in one paragraph, none in the next three.
  This does not add a sixth thing to audit. It replaces five qualitative reads with
  one countable test, which is what makes the consolidation cheap enough to run. It
  also reframes the guidance the skill gives: `SKILL.md`'s "three consecutive
  sentences match length? Break one" is a per-window instruction, and per-window
  instructions are exactly what produce uniform distribution. The replacement is
  distributional: let some windows stay uniform, then break several in a row.
  Recommend filing this together with the consolidation rather than as its own
  entry. That is now three rounds of evidence behind one filing, with no filing.
- Mechanism guess: displacement (already named by the parent proposal; this round
  only measures it)

### Fold-only proposals (no new rule; merge into an existing one)

- **Inference wrong, retrieval right** -> the fifth signature for
  `locally-plausible-globally-incoherent`, and the cheapest test that candidate has
  been given. B2 stated it as a general diagnostic: "verifiable claims are correct
  (burr, wire edge, soaking until bubbles stop, tomato skin), while *inferential*
  claims are wrong (why the stone dished, what the shoulder sound means). That
  asymmetry is retrieval working and reasoning failing." The blog sample's closing
  line asserts that a whetstone dishes in the middle because the grandfather
  "pushed harder on the way out than on the way back," which is not the mechanism;
  a stone dishes because strokes concentrate mid-stone. C1 and C2 found the
  technical sibling independently and twice over: v2.8 pods holding a 30-second
  timeout cannot fail at a 14-second p99, and C2 additionally computed that the
  stated recovery (roughly 79,000 jobs to under 500 in 23 minutes) requires
  quadrupling throughput while removing 43% of the fleet. Prior signatures were
  inverted causal direction (2026-07-28), quantities not derivable from the
  mechanism (2026-08-04), canonical-fix vocabulary without the licensing mechanism
  (2026-08-11), and unearned connectives (2026-08-18). The new test is narrower
  than all four and runs faster: audit only the sentences that infer, and leave the
  sentences that recall alone.
- **The proper-noun-to-number ratio** -> the measurable form `named-entity-vacuum`
  has been missing. D2: "Nine numbers... and exactly one proper noun: Bruce. No
  city, no employer, no flour brand, no recipe, no book, no bakery. Bread people
  are drowning in brand names and named methods. Quantities are safe to invent and
  read as specificity; proper nouns are checkable and get avoided." Corroborated
  externally this round: the StoryScope corpus reports "vague unnamed sources 72%
  vs 50%." Add the ratio as the test and the 72/50 split as population evidence.
- **Emily and Sarah, and descriptive service names** -> two examples for
  `canonical-detail`, from two sources. The 2026-08-03 Forbes piece reports that
  "over 60% of the AI-written articles mentioned either Emily or Sarah," which is
  the modal-instance mechanism that candidate already names, applied to invented
  people. C2 found the infrastructure version this round: "'billing-events,'
  'ledger-sync,' 'ledger API.' Generic-descriptive service names, what a model
  invents when it needs a name. Real systems accumulate names like `hermes`,
  `ledgerd`, `bes-worker-2`." Same move in both: when a name is needed, the model
  emits the category's most transparent instance. Add both; do not file separately.
- **The process-close** -> a fifth door for the exit-shape merge proposed in
  `fix-and-cta-close`. C1: "'I have a PR open for the second one. The first needs a
  real conversation about where timeouts should live.' Reverse-order pairing for a
  chiastic close; easy fix already shipped, hard fix elevated to something cultural
  and unresolved. This is the 'the real bug was our process' beat." C2 flagged the
  same span as "the wise-closer beat... gestures at organizational maturity without
  committing to anything." That entry now proposes merging five exits into one
  mechanism rule, and this is the incident register's version. Corroborated at
  population scale this round: the StoryScope corpus reports AI "spells out the
  moral 77% of the time; humans, 52%," which is the first number the loop has for
  the exit-shape family.
- **The someone / everybody / nobody ladder** -> `patterns.md` faux-insight setups.
  That entry lists "Here's what nobody tells you" as a phrase. B1 and B2
  independently flagged the distributed form, which evades every listed phrasing by
  spreading the move across three sentences: "My father-in-law told me to hold the
  angle. Everybody tells you to hold the angle. Nobody tells you that your wrist
  will lie to you about what it's doing." B2: "a someone / everybody / nobody ladder
  in three beats, anaphora on 'hold the angle,' capped by a personification
  aphorism." The tell is the escalation, not the phrase. Add the ladder shape so the
  rule still fires when no listed phrase appears.
- **Vague expression of connection** -> `patterns.md` content pattern 3 or 5.
  Wikipedia's language-and-grammar section carries this sign for indirect
  constructions ("in connection with", "associated with") that assert a
  relationship without naming it. Our rules cover the participle version
  (superficial -ing analyses) and the attribution version (vague attributions) but
  not the bare prepositional one. The 2026-08-03 Forbes piece names the same shape
  as "redundant clauses," quoting "highlights its importance for the broader
  industry." Same mechanism, one more form.

### Round notes: methodology, misses, and inbox state

1. **This loop introduced a protocol deviation, the same mistake the 2026-08-18
   round recorded.** Four of the eight detectors (A2, B2, C2, D2) received an
   instruction the other four did not: "Be a hostile, forensic reader: assume
   nothing, and check whether the specifics actually cohere." All four returned AI
   at 76-88%. The four unmodified detectors returned AI at 70%, 72%, and 78%, and
   human at 82%. So the headline 7-of-8 split is not comparable to the 3-of-8 of
   2026-08-18, and the comparable figure is the unmodified pool's 3 AI to 1 human.
   Recording it plainly, because the loop's value depends on its rounds being
   comparable and this one is half-deviated. The deviation was also productive:
   every arithmetic failure found this round came from a hostile detector, and the
   coherence failures in the blog and technical samples would have gone unrecorded
   without them. The right resolution is not to drop the hostile prompt but to fix
   the pool: run four detectors on the standard prompt for the verdict rate and
   four on the hostile prompt for the coherence audit, and report them as two
   instruments rather than as one split. That belongs in `weekly-loop.md` step 2
   alongside the isolated-generator protocol, which is still being re-derived every
   round instead of written down.

2. **The 2026-08-18 technical-sample result was caused by the instruction, not by
   the floor, and this round establishes that cleanly.** That round gave its
   technical generator an extra coherence instruction, got the first factually
   sound incident writeup in four rounds, honestly flagged the result as
   confounded, and asked the next round to give all four samples the instruction or
   none. None was the choice here, restoring the baseline. The technical sample
   promptly went incoherent again, in two independent places, both caught by both
   of its detectors. So the conclusion the 2026-08-18 notes suspected now has
   support: an explicit coherence instruction fixes a failure the floor does not
   address, and the floor does not address it. That converts
   `locally-plausible-globally-incoherent` from an open scope question into a
   decision with evidence on both sides. Its scope caveat still stands (a
   factual-accuracy check wearing a slop-detector coat), but the loop has now
   shown that a one-sentence generation-side instruction reliably prevents the
   failure, which is a far cheaper filing than a detect-mode audit rule.

3. **The FATAL binary-contrast family survived generation for the sixth
   consecutive round.** B1 on the blog sample: "'He was a machinist, not a cook',
   the negated-contrast frame in its soft form." B2 independently listed the same
   span: "The X-not-Y contrast, used to preempt an objection." A2 found the diffuse
   version in the linkedin sample and named it precisely: "Nearly every sentence is
   built on a binary... The literal negate-then-correct construction is absent, but
   the scaffolding underneath it is running in almost every line." The 2026-07-28
   round proposed the fix, which is to run the check as a discrete pass over the
   finished draft rather than as one line item in a checklist; 08-04, 08-11, and
   08-18 each repeated it. It remains unmade. Six rounds. This is the
   longest-running unactioned finding in the inbox, it is the cheapest one to act
   on, and it will appear again next week.

4. **Same-span disagreement produced a whole-sample verdict split this round, the
   third consecutive reproduction.** The casual sample drew HUMAN at 82% from D1
   and AI at 88% from D2, and they disagreed on the same spans in both directions.
   On "I want a mild crumb," D1: "A small jargon collision: 'crumb' is structure,
   'mild' modifies flavor. Real bakers slur these; models use jargon in its
   dictionary-correct slot," filed as a human signal. D2 on the identical phrase:
   "Jargon-adjacency error... Correct vocabulary, wrong collocation, which is what
   generation does when it has the domain words but not the domain," filed as an AI
   signal. Both detectors also independently caught the same arithmetic error (100g
   of flour a day is a five-pound bag every three weeks, not six) and drew opposite
   conclusions from it: D1 read the error as human because it understates the
   writer's own consumption, D2 read it as "specificity that *feels* checkable and
   quietly isn't." D2's hostile prompt is a partial explanation, which is round note
   1's point. But the 2026-08-11 and 2026-08-18 instances carried no such confound,
   and the conclusion those rounds drew holds and is now three rounds old: every
   humanizing move has a detectable-as-performance twin, and what separates them is
   whether the detail was observed, which no rule can supply. This remains the
   strongest argument in the inbox for `counterculture-signature` and against any
   candidate whose instruction is "add a human marker."

5. **Two scout-method notes, one of them a correction to how this loop reports.**
   First: the Wikipedia sign count is not comparable across rounds. This round's
   fetch enumerated 54 active named signs plus 6 historical; the 08-04, 08-11, and
   08-18 rounds reported 58, 59, and 61. The difference is a counting method
   (whether subtypes under "Negative parallelisms" and the model-specific markup
   families count as separate signs), not page growth. Those rounds reported the
   delta as if it measured the page changing, and it did not. Stop reporting a
   count; report coverage. Second: the "Biases in content" section and its
   "Pro-authoritarian bias" subsection were truncated in both of this round's
   fetches, so their content is unknown. Recording that as a partial-fetch failure
   rather than guessing at it. It is a named sign with no coverage anywhere in
   `patterns.md`, and it needs a successful fetch before anyone can say whether it
   belongs in a prose-slop skill at all.

6. **The strongest external validation the loop has found for its own first
   principle.** The StoryScope corpus reports that structural features alone
   classify AI versus human at 93.2% accuracy, that a stripped-down set of 30
   features hits 84.8% on its own, and that the models clustered tightly while
   "human stories were scattered everywhere." `SKILL.md`'s spine rule 1 says
   structure is the #1 detection signal and ranks it above vocabulary. That claim
   has been carried on assertion and on this loop's own detector reports for six
   rounds; it now has a controlled corpus behind it. Two things follow. The rule
   library's proportions still contradict its own spine: `patterns.md` spends
   roughly 125 lines on vocabulary tables and roughly 60 on structure patterns. And
   the "scattered everywhere" finding is the same result the loop keeps reaching
   from the inside, that the target is variance rather than a different center,
   which is the argument for the clumping test above and against every candidate
   that would prescribe a new uniform behavior.

7. **Inbox state.** This round adds 5 candidates, 1 consolidation amendment, and 6
   fold-only proposals, taking the inbox past 55 open proposals across six rounds
   with zero filings. The recommendation has not changed since 2026-08-04 and it
   gets cheaper every week: file the second-order-uniformity consolidation with
   this round's clumping test attached (retires four entries for one, and now has a
   countable test), file the single-axis-humanization consolidation (retires three
   for one), and close the em-dash thread with the 2026-08-04
   generation-side/detection-side split. Those three take the inbox down by ten and
   resolve every thread with three or more rounds behind it. Two new items belong
   on that short list because they cost almost nothing: make the binary-contrast
   check a discrete pass (round note 3, six rounds unactioned), and act on
   `elegant-variation-retired`, which is a retirement rather than a filing and
   therefore *buys* budget instead of spending it. Under the size-budget rule, a
   retirement is the only move in this inbox that makes room for the rest.

---

## 2026-08-28: manual scout pointer (Kevin, mid-session)

### simonw-cliche-highlighter [status: proposed]

- Found: 2026-08-28  |  Loop: manual scout (Kevin shared the link)
- Source: https://tools.simonwillison.net/llm-cliche-highlighter (simonw/tools,
  client-side highlighter with per-pattern counts)
- Evidence: ~27 original patterns plus a Wikipedia-derived group. The original
  set is current-generation, punchy-Substack-era tells largely absent from
  patterns.md: "No X, no Y" chains, "That's the whole ...", "Sit with that",
  "You already know", "That's not nothing", "The punchline is", "Worth
  naming", "Here's the twist", "X is dead", "The only X I trust", performative
  honesty, stacked rhetorical questions, repeated sentence openers, colon into
  a triple, stranded auxiliary contrast, echoing sentence runs.
- Proposed action: next scout round diffs the full list against patterns.md
  and the inbox (overlaps: punchline-terminal-paragraphs, the sit-with-that
  sibling at the fake-gravity entry). High-credibility source; several are
  Tier 1/2 candidates.
- Protect-list collision, flagged on arrival: the tool marks "Turns out ..."
  as an LLM cliche. That is a documented pre-AI Kevin signature (voice-dna,
  2020 samples). Do not import that one to the floor as-is; it is evidence for
  per-byline protect lists over global bans, and a live example that tells
  drift INTO real human phrasing.
- Mechanism guess: mixed; several are reward-tuning punchiness tells (sibling
  of punchline-terminal-paragraphs), the chains are structure tells.
