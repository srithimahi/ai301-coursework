# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check                            | Evidence                                                                                                                            | Pass condition                                                                                                                                                                                                                                                                                                                                                                                                             | Weight   |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Environment matches              | The repro report's environment record read against the environment relevant to the issue                                            | Pass when the recorded environment contains enough relevant conditions for another person to test the reported behavior in a comparable environment.                                                                                                                                                                                                                                                                       | required |
| Steps are reproducible           | The repro report's reproduction steps read together with any commands, inputs, setup details, and artifacts they reference          | Pass when another person could follow the described setup and actions to attempt the same reproduction without having to guess a material step or input.                                                                                                                                                                                                                                                                   | required |
| Behavior matches issue           | The reproduction artifacts/output read against the behaviour described in the issue                                                 | Pass when the observed behaviour is the behaviour described by the issue rather than unrelated failure                                                                                                                                                                                                                                                                                                                     | required |
| Outcome is supported             | The stated reproduction outcome read against the reproduction artifacts, observed output, and issue description                     | Pass when the stated outcome is supported by the evidence. An evidenced cannot-reproduce result passes; an unsupported success claim or confident reproduction of different behavior fails.                                                                                                                                                                                                                                | required |
| Repository conventions respected | The claim comment and repro report read against the repository conventions in the repo-facts block and references/evidence-guide.md | Pass only when every applicable repository-specific communication, contribution, and disclosure requirement is satisfied. If the repo requires disclosure of AI assistance, the package must explicitly include the required disclosure, including the tool and extent of assistance when the policy asks for them; absence of that disclosure fails this check even when the technical reproduction is otherwise correct. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Ready if all required checks pass. Hold if any required check fails or is unclear.
