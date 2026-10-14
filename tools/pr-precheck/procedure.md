# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

Determine whether the request is in live mode or eval mode. Identify exactly one PR package to evaluate.

Read rubric.md to identify all checks, their evidence requirements, pass conditions, weights, and the verdict rule. Read references/evidence-guide.md to locate each evidence type.

In live mode, read scope.md before accessing the PR package. Verify that the repository matches the configured scope and that the Repo: field is filled in. Refuse to grade an out-of-scope repository or an unconfigured scope. Also read voice-guide.md for outgoing PR communication requirements. In eval mode, ignore both files.

Read the issue and its discussion first. Record the reported problem, expected behavior, relevant constraints, and acceptance criteria. In eval mode, use only the issue facts provided in the package.

Read plan.md before examining the diff. Record the intended scope, files or components expected to change, proposed implementation, test plan, and any documented deviations. Reading the plan first establishes the expected change independently of what was actually implemented.

Read the complete diff next. In live mode, run git diff main...HEAD from the repository working copy. Record every changed file and the substantive additions, removals, and modifications. In eval mode, use only the diff supplied in the bundle.

Read the test evidence. Record executed commands, actual outputs, reproduction results, before/after behavior, failures, skipped checks, and explanations for unavailable tests.

Read the draft PR title and description after the implementation and evidence. Record the summary, issue reference, changes claimed, testing claims, limitations, deviations, and reviewer notes.

Read the repository's stated standards. In live mode, inspect .github/PULL_REQUEST_TEMPLATE.md, docs/CONTRIBUTING.md, and relevant issue-thread requirements. In eval mode, use only the supplied repository-facts block.

In live mode, compare the outgoing title and description with voice-guide.md and record any specific violations separately.

Do not grade individual checks until these reads are complete, except when a contract-defined refusal condition prevents grading.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

Create an evidence record for each of the following comparisons. Use references/evidence-guide.md to locate the corresponding sources.

A. Plan fidelity

Extract the planned change boundary from the issue and plan.md.

List actual changed files and substantive changes from the diff.

Match each material diff change to a planned change or documented deviation.

Identify planned work that is absent or only partially implemented.

Record whether omissions and deviations are disclosed in the plan and PR description.

Record exact file names, relevant changed behavior, and any contradictory claims.

B. Test evidence

Extract the expected verification steps from the plan's test plan.

Compare those steps against actual commands and observed results in the test evidence.

Check whether before/after reproduction is demonstrated when applicable.

Compare repository-required checks with recorded executions, outputs, and explanations for skipped or unavailable checks.

Distinguish actual failures from missing evidence. A disclosed failed test is not automatically equivalent to an untested change.

Record the specific output, observed behavior, or missing result supporting each conclusion.

C. Diff quality

Inspect every changed file and material hunk for relevance to the issue.

Identify unrelated refactoring, debugging artifacts, generated files, temporary changes, or abandoned implementation.

Determine whether supporting changes are necessary for the fix.

Record which files or hunks create reviewability problems and why they are unrelated or obstructive.

D. Standards and communication

Compare the PR title, summary, changes, and testing statements against the diff, issue, and observed test results.

Identify material contradictions, unsupported claims, and undisclosed limitations.

Extract mandatory fields and disclosure requirements from the repository facts, PR template, and contribution policy.

Check whether required issue references, testing disclosures, and AI-use disclosures are present and accurate.

In live mode, record any violations of voice-guide.md separately.

Do not infer successful tests, missing implementation details, or repository requirements from assumptions.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

Execute the checks in the exact order defined by rubric.md.

Plan fidelity: Compare the actual diff against the plan and documented deviations. Grade pass when all material differences are within scope or honestly disclosed. Grade fail for demonstrated undisclosed drift or false fidelity claims.

Test evidence: Compare the plan's intended tests with the observed evidence. Grade pass when the evidence demonstrates relevant behavior or accurately explains observed limitations. Grade fail when test claims are unsupported or available evidence contradicts the claimed results.

Repository checks: Compare required checks against their recorded executions and results. Grade pass when applicable checks have identifiable outcomes or credible explanations for being unavailable. Grade fail when required checks are silently omitted or claimed without execution evidence.

Diff relevance and reviewability: Inspect changed files and hunks for unrelated changes or debris. Grade pass when the diff is focused and its supporting changes are relevant. Grade fail when unrelated or accidental changes materially obstruct review.

Description accuracy: Compare the PR description and title with the issue, plan, diff, and tests. Grade pass when material claims are accurate and reviewers can understand the change. Grade fail for material contradictions, misleading claims, or missing explanations necessary to understand the implementation.

Repository standards and disclosure: Compare the PR draft against explicit repository requirements. Grade pass when mandatory template information and disclosures are satisfied. Grade fail when a documented mandatory requirement is violated or omitted.

For every check:

Use only evidence permitted by the active mode.

Apply the exact pass condition from rubric.md; this procedure does not override the rubric.

Record a one-line evidence statement identifying the deciding fact, quotation, file, or observed result.

Use unclear when necessary evidence is genuinely missing, incomplete, or contradictory and the check cannot be determined.

Do not grade missing evidence as pass based on optimism or as fail based on invented facts.

Reuse evidence already gathered rather than rereading the entire package unless a contradiction requires verification.

Do not reject solely because a limitation or failed test is honestly disclosed, unless a separate required condition is violated.

If a necessary procedural step cannot be performed, report the gap. Do not invent a substitute procedure.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

Confirm that every check in rubric.md has exactly one grade: pass, fail, or unclear.

Apply the rubric's verdict rule. Return accept only if every required check passes. Return reject if any required check is fail or unclear. Preferred checks never independently change the verdict.

Treat unclear as failing for verdict purposes. Do not introduce a third verdict, conditional acceptance, or numerical score.

When multiple required checks fail or are unclear, identify the first non-passing required check in rubric order as the primary deciding check. Quote or cite its most specific supporting evidence in the readable summary. Also report the evidence for every other check; do not hide additional failures.

If all required checks pass, identify the strongest concrete evidence supporting readiness, while still reporting all check grades.

In live mode, report any voice-guide violations separately, without changing the verdict unless the rubric explicitly makes them relevant.

Produce a concise per-check summary using the rubric's exact check names.

Finish with the exact fenced JSON schema required by SKILL.md and CONTRACT.md. Set item to the PR URL or bundle identifier. Include every check in rubric order, its grade, and its one-line evidence. Set verdict to accept or reject.

Ensure the JSON is valid, preserve the required schema and field order, and output nothing after the closing JSON fence.
