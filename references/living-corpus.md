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
