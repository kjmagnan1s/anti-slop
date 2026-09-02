# Gate run: mannered prose and dense prose

Branch: `feat/mannered-prose-density`
Commit under test: the branch head at the time of this report, see PR
Run date: 2026-09-02
Run by: the authoring agent (Claude Code, driven by the repo owner), manual
read of the owner's local golden set; the golden files are gitignored so this
half is reproducible only on the owner's machine

Candidate under gate: the `mannered prose` corpus entry and the two pattern
bullets it files, `Mannered prose` (P1) and `Dense prose` (P2).

## Slop side

| fixture | result | missing flags |
|---------|--------|---------------|
| slop-01-linkedin | pass | none |
| slop-02-blog | pass | none |
| slop-03-technical-blog | pass | none |
| slop-04-investor-email | pass | none |
| slop-05-docs | pass | none |
| slop-06-casual | pass | none |
| slop-07-blog | pass | none |
| slop-08-linkedin | pass | none |
| slop-09-technical-blog | pass | none |

`slop-09-technical-blog` produces both expected flags, `mannered prose` and
`dense prose`. The eight existing fixtures are unaffected: no expected flag was
lost to the two new matrix rows.

## Golden side

| fixture | P0 hits | P1 hits | offsets |
|---------|---------|---------|---------|
| golden-01 | 0 | 0 | none |
| golden-02 | 0 | 0 | none |
| golden-03 | 0 | 0 | none |
| golden-04 | 0 | 0 | none |
| golden-05 | 0 | 0 | none |
| golden-06 | 0 | 0 | none |

Mannered prose at P1: zero hits across all six files. No span where a metaphor
stands in for a direct statement is present in the set. The nearest candidate
sits in golden-04 and is a literal verdict, not a metaphor standing in for a
statement, so it is not flagged.

Dense prose at P2: one hit, recorded. Longest sentence in the set is 41 words.
Per-paragraph counts for every golden paragraph over 90 words, run at the blog
profile, where the bar is a paragraph past ~100 words with no break and more
than half its sentences over ~30 words:

- golden-04, paragraph 2: 126 words, 6 sentences, 2 over ~30 words. No
  majority, so it does not fire.
- golden-04, paragraph 3: 120 words, 5 sentences, 0 over ~30 words. Does not
  fire.
- golden-05, paragraph 3: 143 words, 7 sentences, 1 over ~30 words. Does not
  fire.
- golden-06, paragraph 3: 101 words, 3 sentences, 2 over ~30 words, character
  offset 434. Both halves are met, so this one fires: one P2 golden hit for
  dense prose.

Per `evals/README.md`, a P2 golden flag is recorded and does not fail the gate.
That hit is the reason dense prose stays at P2 and not higher: the paragraph
sits at the approximate ~100-word edge of the bar, so a stricter tier would
fail the gate on real human prose.

## Result

Both sides pass. No golden P0 or P1 hit, so the P1 tier on mannered prose
stands. One P2 golden hit for dense prose is recorded (golden-06, character
offset 434) and does not fail the gate. No missing flag on the slop side.
