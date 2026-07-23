# Golden set

Real human prose the skill must never flag. This is the false-positive side of
the gate: a candidate rule that produces any P0 or P1 flag on these files is
rejected or tiered down, no matter how much slop it catches.

## Why this directory is empty in the repo

The contents are gitignored (see the repo `.gitignore`). This repo is public
and the samples are the owner's personal writing; only this README is
committed. Everyone who runs the gate seeds their own golden set locally.

## Seed your own

1. Collect 5 or more passages of your real writing, ideally from before you
   used AI tools, or writing you know is 100% yours. 100-300 words each.
2. Vary the register: a blog post, an email, working notes, something casual.
   The more registers, the more false positives the gate can catch.
3. Save each passage as `golden-01.md`, `golden-02.md`, and so on in this
   directory, with a one-line frontmatter note of where it came from:

   ```
   ---
   source: personal blog, March 2019
   ---
   ```

4. Do not edit the passages. The point is what your prose actually looks like,
   quirks included. A quirk a candidate rule would flag is exactly what this
   set is here to protect.
