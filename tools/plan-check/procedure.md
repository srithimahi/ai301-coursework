# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Read the issue/thread highlights first. Note the requested behavior, constraints, and any explicit maintainer requirements.
2. Read the repro evidence next. Note the exact reproduction steps, observed behavior, expected behavior, and evidence about the cause.
3. Read the repo facts/conventions. Note any conventions or constraints relevant to the proposed change.
4. Read the plan and draft comment last. Note the claimed diagnosis, proposed scope, implementation approach, test plan, risks, and unknowns.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

1. Identify the exact reproduced failure and expected result.
2. Identify the plan's claimed cause.
3. Identify proposed files/functions and exclusions.
4. Identify the proposed test steps and expected post-fix result.
5. Note any explicit unknowns or assumptions.
6. Note thread requirements and repo conventions relevant to the change.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Grade the checks in this order: Diagnosis, Scope, Executability, Test plan, Uncertainty handling, Thread and repo alignment.
2. For each check, compare the gathered evidence named by that check's Evidence column against its Pass condition.
3. Grade each check independently as pass, fail, or unclear.
4. Use only evidence actually present in the package; do not assume missing details.
5. Grade a check unclear when the evidence needed to decide it is genuinely absent or insufficient.
6. For each grade, cite the evidence that supports the decision.
7. If evidence conflicts, prefer reproduced evidence and explicit thread/repo facts over unsupported claims in the plan.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Review all required checks.
2. Treat unclear as fail.
3. Accept only if every required check passes.
4. Otherwise reject.
5. In the output, quote the evidence supporting any required check that caused a reject verdict. If all required checks pass, quote evidence supporting the accept verdict.
