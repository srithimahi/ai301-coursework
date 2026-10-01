# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

Where it lives: In an eval package, read the candidate plan's diagnosis or stated cause and compare it with the repro-evidence block's observed behavior, expected behavior, and reproduction results. In live mode, compare the diagnosis in the draft plan with the reproduction evidence posted on the issue thread.

What good looks like: The stated cause explains the reproduced failure and is supported by behavior the repro evidence actually shows. It must not contradict or ignore the observed and expected behavior.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

Where it lives: In an eval package, read the candidate plan's scope, exclusions, and named files or areas, and compare them with the diagnosed cause and repo-facts block. In live mode, use the draft plan and relevant repository files or documentation.

What good looks like: The proposed work is bounded to the changes needed to address the diagnosed cause. Unrelated refactors, rewrites, or changes are excluded unless the evidence shows they are necessary.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

Where it lives: In an eval package, read the candidate plan's proposed files or areas, implementation approach, and order of work. In live mode, use the corresponding sections of the draft plan and the repository locations they reference.

What good looks like: A developer unfamiliar with the issue can identify where to start, what logic or behavior needs to change, and what the intended new behavior is without needing clarification from the plan's author.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

Where it lives: In an eval package, compare the candidate plan's test plan with the repro-evidence block's original reproduction steps, inputs, observed behavior, and expected behavior. In live mode, compare the draft test plan with the student's posted reproduction evidence.

What good looks like: The test plan exercises the reproduced failure and names an observable expected result that distinguishes the fixed behavior from the original failure. It should make clear how the original reproduction will be rerun after the change.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

Where it lives: In an eval package, read the candidate plan's diagnosis, assumptions, risks, unknowns, and deviations. Compare factual claims with the repro evidence and repo facts. In live mode, use the same parts of the draft plan and record any implementation deviation under Deviations.

What good looks like: Claims presented as facts are supported by available evidence. Unresolved assumptions, risks, or unknowns are identified rather than presented as certain, and any change from the posted plan is recorded honestly under Deviations.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

Where it lives: In an eval package, compare the plan comment with the issue context or thread highlights and the repo-facts block, including contribution templates, maintainer requests, contribution policies, and AI-use disclosure requirements. In live mode, compare the draft comment with the GitHub issue thread and the repository's contribution documentation.

What good looks like: The plan comment responds to the issue's actual requirements and maintainer signals and follows explicit repository contribution conventions. It does not use generic boilerplate that ignores constraints or requests present in the thread or repository.
