# anti-slop

<p align="center">
  <img src="assets/hero.png" alt="anti-slop" width="100%" />
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-8B3BFF?style=for-the-badge" alt="MIT license" /></a>
  <img src="https://img.shields.io/badge/Claude_Code-skill-3FE9FF?style=for-the-badge&labelColor=08080B" alt="Claude Code skill" />
  <img src="https://img.shields.io/badge/em_dashes-0-08080B?style=for-the-badge" alt="zero em dashes" />
</p>

<p align="center"><b>One maintained skill that strips AI slop out of writing: detect it, rewrite it, and memorialize new tells as the models change.</b></p>

anti-slop is the floor. It catches the words, rhythms, and structures that mark text as machine-written, and it leaves a writer's real voice alone through a protect-list seam. It consolidates and replaces three earlier skills (avoid-ai-writing, humanizer, stop-slop) into one spec that stays alive instead of going stale.

## See it work

<p align="center">
  <img src="assets/anti-slop.gif" alt="anti-slop annihilating generic AI text" width="100%" />
</p>

## Install

Clone it straight into your skills directory:

```bash
git clone https://github.com/kjmagnan1s/anti-slop.git ~/.claude/skills/anti-slop
```

Or symlink it into a single project:

```bash
git clone https://github.com/kjmagnan1s/anti-slop.git ~/src/anti-slop
ln -s ~/src/anti-slop /path/to/project/.claude/skills/anti-slop
```

It is plain markdown, so any agent that reads skills can use it. In Claude Code, ask it to "de-slop this," "rewrite to remove AI tells," or "audit this for AI writing," and the skill loads.

## Why this exists

The rule lists are commodity. Every "humanize my AI" tool ships the same blocklist, and every one of them goes stale in months, because the trigger to update it is a maintainer's calendar. The tells move faster than that. The delve and tapestry era already burned. The new ones are second-order: a punchy aside shunted out of an em dash and into a colon, balance manufactured where there is no real counterpoint, a both-sides reflex on a point that has no other side.

So anti-slop is built around the part that compounds. A living corpus of dated tells, each tagged with the mechanism that produces it. The trigger to grow it is "I spotted one," which is cheap and high-signal. Naming the mechanism is what lets the skill predict the next tell before it is common.

## Before and after

A generic de-slop pass fixes words and leaves the robot rhythm in place. anti-slop fixes structure first, because uniform sentence length reads as AI even with every flagged word gone.

Slop in:

```
In today's ever-evolving landscape, we delve into a rich tapestry of
synergy. This isn't just a tool, it's a paradigm. Furthermore, it
underscores a robust, seamless journey toward content excellence.
```

Clean out:

```
A tool for cleaning AI writing. It catches the tells, fixes them, and
learns new ones as the models change.
```

What got cut: the flowery opener, the Tier 1 vocabulary (delve, tapestry, robust, seamless), the binary-contrast pattern ("this isn't X, it's Y"), the "Furthermore" transition, the false agency ("it underscores"), and the metronomic rhythm. What stayed: the actual claim.

## The three modes

| Mode | What it does |
|------|--------------|
| **rewrite** (default) | Flags every AI-ism, returns a clean version, shows a diff of what changed. Runs the structure pass, the vocabulary pass, and a transition-iteration pass that varies the seams instead of banning specific connectors. |
| **detect** | Flags only, grouped by severity (P0 credibility killers, P1 obvious smell, P2 polish). No rewriting. For published text, someone else's writing, or a quick scan. |
| **ingest** | The curation flow. Paste text marked `slop:` and the skill dissects it, names the generative mechanism, writes a tiered rule plus a replacement, checks it against the protect list, and files it into the living corpus. |

## The spine

1. **Structure is the number one signal**, above vocabulary. Uniform sentence and paragraph length reads as AI even with every flagged word removed. Vary the rhythm first, swap words second.
2. **Tiered vocabulary, not blanket bans.** Tier 1 always replace, Tier 2 flag in clusters, Tier 3 flag by density. Blunt "never" rules stacked deep recreate the over-polishing they are meant to fix.
3. **Context profiles** adjust strictness per surface: linkedin, blog, technical-blog, investor-email, docs, casual.
4. **The protect-list seam.** On a byline with a voice spec, the floor loads the protect list first and never strips a protected signature.
5. **Self-reference escape hatch.** When writing about slop (quoting bad examples), the quoted patterns are not flagged. Only the author's own prose is.

## It protects your voice

A de-slop pass that runs at full strength on everything will sand a real writer down to the same flat statistical profile it is supposed to fix. Deliberate fragments, an "And" opener, a signature phrase, an uneven cadence: those are what keep text human.

anti-slop separates the two jobs. The floor strips general tells. A per-byline protect list says what must survive. `references/protect-list.md` ships as a fill-in template, and its companion onboarding skill, [voice-dna-builder](https://github.com/kjmagnan1s/claude-skills/tree/main/skills/voice-dna-builder), builds your personal voice spec and protect list from your own writing samples. When a floor flag collides with one of your signatures, the skill surfaces the collision instead of editing it.

## The living corpus (the moat)

`references/living-corpus.md` is the part that compounds. Each entry is a dated tell caught in the wild, tagged with the mechanism that produces it (reward-tuning, repetition-penalty, instruction-tuning, pretraining-register, displacement, and more). Tells age, so entries get re-tiered or retired as the models change. The rule lists you can copy from anyone. This is the asset you cannot.

## What is inside

```
SKILL.md                       The skill: modes, the spine, transition iteration, scoring
references/patterns.md         The deduped rule library (the floor) and the context-profile matrix
references/living-corpus.md    Dated tells caught in the wild, with mechanism tags
references/ingestion.md        The curation flow for memorializing new slop
references/protect-list.md     The per-byline seam, shipped as a fill-in template
CREDITS.md                     Full lineage and attribution
LICENSE                        MIT
```

## Credits

anti-slop is a consolidation of prior open work, credited in full in [CREDITS.md](CREDITS.md):

- **avoid-ai-writing** by Conor Bronsdon (MIT): the tiered vocabulary, context profiles, and severity tiers.
- **humanizer** (MIT), based on Wikipedia's "Signs of AI writing" (CC BY-SA 4.0): the content-pattern catalog and the adversarial self-audit.
- **stop-slop** by Hardik Pandya (MIT): the false-agency rule, the binary-contrast table, and the scoring rubric.

## License

MIT. The pattern examples are written in our own words; the Wikipedia-derived lineage stays attributed under share-alike terms in CREDITS.md.
