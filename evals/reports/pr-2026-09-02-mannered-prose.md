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

Dense prose at P2: zero hits. Longest sentence in the set is 41 words. Densest
paragraph is 143 words at 20 words per sentence. That paragraph exceeds the
~100-word half of the bar, but at a 20-word average it does not carry a
majority of sentences over ~30 words, so the second half is not met and the bar
does not fire. It is the one golden data point already over half the bar; a
later revision that lowers the ~30-word sentence bar, drops the majority
requirement, or switches the AND to an OR flags it.

## Result

Both sides pass. No golden P0 or P1 hit, so the P1 tier on mannered prose
stands; no missing flag on the slop side.
