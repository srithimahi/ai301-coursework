# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
| Plan fidelity | Compare the issue, the plan's intended changes and ## Deviations, the diff's actual changed files and hunks, and the PR description's implementation claims. | Every material change in the diff is within the plan or an explicitly explained deviation. Any planned work that was omitted or only partially completed is disclosed accurately in the plan's deviations and PR description. The description does not falsely claim that the implementation matches the original plan. An honestly disclosed shortfall is acceptable. | required |
| Test evidence | Compare the plan's test plan and reproduction steps with the PR's test evidence, including commands, observed results, and before/after behavior. | The evidence provides observable results relevant to the changed behavior, including before/after reproduction where applicable. Test claims are supported by actual outputs or specific observed results rather than unsupported assertions. Failed or incomplete tests are acceptable when their outcomes and implications are disclosed accurately. | required |
| Repository checks | Compare the repository's stated testing requirements with the commands and results recorded in the test evidence and PR description. | Every applicable repository-required check has an identifiable execution result, or an explicit, credible explanation of why it could not run. A reported failure does not automatically reject the PR when it is honestly disclosed and its implications are explained. Merely listing intended commands or checking boxes without execution evidence does not pass. | required |
| Diff relevance and reviewability | Examine the diff's changed files and hunks against the issue, the plan's intended scope, and any documented deviations. | The diff contains only changes reasonably necessary for the issue and its implementation. It does not contain unrelated cleanup, temporary debugging output, abandoned code, accidental generated files, or other debris that obscures the fix. Necessary supporting changes are acceptable when their relevance is evident. | required |
| Description accuracy | Compare the PR title, summary, changes, testing claims, and reviewer notes against the actual diff, issue, plan, and test evidence. | A reviewer can determine what changed, why it changed, and what was actually tested without encountering material contradictions. The description accurately identifies known limitations and deviations. Concise descriptions pass when they convey the relevant facts; length and formatting alone are not grading criteria. | required |
| Repository standards and disclosure | Compare the PR description and available repository facts against the repository's PR template, contribution requirements, and AI-use disclosure policy. | The submission satisfies the repository's explicitly required PR information, issue reference, testing disclosures, and AI-use disclosure requirements. A requirement is not considered satisfied merely because the description is polished. Optional template fields may be marked not applicable when appropriate, but mandatory information cannot be silently omitted. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Evaluate all six checks using the evidence sources identified in the table and the evidence guide.

Assign each check one of three grades:

pass: The available evidence satisfies the check's stated pass condition.

fail: The available evidence establishes a material violation of the pass condition.

unclear: The evidence is missing, contradictory, or insufficient to determine whether the condition is satisfied.

Return accept only when every required check passes.

Return reject if any required check is graded fail or unclear. Treat unclear as a failure for verdict purposes because an unverifiable requirement cannot establish submission readiness.

A preferred check, if added later, may inform the written feedback but must never independently change the verdict.

Apply the honest-outcome principle consistently. Do not reject a PR solely because an implementation is incomplete, a test failed, or a limitation exists, provided the actual state is accurately disclosed and the other required conditions are satisfied.

Do not allow disclosure to excuse unrelated changes, fabricated evidence, or missing mandatory repository requirements.

Evaluate the actual artifacts and their consistency rather than requiring arbitrary description lengths, commit counts, or formatting conventions beyond the repository's explicit standards.

Report the deciding evidence for each check and apply the verdict rule without overriding individual grades based on overall impressions.
