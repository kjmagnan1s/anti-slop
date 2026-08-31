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
   file under `scratch/`, which the repo gitignores, so nothing a round writes
   can be swept into a commit.
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

Start by reconciling with origin: `git fetch origin`. If `origin/main` moved
since the last round (the previous month's PR merged) and its
`references/candidates.md` already contains every round section that sits on
local main, reset local main onto it: `git reset --hard origin/main`. The
squash merge already carries that content, and skipping this step leaves local
main permanently diverged from origin, which is what makes the next month's
branch base wrong. If any local section is missing from `origin/main`, do not
reset. Leave main alone and say so in the round summary.

Append one dated section to `references/candidates.md` using its entry format,
including a two-line round summary (samples generated, flags found, flags
surviving dedup, scout finds, aging proposals, PR opened or skipped). Commit
that path by name (`git commit references/candidates.md -m "chore: ..."`),
never `git add -A`: the round's scratch samples and detector reports are
working files, and a blanket add sweeps them into the repo. Never push main;
the only pushes are `loop/` branches through the PR leg below. Do not file
into the corpus or patterns on main.

## Step 6: propose-as-PR (runs only in a round where scout ran)

The inbox is where candidates wait; the PR is where they stop waiting. After
the round commits, take the cleanest candidates in the inbox and do the filing
legwork:

1. **Select.** Draw from the whole inbox, not only this month's finds. The
   backlog is where the cheapest moves are, and a selection pool scoped to the
   current month guarantees intake outruns drain. A candidate qualifies when it
   has a clear mechanism tag, survives dedup, and does not collide with the
   protect list. Rank in this order: retirements first (a retirement buys size
   budget instead of spending it, so it never counts against the cap), then
   consolidations that fold several entries into one, then threads proposed for
   three or more rounds, then this month's new finds. Cap: 3 rule additions or
   merges per PR, so review stays cheap. Everything else waits in the inbox.
2. **Draft on a branch.** `git fetch origin`, then cut `loop/scout-YYYY-MM`
   from `origin/main`, not from local main. Local main carries the unpushed
   round commits, so branching from it drags every one of them into the PR diff
   and breaks the cap. Bring the unpushed inbox sections over deliberately
   (`git cherry-pick origin/main..main`) so the evidence the PR cites is
   reviewable at origin and origin's inbox stays current; those sections are
   append-only, so the reviewable change is still the rule edits. Then make the
   real edit on top: a new or merged rule in `patterns.md`, a corpus entry, or
   a retirement (aging proposals ride the same PR). The size budget applies
   inside the PR: at budget, every add merges into an existing mechanism or
   retires an entry in the same commit.
3. **Run the eval gate locally, and commit the report.** The branch must still
   catch every `evals/slop/` fixture and flag nothing in `evals/golden/`.
   Golden is gitignored, so the reviewer cannot rerun that half, and a claim
   typed into the PR body is the same agent grading the rule it just wrote.
   Write the run to `evals/reports/scout-YYYY-MM.md` in the format that file's
   README defines and commit it on the branch, so the check is an artifact the
   reviewer can diff: one line per `evals/slop/` fixture with its ID, pass or
   fail, and any missing flag by name; one line per `evals/golden/` file with
   its ID, the flag severity, and the character offset of each hit. Record
   golden hits by ID and offset only, never by content, so the report is safe
   in a public repo. A rule that flags golden human prose is tiered down or
   dropped, not shipped.
4. **Push, open the PR, and get back to main.** `git push origin
   loop/scout-YYYY-MM`, then `gh pr create` with the body below. This is a
   standing, scoped exception to the repo's no-mistakes push rule: `loop/`
   branches only, decided 2026-08-27. Main is never pushed; no other branch is
   pushed. Then `git switch main` and verify it took: `git branch --show-current`
   must print `main` before the round reports done. A switch that fails on a
   dirty tree parks an unattended session on the loop branch, where next week's
   `candidates.md` commit lands on the wrong branch. On failure, commit or
   discard the stray working-tree changes and switch again; if it still fails,
   report the round as incomplete and name the branch it is stuck on.
5. **PR body.** Per change: the evidence (source links with dates), the
   mechanism tag, a link to the committed eval report, and what was merged or
   retired to pay for it.

A month with no qualifying candidates skips this step and says so in the round
summary. Do not lower the bar to have something to ship.

## Gate (runs at filing time, not in this loop)

When the writer approves a candidate, run the ingestion six-step, then the eval
gate: the proposed rule must still catch the `evals/slop/` fixtures and must
flag nothing in `evals/golden/`. A rule that flags golden human prose is
rejected or tiered down, not filed.

The monthly PR leg (step 6) runs this same gate before pushing, commits the
run to `evals/reports/scout-YYYY-MM.md` on the branch, and links it from the PR
body, so the reviewer reads an artifact rather than the authoring agent's
self-report. For those candidates, the writer's approval is the PR review:
merging is filing.

The size budget also applies (SKILL.md, Maintenance): fold candidates into
existing mechanism rules wherever possible, and at budget, every filing must
merge or retire something in the same commit. The loop's job is to keep the
rule set current, not to grow it.
