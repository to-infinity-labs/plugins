---
name: decide
description: 'Produce a decision brief — TL;DR, pros, cons, and one explicit recommendation — for a choice the user is weighing. Use on "/decide", "help me decide", "pros and cons", "which approach", "what should I do here", "compare these options", "talk me through the tradeoffs". Two hard constraints: no hacks or workarounds may appear as options, and it ends with a single recommendation, not a menu. Stops at the brief; never implements.'
argument-hint: the decision, or blank to use the current conversation
user_invocable: true
---

# /decide

The user has a decision to make and wants a brief, not a lecture. Give them
enough to decide in one read, then tell them what you'd do.

## The subject

$ARGUMENTS

If empty, the decision is whatever is live in the conversation. Identify it,
state it back in one line, and proceed. Don't ask "what would you like me to
compare?" when the answer is on screen.

## Before writing anything

**Ground it.** If the decision touches this codebase, read the relevant code
first. A pros/cons list built from assumption is worse than none — it's
confident and wrong.

**Find the real options.** The user's framing may be incomplete. If a third
option is genuinely better, include it and say where it came from. If one of
their two is plainly disqualified, say so rather than padding it out for
symmetry.

**Doing nothing is always an option.** It appears in the list whenever the
status quo is survivable, or gets dismissed in one explicit line saying why it
isn't. Never silently omit it — it wins more often than briefs admit, and
leaving it out smuggles in "we're definitely changing something."

**No hacks. This is the hard constraint.** Every option must be one you'd
defend in six months. Disqualified on sight:

- Suppressing a symptom while leaving the cause in place
- Relying on an implementation detail that isn't guaranteed
- Anything needing a comment that starts "we have to do this because…"
- Trading correctness for a faster path to green
- Sleeps, blind retries, and `except: pass` standing in for understanding a failure

If a hack is the *only* thing that fits the stated constraints, don't list it.
Say directly that the constraints and a clean solution are in conflict, and
name which constraint has to move.

## Output format

Exactly four sections. No preamble, no closing summary.

**TL;DR** — Two or three sentences: what the decision actually is, and what
turns on it. Someone who reads only this can still act. Write it to the
plain-language standard — short words, no jargon, nothing a smart outsider
would have to decode. The rest of the brief may use precise technical
vocabulary; this section may not.

**Pros / Cons** — Two or three options, no more; past that you haven't finished
thinking. Each option's header line carries two tags:

- **Reversibility** — one-way door / reversible / reversible-but-painful
- **Size** — hours / days / weeks. An order of magnitude, not an estimate.

Then 2–4 pros and 2–4 cons, one line each, concrete to *this* situation.
"Harder to maintain" is filler; "every new event type needs edits in three
files" is a con. Include the cost they haven't thought about — migration,
lock-in, what breaks at 10x, who carries the pager. No false balance: a weak
option gets a short list that says so.

Both tags are mandatory because they're the axes most often left implicit and
they routinely change the answer. A one-way door deserves more caution than its
cons alone suggest, and an option the user can't afford in time isn't an option.

**Recommendation** — One option, named and unhedged in the first sentence. Then
two or three sentences on why it wins *given this situation*, not in the
abstract. Then, if it applies, the one condition that would flip the answer:
"if you expect more than one writer, take the other one instead."

**Watch for** — Optional, at most three bullets: the traps inside the path you
just recommended. Omit the section entirely if there aren't any.

## Say what you couldn't check

If any load-bearing claim rests on code you didn't read or a fact you couldn't
verify, one line at the end names it — "I haven't checked how the watcher
handles partial writes; if it doesn't, option B gets worse." Without this a
guess reads identically to a verified fact, which is the failure most likely to
burn them. One line, not a disclaimer section. Omit it when everything checked out.

## Rules

- One recommendation. "It depends" is a failure to do the work. If it truly
  hinges on something only the user knows, name that thing and recommend for
  each branch of it.
- Fits one screen. A long section is a padded section.
- Don't restate the pros inside the recommendation. They just read them.
- Say the uncomfortable thing. If their preferred option is the wrong one,
  that's the most valuable sentence in the brief — lead with it.
- No table unless there are 3+ options across 3+ comparable dimensions.
- **Ends at the brief.** Don't start implementing, and don't tack on "want me
  to build it?" They'll say.
