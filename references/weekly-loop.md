# Weekly loop: harvest, self-play, scout, aging

The scheduled read-path. Runs weekly on a cron session; two legs run on a
slower calendar (scout: first run of each month; aging: first run of each
quarter). On main, its only write target is `references/candidates.md` (one
dated section per run) plus a commit. Rule edits happen only on `loop/`
branches through the PR leg (step 6); nothing lands in `living-corpus.md`,
`patterns.md`, or the protect list on main until the writer merges a PR. The
writer's approval and the ingestion six-step still sit between proposal and
rules; the PR leg just does the drafting legwork up front.

## Step 1: harvest pass

Run the fetch-back path from `references/harvest.md`. Diff each `harvest/`
ledger entry against its published version, classify hunks, queue candidates,
prune harvested entries. Empty ledger: note it and continue.

## Step 2: adversarial self-play

The loop that catches displacement tells: the new uniformities our own rules
create. A crackdown on one tell pushes the model to a different small set;
nobody notices from inside. So the detectors must be outsiders.

1. **Generate.** Write 4 fresh samples (150-250 words each) on realistic,
   varied topics, one per context profile: linkedin, blog, technical-blog,
   casual. Apply this skill in full while writing. Do NOT load any personal
   voice spec; the floor is what is under test. Save each sample to a scratch
   file.
2. **Detect.** For each sample, 2 detector agents that have NOT read this repo
   or any anti-slop material. They get only the sample text and this prompt:
   "Does this read as AI-written? Quote every phrase, structure, or rhythm that
   tips you off, and say why. Judge structure as well as words: sentence-length
   uniformity, seam monotony, symmetric paragraphs."
3. **Dedup.** Collect every flag. Drop anything `patterns.md` or
   `living-corpus.md` already covers. What survives is a candidate. Tag the
   mechanism per the ingestion taxonomy; if the tell looks like a side effect
   of one of our own rules (the model routing around a ban), tag it
   `displacement` and name the rule that likely caused it.
4. **Score the round.** Report flags-per-sample. A round with zero uncovered
   flags is a pass, not a failure to find; say so plainly.

## Step 3: scout (wild evidence; first run of each calendar month only)

Monthly, not weekly: last30days reads a 30-day window, so weekly runs re-read
three quarters of the same material. Go where people are actively cataloging
AI tells:

- Run the last30days skill on: what people are identifying and complaining
  about as AI-written text tells / AI slop phrases (Reddit, X, HN, YouTube).
- Run a second sweep on the other side of the trade: new anti-slop skills,
  humanizer prompts, and AI-writing systems people are shipping and praising.
  Competitors converge on the same rules fast; a technique two of them invent
  independently is high-confidence (the 2026-08 read found the portability
  test in both Yang's and poteto's skills). Diff anything notable against
  `patterns.md` before proposing.
- Fetch Wikipedia "Signs of AI writing" and compare against our coverage; that
  page is actively maintained by WikiProject AI Cleanup and was the humanizer
  lineage's source, so new signs there are pre-vetted.
- Each new tell becomes a candidate with a source link and a date. A tell
  people mock in public is a Tier 1 candidate; burned tells burn fast.

## Step 4: aging (first run of each quarter only)

Self-improvement includes forgetting. For each Tier 1/2 entry in the living
corpus, generate a few current-model samples in contexts where the tell used
to fire, and check whether it still does. Propose retire or re-tier for tells
that no longer appear. Stale rules are not free: every dead rule adds
over-correction pressure (see displacement).

## Step 5: report and commit

Append one dated section to `references/candidates.md` using its entry format,
including a two-line round summary (samples generated, flags found, flags
surviving dedup, scout finds, aging proposals, PR opened or skipped). Commit
with a `chore:` message. Never push main; the only pushes are `loop/` branches
through the PR leg below. Do not file into the corpus or patterns on main.

## Step 6: propose-as-PR (runs only in a round where scout ran)

The inbox is where candidates wait; the PR is where they stop waiting. After
the round commits, take the month's cleanest candidates and do the filing
legwork:

1. **Select.** A candidate qualifies when it has a clear mechanism tag,
   survives dedup, and does not collide with the protect list. Cap: 3 rule
   changes per PR, so review stays cheap. Everything else waits in the inbox.
2. **Draft on a branch.** `loop/scout-YYYY-MM`, branched from main. Make the
   real edit: a new or merged rule in `patterns.md`, a corpus entry, or a
   retirement (aging proposals ride the same PR). The size budget applies
   inside the PR: at budget, every add merges into an existing mechanism or
   retires an entry in the same commit.
3. **Run the eval gate locally.** The branch must still catch every
   `evals/slop/` fixture and flag nothing in `evals/golden/`. Golden is
   gitignored, so this local run is the only place the check can happen;
   record the results in the PR body. A rule that flags golden human prose is
   tiered down or dropped, not shipped.
4. **Push and open the PR.** `git push origin loop/scout-YYYY-MM`, then
   `gh pr create` with the body below. This is a standing, scoped exception to
   the repo's no-mistakes push rule: `loop/` branches only, decided
   2026-08-27. Main is never pushed; no other branch is pushed. Then
   `git switch main` so the next weekly run starts clean.
5. **PR body.** Per change: the evidence (source links with dates), the
   mechanism tag, the local eval results, and what was merged or retired to
   pay for it.

A month with no qualifying candidates skips this step and says so in the round
summary. Do not lower the bar to have something to ship.

## Gate (runs at filing time, not in this loop)

When the writer approves a candidate, run the ingestion six-step, then the eval
gate: the proposed rule must still catch the `evals/slop/` fixtures and must
flag nothing in `evals/golden/`. A rule that flags golden human prose is
rejected or tiered down, not filed.

The monthly PR leg (step 6) runs this same gate before pushing and records the
results in the PR body. For those candidates, the writer's approval is the PR
review: merging is filing.

The size budget also applies (SKILL.md, Maintenance): fold candidates into
existing mechanism rules wherever possible, and at budget, every filing must
merge or retire something in the same commit. The loop's job is to keep the
rule set current, not to grow it.
