# Living corpus

Dated AI tells caught in the wild, each tagged with the mechanism that produces
it. This is the part of the skill that compounds. Grow it with the ingest flow
(`ingestion.md`). Entry format is defined there.

Tells age. Re-tier or retire entries as the models change. Note the date so we
can see how fast a tell rises and falls.

---

### anti-em-dash displacement

- Added: 2026-06-21  |  Tier: context-dependent
- Mechanism: displacement
- Context: A second-order tell. Now that every slop skill flags em dashes, models
  shunt the same "punchy aside" rhythm into colons and comma-spliced
  appositives. The punctuation changed; the metronome did not. Flag when the
  colon-or-appositive rhythm repeats across several sentences, not on a single
  clean use.
- Before: "The fix is simple: stop. It works, a clean little loop, every time."
- After: "The fix is simple. Stop. It runs as a clean loop every time."
- Rule: Removing em dashes is not enough. Check whether the same interruptive
  rhythm just moved into colons or paired commas. Vary the sentence shape, not
  only the punctuation mark.
- Source: my own output (Claude, Opus-class)

---

### concession reflex

- Added: 2026-06-21  |  Tier: 2
- Mechanism: reward-tuning
- Context: "To be fair, X. That said, Y." dropped in to simulate balance when
  there is no real counterpoint. avoid-ai flags false concession as a structure;
  the tell here is the tic-frequency, the reflex to both-sides even trivial
  points. Fine once when there is a genuine tradeoff; a tell when it is reflexive.
- Before: "To be fair, the tool has limitations. That said, it is still useful."
- After: "The tool is useful for X and weak at Y." (or just state the limitation)
- Rule: Do not manufacture balance. If there is a real counterpoint, name it
  specifically. If there is not, drop the concession and make the claim.
- Source: my own output (Claude, Opus-class)

---

### validation tail

- Added: 2026-07-24  |  Tier: 1
- Mechanism: displacement (from assistant-persona)
- Context: The reply-and-quote-tweet descendant of "great post." Once overt
  flattery is banned, the approval reappears as a subordinate clause bolted to
  the end of a genuine fact, so it reads like part of the receipt instead of a
  compliment. It survives every existing check because it is first person, never
  addresses the reader, and rides behind real specifics. Variants all share one
  frame, "[my real fact], so this one <verb of impact>": lands, hits, tracks,
  resonates, hit home, hits different, stings, is real, plus the fronted form
  ("which is why this lands") and the standalone ("this one hit me"). A tell in
  every register. NOT this pattern: a specific verdict on the thing itself
  ("nice no frills article about loops"), which is direct and falsifiable, and
  is the first move of a reaction-with-receipt reply. The test is whether the
  clause describes the source or reports your reaction to it.
- Before: "I have 52 skills installed, and Compound Engineering sits in my
  pipeline the same way, so this one lands."
- After: "I have 52 skills installed, and Compound Engineering sits in my
  pipeline the same way."
- Rule: Never append a clause reporting that something landed, hit, or tracked.
  If you have stated an overlapping fact, the relevance is already proved and
  the tail is flattery wearing a receipt's clothes. Delete it and let the fact
  do the work. If you have not stated one, the tail is the only content you had,
  which means there is no reply worth posting.
- Source: caught in the wild in the owner's own draft reply, 2026-07-24

---

### mannered prose

- Added: 2026-09-02  |  Tier: 1
- Mechanism: reward-tuning (vivid phrasing rated as "engaging"), with a
  density side effect on Fable-class models
- Context: Anthropic's own prompting guide for Claude Fable 5.1 names two
  regressions relative to Fable 5: prose that is denser (longer sentences,
  fewer paragraph breaks) and a habit of substituting metaphor and flourish
  for direct statement. Their definition: "Mannered prose substitutes metaphor
  and flourish for direct statement... The phrases exist to display the writer,
  not to convey the idea, and readers can tell... Metaphors drag in
  connotations the writer did not choose and cannot control. The fix is to say
  what you mean. When a literal phrase is available, use it." This is the
  mechanism the skill's scattered metaphor rows (landscape, symphony, embrace,
  ecosystem) and the fake-profound kicker were examples of. It also collides
  with spine rule 8 (sterile is also slop) unless that rule says where a pulse
  comes from: a position, never a flourish. NOT this pattern: any phrase on a
  byline's protect list, including pet metaphors and coined terms ("lock in",
  "playbook"); the byline chose those connotations, so do not surface them as a
  collision.
- Before: "Temperature is a dial worth turning here, and the caching layer
  earns its keep once the corpus grows past a few thousand documents, which is
  the point at which the naive approach starts to buckle under its own weight."
- After: "Temperature is a parameter worth varying here. The caching layer
  still matters once the corpus passes a few thousand documents. Past that,
  the naive approach gets slow."
- Rule: When a literal phrase is available, use it. Replace a metaphor that
  stands in for a statement with the statement. Separately, break a sentence at
  its second clause and a paragraph at its second idea when the text runs
  dense. Short prompt form for ad hoc use: "Remove all mannered prose. Say what
  you mean. When a literal phrase is available, use it."
- Source: Anthropic, "Prompting Claude Fable 5.1", Writing density section,
  https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-fable-5-1#writing-density
  (read 2026-09-02)
