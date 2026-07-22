# Shipped-diff harvest (loop 1)

The highest-signal learning input this skill can get: the gap between what it
produced and what actually shipped. Every hunk the writer edits by hand is a
labeled example. Either the floor missed a tell, or it flattened voice. Both are
rule changes waiting to be filed.

## Capture paths, in order of preference

1. **In-session (automatic, no user action).** When a shipping flow holds both
   the skill's final output and the shipped version in context (a newsletter
   editor pass, a tweet approval, any session where the final gets pasted back
   or approved), run the classification below at ship time.
2. **Fetch-back (the weekly loop).** At ship time, save the skill's final text
   to `harvest/` (a gitignored local ledger; one file per piece with date,
   surface, URL when known, and the full text). The weekly loop fetches the
   published version and diffs it against the ledger. Covers edits made outside
   any session, as long as the piece is publicly fetchable.
3. **Paste fallback (manual, rare).** The writer pastes final copy marked
   `shipped:`, symmetric to `slop:`. Only needed when the copy was edited
   outside a session AND is not fetchable (a sent email, a DM).

## Classification

For each diff hunk (skill output -> shipped version), assign one of three:

- **Missed tell.** The writer removed or rewrote something the floor should
  have caught. Becomes a corpus candidate; run the ingestion six-step on it.
- **Flattened voice.** The writer restored something the floor stripped.
  Becomes a protect-list candidate. Also check whether the floor rule that
  caused it needs a tier-down or a context-profile exception.
- **Content edit.** The meaning changed: new facts, cut sections, restructure.
  Not a slop signal. Skip.

When unsure between missed-tell and content-edit, ask what the hunk did to the
prose, not the argument. A swapped word with the same meaning is signal; a new
sentence with new information is not.

## Filing

Candidates go to `references/candidates.md`, never straight into the corpus or
patterns. The ingestion friction dial still governs the final write: the writer
approves inbox entries, then the six-step and the eval gate (`evals/`) run
before anything is filed.

## Ledger hygiene

`harvest/` is local-only (gitignored) because it holds full pre-publication
drafts. Prune entries once harvested. If the ledger is empty on a weekly run,
say so and move on; do not reconstruct drafts from memory.
