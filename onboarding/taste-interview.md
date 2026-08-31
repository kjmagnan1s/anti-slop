# The taste interview

The judgment layer of a voice spec. A writing corpus can teach an agent how you
sound. It cannot teach what you think, what you'd never do, or what makes you
close the app. This interview collects that layer.

Inspired by Ruben Hassid's "I am just a text file" (100-question taste
interview). The questions here are original; the trim is the point. His method
is interview-only. Ours is corpus-first: extract everything a writing sample can
answer automatically, then interview only for what no sample can show. That
cuts roughly half the questions and produces better data, because behavioral
evidence beats self-report on style.

## How to run it

**Step 0: corpus first.** Collect 3-5 authored samples (published writing,
dictation transcripts, working notes). When the person can't produce samples on
demand, which is the common case, `voice-sources.md` finds the corpus already
on their machine. Extract the style layer from those samples: rhythm, openers,
closers, signature phrases, formatting habits, banned words. That work replaces
the style/mechanics questions entirely.

**Step 0, fallback: no corpus and none discoverable.** Don't stop here. Make a
small corpus, then run the interview with a style round in front of it:

- Have them write or dictate three short pieces cold, on topics from Section 1:
  a post, a reply to someone who is confidently wrong, and a piece of bad news.
  That is a corpus. Ten minutes of real writing beats an hour of self-report
  about writing.
- Then ask the six style questions self-report can actually carry. What words
  and phrases do you use that other people in your space don't? What words
  would you never use? How long are your sentences and paragraphs when the
  writing is going well? What do your openers and closers look like? What
  punctuation do you overuse? What formatting do you reach for on your own,
  and what do you only use because a tool suggested it?
- Mark every style-layer line sourced this way as self-reported, and treat it
  as the weakest data in the spec. Once real writing exists, the mirror
  (Step 3) re-derives the layer from it, and the corpus wins per the conflict
  rule below.

**Step 1: the interview.** The five sections below, ~47 questions. Rules:

- Dictate the answers. Don't polish. Rambling is fine; the compiler's job is
  to distill.
- Every answer needs one specific: a name, a quoted phrase, a real incident, a
  link. "I hate hype" is unusable. "I unfollowed X the day they posted Y" is
  data.
- "Skip" beats an invented answer. A stance you don't actually hold will
  poison every draft written from it.
- Interviewer: push back on vague answers, follow interesting threads, and ask
  "give me the example" whenever one is missing. One section per sitting is
  fine; the whole thing is 60-90 minutes of talking.
- On any conflict between what the person says here and what their corpus
  shows, the corpus wins. Flag the conflict; don't silently resolve it.

**Step 2: the veto round.** After compiling, generate three short takes in the
person's voice on topics from Section 1. Have them veto lines. Record every
rejection and why. Repeat once. Taste is boundaries; rejections are the
cleanest boundary data there is.

**Step 3: the mirror.** Show them what the corpus says about them (the style
layer summary). Ask: what's wrong in this? What would you veto? Corrections
here are gold; they mark where habit and identity diverge.

**Output:** a stance layer for the voice spec: beliefs, hard nos, aesthetic
crimes, red flags, and the disagreement/excitement registers. It sits beside
the style layer, and writing agents load both.

## The contamination guard

The interviewer and compiler are usually an AI, and an AI's default prose is
the exact thing this system exists to remove. Slop injection risk is highest
in paraphrase and summary, lowest in selection and quotation. So:

- **Selection, not paraphrase.** The compiled layer is built from the
  speaker's verbatim phrases. The compiler contributes structure and labels
  only. If a sentence in the stance layer uses words the speaker never said,
  it's contaminated; go back to the transcript.
- **Keep the raw transcript.** Store the unedited dictation beside the
  compiled spec. The transcript is ground truth; the compiled layer is
  derived and can be regenerated from it at any time.
- **Don't feed phrasings.** During the interview, clarify using the speaker's
  own words. A tidy reframe ("so what you're really saying is...") plants the
  interviewer's phrasing in the subject's mouth and comes back as fake data.
  Ask the open question again instead.
- **Quotes are untouchable.** Any de-slop pass on the compiled spec runs on
  the compiler's scaffolding only, never on the speaker's quoted words. The
  veto round and the mirror are the final catch: anything that doesn't sound
  like the speaker gets killed there.

---

## Section 1: beliefs and stances

The biggest gap in any style-only voice file. An agent that nails your rhythm
but has nothing to say produces fluent emptiness.

1. What do you believe about your field that most people in it don't?
2. Name three pieces of conventional wisdom you think are flat wrong. What's
   your counter for each?
3. What take would you defend under your own name even if a client or boss
   pushed back?
4. What have you changed your mind on in the last two years? What flipped it?
5. What does everyone in your space pretend to believe because it's safe?
6. What opinion would cost you followers or business to say out loud? Would
   you say it anyway?
7. Who's getting something important wrong right now? A person, a company, a
   movement. Be specific.
8. What are you certain of that you can't fully prove yet?
9. What's overhyped right now? What's underhyped?
10. What prediction are you willing to be publicly wrong about?
11. When you catch yourself saying "it depends," what do you actually think
    most of the time?
12. What question do people keep asking you that you think is the wrong
    question? What's the right one?
13. What do you want to be on record saying early, before it's consensus?
14. What belief of yours sounds obvious until people watch you act on it?

## Section 2: aesthetic crimes

Content-level taste. Banned words live in the style layer; this is about the
moves and formats you find embarrassing.

15. What kind of post makes you close the app instantly? Quote a real one if
    you can.
16. What's a recent piece of content that made you cringe? Name the exact
    mechanism, not just the vibe.
17. What formats are dead to you? (Threads, carousels, "5 lessons," reaction
    stitches, whatever applies.) Why?
18. What do people do to sound smart that reads as insecure to you?
19. What's a writing move you used to make and now hate?
20. Whose writing do you envy? Name the writer and the specific move you'd
    steal.
21. What's the fastest way a writer loses you in the first two sentences?
22. What does "trying too hard" look like in your niche, concretely?
23. What earnest thing do you actually like that your peers would mock you
    for?

## Section 3: hard nos

The lines that don't move. These become FATAL-class rules in the voice spec.

24. What topics will you not touch under your byline, ever? Why?
25. What claims won't you make even when they'd sell? Where's your hype
    ceiling?
26. What won't you say about your own past, your family, or your clients?
27. What engagement mechanics do you refuse? (Rage bait, fake urgency,
    manufactured beef, borrowed outrage.)
28. What would you never let an AI write for you, even if it wrote it
    perfectly?
29. Whose style would you never imitate even though it clearly works?
30. What's a compliment you don't want your writing to get?
31. What line, if you crossed it, would make you feel like a different
    creator?

## Section 4: red flags

Detect-mode taste: what you notice in other people's writing. This tunes how
your agent audits drafts and judges sources.

32. What tells you a piece is AI-written before any specific word does?
33. What makes you stop trusting a newsletter or creator, instantly?
34. What tells you a writer doesn't actually do the work they write about?
35. What do you check before you repeat someone else's claim?
36. What's the red flag in your own drafts, the thing you catch yourself doing
    when you're tired?
37. What in the comments or DMs tells you a post of yours missed?
38. When numbers show up in writing, what separates credible from decorative
    for you?
39. What's the tell that a hot take is manufactured?

## Section 5: registers a corpus rarely shows

Most writing samples are one mode. These questions cover the modes that only
show up under pressure.

40. How do you disagree with someone you respect? Write or dictate the actual
    sentence you'd send.
41. How do you disagree with a stranger who's confidently wrong?
42. What do you sound like when you're genuinely excited, not performing
    excitement?
43. What's your skeptical register? The words and moves you reach for when you
    don't buy it.
44. How do you deliver bad news, to a client or to your audience?
45. What won't you joke about? What do you always joke about?
46. When the stakes are real, what changes in your writing?
47. How do you walk back a wrong take in public?

---

## Compiling

Distill the answers into the voice spec's stance layer:

- **Positions**: the standing opinions, each with its one-line defense. These
  are what the agent reaches for when a draft needs a point of view.
- **Hard nos**: FATAL-class. Zero tolerance, same enforcement as the style
  layer's fatal patterns.
- **Aesthetic crimes and red flags**: fed to detect mode as taste, and to the
  self-audit gate ("would the author veto this line?").
- **Registers**: disagreement, excitement, skepticism, bad news, walk-backs.
  Quoted examples from the answers, not paraphrases.

Then run the veto round (Step 2) and the mirror (Step 3) before calling the
spec done. A stance layer nobody vetoed is a first draft.
