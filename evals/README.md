# Evals: the regression gate

The regression gate for the learning loops. Harvest, self-play, scout, and aging
propose rules into `references/candidates.md`; nothing files into `patterns.md`
or `living-corpus.md` until it passes this suite (see the Gate section of
`references/weekly-loop.md`). The gate exists to stop rule bloat: a rule that
catches one new tell but starts flagging real human prose is a net loss.

## The two-sided check

A candidate rule passes only if both hold:

1. **Still catches known slop.** Detect mode over every file in `slop/` must
   produce every flag listed in that fixture's `expected_flags` frontmatter.
   Extra flags are fine. A missing flag is a regression.
2. **Flags nothing golden.** Detect mode over every file in `golden/` must
   produce zero P0 or P1 flags. P2 flags get recorded but do not fail the gate.
   A rule that flags golden human prose is rejected or tiered down, not filed.

## How to run it

Prompt-based, no code. Run the skill's detect mode over each fixture:

1. For each file in `slop/`, run detect with the `profile:` from its
   frontmatter. The frontmatter itself is metadata, not text under test.
   Compare output against `expected_flags`.
2. For each file in `golden/`, run detect (blog profile unless the file says
   otherwise). Confirm zero P0/P1.
3. When gating a candidate, run both passes with the candidate rule applied.
   The candidate must not lose any expected flag on slop and must not add a
   P0/P1 flag on golden.

Report per fixture: pass or fail, any missing flags by name, and any golden
P0/P1 hit with the offending span quoted.

## How it grows

Every corpus entry approved out of `references/candidates.md` contributes its
before-text as a new slop fixture: add a file under `slop/` with the profile it
was caught in and the new pattern named in `expected_flags`. The golden set
grows from the owner's real pre-AI writing; see `golden/README.md`.

When aging retires a rule, remove that flag from any `expected_flags` lists but
keep the fixture text. Old slop stays useful as a negative-drift check.
