# How PRDs work

If you want something built, changed, or stopped, file it as a **PRD**. Go to
the project it's about, pick *Issues* → *New issue* → *PRD*, and fill the
form in.

**If you don't know which project to file it under, file it anywhere you can and say so in
the Problem field.** Engineering will move it. Guessing wrong costs nothing and is much
better than not filing. If you're not sure which project is which, ask once and you'll be
told — that mapping isn't written down here on purpose.

You describe **what should exist and why**. Engineering works out **how**. That's the whole
division of labour, and the form is built around it.

## What the fields are asking for

**Problem.** What's happening today that makes this worth doing, and who it affects. Not
what you want built — that comes later in the form.

**Evidence.** What makes you confident. A ticket, a quote, a number, a contract, a
competitor. **"It's my gut" is a real answer and you should write it when it's true.** A
hunch you've labelled as a hunch is useful. A hunch dressed up as a finding is worse than
saying nothing, because it can't be argued with.

**Is this decided?** Three options, and they're genuinely different:
- *We've decided* — this is settled, build it.
- *Proposing* — here's what I think, tell me if I'm wrong.
- *Problem only* — I don't know what the answer is, you propose something.

**Solution — the what.** The thing that should exist. "Coaches can save a filter set and
reuse it." Not the database, not the screen layout, not the library.

**How we'll know it worked.** What you'd expect to *see* change. "Coaches stop re-entering
the same three filters every morning." This isn't the same as the field above — that one
is the thing, this one is how we'd know the thing worked. Something can ship exactly as
described and change nothing, and this field is what catches that before we build it.

**Appetite.** How much the problem is *worth* — not how long you think it'll take. This
is the most useful field in the form. If you say "days" and it turns out to be a month's
work, that's not a problem: it means we cut it down to the part that's worth days, or we
decide together that it's worth a month after all. Guessing at duration gives nobody that
option.

**Deadline.** Only mark *hard external date* if something real happens on that day — a
demo, a client commitment, an App Store review. "Soon" is not a deadline, and marking
everything urgent is the same as marking nothing urgent.

Everything else is optional.

## What happens after you submit

1. Engineering reads it and either asks a question, declines it with a reason, or accepts
   it.
2. On acceptance you get **one comment** restating what's going to be built, what is
   explicitly *not* being built, and how big it's judged to be.
3. **You confirm or correct that comment.** This is the only thing the process asks of you
   after submitting, and it's the step that matters most — it's where a misunderstanding
   costs a sentence instead of a fortnight.
4. Then it gets built.

Nothing is built before step 3.

### If the size doesn't match your appetite

Engineering sizes every submission, because how big something is from the outside is a
poor guide. "A toggle for light mode" sounds like an afternoon and wasn't. "Just rename
one label everywhere" sounds like find-and-replace and isn't.

When that size and your appetite disagree, the restatement comment will say so and offer
three ways out: cut it down to fit, raise the appetite, or park it. Pick one. That
conversation is the point — having it before anything is built is much cheaper than
having it after.

### Declines

A decline always comes with a reason written in the issue. If a queue swallows things
quietly, people stop using it, so this one doesn't.

## Filing without the form

You can still open a blank issue, and sometimes that's right — a bug, a question, a quick
note. It just won't be tracked as a PRD, so if it is one, you'll be asked to refile
it, or the form will be filled in on your behalf for you to check. Nothing gets lost
either way.

---

## Turning a document you already have into a submission

If the thinking is already written down — a doc, a call transcript, a Slack thread, an
email chain — don't retype it into the form. Paste the prompt below into Claude, paste
your document after it, and it will fill the fields in for you. Then copy each block
across, answer anything in the **Gaps** list, and submit.

It is told never to invent, and it prints the line of your document it drew each answer
from. **Skim those `Source:` lines before you copy anything across** — that is what they
are for. It is good at this and it is not infallible, so a thirty-second check beats
finding out later that a sentence nobody wrote ended up in an issue.

````text
You are converting a document into a PRD submission for the ArtemyxLabs
intake form. The person pasting this is on the product side; the engineer who reads your
output is not in the room.

Read the document that follows and produce one submission per decision it contains.

## Absolute rule: never invent

Every field you fill must trace to something actually in the document. After each filled
field, add a line `Source: "<short quote from the document>"`.

The quote must be a character-for-character span of the document — not a tidied-up
version of it. Choose a span that contains no double quote marks of its own; shorten the
span or move it rather than deleting the inner quotes, because deleting them makes the
line look verbatim when it is not. If no quotable span supports the field, the field is
`(not in source)`.

**The quote must contain the thing the field asserts, not merely come from nearby.** A
real quote attached to a claim it does not support is the same failure as a made-up
quote, and it is harder to spot because the quote checks out. If you find yourself
reaching for a quote from the same paragraph because no sentence actually says it, the
honest answer is `(not in source)`.

If the document does not answer a field, DO NOT fill it. Write
`(not in source)` and add the field to the Gaps list at the end. This applies most of all
to Evidence: if the document contains no evidence, write
`(no evidence in source — answer this yourself, or write "my gut")`.

A plausible sentence you composed is not evidence. It is the single most damaging thing
you can produce here, because it reaches the engineer looking like fact.

## Second rule: one PRD per decision

Documents usually contain several decisions. Identify them. Produce one complete
submission for each, numbered. If two decisions are genuinely entangled, say so and name
the one that has to happen first.

If the document contains only one decision, say that too.

If it contains more than about five, do not produce twenty submissions nobody will read.
Write full submissions for the ones the document itself treats as most important — the
ones it marks high priority, or puts first — and list the rest by name at the end so none
of them is lost. Say how many you found and how many you wrote out.

## Third rule: what, not how

The submitter owns what should exist. The engineer owns how it gets built. Documents mix
these freely, often inside one sentence.

- The *what* goes in the Solution field: the feature, the change, the behaviour.
- The *how* — technology choices, schema, vendors, libraries, screen layouts, "use
  Postgres full-text search" — does NOT go in any field. Collect it at the end under
  `The source also proposed this approach:` so the engineer sees it as context rather
  than as a requirement.

When a sentence contains both, split it.

## Output format

For each decision, output exactly this, with the fenced blocks intact so they can be
copied one at a time:

### Submission N: <short name>

**Problem**
```
<text>
```
Source: "<quote>"

**Evidence**
```
<text, or the not-in-source line>
```
Source: "<quote>"

**Is this decided?**
```
<one of: We've decided — build it | Proposing — tell me if this is right | Problem only — you propose the solution>
```
Source: "<quote>"

**Solution — the what**
```
<text>
```
Source: "<quote>"

**How we'll know it worked**
```
<text>
```
Source: "<quote>"

**Appetite**
```
<one of: Days | A week or two | Worth a month | Don't know>
```
Source: "<quote>"
<if nothing in the document says how much the problem is worth, use Don't know and write
(not in source) on the Source line instead of a quote. An engineering effort estimate is
NOT an appetite — do not convert one into the other.>

**Is there a real deadline?**
```
<one of: No date | Soft preference | Hard external date>
```
Source: "<quote>"

**If there's a hard date — what is it, and what's driving it?**
```
<the date and what happens on it, or (not in source)>
```
Source: "<quote>"

**Which product or area is this about?**
```
<text, or (not in source)>
```

**Out of scope**
```
<text, or (not in source)>
```

**Who else needs to know?**
```
<names or roles the document says should be involved, or (not in source)>
```

Then, once, at the very end:

**The source also proposed this approach:**
- <any how-level detail you stripped out, each with a quote>

**Gaps — you need to answer these before submitting:**
- <field>: <the question the submitter needs to answer>

Keep every field under 150 words. If the source is long, summarise rather than quote at
length — but the Source lines must still be real quotes.

The document follows.
````

Two things to do with the output before you submit:

- **Carry the `Source:` lines for Evidence into the Evidence field**, under what you paste.
  They're the one thing that distinguishes a quote from a summary, and they're dropped if
  you only copy the fenced blocks.
- **Anything still in the Gaps list** goes at the bottom of the **Problem** field as a line
  starting `Open questions:`. An honest gap is useful; a blank field is just a question
  someone has to come back and ask you about.
