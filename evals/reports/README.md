# Eval reports

Committed runs of the regression gate. The monthly PR leg
(`references/weekly-loop.md`, step 6) writes one file here per PR and links it
from the PR body.

## Why the artifact exists

`evals/golden/` is gitignored, so a reviewer cannot rerun the false-positive
half of the gate. Without a committed report, the only evidence that a proposed
rule leaves real human prose alone is a sentence typed into the PR body by the
same agent that wrote the rule. The report doesn't remove that trust gap, but it
turns the claim into something a reviewer can diff across months and something a
later run can contradict.

## Format

One file per PR, named `scout-YYYY-MM.md`. Two tables, plus a header line with
the branch, the commit under test, and the run date.

Slop side, one row per fixture in `evals/slop/`:

```
| fixture | result | missing flags |
|---------|--------|---------------|
| slop-01-linkedin | pass | none |
| slop-04-investor-email | FAIL | false-agency |
```

Golden side, one row per file in `evals/golden/`. Record hits by file ID,
severity, and character offset. Never quote the span: this repo is public and
the golden set is the owner's personal writing.

```
| fixture | P0 hits | P1 hits | offsets |
|---------|---------|---------|---------|
| golden-01 | 0 | 0 | none |
| golden-03 | 0 | 1 | 412 |
```

Any P0 or P1 hit on the golden side fails the gate. The rule gets tiered down
or dropped; it does not ship because the rest of the table looks good.
