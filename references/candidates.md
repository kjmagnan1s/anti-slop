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

## Round 2026-09-01 (weekly loop)

Harvest: 1 ledger entry (`2026-07-23-trimhero-gate-qt.md`, tweet). Fetch-back
FAILED for the seventh consecutive round. WebFetch on x.com returned **HTTP 402
again**, so the 403 of 2026-08-25 was transient and the 402 is the stable
failure mode. The Grok Build fallback was attempted again and refused again, and
the refusal confirms the 2026-08-25 diagnosis over the 2026-08-18 one: this
session's shell is scoped to the repo working directory, so both `ls
/Users/kevinmagnan/.grok/bin/` and any invocation of the binary are blocked
before an allowlist question arises. Adding a Bash permission would not fix it.
No published text was retrieved and none was reconstructed. Ledger entry
retained, not pruned. No new harvest candidates: the entry was classified in the
2026-07-28 round from its capture-path-1 record, and re-reading it would only
duplicate `unnamed-attributor-social`, `fix-and-cta-close`, and
`lineage-credit-signature`. The 2026-08-25 note stands: a successful fetch-back
would now only confirm a classification the loop already holds, so the honest
options are to widen the session's allowed directories or to demote fetch-back
below the paste fallback in `harvest.md` and stop budgeting a weekly step for
it.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), fresh topics
(municipal parks scheduling, urban birding, a duplicate-push-notification
incident, an aquarium forum post). The isolated-generator protocol was applied:
four subagents, each reading only `SKILL.md`, `patterns.md`, and
`living-corpus.md`, explicitly forbidden to open `candidates.md`. Samples saved
to `scratch/selfplay-2026-09-01/` (gitignored). **The 2026-08-25 round-note-1
fix was applied**: the pool ran as two instruments rather than one split. Eight
standard detectors (2 per sample, the weekly-loop prompt verbatim) and four
hostile detectors (1 per sample, the same prompt plus a forensic-coherence
instruction), reported separately. Standard instrument: **4 AI (72-82%), 4 human
(60-92%)**. Hostile instrument: **3 AI (75-85%), 1 human (65%)**. ~165 raw
flags, ~35 distinct tells, 4 survivors after dedup plus 1 amendment to an open
candidate, 1 evidence entry, and 8 fold-only proposals. Read round note 1 before
treating the hostile instrument as a verdict count; its job is the coherence
audit, not the verdict rate.

Scout: last30days FAILED to execute for the seventh consecutive round (the skill
errored on invocation). Fell back to WebSearch plus direct fetches. Four direct
fetches succeeded: the full pattern list behind Simon Willison's cliche
highlighter (executing the 2026-08-28 manual pointer), a Georgia Tech controlled
study on human AI-detection, a competitor-skill survey, and the Wikipedia signs
page. Per the 2026-08-25 note, no sign count is reported; coverage is reported
instead. The Wikipedia "Biases in content" section and its "Pro-authoritarian
bias" subsection were truncated again, the third consecutive partial fetch of
that section; recording it as an unresolved fetch failure rather than guessing.
4 candidates, 8 fold-only proposals.

Aging: SKIPPED. Not the first run of the quarter; Q3 2026 opened with the
2026-07-22 bootstrap round. The Q4 round still owes the three things listed on
2026-08-18. One of them shrinks this round: the PR leg below files the em-dash
generation-side/detection-side split, so what remains for Q4 is only the
rule-off generation pass for our own base rate.

### chimera-proper-noun [status: proposed]

- Found: 2026-09-01  |  Loop: self-play
- Evidence: Three detectors, independently, on the same two words. The blog
  sample placed a bird sighting at "the retention pond behind Fastrac Tire."
  B1: "Fastrac is a convenience-store chain, not a tire business. A composite or
  confabulated local business name is a recognizable generation artifact; a real
  person usually writes either the true name or 'the tire place.'" B2: "Aldi,
  Sunoco, Nikon, and Merlin are all real. 'Fastrac Tire' is a plausible-sounding
  blend sitting in the middle of verifiable brands. That is exactly what
  proper-noun generation looks like when it fills a slot." Bh reached it from
  the other direction, using the real brands to geolocate the piece and then
  finding the one name that does not resolve.
- Source: self-play round 7 detector reports (sample B)
- Proposed rule: Distinct from the two open naming candidates, and it completes
  the family. `named-entity-vacuum` covers the case where no proper noun
  appears; `canonical-detail` covers the case where the name supplied is the
  category's most transparent instance ("billing-events", "Emily"). This covers
  the case where a name IS supplied, IS specific, and IS wrong: a real entity's
  name welded to the wrong business, place, or product category, sitting in a
  run of verifiable names that lends it cover. Test: for every proper noun, ask
  whether that entity does the thing the sentence says it does. Where the real
  name is not available, name the category ("the tire place") rather than
  inventing a specific. Suggested Tier 2, escalating anywhere the text claims
  first-hand knowledge. Note for the writer: this is a counterexample to the
  mechanism `named-entity-vacuum` proposes. That entry argues proper nouns get
  avoided because they are checkable and a fabricated one is a penalized error.
  Here the model fabricated one anyway, and a blend of two real names is what a
  checkable-error-avoidant system should never produce. Either the mechanism is
  wrong or an explicit be-specific instruction defeats it, and the two entries
  should be filed together so that question gets settled once.
- Mechanism guess: pretraining-register (local-business names sit in a dense
  n-gram neighborhood, so the model samples a plausible name rather than
  retrieving one, and the be-specific pressure supplies the slot)

### weight-assignment-phrases [status: proposed]

- Found: 2026-09-01  |  Loop: scout
- Evidence: The full pattern list behind Simon Willison's LLM cliche
  highlighter, read from source this round (the 2026-08-28 inbox pointer asked
  for exactly this diff). Roughly a third of its original patterns are one
  mechanism `patterns.md` does not carry: a sentence whose only job is to tell
  the reader how much the preceding sentence weighs. Labels and examples from
  the tool: "That's the whole X" (point/game/thing), "Is the entire X", "The
  entire X is", "Is the whole X", "That's not nothing", "The punchline is",
  "That's the part..." ("the part that makes me trust"), "Here's the twist"
  (also thing/catch/kicker), "Sit with that", "You already know", "Worth
  naming", "The only X I trust", "Don't take my word for it", "That's why X
  mattered".
- Source: https://tools.simonwillison.net/llm-cliche-highlighter (patterns read
  from https://raw.githubusercontent.com/simonw/tools/main/llm-cliche-highlighter.html,
  fetched 2026-09-01)
- Proposed rule: One Tier 1 phrase family, not fourteen entries. `patterns.md`
  already carries the two positional cousins: faux-insight setups (the opener
  that promises a payoff) and the fake-profound kicker (the closer that inflates
  the point). This is the mid-piece member of the same family, and it is the one
  that survives a crackdown on both, because it neither opens nor closes
  anything. It attaches to a sentence already written and grades it. Cut the
  grading sentence; if the preceding line carries weight, the reader feels it.
  File as a third bullet under the same mechanism rather than as a new rule,
  with the list above as examples. Cross-check done: "let that sink in" and "sit
  with that" were already proposed on 2026-07-22 as `let-that-sink-in`, so file
  these together and retire that narrower entry in the same commit.
- Mechanism guess: reward-tuning (engagement-optimized corpora reward
  significance marking, and the marking survives when the inflated vocabulary
  around it is scrubbed)

### feature-blind-detection [status: proposed]

- Found: 2026-09-01  |  Loop: scout (methodology)
- Evidence: A controlled two-phase experiment. 21 participants wrote paired
  opinion pieces with an AI chatbot; half were warned their submission would be
  scanned by an AI detector. 251 independent judges then made 1,999 paired
  comparisons, choosing which document was "written by a human." Judges picked
  the warned writer's document 54.13% of the time against 45.87% for the
  unwarned one, rejecting chance at p = 0.000243. The finding that matters here
  is the second one, quoted from the abstract: "on every measurable text feature
  I extracted, including AI overlap scores, lexical diversity, sentence
  structure, and pronoun usage, the two groups were indistinguishable. The
  judges are picking up on something that feature based methods do not capture."
- Source: Daniel Tabach, Georgia Institute of Technology, April 2026, "Can
  Humans Detect AI? Mining Textual Signals of AI-Assisted Writing Under Varying
  Scrutiny Conditions", https://arxiv.org/pdf/2604.23471 (PDF fetched and read
  directly, 2026-09-01; pages 1-6 read, later sections not read, so the feature
  list above is the abstract's and not the full methods section's)
- Proposed change: A methodology entry, and the first external result that
  speaks to what this skill can and cannot be. Two consequences for the writer.
  First, it is corroboration for `counterculture-signature` (2026-08-11) from a
  controlled setting rather than from reporting: writing under detection
  pressure does shift reader judgments, and the shift is real but small, a few
  points above chance. Second, and harder: the shift was invisible to every text
  feature the study extracted. A rule library is a feature library. If what
  judges respond to is not in the features, a rule set has a ceiling, and this
  loop has been finding that ceiling from the inside for three rounds, in the
  same-span disagreements of 2026-08-11, 2026-08-18, and 2026-08-25 where two
  readers split on one sentence. Suggested filing: one sentence in the
  over-polishing warning recording the measured size of the effect, so future
  rounds stop reading verdict-rate swings as progress. Honest limits: 21 writers
  on one prompt, judges making a forced binary choice, and a feature set that is
  not our rule set.
- Mechanism guess: n/a (detection calibration; external)

### scored-gate-convergence [status: proposed]

- Found: 2026-09-01  |  Loop: scout (new-techniques sweep)
- Evidence: Three independently built writing skills have converged on the same
  machinery: a numeric rubric plus a re-run threshold. stop-slop scores 1 to 10
  across five dimensions and revises below 35/50. claude-blog runs a 100-point
  rubric across five gates and re-runs automatically, up to three times, on
  anything below 90. AI-Research-SKILLs scores six rigor dimensions. Per the
  weekly-loop rule that a technique two competitors invent independently is
  high-confidence, three is worth acting on.
- Source: https://www.analyticsvidhya.com/blog/2026/08/top-5-claude-writing-skills/
  (fetched 2026-09-01; the individual repos were not read, so treat the scoring
  details as secondary). Fourth skill surveyed for rule structure:
  https://github.com/jalaalrd/anti-ai-slop-writing
- Proposed rule: Take the trigger, not the rubric. `SKILL.md`'s gate already
  says "If question 1 keeps finding the same class of tell across passes, stop
  patching and regenerate from a tighter brief," which is the same move these
  three skills make, with no threshold on it and so no way to know when it
  fires. Proposal: give the existing regenerate rule a countable trigger (the
  same class of tell surviving two passes, or three or more P1 flags after a
  rewrite pass) and cap the retries. Deliberately NOT proposed: adopting a
  five-dimension score. This round's own evidence argues against it, and so does
  the whole second-order-uniformity thread. A fixed rubric applied to every draft
  is a uniform transform, and uniform transforms are what this loop keeps
  catching. The value in the convergence is the stopping rule, not the
  scorecard. Suggested filing: one clause in the existing gate, no new section.
- Mechanism guess: n/a (competitor convergence; methodology)

### Amendment: locally-plausible-globally-incoherent (scope extension and a runnable test)

- Found: 2026-09-01  |  Loop: self-play (both instruments)
- Evidence: The dominant finding of the round, and the first time this failure
  has appeared outside the technical sample. The hostile instrument found
  substantive coherence failures in 3 of 4 samples, in three registers, and the
  standard instrument independently found one of them without being asked to
  look.
  - Technical (Ch): "38% of our mobile users got every push notification two to
    four times" caps total volume at 1.38x to 2.14x, so the timeline's "Send
    volume hit 3.4x expected and paged notifications on-call" could not have
    fired at all against a 3x threshold. Ch also caught that a p99 latency rise
    cannot duplicate every notification for 38% of users, that an FCM-only
    trigger cannot produce an all-mobile blast radius, and that the stated fix
    (a transaction around the write and the check) does not move the hash
    computation the document itself names as the bug.
  - Linkedin (Ah, corroborated by A2 on the standard prompt): "asking council
    for a tenth crew" implies nine crews, and nine crews recovering 40 minutes a
    day is about 0.7 of a crew, while holding "two staff unassigned" removes
    about one. The package nets out below where the department started and is
    presented as the reason the tenth crew was unnecessary. A2 found the same
    contradiction from the other side: quadrant ownership is incoherent at nine
    or ten crews across four quadrants. Ah also caught a shift that silently
    changed length, 7:00-3:30 against 5:45-2:00.
  - Blog (Bh): "Around month five" collides with "I got bored in July. Six weeks
    without picking them up," and it is the only elapsed-month count in a piece
    that otherwise names months. "The register shifts to the vaguer unit
    precisely where the arithmetic would fail."
- Source: self-play round 7 detector reports (samples A, B, C; both instruments)
- Proposed change: Two amendments to the open 2026-07-28 candidate, which has
  now carried five failure signatures across five rounds with no filing
  decision. **Scope.** The candidate is written as a check on "explanatory or
  incident text," and its open question is whether a factual-accuracy check
  belongs in a slop skill at all. This round answers half of that: the failure
  is not a property of technical writing. It appears anywhere the prose makes
  claims whose constraints only a practitioner would check, including a 200-word
  LinkedIn post about mowing schedules. **Test.** The candidate has lacked a
  runnable form. This round supplies one that is cheaper than reading the causal
  chain end to end: take any two quantities in the piece and ask whether one
  constrains the other. In real reporting they do, because they came off the same
  system (crew count times crew size is headcount; blast radius times copies is
  volume). In generated prose each number is locally plausible and jointly
  unconstrained, which is why A2 could say "there's no arithmetic a reader could
  check" about one sample while Ch found arithmetic that contradicts itself in
  another. Both are the same failure: the numbers were chosen for the sentence,
  not read off a shared source. Where they do reconcile, check whether they
  reconcile too well (C2: 1.5x is exactly half of 3x and buys exactly one hour).
- Mechanism guess: n/a (generation coherence, not a style tell) — unchanged

### em-dash-retier-evidence-4 [status: proposed]

- Found: 2026-09-01  |  Loop: self-play (evidence for the open em-dash thread)
- Evidence: **Seven of twelve detectors named the absence of the banned marks as
  positive evidence, unprompted, and three generalized it past the em dash to
  the whole punctuation palette.** Bh: "no em dashes, no 'not just X but Y,' no
  tricolons, no elevated diction. That absence, sitting on top of this much
  architectural symmetry, reads like output that was written against a tell
  list, or scrubbed after the fact. Slop removal is easier than shape removal,
  and the shape is untouched." Ah: "No em dashes at all, unusual in a piece with
  this cadence, which suggests deliberate suppression rather than natural
  style." B2: "There is not one dash, colon, or semicolon anywhere in the text,
  which in a piece with this much appositive instinct reads like a constraint
  being obeyed rather than a natural plain style." Dh: "If this is
  machine-written, it was written by a model explicitly instructed to avoid em
  dashes and vary sentence length."
- Source: self-play round 7 detector reports (all 4 samples, both instruments)
- Proposed change: The 2026-07-28 entry found 3 of 8 detectors treating em-dash
  absence as a de-slopping signature. This round it is 7 of 12, and the finding
  has widened from one mark to the palette, which is the result
  `flat-syntactic-spine` (2026-08-04) reached from the syntax side. Two things
  follow, and neither changes the generation-side conclusion
  `em-dash-retier-evidence-3` already quantified. First, the detection-side
  tier-down now has support from two independent directions: a population
  argument (human literary prose overlaps the model range) and a behavioral one
  (readers read absence, not presence, as the machine signal). Second, the seam
  `flat-syntactic-spine` flagged is real and the PR leg below does not resolve
  it. The em-dash rule and the hedging rules both thin the punctuation palette,
  and a thinned palette is now itself a flag. The writer should expect to pay
  for the em-dash rule somewhere, and the honest place is the spine check
  `flat-syntactic-spine` proposes.
- Mechanism guess: n/a (aging; the ecosystem moved, and the loop can now measure
  the move from inside its own detector pool)

### Fold-only proposals (no new rule; merge into an existing one)

- **Zero ballast** -> the general statement of the merge already proposed
  between `closed-loop-narrative-economy` and `zero-residue-argument`, and the
  most-cited tell of the round: five detectors, all four samples. Dh gave the
  cleanest form, on the casual sample: "Every single detail is load-bearing. No
  brand of sand, no how-long-the-10-gallon-has-run, no LFS guy, no stand, no
  reason he set the tank up. Real distressed posts carry dead weight. This one
  is 100% signal, which is the strongest machine signature present." C2: "There
  is not one word of ballast here." A2: "Every clause pays rent." B2: "Nothing
  is redundant, nothing is out of order, nothing is wasted." Those two open
  candidates cover details that pay off and objections that get answered; this
  is the third and simplest register of the same mechanism, material included
  for no reason at all. File all three as one rule.
- **One engine, iterated** -> the whole-piece instance of the open
  second-order-uniformity consolidation, and evidence for filing it. B2: "The
  entire piece is a single move iterated... An essayist writing from actual
  memory usually varies the machine, or forgets to run it once." Bh, on the same
  sample, counted the device: "every anecdote lands on a short wry deflating
  tag. That is not variety, that is one punchline mechanism applied uniformly
  five or six times." Ah found the same shape in another register: "long setup,
  short self-aware button, repeat. Sentence length varies, but the variation is
  patterned." That is the 2026-08-25 clumping test measured at the scale of a
  whole piece rather than a paragraph. Do not file separately.
- **Elided dead time** -> fold into `monotonic-recall-order` (2026-08-11) as its
  second variant. That entry covers narrative order; this covers narrative
  duration. C2: the incident timeline has "a 2 hour 18 minute hole between
  '11:22 Rollback started' and '13:40 Backlog cleared' with no entry in it. That
  is the messiest stretch of any real incident, the part with the drain-rate
  estimates and the second scare, and it is empty because it does not serve the
  story." Ch listed the same absence from the other side, naming "a 90-minute
  hole with nothing in it" among the things real timelines contain. Same
  mechanism as monotonic order: the timeline was planned rather than recalled,
  and planning skips the interval where nothing happened.
- **Precision on the wrong axis** -> sharpens `canonical-detail`. That entry
  tests retrieved against observed; this tests whether the precision is the kind
  the stated role would actually carry. Bh on the binoculars: "'Refurbished
  Nikons, eight power' is how a writer renders binoculars, not how an owner
  describes them; an actual user writes 8x32 or 8x42... Specificity here is
  distributed by flavor yield, not by what a person would actually retain." Add
  as a second test under the same entry.
- **The vague unit at the load-bearing seam** -> fold into
  `uniform-hedge-per-number` (2026-08-11), which already carries the 2026-08-11
  version of this ("'a great deal longer' is the one place the writer had a
  number available and didn't give one"). Bh found it again in a different
  register: "Around month five" is the only elapsed-month count in a piece that
  otherwise names months, and it sits exactly where the arithmetic breaks. Two
  independent rounds, two registers. The check is one line: find the vaguest
  quantity in the piece and ask what it is covering.
- **The absent stakes field** -> fold into `reply-shaped-registers`
  (2026-08-11). Both casual detectors independently noticed that the aquarium
  post never says whether anything is living in the tank, which is the first
  thing a responder asks at 0.5 ammonia. They drew opposite conclusions from it,
  D2 reading the omission as checklist tidiness ("that is the whole stakes") and
  Dh reading it as human forgetfulness ("a checklist-driven generator usually
  fills that slot; a panicking human forgets it"). Both readings support the
  same rule: on a participant surface, the fields a real poster leads with are
  set by stakes, not by completeness, and generated posts fill the canonical
  fields evenly while missing the one the genre actually turns on.
- **Stranded auxiliary contrast, and the "No X, no Y" chain** -> two additions
  to existing `patterns.md` entries, from the simonw pattern list. The stranded
  auxiliary ("The tool died; the data didn't") is a binary-contrast variant our
  table lacks, and it is the sibling of the already-open
  `matched-antithesis-pairs` and `rather-than-variant`: file all three into the
  binary-contrast table at once. The "No X, no Y" chain and the "Did not X, did
  not Y" chain belong in negative listing, which currently lists only the "Not a
  X... Not a Y... A Z." form.
- **Measured forms for three open candidates**, all from the scout sweep. The
  simonw list supplies "repeated sentence openers" (three or more consecutive
  sentences starting with the same word) as the countable form of
  `paragraph-opener-monotony`, and "echoing sentence runs" (consecutive
  sentences sharing a repeated multi-word skeleton) as the countable form of the
  parallelism family. A separate 2026 write-up supplies a sentence-length
  population figure to sit alongside the burstiness numbers folded on
  2026-08-18: humans average 14-18 words per sentence, AI 20-25. Source:
  https://imperfectly.app/post/remove-ai-slop-from-writing (fetched 2026-09-01;
  the underlying measurement is not sourced on the page, so treat it as weaker
  than the burstiness figures).

### Round notes: methodology, misses, and inbox state

1. **The two-instrument split works, and it belongs in `weekly-loop.md` step
   2.** The 2026-08-25 round ran a half-deviated pool and correctly called its
   own 7-of-8 headline incomparable. This round ran the fix: eight standard
   detectors for the verdict rate, four hostile detectors for the coherence
   audit, reported separately. Both instruments earned their place. The standard
   pool's 4 AI / 4 human is directly comparable to prior rounds (against
   2026-08-25's unmodified 3 AI / 1 human and 2026-08-18's 3 AI / 5 human), and
   the hostile pool produced every coherence finding in the amendment above,
   including two the standard pool would have missed. The protocol is now two
   rounds old and has been re-derived from the round notes both times. It and the
   isolated-generator protocol both belong in the file.

2. **The coherence failure is not a technical-writing failure, and that is this
   round's most consequential finding.** Four prior rounds found factually
   incoherent prose in the technical sample and asked, reasonably, whether an
   accuracy check belongs in a slop skill. This round the hostile instrument
   found substantive failures in three of four samples across three registers: an
   incident writeup whose blast radius contradicts its own alert threshold, a
   LinkedIn post whose staffing arithmetic nets below where it started, and a
   personal essay whose timeline collides with itself. The standard instrument
   found the LinkedIn contradiction independently, with no coherence instruction,
   which means it is visible to an ordinary reader. The scope question is settled
   on the evidence: this is not a property of the technical register, it is a
   property of any prose making claims a practitioner could check. What remains
   open is whether the fix belongs here, and the 2026-08-18 finding still points
   at the cheapest answer: one generation-side coherence instruction prevented
   it, where no detect-mode rule has.

3. **The FATAL binary-contrast family did not survive generation this round, for
   the first time in six rounds.** No detector across either instrument flagged a
   negate-then-correct construction in any of the four samples. Two of them noted
   the absence: Ah observed the list "mowing, trash, restroom checks, and
   playground inspections" is a four rather than the reflexive triad, and Dh
   noted the one negation present ("It's the white kind, not algae green") is
   informative rather than rhetorical, which is the correct call. Recording this
   as a clean result and not as a trend. The round note asking for a discrete
   pass over the finished draft (2026-07-28, repeated 08-04, 08-11, 08-18,
   08-25) has still not been actioned, so nothing in the skill changed to cause
   this. One round is sample variance. If it holds next round, the standing
   recommendation gets cheaper to argue against.

4. **The protect-list collision flagged on 2026-08-28 is now confirmed against
   the golden set.** The simonw highlighter marks "Turns out ..." as an LLM
   cliche. That phrase appears four times across two of the six golden files, in
   writing dated 2020, five years before any of this. Importing that pattern to
   the floor would fail this repo's own gate on the first run. It is the cleanest
   available argument for the protect-list seam over global phrase bans, and it
   is worth keeping as a worked example: a tell can drift into a real person's
   prose, or a real person's prose can predate the tell, and a rule library with
   no per-byline layer cannot tell those apart.

5. **Inbox state, and the first drain.** This round adds 4 candidates, 1
   amendment, 1 evidence entry, and 8 fold-only proposals. It is also the first
   round to drain rather than only fill: the PR leg below drafts three rule
   changes plus one retirement, and they close eleven inbox entries between them
   (four uniformity candidates, three humanization candidates, three em-dash
   evidence entries, and the elegant-variation aging proposal). The two
   consolidations recommended since 2026-08-04, and the em-dash thread open since
   2026-07-23, are all in it. What stays queued and should lead next month:
   `locally-plausible-globally-incoherent` with this round's test attached, the
   zero-ballast three-way merge, and the binary-contrast discrete pass from round
   note 3, which remains the cheapest unactioned item in the file.

### Round 2026-09-01 addendum: PR leg drafted, not opened

Correcting the round summary above, which was written before the push was
attempted. Step 6 ran to completion locally and then stopped at the push.

- Branch `loop/scout-2026-09` exists **locally only**, cut from `origin/main`,
  with the round commit cherry-picked and two commits on it: `8fe8c4b` (this
  inbox section) and `d01a969` (the rule edits plus the eval report at
  `evals/reports/scout-2026-09.md`).
- `git push origin loop/scout-2026-09` was **refused**, and the refusal is a
  configuration failure rather than a missing decision. This repo's
  `.claude/settings.local.json` already carries `Bash(git push origin loop/:*)`,
  which is exactly this command, so the standing 2026-08-27 exception is
  configured and did not take effect in this headless run. `gh pr create:*` sits
  in the same allow list and was never reached. Diagnose it there before adding
  a broader permission. This is the same class of blocker as the harvest
  fetch-back, which has now failed seven consecutive rounds for a permission
  reason rather than a technical one.
- No PR was opened. Nothing was pushed. `main` was not pushed and no other
  branch was touched.
- The eval gate DID run, locally and in full, before the push attempt: all 8
  `evals/slop/` fixtures still catch, and the golden side has one P1 hit
  (`golden-05`, offset 884) that predates this PR and comes from the untouched
  signposting rule. The report on the branch records both, including the
  limitation that both new rules were filed at P2 and therefore could not have
  failed the golden side.
- To finish the leg by hand: `git push origin loop/scout-2026-09`, then
  `gh pr create` with the body drafted in the branch's commit message. Or grant
  the push and re-run the loop, which will find the branch already built.

Note for the writer: two of the four legs of this loop now end at a permission
boundary in a headless run, and in both cases the boundary is not where the
docs assume it is. Harvest fails on directory scope, not on a command allowlist
(corrected 2026-08-25). Step 6 fails with the correct allowlist entry already in
place. Until the headless session actually honors `.claude/settings.local.json`,
`weekly-loop.md` step 6 should say plainly that an unattended run stops at a
local branch, so a future round does not report a PR it did not open.

## 2026-09-04: shipped-diff harvest, Naperthrill issue 16

In-session capture (harvest.md path 1): the newsletter's editor pass and the
shipped version both sat in one session, so the diff is labeled at ship time.
Ledger entry: `harvest/2026-09-04-issue-16.md`. Sixteen story edits plus a
weather and preview rewrite; most classify as content edits (factual
corrections, an invented venue characterization, an invented event category)
and are skipped per the classification rule. Three hunks are generation-side
signal. No flattened-voice hunks this round: nothing the floor stripped got
restored.

### sourcing-apparatus-in-copy [status: proposed]

- Found: 2026-09-04  |  Loop: shipped-diff harvest
- Evidence: A take shipped to a consumer newsletter read "The city's event
  listing doesn't post a price, so check with the temple before you plan around
  one." The reader has no relationship with the city's event listing. The
  generator, having noticed a gap in its own retrieval, narrated the gap in the
  reader's voice. Edited to "There is no price posted, so ask the temple before
  you plan around one," which states the same fact with the apparatus removed.
- Source: Naperthrill issue 16, story 7551 (draft -> shipped)
- Proposed rule: Distinct from hedging, which softens a claim the text does
  make. This one is a true claim about the WRITER'S SOURCES presented as
  information for the reader. Family includes "the source doesn't say," "the
  article notes," "according to the listing," "per the press release," and any
  construction where the retrieval channel becomes a character. Test: would the
  reader recognize the noun as something they interact with? A city website is
  the reader's; "the city's event listing" as an epistemic authority is not.
  Fix is always the same shape: assert the fact, drop the channel, keep the
  caveat. Suggested Tier 1 for consumer-facing surfaces, Tier 3 for internal
  research writing where provenance is the point.
- Mechanism guess: retrieval-honesty pressure discharging into prose. The model
  is trained not to assert unsourced facts, so when the source is silent it
  reports the silence rather than restructuring the sentence to avoid needing
  the fact.

### second-person-conditional-premise [status: proposed]

- Found: 2026-09-04  |  Loop: shipped-diff harvest
- Evidence: Four in one 19-item issue, from four different generation passes:
  "If Last Fling is your Friday...", "If a rainy weekday there is your usual
  escape hatch...", "if the tanks are the real draw for your kid...", "if you
  would rather stay home." The house style already rations the permission-slip
  variant ("if you've been looking for a reason to"), and this is the same move
  with the excuse removed: it invents a reader premise, then addresses it.
- Source: Naperthrill issue 16, stories 7539, 7550, 7554 and the weather segment
- Proposed rule: Extends the tracked permission-slip family rather than opening
  a new one. Current detection keys on "reason/excuse to" and "if you've been
  (looking|meaning|waiting)"; it misses the bare form, `If <noun phrase> is your
  <noun>` and `if you would rather <verb>`. The tell is not the conditional, it
  is that the protasis asserts a fact about the reader the writer cannot know.
  Test: does the "if" clause describe the reader's habits, preferences, or
  household rather than a checkable condition? "If it rains" is fine; "if a
  rainy weekday is your usual escape hatch" is not. Fix: state what the thing
  is and let the reader decide whether it is theirs. Suggested Tier 2, with a
  per-document cap rather than a flat ban, since one instance reads as voice
  and four read as a template.
- Mechanism guess: second-person engagement training. Addressing a reader
  directly scores as warmth, and a conditional is the cheapest way to
  manufacture direct address when the source supplies no actual relationship.

### design-thinking [status: proposed]

- Found: 2026-09-04  |  Loop: shipped-diff harvest
- Evidence: "covering the 1893 Chicago World's Fair thread and the rest of the
  design thinking." The source material was concrete (the fair, the origins of
  everyday Americana in the garden beds). The generator had specifics available
  and reached for the abstraction anyway. Edited to "and where the everyday
  Americana in the beds came from."
- Source: Naperthrill issue 16, story 7397 (draft -> shipped)
- Proposed rule: Fold into the existing dead-vocabulary list rather than filing
  standalone, alongside "leverage" and "landscape." Note the specific failure
  mode, which is worth more than the phrase: it appeared as a summarizing tail
  ("and the rest of the design thinking") after the sentence had already named
  one concrete item. The abstraction was substituting for the second and third
  items the source actually supplied. Test: when consultant vocabulary appears
  in a trailing "and the rest of the X" clause, the source usually contains the
  items being elided; retrieve them instead of naming the category.
- Mechanism guess: enumeration fatigue. Listing two concrete items costs more
  tokens than one item plus a category label, and the category label reads as
  competent summary rather than omission.

## Round 2026-09-08 (weekly loop)

Harvest: 2 ledger entries. `2026-09-04-issue-16.md` (newsletter, Naperthrill
issue 16) was already classified in-session on 2026-09-04 (the section above,
which sat uncommitted on main until this round's commit carried it). Fetch-back
was attempted on the published page and came back PARTIAL: the summarizing
fetcher returned a paraphrase rather than the page text, and a raw fetch of the
same URL returned a Cloudflare managed challenge ("Just a moment...") instead of
the article. A prose-level diff was therefore not possible. A fact-level
comparison of the paraphrase against the ledger found every quoted span it
carried verbatim in the ledger ("11 straight days without the rainy-weekday
fallback", "tickets go out at the Customer Services Desk at 6:45 p.m. and the
cap is 40", "from Country up to Angry", and five others) and no fact the ledger
lacks, so no post-editor edits are detectable and no new harvest candidates
result. Entry retained, not pruned, because fetch-back was not confirmed at the
prose level. `2026-07-23-trimhero-gate-qt.md` could not be READ this round: it
is a symlink into the private `anti-slop-local` repo and the session's read
permission for that path was not granted. Eighth consecutive round without a
confirmed fetch-back on that entry; the 2026-08-25 note on scope, not
allowlist, still stands. Nothing was reconstructed.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), fresh topics
(permit-intake pilot, wheel truing, cron-to-Sidekiq migration, sourdough
starter). Samples saved at `scratch/selfplay-2026-09-08/` (gitignored).
PROTOCOL DEVIATION, recorded before the numbers: the samples were written by the
main loop session, not by isolated generator subagents, and that session had
read the first third and the last tenth of this inbox before writing. The
2026-08-18 isolated-generator protocol was not followed, and the 2026-09-01
two-instrument split (8 standard + 4 hostile) was not run either; this round
ran the 8 standard detectors the weekly-loop file specifies. Read the verdict
split as a contaminated-generator figure comparable to 2026-08-11, not to
2026-08-18 through 2026-09-01. 8 fresh-eyes detectors, tool-free, given only the
sample text. Verdicts: **6 of 8 called AI** (70-80%), 2 called human (65% and
72%, both on the casual sample). ~95 raw flags, ~26 distinct tells, 1 survivor
after dedup, 2 evidence entries against open threads, 1 amendment, and 6
fold-only proposals. The dedup rate is the highest the loop has recorded:
almost every structural flag this round landed on a candidate already open,
and three of them (`punchline-terminal-paragraphs`, `one-job-per-paragraph`,
`single-use-character`) were each flagged by five or more detectors.

Scout: SKIPPED. Not the first run of the month; the 2026-09-01 round ran it.

Aging: SKIPPED. Not the first run of the quarter. Q4 opens with the first
October round, which owes the three things listed on 2026-08-18.

### stance-discharged-at-hook [status: proposed]

- Found: 2026-09-08  |  Loop: self-play
- Evidence: Both linkedin detectors flagged the same sentence for the same
  reason, then each flagged its mirror image elsewhere in the piece. On "I want
  to write down what it did before the vendor writes it up for me": A1, "It's
  the stance-sentence a model produces when asked to give a post a point of
  view"; A2, "a framing kicker that sets the whole post's stance in one clever
  inversion... the kind of line a model produces when told to 'have a
  stance.'" Then, on the close: A1, "it withholds the author's own view, which
  a human who ran the pilot would almost certainly have... the total absence
  of the author's own opinion on a decision they clearly care about"; A2, "a
  tricolon of curated specifics chosen so the reader does the arithmetic
  themselves ($48k vs. three salaries) without the author saying it. Very
  composed."
- Source: self-play round 8 detector reports (sample A)
- Proposed rule: A displacement tell with a named parent, and the parent is
  SKILL.md spine rule 8 (sterile is also slop; the draft needs a position).
  The rule gets satisfied by one quotable attitude line in the hook slot, about
  the framing of the piece, while the question the piece actually turns on
  (renew or not) is handed to the reader as an arranged set of facts. The
  position is performed where it is cheap and withheld where it would cost
  something. Test: name the piece's central open question, then find every
  sentence where the writer takes a side. If the only one is in the first two
  sentences and it is about the writer's posture rather than the question, the
  stance was a slot. Fix: say what you think about the actual question, even
  hedged ("I would not renew at that price"), or drop the hook line so the
  piece is honestly a report. Sibling of `performed-refusal` (2026-08-04),
  which narrates the exit it is not taking; this narrates a position it does
  not hold anywhere else. Suggested Tier 2, linkedin and blog profiles; exempt
  on docs and technical reference, where spine rule 8 already does not apply.
- Mechanism guess: displacement (spine rule 8 asks for a position, and
  "position" is resolved as a voice feature to install at the top rather than a
  judgment to render on the content; the be-specific and no-generic-conclusion
  rules then strip the place a judgment would normally go)

### single-use-character-evidence [status: proposed]

- Found: 2026-09-08  |  Loop: self-play (evidence for the open 2026-08-25 entry)
- Evidence: **All 8 detectors on all 4 samples**, the widest single-round
  agreement the loop has recorded, and each sample had exactly one such
  person. A1: "Named person + tenure number + balanced antithesis... That's the
  AI 'quotable human' device." A2: "first name only, no title, with a tenure
  number attached. This is the canonical humanizing prop." B1: "Dale appears
  exactly once, serves one function, and vanishes." B2: "named minor character
  plus self-deprecating tag clause." C1 and C2 both on Priya: "One named
  person, one action, never mentioned again." D1 and D2 both named the wife
  sentence as "the single line most likely to have been written by a model."
- Source: self-play round 8 detector reports (all samples)
- Proposed change: Promote `single-use-character` to the head of the filing
  queue. Three consecutive rounds (2026-08-25, 2026-09-01 via the zero-ballast
  fold, 2026-09-08), and this round the generator was explicitly trying to
  satisfy `actorless-scene` and `named-entity-vacuum` by naming someone, which
  is the displacement chain the 2026-08-25 entry predicted. Two details for the
  entry when filed. First, the tenure number: "eleven years" and the 2026-08-25
  "nineteen years" are the same slot, a character card's one stat, and A2
  noticed the number was the only one in the piece spelled out rather than in
  digits, "the prose switches style precisely at the 'human touch' moment."
  Second, the ventriloquized aphorism (see fold-only below): when the character
  speaks, the line is a crafted antithesis in the author's voice.
- Mechanism guess: displacement (the presence and proper-noun rules demand a
  person; plan-then-write supplies one per function)

### em-dash-retier-evidence-5 [status: proposed]

- Found: 2026-09-08  |  Loop: self-play (evidence for the open em-dash thread)
- Evidence: 5 of 8 detectors read the absence of the banned marks as evidence
  of a scrub, unprompted, and three of them opened their verdict with it. A1:
  "Word-level tells are almost absent. That is itself the first tell." A2:
  "This reads like text that has passed through an anti-slop pass... It
  over-corrects into a second, quieter house style: minimalist, receipt-heavy,
  aphoristic." C2: "The surface is clean, which is exactly the problem." B2:
  "The word-level cleanliness is exactly what makes it suspicious."
- Source: self-play round 8 detector reports (samples A, B, C)
- Proposed change: No new argument; the count moves from 3/8 (2026-07-28) to
  7/12 (2026-09-01) to 5/8 here, and A2's phrase "a second, quieter house
  style" is the most compact statement of `counterculture-signature` a detector
  has produced. The thread is on the drafted `loop/scout-2026-09` branch
  already; this entry closes with it.
- Mechanism guess: n/a (aging; the ecosystem moved)

### Amendment: locally-plausible-globally-incoherent (third failure shape)

- Found: 2026-09-08  |  Loop: self-play
- Evidence: Both technical detectors found the same two holes and one found a
  third. C1: "A reboot kills every process on the box. If the reboot happened
  at 02:14 and cron fires at 02:15, there is one run, after the reboot. The word
  'again' and the 'still alive' process have no source. The sentence has the
  *shape* of a root cause without being one." C2, independently, the same
  sentence: "a process does not survive a reboot." Then C1 on the fix: "The fix
  converts a double invoice into a silent missing invoice... on retry after a
  failed render, the job now bails and the PDF is never produced." Both caught
  that the prose says "inside a transaction" and the code block has none.
- Source: self-play round 8 detector reports (sample C)
- Proposed change: Add two shapes to the 2026-09-01 amendment's runnable test.
  The first is a fix that resolves the stated failure by introducing an
  unstated one; check what the fix does on the failure path it was written
  for, not only on the happy path. The second is a claim in prose about the
  code that the code shown does not contain; on any piece with a snippet, read
  the snippet against every sentence that describes it. Both are checkable by
  a reader with no domain knowledge beyond the piece itself. Also a protocol
  note: the 2026-08-18 round showed that one coherence instruction prevents
  this, and the 2026-09-01 notes said the next round should give the
  instruction to all four samples or to none. This round gave it to none, and
  the technical sample failed again. The result is now: with the instruction,
  coherent (1 of 1); without it, incoherent (5 of 5 rounds). That is enough to
  stop treating the check as optional at generation time regardless of where
  the detect-mode rule ends up.
- Mechanism guess: n/a (generation coherence, not a style tell), unchanged

### Fold-only proposals (no new rule; merge into an existing one)

- **Ventriloquized aphorism** -> fold into `single-use-character`, and
  cross-reference `matched-antithesis-pairs`. When the one-line character
  speaks, the line is a balanced antithesis in the author's voice. A1 on
  "the queue looks the same length and the work inside it got harder": "The
  quote is too shaped to be a paraphrase of what a clerk actually said." A2:
  "Clerks don't talk in balanced antitheses; writers do. This is a paraphrase
  shaped for the screenshot." The `actorless-scene` rule asks for a quoted
  line, and this is what the slot gets filled with. Test: would that person say
  it that way? If the quote scans like the author's best sentence, it is the
  author's sentence with a name on it.
- **Emphatic tail clause** -> fold into `weight-assignment-phrases` as its
  clause-level form, with a cross-reference to the anti-em-dash displacement
  corpus entry. C1 and C2 both flagged, independently, "and does nothing else",
  "on purpose", and "with a note that says why": "Emphasis tail bolted onto a
  sentence that was already complete. Same family as 'and that's it.'" The
  weight-assignment entry covers a whole sentence that grades the one before;
  this is a trailing clause that does the same job inside the sentence, and it
  is where the em-dash aside went when the dash was banned. Delete-test: if the
  sentence is complete before the last comma and the tail adds emphasis rather
  than information, cut the tail.
- **The first-timer who gets nothing wrong** -> fold into
  `monotonic-recall-order` (2026-08-11) as a third variant beside order and
  elided duration. B1 on the wheel-truing sample: "The procedure is described
  flawlessly and in the correct order... A first-timer's account usually
  includes at least one thing they got wrong first (over-tightening, chasing
  the wobble around the wheel)." D1 on the starter post: "Everything stated is
  textbook-correct... Real novices often carry one wrong assumption." Same
  mechanism as the other two variants: the account was planned from the
  correct procedure rather than recalled from the attempt, and planning omits
  the wrong turn. Guard, per `counterculture-signature`: do not manufacture an
  error; report the one that happened, or report none and accept the tell.
- **Multi-axis informality read as human** -> evidence for the open
  single-axis-humanization consolidation (2026-08-11), from the other side.
  Both casual detectors returned human, and both cited the same thing: mixed
  "i"/"I" capitalization alongside dropped apostrophes, mid-phrase "like"
  hedges, and a trailing thought with no period. D1: "That pattern (phone
  autocorrect catching some, not others) is hard for a model to produce; models
  imitating lowercase style go uniformly lowercase." D2 read the same
  inconsistency as "either a human on a laptop with occasional autocorrect, or
  a model sprinkling lowercase to look casual," and still called it human. The
  consolidation predicts exactly this: variance on several axes at once reads
  as typing, uniform variance on one reads as a filter. Two rounds of
  fresh-eyes evidence now sit on each side of that prediction.
- **Title template** -> one example for the slot-fill phrases list in
  `patterns.md`, if the writer wants it. C2 only: "Title: '..., and the retry
  bug it exposed.' The ', and the X it exposed/taught us' title template."
  Single detector, single sample, logged so it is not rediscovered.
- **Every paragraph lands on the shortest sentence** -> a countable form for
  `punchline-terminal-paragraphs`, to sit beside the simonw measured forms
  folded on 2026-09-01. C2: "Seven paragraphs, each two to four sentences, each
  ending on the shortest sentence in the paragraph." B1 and B2 both listed the
  five closing clauses of the blog sample as a block. The check is mechanical:
  for each paragraph, is the last sentence its shortest? Three or more in a row
  is the tell.

### Round notes: misses, protocol, branch state

1. **The FATAL binary-contrast family shipped again, in two of four samples,
   after one clean round.** "The clerks did not get faster. Two of them told me
   the opposite" (A1 and A2 both named it negate-then-correct) and "That was
   the easy half. The hard half was that..." (C1: "a symmetric hinge is a
   classic generated transition"; C2: "mirrored antithesis pivot"). Seven of
   eight rounds now. The 2026-09-01 clean round was sample variance, as that
   note allowed for. The discrete-pass recommendation from 2026-07-28 remains
   the cheapest unactioned item in the file.
2. **The generator this round was not isolated, and the round should be read
   accordingly.** The main session wrote the samples after reading roughly
   1,000 lines of this inbox, which is the 2026-08-11 confound repeated. The
   consequence is visible in the results: the samples avoided every named
   vocabulary tell and several open structural candidates, and the detectors
   flagged what was left, which was almost entirely already-open candidates.
   That is useful as a dedup-rate measurement and useless as a floor
   measurement. Next round should spawn four isolated generators per the
   2026-08-18 protocol; both that protocol and the two-instrument detector
   split are still not written into `weekly-loop.md`, which is why an
   unattended round can skip them.
3. **The drafted PR branch is stale and should not be pushed as it stands.**
   `loop/scout-2026-09` still exists locally only. Its merge base with
   `origin/main` is `2e3b9d6` (PR #2), and PRs #3 and #4 have merged since, so
   a diff against `origin/main` shows the branch removing the completeness
   verifier, the validation-tail entry, the mannered-prose entry, and
   `slop-09`. None of that is intentional; it is the branch being behind.
   Before the next PR leg pushes it, rebase onto `origin/main`, resolve the
   `patterns.md` and `living-corpus.md` overlap by hand, and rerun the eval
   gate (the report on the branch predates `slop-09`, so it must be regenerated
   to cover 9 fixtures rather than 8). Not done this round: step 6 runs only in
   a scout round, and a rebase touching `patterns.md` is a rule edit.
4. **Step 5 reconciliation.** `origin/main` and local `main` were identical at
   the start of the round (the 2026-09-01 round section reached origin through
   PR #4), so no reset was needed. This round's commit carries two sections:
   the uncommitted 2026-09-04 harvest section that the in-session capture left
   on the working tree, and this one.
5. **Inbox state.** This round adds 1 candidate, 2 evidence entries, 1
   amendment, and 6 fold-only proposals, and closes nothing. The dedup rate
   (25 of 26 distinct tells already on file) is the strongest signal yet that
   the inbox has saturated on the self-play loop's reachable tells and that the
   marginal weekly round is now mostly re-measurement. Two consequences worth
   the writer's attention: `single-use-character` has three rounds and 8/8
   detectors behind it and should lead the next PR, and the self-play leg's
   value now depends on either isolated generators (a floor measurement) or a
   different generating model (an aging measurement), not on more rounds of
   the same setup.

## 2026-09-11: shipped-diff harvest, Naperthrill issue 17

In-session capture (harvest.md path 1): the editor pass and the shipped version
both sat in one session, so the diff is labeled at ship time. Ledger entry:
`harvest/2026-09-11-issue-17.md`. Eleven story edits plus a weather and preview
rewrite. Most classify as content edits (a timezone correction, an accuracy
downgrade from a blanket claim to a single report, added ticket prices, digit
style) and are skipped per the classification rule. Two hunks are generation-side
signal, one of them a second round of evidence for an open candidate. No
flattened-voice hunks: nothing the floor stripped got restored.

### quantity-means-implication [status: proposed]

- Found: 2026-09-11  |  Loop: shipped-diff harvest
- Evidence: Two adjacent stories in one section reached for the same frame.
  "Nine hours means you can eat your way through it" and "Eleven hours means
  there is no wrong time to show up." A third item in the same issue landed a
  duration joke too. Each reads fine alone; together they read as a form. Edited
  to "Graze your way down one side and start over on the other" and "There is no
  wrong time to show up," which keep the duration as a stated fact and drop the
  inference scaffolding.
- Source: Naperthrill issue 17, stories 6968 and 6386 (draft -> shipped)
- Proposed rule: The shape is `<quantity> <unit> means <reader inference>`. The
  generator takes the one hard number a thin source supplies and manufactures
  significance from it, because the number is the only material it has. Family
  includes "X hours means", "at N dollars that is", "with N vendors you can".
  Test: strip the "means" clause. If the sentence still carries the fact and the
  clause was only telling the reader how to feel about a number, cut it. Note
  this is a per-document frequency tell, not a per-sentence one: a single
  instance is ordinary prose, which is why a per-story pass cannot see it and a
  whole-issue read can. Suggested Tier 2 with a per-document cap of one.
- Mechanism guess: thin-source compensation. When the source yields one number
  and little else, the number gets promoted from detail to thesis, and "means"
  is the cheapest bridge from datum to takeaway.

### second-person-conditional-premise-evidence-2 [status: evidence]

- Found: 2026-09-11  |  Loop: shipped-diff harvest
- Evidence: Five instances in a 15-item issue, one issue after the four-instance
  round that opened the candidate: "If you are a first responder", "If you see
  smoke", "If Saturday is spoken for", "If you skipped The Odyssey", "If you
  walk past it". Two survived the edit as voice (the headline where the
  conditional IS the service, and one alternate-date offer); three were rewritten
  to direct statements.
- Source: Naperthrill issue 17, stories 7792, 7641, 7794 (draft -> shipped)
- Bearing on the open candidate: confirms the per-document cap shape proposed on
  2026-09-04 rather than a flat ban, since the two kept instances are the ones
  whose "if" clause states a checkable condition ("if you see smoke", "if
  Saturday is spoken for") and the three cut ones assert a reader habit. That is
  the test the original entry proposed, and it held on a second, independently
  generated issue. Two rounds, nine instances.

### Fold-only proposals (no new rule; merge into an existing one)

- **Tail negation, into the negate-then-correct family.** Two hunks shipped the
  weaker cousin of the fatal pattern, where the negation trails instead of
  leading: "is a scheduled burn, not an emergency" and "the grounds are part of
  what you paid for rather than a backdrop." Current detection keys on the
  leading forms ("This isn't X, it's Y", "Not X. Y."). The trailing forms
  `<claim>, not <foil>` and `<claim> rather than <foil>` pass it. Same defect,
  same fix (state the claim, drop the foil); suggest extending the existing
  rule's surface rather than opening a candidate.

## Round 2026-09-15 (weekly loop)

Harvest: 3 ledger entries, and the first fetch-back the loop has confirmed at
the prose level. `2026-09-11-issue-17.md` (newsletter, Naperthrill issue 17)
was classified in-session on 2026-09-11 (the section above, which sat
uncommitted on main until this round's commit carried it). Fetch-back
SUCCEEDED: a plain curl with a browser user agent on `www.naperthrill.co`
returned the article page (HTTP 200, no Cloudflare challenge; the 2026-09-08
round got the challenge on the same host). The strip-to-text step was blocked
(`python3` needs approval in a headless run) and the summarizing fetcher
returned only 7 of the 15 stories, so the comparison was done by extracting
each story's text node from the raw HTML by its opening phrase and reading it
against the ledger. Result: the forecast, all 15 story bodies, and all 15
headlines match the ledger verbatim. Zero post-editor prose edits, zero new
harvest candidates beyond the in-session capture. One field differs: the page
subtitle (the Beehiiv meta description, set separately from the pasted body)
reads "Plus 13 wine tastings downtown and 60 vendors out at the Arboretum"
against the ledger's preview line, and no wine-tastings story exists in the
published body. Classified as a content edit in a field the body paste does not
carry; direction relative to the ledger undetermined; no prose signal. Entry
harvested; see the pruning note below. `2026-09-04-issue-16.md` was retried on the same
path and also SUCCEEDED (HTTP 200, no challenge): the forecast, all 19 story
bodies, and all 19 headlines match the ledger verbatim, which closes the
PARTIAL of 2026-09-08. Same subtitle-field discrepancy ("a 1915s style escape
room" against the ledger's "a 1915 code-breaking mission"), same
classification. Entry harvested. Pruning note: ledger hygiene says delete a
harvested entry, and this session's deletion-guard hook refused `rm`, so both
harvested entries were moved to `harvest/harvested/` (still under the
gitignored `harvest/`) instead. The top-level ledger no longer lists them, so
the next round will not re-harvest them; the writer can delete the subfolder
by hand. `2026-07-23-trimhero-gate-qt.md` could not be READ for the ninth
consecutive round: the symlink resolves into the private `anti-slop-local` repo
and the session's read permission for that path was not granted. Nothing
reconstructed; entry retained; the 2026-08-25 note stands.

Self-play: 4 samples (linkedin, blog, technical-blog, casual), fresh topics
(fine-free library operations, a garage tool library's first year, a nightly
report OOM fixed with a named cursor, a running-club chat about a shoe-drop
injury). Samples and a detector digest at `scratch/selfplay-2026-09-15/`
(gitignored). Both protocols the 2026-09-08 round asked for were applied.
Isolated generators: four subagents, each reading only `SKILL.md`,
`patterns.md`, and `living-corpus.md`, explicitly forbidden to open
`candidates.md`, `scratch/`, `harvest/`, and both protect lists; the main
session wrote none of the samples. Two instruments: eight standard detectors
(2 per sample, the weekly-loop prompt verbatim plus a request for a one-line
verdict with a percentage) and four hostile detectors (1 per sample, the same
prompt plus the 2026-08-25 forensic-coherence sentence), all tool-free, given
only the sample text. One deliberate change from 2026-09-01: the coherence
instruction went to all four generators, not only the technical one, as that
round's notes required. For the record, subagents ran on the session default,
which inherits the parent model unless configured otherwise: Claude Fable 5.1.
Verdicts, standard instrument: **8 of 8 called AI (70-85%)**, the first
unanimous standard pool since the 2026-07-22 bootstrap round (2026-08-18: 3 of
8; 2026-08-25 unmodified pool: 3 of 4; 2026-09-01: 4 of 8; 2026-09-08,
contaminated: 6 of 8). Hostile instrument: **4 of 4 called AI (72-85%)**. ~200
raw flags, ~36 distinct tells, 2 survivors after dedup, 3 evidence entries
against open threads, and 12 fold-only proposals. Ten of twelve detectors
described the text as output that had been through a de-slopping pass or
filter, and every one of them put the structural tells above the clean
vocabulary.

Scout: SKIPPED. Not the first run of the month; the 2026-09-01 round ran it.

Aging: SKIPPED. Not the first run of the quarter. Q4 opens with the first
October round, which owes the three things listed on 2026-08-18.

### affect-vacuum [status: proposed]

- Found: 2026-09-15  |  Loop: self-play
- Evidence: Four detectors, two samples, the same absence. B2 on the blog
  sample: "This is a story about neighbors damaging and losing your property,
  and there is not one feeling in it... A person who ate $140 has an opinion
  about it. A model told to remove mannered prose strips the reactions along
  with the adverbs, and what is left is affectless." B1, independently:
  "Interior life absent. Thirteen first-person verbs, all action ('started',
  'bought', 'paid', 'glued', 'switched') except 'imagined'. No surprise, no
  irritation, no 'I think.'" A2 on the linkedin sample: "Someone who was the
  lone skeptic and then sat through a hostile board meeting would leave some
  emotional residue: relief, irritation, vindication. There is none." A1: "The
  register is flat-confident throughout, including in the two places where it
  claims to have been wrong."
- Source: self-play round 9 detector reports (samples A, B)
- Proposed rule: The reaction half of spine rule 8, which asks for "a position
  and a pulse: react to facts." `stance-discharged-at-hook` (2026-09-08) covers
  the position half: the writer's view on the piece's central question is
  missing or parked in the hook. This covers the pulse half: events that would
  produce a reaction in the person who lived them arrive with none. Test: list
  the events in the piece that cost the narrator something (money, time, a
  public prediction, a lost tool). For each, find the sentence that reports how
  the narrator took it. If none exists, the reactions were stripped, and the
  piece reads as a ledger with a byline. Fix: report the reaction that actually
  occurred, in plain words, once or twice, where it occurred. Do not
  manufacture one; the emotional-flatline rule in `patterns.md` bans the
  claimed feeling, and this rule must not license it. Suggested Tier 2, blog,
  linkedin, and casual profiles; exempt on docs and technical reference, where
  neutral is correct. File together with `stance-discharged-at-hook` as one
  rule-8 entry with two positions rather than as two rules.
- Mechanism guess: displacement. B2 named the parent: the mannered-prose rule
  filed 2026-09-02, plus the confidence-calibration-adverb and
  emotional-flatline rules, remove the vocabulary a reaction is usually carried
  in ("frustrating", "honestly", "what surprised me"), and the be-concrete
  pressure fills the reaction slot with a figure. First candidate the loop has
  tied to the 2026-09-02 rule, which is two weeks old; if the dependence is
  real, the aging pass should see it fire more on Fable-class output, not less.

### instrumentless-precision [status: proposed]

- Found: 2026-09-15  |  Loop: self-play (hostile instrument)
- Evidence: Both hostile detectors that found no arithmetic contradiction found
  this instead, on different samples. Bh on the blog sample: "'In April and May
  the post-hole digger never sat on the shelf for more than two days' requires
  return dates on a first-names clipboard. Possible, not contradictory, but the
  precision of that claim does not match the sloppiness of a system that lost
  three tools." Ah on the linkedin sample: "'Most for the first time since
  2023.' For most of 1,400 reactivated cards to have last checked out in one
  specific year requires a mechanism (a 2022 amnesty, a policy start date) that
  is never given. Decorative precision." Also Ah: three staff hours spread
  across five branches "moved to holds... at Central" cannot be reassigned to
  one building.
- Source: self-play round 9 detector reports (samples A, B)
- Proposed rule: A figure that nothing in the piece contradicts, and that
  nothing in the piece could have measured. The four open specificity
  candidates cover rate (`metered-specificity`), texture (`canonical-detail`),
  kind (`named-entity-vacuum`), and confidence marking
  (`uniform-hedge-per-number`); the coherence thread covers figures that
  collide. This is the figure that stands alone: exact, load-bearing, and
  sourceless by the text's own account of its instruments. Test, checkable with
  no domain knowledge: for each precise claim, name the instrument in the text
  that produced it (a log, a ledger, a dashboard, a stated count). A clipboard
  of first names cannot yield a two-day return ceiling; a piece that never
  names a report cannot know the year 1,400 people last borrowed. Fix: name the
  instrument, or round the claim to what the narrator could know ("it was
  rarely on the shelf"). Suggested Tier 2, narrative, incident, and linkedin
  registers. Recommend filing as the fourth shape of the
  `locally-plausible-globally-incoherent` runnable test rather than as a fifth
  specificity entry: it is the same read (does the text support its own
  claims) applied to provenance instead of consistency.
- Mechanism guess: uncertainty-conditioning, the same as `named-entity-vacuum`:
  a count is unfalsifiable, so the be-specific pressure resolves into counts,
  and nothing asks whether the narrator could have counted.

### contraction-register-mismatch-evidence [status: evidence]

- Found: 2026-09-15  |  Loop: self-play (evidence for the open 2026-07-28 entry)
- Evidence: Six detectors, three samples, and in two of them the strongest
  single tell. A1: "Seven paragraphs of conversational first person with no
  contraction at all is the strongest single tell here." A2: "the combination
  of zero contractions in conversational first person... is what a model
  produces after an anti-slop pass." C1: "Zero contractions across 20 sentences
  of casual first-person narrative is edited or generated prose." C2: "That is
  an editor's fingerprint, not a person typing a postmortem." Ch: "Zero
  contractions in about 25 sentences." B2 caught the mismatch form in the one
  sample that did contract: "'That is what I'd tell anyone': uncontracted 'That
  is' beside contracted 'I'd' in the same sentence... The mismatch reads like
  contractions varied by rule."
- Source: self-play round 9 detector reports (samples A, B, C)
- Bearing on the open candidate: `patterns.md` carries no contraction rule at
  all, and the generators were isolated, so this is the floor's gap. The
  linkedin and technical samples went fully uncontracted under a first-person
  brief; the blog sample contracted once. The 2026-07-28 entry absorbs
  `strategic-de-contraction`, and the 2026-08-11 consolidation absorbs both into
  single-axis humanization; this round adds a register the entry did not list,
  technical-blog, where a first-person incident note reads as edited when it
  never contracts. Three rounds of evidence (2026-07-28, 2026-08-11,
  2026-09-15). Should ride the next PR beside `single-use-character`.
- Mechanism guess: pretraining-register (unchanged)

### coherence-instruction-tally [status: evidence]

- Found: 2026-09-15  |  Loop: self-play (evidence for the
  `locally-plausible-globally-incoherent` amendments)
- Evidence: The instruction went to all four generators. Results by sample. A:
  arithmetic and timeline hold (Ah: "175 min; $6.3M budget implied; $25/hr
  implied"); six soft framing incoherences, no hard one. B: no contradiction,
  timeline in order. D: one causal seam (Dh: the friend who evangelizes Altras,
  "whose entire brand pitch is zero drop," and the poster discovering the drop
  only after the injury: "two details chosen for texture separately and not
  checked against each other"). C, the technical sample, FAILED despite the
  instruction, with all three shapes on file. Shape 1, contradiction: "'was
  killed early on August 27' vs 'the scheduler reruns.' If so, the Aug 27 OOM
  was not one kill; it was a retry loop... The text treats it as a single event
  and never reconciles the two." Also "Until August a day was about 4 million
  rows" against a migration that "finished on August 25," which fits neither a
  ramp nor a step. Shape 2, the fix's failure path: rerun-from-the-first-row
  does not address a drop caused by the long transaction the named cursor
  itself opens; "never picks up a partial file" is not supported by code that
  writes to the final path. Shape 3, prose against code: "sums events"
  describes a loop that does `+= 1`; "the old cursor" and "the same staging
  copy" have no antecedent. Plus an arithmetic collision inside the text's own
  model: the stated memory accounting sums to about 25 MB against a claimed
  140 MB, "off by 5x," presented as matching.
- Source: self-play round 9 detector reports (all samples; hostile instrument)
- Bearing on the open thread: the 2026-09-08 tally read "with the instruction,
  coherent (1 of 1); without it, incoherent (5 of 5 rounds)." It is now 1 of 2
  with the instruction on the technical register, so the instruction is
  necessary and not sufficient, and the hostile instrument stays. Two
  additions for the runnable test. First, a fourth shape that only a domain
  reader can check, recorded as such: expertise incoherence, where the
  knowledge the piece performs does not match the decision it reports (Ch: the
  author explains libpq buffering and never mentions the `GROUP BY` that would
  return 12,000 rows instead of 19 million; "libpq-level detail without the
  practitioner's first instinct"). Second, the cost of the instruction, which
  three of four hostile detectors cited as evidence of generation: Bh, "no
  contradictions, and that tidiness is itself evidence... a model back-solves
  from the figure it already planted" ($150 deposit against a $140 repair); Ah,
  "The specifics cohere arithmetically because they were built to"; Dh, "every
  number reconciles exactly and the only hedge ('450ish') is on the one number
  that doesn't matter." That is the "perfectly reconciling arithmetic" clause
  of `metered-specificity`, produced on demand by the instruction meant to fix
  the opposite failure. Displacement from a generation-side instruction rather
  than a rule, and worth recording before the instruction is written into the
  loop file.
- Mechanism guess: n/a (generation coherence), with the displacement note above

### single-use-character-evidence-2 [status: evidence]

- Found: 2026-09-15  |  Loop: self-play (evidence for the open 2026-08-25 entry)
- Evidence: Fourth consecutive round. The casual sample carried exactly one
  named person. D1: "'because Dev won't shut up about them.' One named friend,
  dropped in a subordinate clause, never mentioned again. A single proper noun
  as a credibility token." D2: "The only proper noun besides shoe brands is
  'Dev,' a one-syllable friend name that functions as a plausibility token." Dh
  built the round's one causal seam on him. The other three samples carried no
  named person, and their detectors flagged the vacuum instead (B1:
  "Fifty-two households, one seized pump, one cracked guard, three missing
  tools, and not one person gets a name"; A2 and Ah: no trustee, no colleague,
  no city; C1, C2, Ch: no on-call name, no ticket, no artifact).
- Source: self-play round 9 detector reports (all samples)
- Bearing on the open candidate: the two entries this one is "distinct from"
  fired on the same round, on complementary samples. That is the argument for
  filing `single-use-character` and `named-entity-vacuum` together: a generator
  either supplies one person as a token or none at all, and both read as
  generated. The 2026-09-08 promotion stands; this round adds nothing to the
  rule and one more round to the count.
- Mechanism guess: instruction-tuning (unchanged)

### Fold-only proposals (no new rule; merge into an existing one)

- **Hollow confession** -> fold into `scheduled-humility-beat` as a content
  test beside its position test. A1 and Ah on the linkedin sample,
  independently: "I was the one in the room saying returns would slip" and
  "Staff time was the number I got most wrong" both confess an error without
  stating the prediction (Ah: "the humility is content-free; he never says what
  he predicted... both err in the direction that flatters the policy"). C1 and
  C2 on "I wrote that line in 2024": "maxim then mea culpa is a constructed
  beat"; "the bare year with no PR, no ticket." Test: a confession must contain
  the thing confessed, the prior number or the wrong belief. A candor-shaped
  sentence with nothing inside it is the slot without the move.
- **Unsignaled objection handling** -> fold into `zero-residue-argument`, with
  a displacement note. C1 and C2 both flagged the same paragraph: two reviewer
  objections ("why not fetchmany", "what about a dropped connection") answered
  back to back in one sentence each, never named. C2: "Pre-emptive objection
  handling that never names the objection is a model habit. A person writes
  'someone asked about dropped connections.'" The rhetorical-setups rule bans
  "What if...?" and "Here's what I mean:", so the question is cut and the
  answer stays, which is how a residue-free argument reads once the setups are
  gone.
- **Mid-piece maxim** -> fold into `universalized-maxim-closer`, which should
  not be limited to the close. C1 and C2 on "fetchall on a query with no LIMIT
  is a bug that surfaces when the table grows" ("a maxim dropped between two
  specifics"; "the lesson sentence move"); B1 and Bh on "Stock what people need
  twice a year and hate storing. Skip the aspirational tools" ("pull-quote
  aphorism"; "two-beat aphorism pair"). Same inflation, mid-paragraph. Also the
  topic-sentence template "X was harder than Y itself" (A1, A2, Ah), for the
  slot-fill list.
- **Voice tokens, and the informality that evaporates** -> fold into the
  single-axis humanization consolidation as examples plus one added check. D1
  and D2 on "Cool cool cool" (D2: "the single most common voice-token an LLM
  inserts when told to sound like a real person. Same tier as 'love that for
  me'"), trailing "honestly" (D1: "a bolt-on casualness marker"), and "So." as
  a one-word pivot (D1, D2, Dh). And D1's shape, which no open entry states:
  "The costume is all in the first two paragraphs: lowercase 'ok,' two comma
  splices, trailing 'honestly,' '450ish.' After that the prose tightens into
  clean, correctly punctuated short declaratives with zero errors. A person who
  writes comma splices in paragraph 2 keeps writing them in paragraph 5."
  Check: does the informal axis hold to the end of the piece, or was it applied
  to the opening and left to lapse?
- **The empty ask** -> fold into `reply-shaped-registers` as a casual-profile
  test. D2: "A PT rec request without a location is useless, and a real poster
  knows that... The ask is structurally complete and practically empty." No
  plan name, no shoe model, no race. Test: does the request contain what a
  responder would need to answer it?
- **Hindsight before discovery** -> fold into `monotonic-recall-order`, beside
  the 2026-09-08 "first-timer who gets nothing wrong" variant. D1 only: "'No
  rotating, no easing in.' The narrator writes the mistake with hindsight
  clarity before the paragraph where they claim to discover it ('THEN I looked
  it up')... The prose knows the answer while pretending not to." Same cause,
  planned from the answer rather than recalled from the attempt. Dh's
  "pedagogical tell" is the same thing from the other side: "the injury
  sequence hits every step of the standard cascade in order with no noise...
  written from general knowledge, not from a body."
- **Paired paragraph openers** -> fold into `matched-antithesis-pairs`,
  extending it from adjacent sentences to adjacent paragraphs. C1, C2, and Ch
  all flagged "With name=, psycopg2 declares..." / "Without name=, libpq
  receives..." as consecutive paragraph openers, and C1 and Ch the before/after
  RSS measurements in matched syntax across paragraphs. D1 and D2 flagged "12
  to 0" mirrored by "10 vs zero" two paragraphs apart (D2: "Once is a person.
  Twice is a pattern.").
- **Label-then-gloss** -> fold into the anti-em-dash displacement corpus entry
  as a third relocation site. Ch: "'exit code 137. That is the OOM killer.' /
  'The fix is a named cursor. DAY_SQL is the old SELECT, unchanged.' Same shape
  twice: a flat statement, then a one-line explanatory aside as its own
  sentence." The aside the dash used to carry now stands as its own sentence;
  the entry lists colons and paired commas and should list this.
- **Variance by the paragraph, not the sentence** -> evidence for the clumping
  test (2026-08-25 amendment). Ch: "Paragraphs 1 through 5 and 7 are all short
  declaratives (4 to 19 words, most under 14). Paragraph 6 is two long compound
  sentences of 28 and 26 words, and both use the same 'X, so Y' hinge. One
  paragraph of long sentences inserted for variety, and even that paragraph is
  internally symmetric." B1's "long-then-shorter, always: no long sentence is
  ever followed by a longer one" is the same measurement on the blog sample.
- **Count-then-enumerate topic sentence** -> one example for the signposting
  bullet. B1 and Bh on "Two things broke.": "count-noun
  announce-then-enumerate"; "announces a count, then delivers exactly two, each
  in cause-then-resolution form."
- **Style-guide consistency as a tell** -> fold into
  `clean-mechanics-in-casual`, widening it past casual. B2: "'Fifty-two
  households' spelled out at sentence start; '34' and '91' as digits
  mid-sentence. Correct AP style, automatically applied." C2: "'million' spelled
  out both times rather than mixing '4M'. Humans are inconsistent with units;
  editors are consistent." Ch: "'about 4 million' and 'about 12,000' but '19
  million' with no 'about.'" Same mechanism as the casual entry, on blog and
  technical registers.
- **Title formula** -> one more example for the 2026-09-08 title-template note:
  Bh, "The title formula 'X, year one.'"

### Round notes: verdicts, harvest path, protocol, branch state

1. **The unanimous standard pool is the round's headline, and it should be
   read against the setup, not only the floor.** Two things changed at once
   from 2026-09-01: the generators were isolated (a floor measurement, per the
   2026-09-08 note 2) and the coherence instruction went to all four. The
   verdict rate moved from 4 of 8 to 8 of 8. The isolated-generator rounds
   without the instruction (2026-08-18, 2026-08-25) sat at 3 of 8 and 3 of 4.
   One reading is that the instruction costs more in tidiness than it buys in
   coherence; three hostile detectors said so in as many words (the tally
   entry above). Another is that the floor itself has drifted: every detector
   this round read the absence of vocabulary tells as evidence, which is
   `counterculture-signature`'s prediction arriving. The next round can
   separate the two by giving the instruction to two generators and not the
   other two, holding isolation constant.
2. **The FATAL binary-contrast family did not ship in any of the four
   samples.** No detector flagged a negate-then-correct construction. A2 noted
   one soft instance ("We kept the part that does": "they asked what stops
   people; we kept the thing that stops people") and read it as a callback
   rather than a reversal. Second clean round of nine (the other was
   2026-09-01). The discrete-pass recommendation from 2026-07-28 remains
   unactioned; two clean rounds under isolated generators are the first
   evidence that the floor can produce this without a discrete pass, and not
   yet enough to retire the recommendation.
3. **The harvest fetch-back path works, and the loop notes describe the wrong
   failure.** Nine rounds of harvest notes say fetch-back fails on permission
   scope. This round the newsletter path succeeded on a plain curl with a
   browser user agent, on both pending entries, and the blocker moved to the
   strip step (`python3` needs approval in a headless run) and to the
   summarizing fetcher (7 of 15 stories returned). The workaround,
   grep-extracting each story's text node by its opening phrase and reading it
   against the ledger, is manual and complete, and it is what confirmed both
   issues at the prose level. `harvest.md` should say: curl the page, grep the
   story bodies, do not rely on WebFetch for a diff. The x.com entry stays
   blocked for the reason the 2026-08-25 note gives, unchanged.
4. **Step 5 reconciliation.** `origin/main` sits at `0d02388` (PR #4). Local
   `main` carries one unpushed round commit (2026-09-08) that origin does not
   have, so per the rule local main was not reset. This round's commit carries
   two sections: the uncommitted 2026-09-11 harvest section that the
   in-session capture left on the working tree, and this one. `main` was not
   pushed.
5. **Step 6 SKIPPED (not a scout round), and the drafted branch is still
   stale.** `loop/scout-2026-09` exists locally only, in the state the
   2026-09-08 note 3 describes: its merge base predates PRs #3 and #4, so it
   must be rebased onto `origin/main`, its `patterns.md` and
   `living-corpus.md` overlap resolved by hand, and its eval report regenerated
   over 9 fixtures before anyone pushes it. Not touched this round.
6. **Inbox state.** This round adds 2 candidates, 3 evidence entries, and 12
   fold-only proposals, and closes nothing. Two consequences. First, the drain
   queue for the next PR has three entries with three or more rounds each:
   `single-use-character` (4 rounds; 8 of 8 detectors on 2026-09-08, 3 of 12
   here with the vacuum flagged on the other nine), `contraction-register-
   mismatch` (3 rounds; 6 of 12 here), and `punchline-terminal-paragraphs`
   with `one-job-per-paragraph` (each flagged by 12 of 12 detectors this round,
   and by every round since 2026-07-22). Second, `affect-vacuum` is the first
   candidate tied to the 2026-09-02 mannered-prose rule, and it is the kind of
   displacement the size budget exists to catch: a Tier 1 rule two weeks old
   with a side effect already visible to outsiders. File it with
   `stance-discharged-at-hook`, or add the guard to the mannered-prose entry,
   before the next scout PR adds anything else.
