# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check                     | Evidence                                                                                                         | Pass condition                                                                                                                                                                  | Weight   |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Diagnosis                 | The plan's stated cause read against the repro evidence's observed and expected behavior                         | Pass if the stated cause is consistent with the reproduced evidence and explains why the observed behavior differs from the expected behavior                                   | required |
| Scope                     | The plan's proposed changes and exclusions read against the diagnosed cause and repo facts                       | Pass if the proposed change is bounded to what is needed to address the diagnosed cause and does not include unrelated changes                                                  | required |
| Test plan                 | The plan's test steps and expected results read against the repro evidence's original failing steps and behavior | Pass if the tests exercise the reproduced failure and define an observable result that distinguishes the fixed behavior from the original failure                               | required |
| Executability             | The plan's proposed approach, files/functions to touch, and implementation details                               | Pass if a developer unfamiliar with the issue could identify where to start, what logic to change, and what the new behavior should be without needing clarification            | required |
| Uncertainty handling      | The plan's diagnosis, risks, and unknowns read against the repro evidence and repo facts                         | Pass if claims presented as facts are supported by evidence, and any unresolved assumptions, risks, or unknowns are explicitly identified instead of being presented as certain | required |
| Thread and repo alignment | The plan comment read against the issue thread highlights and the repo-facts/conventions                         | Pass if the proposed change addresses the issue's stated requirements and does not conflict with explicit repository conventions or constraints                                 | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes.
Treat unclear as fail.
Otherwise reject.
