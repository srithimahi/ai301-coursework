---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

Determine whether exactly one candidate pull request is ready to submit. Evaluate the PR package, including its title, description, committed changes, diff, and test evidence, against the issue it addresses, its implementation plan, documented deviations, and applicable repository standards.

Do not evaluate unrelated work or substitute general impressions for evidence. The only question is whether this specific PR package is ready to submit.

## Inputs and modes

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

Determine the mode before gathering evidence.

Live mode: Evaluate the student's own proposed PR. Read the issue URL and issue discussion, plan.md including its ## Deviations section, the branch's committed changes using git diff main...HEAD, the PR title and description in pr_draft.md, and test results in test_evidence.md. Also read the repository's .github/PULL_REQUEST_TEMPLATE.md and docs/CONTRIBUTING.md to identify required standards.

Run the diff command from the working copy of the Path Review repository. Evaluate committed changes relative to main, not unrelated uncommitted working-directory changes.

For a house-chain submission, use the supplied house issue, house plan, reproduction package, and working branch instead of the student's corresponding artifacts. Apply the same checks and verdict rule.

Eval mode: Evaluate exactly one supplied practice package bundle. Treat the bundle as the complete evidence universe. Read only facts included in that bundle. Do not fetch repository content, inspect local files outside the bundle, search the web, or assume missing facts. Execute every rubric check and apply the complete verdict rule. Do not use a shortened evaluation process.

## The scope seam (live mode only)

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

Before grading in live mode, read scope.md.

Identify the repository specified by its Repo: line and apply the scope's stated rules.

If the repository value is an unfilled placeholder, stop without grading and instruct the student to replace the placeholder with the correct Path Review repository.

If the requested PR belongs to a repository outside the specified scope, refuse to grade it. Never infer, expand, or silently replace the allowed scope.

In eval mode, ignore scope.md completely.

## The voice seam (live mode only)

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

In live mode, read voice-guide.md and evaluate the outgoing PR title and description against its communication rules.

Report any violated voice rule in the readable per-check summary, citing the specific wording or requirement involved.

Voice-guide violations do not independently change the final verdict unless a check in rubric.md explicitly makes that violation relevant.

In eval mode, ignore voice-guide.md completely. Apply only the universal communication checks explicitly defined in the rubric.

## Component reads

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

Read rubric.md, procedure.md, and references/evidence-guide.md before evaluating the PR.

Use rubric.md as the authoritative definition of checks, pass conditions, check weights, and the final verdict rule.

Use references/evidence-guide.md to locate and interpret the evidence required by each check, according to the active mode.

Execute procedure.md in its documented order. Do not invent missing steps or silently substitute a different evaluation procedure. If a necessary step is absent or cannot be completed, report the limitation and reflect the missing evidence in the appropriate check grades.

If rubric.md or procedure.md contains no substantive student-written content beyond template comments, refuse to grade. Explain which component is incomplete instead of generating checks or procedures at runtime.

Do not create additional grading components or rename required files.

## Verdict and output

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

Produce exactly one binary verdict:

accept: The PR is ready to submit according to the rubric's verdict rule.

reject: The PR must be held because the rubric's verdict rule is not satisfied.

There is no third verdict, numerical score, or conditional acceptance.

Evaluate every check defined by the rubric. Assign each check pass, fail, or unclear, with a concise evidence line identifying the deciding fact, quotation, or missing information.

Apply the rubric's verdict rule exactly as written. Do not replace it with personal judgment.

Provide a readable per-check summary before the final JSON block if useful.

End every completed grading response with the following exact JSON schema. Populate the item, checks, evidence, and verdict with the actual evaluation results. Keep the schema, field names, and field order unchanged. The fenced JSON block must be valid and must be the final content of the response, with nothing after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->

Evidence first: Base every check grade on identifiable facts or quotations from the permitted evidence. Never use statements such as "looks good" without supporting evidence.

Grade substance, not polish: Judge whether the actual implementation, evidence, and description satisfy the plan, issue, and repository requirements. Do not reward confident language or attractive formatting when substantive requirements are missing.

The rubric decides: Apply each check's written pass condition and the rubric's verdict rule consistently. Do not change a grade because the result feels too strict or too lenient. Improvements belong in rubric.md, not in an individual evaluation.

The procedure decides how: Follow the written evidence-gathering and check-execution steps. Report procedural gaps instead of improvising around them.

Unclear defaults to fail: Use unclear when the available evidence cannot establish whether a check passes. Apply the rubric's explicit handling of unclear grades. If its verdict rule is silent, treat an unverifiable claim as failing for verdict purposes.

Never invent missing tests, results, repository policies, implementation details, or supporting evidence.
