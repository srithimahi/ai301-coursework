# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

srithimahi

---

## Posted upstream

**Claim comment**

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/64#issuecomment-5864019055

Hi! I'd like to investigate this issue. I'll attempt to reproduce the failing test_query_with_partial_overlap test and check whether the fixture gives the scorer full query-term overlap instead of the intended partial overlap. I'll report back here with the environment, steps, and observed result before making any changes.

**Reproduction comment**

[[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]] 
(https://github.com/codepath/pathreview-ai301-fa26-s1/issues/64#issuecomment-5874798837)
Environment:

Windows, Git Bash
Python 3.12
pytest 9.1.1
Repository: my fork of codepath/pathreview-ai301-fa26-s1
Branch: main
Test file: tests/unit/test_relevance_scorer.py
Steps:

Created and activated a Python virtual environment.

Installed pytest and the dependency needed by the relevance scorer (structlog).

Ran the full unit test file:

python -m pytest tests/unit/test_relevance_scorer.py -q

Result:

18 passed, 1 xfailed

Re-ran the affected test while ignoring the xfail marker:

python -m pytest "tests/unit/test_relevance_scorer.py::TestRelevanceScorer::test_query_with_partial_overlap" -q --runxfail

Observed:
The test fails at:

assert 0.3 < score < 0.9

with:

E assert 1.0 < 0.9

The captured scorer output also reports:

avg_score=1.0

The fixture uses the query Python Django web framework and the chunk Django is a Python web framework for rapid development, so all four query terms are present. This gives full keyword overlap rather than the partial overlap the test is meant to exercise.

Outcome:
I reproduced issue #64. The test fixture produces a relevance score of 1.0, so the assertion expecting a middle-range partial-overlap score fails when the xfail marker is bypassed.



## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

- Full run 1: 19/20 agreement. The only disagreement was `pkg-20`, where my rubric returned `accept` while the gold label was `reject`. The disclosure category was 0/1.
- Targeted rerun with `--only pkg-20`: the rubric returned `reject`, matching the gold label, after I revised the repository-conventions check and evidence guide to make required AI-assistance disclosure explicit.
- Final full run: 20/20 agreement. All categories matched: clear-accept 8/8, disclosure 1/1, no-evidence 4/4, unfollowable-comms 3/3, and wrong-target 4/4.

**Package analysis**

I analyzed `pkg-20`. My final rubric decided `reject`, which matched the gold label of `reject`. The technical reproduction itself was strong: it recorded a specific Ghostty 1.3.1 environment, gave reproducible steps, showed the mode-2031 output for both configurations, and matched the behavior described in the issue. However, the repo-facts block stated that Ghostty requires all AI usage to be disclosed, including the tool used and the extent of assistance. The candidate claim comment and reproduction report contained no such disclosure. Because my repository-conventions check is required, the missing mandatory disclosure caused the package to be rejected even though its technical evidence was otherwise sufficient.

**Check rationale**

> `| Repository conventions respected | The claim comment and repro report read against the repository conventions in the repo-facts block and references/evidence-guide.md | Pass only when every applicable repository-specific communication, contribution, and disclosure requirement is satisfied. If the repo requires disclosure of AI assistance, the package must explicitly include the required disclosure, including the tool and extent of assistance when the policy asks for them; absence of that disclosure fails this check even when the technical reproduction is otherwise correct. | required |`

I revised this check after my first full evaluation scored `pkg-20` as `accept` even though its gold label was `reject`. My earlier wording mentioned AI disclosure, but it did not make sufficiently explicit that a missing required disclosure must fail the check. I changed the pass condition to state that every applicable repository-specific requirement must be satisfied and that absence of a required AI disclosure is a failure even when the reproduction itself is technically correct. I also made the corresponding guidance more explicit in `references/evidence-guide.md`.

**Trade-offs**

The revision deliberately makes repository-specific disclosure requirements a hard gate. This changed `pkg-20` from `accept` to `reject`: its technical reproduction was otherwise strong, but Ghostty's captured repository policy required disclosure of AI assistance and the candidate supplied none. I reran `pkg-20` with `--only` after making the change and it matched the expected `reject`. I then ran the complete 20-package evaluation again; it scored 20/20 with every category matched, showing that the tighter disclosure rule fixed the disclosure case without changing the expected outcomes of the other scored packages.
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
