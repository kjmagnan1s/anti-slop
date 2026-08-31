# Voice sources: the discovery manifest

Step 0.5 of onboarding, between "install" and the taste interview. "Bring 3-5
writing samples" is where onboarding funnels die; most people can't produce
good samples on demand. But almost everyone running an AI coding tool is
sitting on a voice corpus they forgot exists: their own prompts, dictation
history, and commit messages. This manifest is the map of where that corpus
lives and the rules for touching it.

## Three rules, non-negotiable

1. **Consent per source, loudly.** Detect paths first (names and counts only,
   no content). Propose each source with what was found: item count, date
   range, one example filename. Read only what the user approves, source by
   source. Session logs contain client work and secrets; treat every source
   as sensitive until the user says otherwise.
2. **Local only.** Extraction and profiling happen on the user's machine. Raw
   corpus never leaves it. The output is a derived profile (patterns,
   frequencies, quoted signature phrases); offer to delete intermediate
   copies when done.
3. **Register-tag everything.** Prompt history is working voice: commands to
   an agent. It is the right source for vocabulary, quirks, hedges, and
   signature phrases, and the wrong source for published-prose structure.
   Blend registers and every blog post starts sounding like a terminal
   command. Tag at ingest; never average across tags.

## The manifest

Paths are macOS. "Verified" means confirmed present on the reference machine
(2026-08-28); absence elsewhere is normal, detection handles it.

### Dictation and transcription (register: dictated-spoken; highest value)

- **VoiceInk** — `~/Library/Application Support/com.prakashjoshipax.VoiceInk/`
  (`default.store` SwiftData/SQLite holds transcription history; `Recordings/`
  holds audio). Verified.
- **Wispr Flow** — `~/Library/Application Support/Wispr Flow/` when installed;
  history in its local database. Not present on the reference machine, but its
  exported history built the reference corpus.
- **superwhisper** — `~/Documents/superwhisper/` (per-recording folders with
  `meta.json` transcripts).
- **MacWhisper / Aiko** — app containers under `~/Library/Containers/`;
  detect by bundle id.
- **Apple Voice Memos** —
  `~/Library/Group Containers/group.com.apple.VoiceMemos.shared/Recordings/`.
  Audio only; needs a transcription pass before it counts as corpus. Verified
  (4 recordings).

### Agent session history (register: prompt-working; highest volume)

- **Claude Code** — `~/.claude/projects/*/[session].jsonl`. Extract user-turn
  content only; never tool outputs, never assistant turns (assistant text is
  the contamination this whole system exists to avoid). For dictation users
  this source is literally spoken voice, captured daily. Verified (156
  project directories).
- **Codex CLI** — `~/.codex/sessions/` (JSONL rollouts; same user-turns-only
  rule). Verified.
- **Gemini CLI** — `~/.gemini/tmp/` session state. Verified.
- **Cursor** — `~/Library/Application Support/Cursor/User/workspaceStorage/`
  (`state.vscdb` per workspace; chat is buried in SQLite blobs). Best-effort;
  skip on any parse trouble. Verified (10 workspaces).

Recency window for all session sources: last 30 days by default, expandable
on request. Volume floor: a source needs roughly 50+ user turns before its
frequencies mean anything.

### Authored text (register: published / notes-working)

- **Git commit messages** — `git log --author=<user> --format=%B` across the
  user's repos. Authored, terse, plentiful. Register: notes-working.
- **Blog posts, newsletters, social exports** — user points at them. The only
  source group where structure (openers, closers, paragraph shape) should be
  learned. Register: published.
- **Obsidian / notes vaults** — user points at a vault. Ask before touching
  any shared or team vault; a business vault with a co-founder in it is not
  the user's solo voice. Register: notes-working.

### Out by default (propose only if the user brings them up)

- **iMessage** (`~/Library/Messages/chat.db`): personal correspondence;
  scanning it uninvited is how the product dies. Also remember the owner's
  rule: the personal stays human-written, so it is thin voice evidence for
  outbound anyway.
- **Email**: same category.
- **Anything belonging to another person** in a shared folder or vault.

## The consent flow

1. **Detect.** Stat the manifest paths. Output: source name, present or
   absent, item count, date range. No content read.
2. **Propose.** Show the table. The user approves sources individually; an
   unchecked source is never read.
3. **Extract locally.** User turns, transcripts, commit messages into a raw
   corpus file per source, register-tagged.
4. **Profile.** Compute the fingerprint (below) and pull candidate signature
   phrases with quoted evidence.
5. **Review.** Show the derived profile. The raw extracts stay on disk where
   the user can read them; offer deletion once the profile is accepted.

## What the profiler extracts

Frequencies and patterns, with quoted examples for each claim:

- Signature phrases and pet vocabulary (recurring n-grams that are theirs,
  not the language's)
- Openers and closers by register
- Hedge words and the hedge-to-commit ratio
- First-person density, question-mark rate, exclamation rate per 1k words
- Sentence-length distribution (median and spread, not just the mean)
- Profanity pattern if any (frequency, placement, function)
- Punctuation habits: fragments, comma splices, parentheticals, dash use
- Words they never use (absence is taste too; feeds the personal ban list)

Everything lands in the same shape as the reference corpus: raw JSONL per
source, a classified pass, a quantitative fingerprint, and the compiled voice
spec. Reference implementation (built by hand before this manifest existed):
`wispr.jsonl` + `voiceink.jsonl` -> `classified.jsonl` ->
`quantitative_fingerprint.md` + `voice_fingerprint.md` + `anti_patterns.md`
-> the voice spec. The manifest exists so the next person gets that pipeline
without the weeks of hand work.

## Seams

- The **taste interview** (`taste-interview.md`) runs after this. Corpus
  answers the style questions; the interview covers only what no sample can
  show (beliefs, hard nos, registers under pressure).
- The **protect list** (`../references/protect-list.md`) is a direct output:
  verified signature phrases become protected signatures the de-slop floor
  must never strip.
- The **contamination guard** applies end to end: assistant-generated text is
  never corpus. If a source mixes user and machine text, extract the user
  side only or drop the source.
