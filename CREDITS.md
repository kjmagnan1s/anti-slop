# Credits

anti-slop consolidates and extends three prior open-source writing skills. Each
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
  (directness / rhythm / trust / authenticity / density).

### no-ai-slop
- Author: Peter Yang (github.com/petergyang/no-ai-slop)
- License: MIT
- Contributed (folded in 2026-07-22, after the consolidation): the
  faux-insight-setup pattern ("what most people get wrong"), the colon-reveal
  pattern, the fake-profound-kicker pattern, and the practice of extracting 3-5
  voice signals from a draft before editing when no voice spec exists.
- Note: anti-slop is not a fork of no-ai-slop; the rest of its catalog was
  already covered by the three sources above.

## What anti-slop adds

- One deduplicated rule library instead of three overlapping ones.
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
