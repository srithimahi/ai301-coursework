# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I am a student developer contributing to this repository as part of learning open-source development. When I comment on an issue, I am investigating and reproducing reported behavior before attempting any fix. Readers can expect me to be specific about what I tested, what I observed, and what I have not confirmed yet.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->

### Rule: Say only what I have actually done

I do not describe an investigation, reproduction, or result as completed before I have actually done it. If I am claiming an issue, I state what I plan to investigate rather than predicting the result.

- Wrong: "I reproduced this issue and will work on it."
- Right: "I'd like to investigate this issue. I'll try to reproduce the reported behavior and post my findings here."

### Rule: Name the specific issue behavior

I avoid generic comments that could be pasted onto any issue. I mention the actual behavior or condition I am investigating so readers know what I intend to test.

- Wrong: "I'll take a look at this bug and report back."
- Right: "I'll investigate the reported behavior under the conditions described in this issue and post the environment, reproduction steps, and observed result."

### Rule: Separate what I observed from what I think caused it

I report evidence before making explanations about the cause. If I have not established the cause, I do not present a guess as a fact.

- Wrong: "This happens because the parser is broken."
- Right: "I observed the reported failure during this test; I have not confirmed the underlying cause."

### Rule: Be explicit when reproduction fails

A failed reproduction attempt is still useful evidence. I say that I could not reproduce the behavior instead of stretching different output into a successful reproduction.

- Wrong: "Confirmed, I reproduced it," when my output differs from the issue.
- Right: "I could not reproduce the reported behavior in this environment; here are the steps I tried and the result I observed."

### Rule: Follow the repository's communication rules

Before posting, I check the repository's contribution and issue guidance and follow any required templates or disclosures, including AI-assistance disclosure when required.

- Wrong: "Here is my reproduction report," while ignoring a disclosure required by the repository.
- Right: "I used AI assistance while preparing this reproduction report." when that disclosure is required by the repository.

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

- A claim that I reproduced something before I actually tested it.
- A promise that I will fix an issue or finish it by a specific date.
- A successful-reproduction claim when the evidence shows different behavior.
- Guesses about the cause presented as established facts.
- Generic claim comments that do not identify what I am investigating.
- Comments that ignore repository-specific contribution or disclosure requirements.
