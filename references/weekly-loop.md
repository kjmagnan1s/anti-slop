# Weekly loop: harvest, self-play, scout, aging

The scheduled read-path. Runs weekly on a cron session. Its only write target
is `references/candidates.md` (one dated section per run) plus a commit. It
never files into `living-corpus.md`, `patterns.md`, or the protect list; the
writer's approval and the ingestion six-step sit between the inbox and the
rules.

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

## Step 3: scout (wild evidence)

Go where people are actively cataloging AI tells:

- Run the last30days skill on: what people are identifying and complaining
  about as AI-written text tells / AI slop phrases (Reddit, X, HN, YouTube).
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
surviving dedup, scout finds, aging proposals). Commit with a `chore:` message.
Do not push. Do not file into the corpus or patterns.

## Gate (runs at filing time, not in this loop)

When the writer approves a candidate, run the ingestion six-step, then the eval
gate: the proposed rule must still catch the `evals/slop/` fixtures and must
flag nothing in `evals/golden/`. A rule that flags golden human prose is
rejected or tiered down, not filed.

The size budget also applies (SKILL.md, Maintenance): fold candidates into
existing mechanism rules wherever possible, and at budget, every filing must
merge or retire something in the same commit. The loop's job is to keep the
rule set current, not to grow it.
