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
groups deduped as already covered. Self-play results appended separately below.

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

### Round notes: generation-side misses (not candidates)

1. A tailing-negation binary contrast ("before you turn the thing on, not
   after") shipped despite the FATAL family being on the books. Rule exists;
   application missed it.
2. A conscious reroute around the faux-insight ban ("Nobody warned us about
   the GPS stamps") was still caught as the identical template slot. Rewording
   a banned phrase does not vacate the slot; the fix is structural.

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
