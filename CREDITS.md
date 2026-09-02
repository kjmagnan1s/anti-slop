# Credits

anti-slop consolidates and extends prior open-source writing skills. Each
contributed something distinct, and each is credited here. The point of this
file is honesty about lineage: the rule lists are not original to anti-slop.

## Sources

### avoid-ai-writing
- Author: Conor Bronsdon
- License: MIT
- Contributed: the tiered vocabulary system (Tier 1 always-replace, Tier 2
  flag-in-clusters, Tier 3 flag-by-density), the context-profile matrix
  (linkedin / blog / technical-blog / investor-email / docs / casual), and the
  severity tiers (P0/P1/P2).
- Note: its vocabulary tiering was itself adapted from `brandonwise/humanizer`
  (github.com/brandonwise/humanizer), which is credited transitively here.

### humanizer
- License: MIT
- Basis: Wikipedia, "Signs of AI writing", maintained by WikiProject AI Cleanup.
  Wikipedia content is licensed CC BY-SA 4.0.
- Contributed: the content-pattern catalog (significance inflation, superficial
  -ing analyses, promotional language, false ranges, copula avoidance,
  negative parallelisms) and the adversarial self-audit step ("what makes this
  obviously AI? now fix it").

### stop-slop
- Author: Hardik Pandya (https://hvpandya.com)
- License: MIT
- Contributed: the false-agency rule (inanimate things doing human verbs), the
  expanded binary-contrast variant table, and the 5-dimension scoring rubric
  (directness / rhythm / trust / authenticity / density). The rubric was
  retired 2026-08-27 in favor of the two-question delivery gate.

### no-ai-slop
- Author: Peter Yang (github.com/petergyang/no-ai-slop)
- License: MIT
- Contributed (folded in 2026-07-22, after the consolidation): the
  faux-insight-setup pattern ("what most people get wrong"), the colon-reveal
  pattern, the fake-profound-kicker pattern, and the practice of extracting 3-5
  voice signals from a draft before editing when no voice spec exists.
- Contributed (folded in 2026-08-27): minimum effective edit as a spine rule,
  the portability test, and detect mode's no-authorship-claims rule (name the
  pattern; never declare the author a machine).
- Note: anti-slop is not a fork of no-ai-slop; the rest of its catalog was
  already covered by the three sources above.

### unslop
- Author: @poteto (github.com/cursor/plugins, pstack plugin)
- License: none carried here. Concepts only; no text or code was reused, so no
  upstream terms travel with anti-slop. Check the source repo before copying
  anything from it directly.
- Contributed (folded in 2026-08-27): the adding-soul doctrine (sterile,
  stanceless prose is also slop: have opinions, vary rhythm, let some mess in)
  and the single-question runtime self-audit ("what makes this obviously AI
  generated?"). Concepts adopted; text not copied.
- Note: unslop independently arrived at the portability test Yang also ships.
  Two independent inventions moved it into the spine.

### soundshuman
- Author: aashaexo (github.com/aashaexo/soundshuman)
- License: MIT
- Contributed (folded in 2026-08-27): the no-fabrication rule (a rewrite may
  not add any fact, name, number, date, or quote absent from the source) and
  the false-positive guardrails behind minimum effective edit (signs of human
  writing to preserve; judge clusters of tells, not isolated ones).
- Note: itself a consolidation of blader/humanizer, stop-slop, and
  brandonwise/humanizer, so its lineage overlaps anti-slop's own sources.

### I am just a text file (concept)
- Author: Ruben Hassid (ruben.substack.com/p/i-am-just-a-text-file)
- Contributed (2026-08-27): the taste-interview concept behind
  `onboarding/taste-interview.md` (taste is boundaries; the do-nots are the
  data). The questions in that file are original, and the corpus-first trim
  is ours.

### Prompting Claude Fable 5.1 (model documentation)
- Author: Anthropic, Writing density section
  (https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-fable-5-1#writing-density),
  read 2026-09-02.
- Contributed (2026-09-02): the definition of mannered prose behind the
  `mannered prose` corpus entry and the `Mannered prose` and `Dense prose`
  bullets in `references/patterns.md`. That definition is quoted verbatim in
  `references/living-corpus.md` for attribution and commentary; the rule text
  around the quote, the tiering, and the examples are our own.

## What anti-slop adds

- One deduplicated rule library instead of six overlapping ones: three
  replaced outright, three folded in later.
- The ingestion flow: a defined process for memorializing new tells, tagged to
  the generative mechanism that produces them.
- The living corpus: dated, mechanism-tagged tells caught in the wild.
- The protect-list seam: a per-byline overlay so the floor never strips a
  writer's genuine signatures.

## Licensing for distribution

anti-slop's own prose is MIT (see `LICENSE`). Example text in the humanizer /
Wikipedia lineage has been rewritten rather than copied verbatim, but the
underlying material is CC BY-SA 4.0. The Wikipedia-derived portions stay clearly
attributed here; if you adapt them further, keep the attribution and the
share-alike terms. This file serves as the NOTICE for that lineage. It is not
legal advice.
