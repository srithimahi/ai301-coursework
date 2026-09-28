# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

**Where it lives:** In an eval bundle, look at the repro report's environment record and compare it with the issue context and any relevant repo-facts. In live mode, look at the student's draft repro report and compare the recorded environment with the issue thread and repository documentation.

**What good looks like:** The environment records the relevant versions, platform, configuration, dependencies, or other conditions needed to test the issue. Those conditions match what the issue targets, or any meaningful difference is explicitly called out.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

**Where it lives:** In an eval bundle, look at the reproduction steps in the repro report together with commands, inputs, setup details, and referenced artifacts. In live mode, look at the student's draft repro report and any repository setup instructions it relies on.

**What good looks like:** The steps take a stranger from a stated starting condition through the actions needed to trigger the tested behavior. Material setup, commands, inputs, or actions are not left for the reader to guess.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

**Where it lives:** In an eval bundle, look at the repro report's observed results and its artifacts, such as output excerpts, logs, error messages, or screenshots, and compare them with the behavior described in the issue context. In live mode, compare the evidence in the student's draft report with the issue thread.

**What good looks like:** The artifacts provide observable evidence of the behavior being tested and correspond to the specific behavior described by the issue. Evidence of an unrelated or adjacent error does not establish reproduction of the reported issue.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

**Where it lives:** In an eval bundle, compare the stated reproduction outcome in the repro report with its observed results and artifacts and with the issue context. In live mode, compare what the student's draft says happened with the evidence the draft provides.

**What good looks like:** The stated outcome does not claim more than the evidence supports. A report that could not reproduce the issue passes this family when it states that result clearly and provides evidence of the attempt; claiming successful reproduction when the evidence shows different behavior does not.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

**Where it lives:** In an eval bundle, compare the claim comment and repro report with the issue context, repo-facts block, and any repository contribution, comment, template, or AI-use policies stated there. In live mode, check the issue thread, repository contribution documentation and templates, AI-use policy if present, and the student's draft comments.

**What good looks like:** The package follows every applicable repository-specific communication and contribution requirement. When the repository requires AI-assistance disclosure, the disclosure must actually appear in the candidate comment or report and contain whatever details the policy requires, such as the tool used and extent of assistance. A package with no required disclosure fails this family even if its reproduction evidence is otherwise complete and correct. The claim should also identify the issue specifically and avoid claiming work that has not yet been performed.
