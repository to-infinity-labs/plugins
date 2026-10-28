---
name: tldr
description: 'Give a short summary in plain concise words with zero jargon. Use on "/tldr", "tldr", "in plain english", "plain words", "no jargon", "explain simply", "what does that actually mean", "shorter version". Replaces the previous answer rather than appending a summary to it. Accepts a length dial — "/tldr 3" for three bullets, "/tldr one line" for one sentence.'
argument-hint: what to summarize, or a length (3, one line), or blank
user_invocable: true
---

# /tldr

Say the thing, short, in words anyone would use out loud.

## The subject

$ARGUMENTS

If it names something — a file, a concept, a pasted block — summarize that. If
it's empty, the subject is the last substantive answer or the current topic.

`/tldr` on the heels of a long answer means "say that again, shorter and
plainer." It **replaces** that answer. Never append a summary section to what
you just wrote and never re-explain first.

## Length dial

If the argument is a bare number or a length phrase, it sets the shape and the
subject is whatever's live:

- `/tldr 3` → three bullets
- `/tldr one line` → one sentence
- `/tldr 2 sentences` → two
- `/tldr 3 the auth options` → both: three bullets, about that subject

A requested length is a hard ceiling. If it genuinely can't hold the truth, say
the one thing that fits and add a single line naming what got left out. Never
quietly overrun the dial.

## Chaining after /decide

`/tldr` on a decision brief collapses it to the call and the reason it won, in
plain words. Don't re-list the options or replay the pros and cons — they just
read them and are asking for the punchline.

## The jargon rule

This is the load-bearing part and the easiest one to quietly skip. **Never use
the term. Describe the thing.** Ordinary words, even when it takes a few more:

- "idempotent retries prevent duplicate writes" → "if it runs twice, nothing
  gets written twice"
- "we're rate-limited by the upstream API" → "their server starts refusing us
  if we ask too often"
- "the migration is backwards-incompatible" → "old code stops working the
  moment this ships"
- "we need to decouple these services" → "right now you can't change one
  without breaking the other"

Three kinds of jargon, all banned:

- **Technical terms** — the ones above.
- **Business filler** — "leverage", "surface area", "align on", "unlock",
  "at scale", "net-net".
- **Internal shorthand** — project code names, acronyms, service names, unless
  the user used it first.

Proper nouns they already use are fine. The rule is about vocabulary, not about
pretending the system has no names.

## Plain is not vague

This is the counterweight, and without it the skill produces mush. Plain words,
specific claims. Keep every number, name, condition, and caveat that would
change what the user does. If something is genuinely unknown, say "we don't
know yet" in exactly those words — don't dissolve it into softness.

Never trade a true statement for an easier one. Simplifying to the point of
being wrong is the one unrecoverable failure here; a slightly longer sentence
is always the cheaper price.

## Shape

Absent a length dial: a short paragraph, or three to five bullets when the
items are genuinely parallel. No headers, no bold labels, no preamble ("Here's
the TL;DR:"), no closing offer. Short sentences. One idea per sentence. Ceiling
around 150 words — go past it only when dropping a detail would make the
summary wrong, and never past a short screen.

## Rules

- Write like you're explaining to a smart friend outside the field, not to a
  child. No condescension, no "basically", no "think of it like a…" unless the
  analogy genuinely lands faster than the plain description.
- Lead with the conclusion. Background only if it's load-bearing.
- Cut every sentence whose only job is announcing the next sentence.
