# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`.

---

## Posted upstream

**GitHub username**

srithimahi

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/64#issuecomment-5924199041

I reproduced the failure in `test_query_with_partial_overlap` and traced it to the test fixture. The current query is `Python Django web framework`, while the chunk is `Django is a Python web framework for rapid development`. Since all four query terms appear in the chunk, the fixture produces full overlap and a score of `1.0` instead of the partial-overlap score the test expects.

I plan to update the fixture in `tests/unit/test_relevance_scorer.py` to use the chunk `Django is a Python framework for rapid development`. With the existing query, that matches 3 of the 4 query terms, so the expected relevance score is `0.75`, which falls within the test's `0.3 < score < 0.9` range.

After confirming the corrected fixture passes, I will remove the strict `@pytest.mark.xfail` marker as required by the repository once the test is fixed.

I will keep the change limited to this test and avoid changing the relevance scorer implementation unless further testing shows that the scorer itself is responsible.

After the change, I will rerun the affected test, then the full `tests/unit/test_relevance_scorer.py` file, and finally the repository-required `make check && make test-unit` checks.

---

## Your branch

**Branch**

`fix/64-partial-overlap-fixture`

**Evidence**

Before the fix:

```text
python -m pytest "tests/unit/test_relevance_scorer.py::TestRelevanceScorer::test_query_with_partial_overlap" -q --runxfail

FAILED tests/unit/test_relevance_scorer.py::TestRelevanceScorer::test_query_with_partial_overlap

assert 0.3 < score < 0.9

E assert 1.0 < 0.9

Captured scorer output:
avg_score=1.0
```

The original fixture used:

```text
Query: Python Django web framework
Chunk: Django is a Python web framework for rapid development
```

All four query terms were present, so the scorer produced full overlap instead of partial overlap.

After changing the chunk to:

```text
Django is a Python framework for rapid development
```

the scorer reported:

```text
avg_score=0.75
```

The test initially produced `XPASS(strict)` because the old expected-failure marker was still present. I then removed the strict `@pytest.mark.xfail` marker and reran the test:

```text
python -m pytest "tests/unit/test_relevance_scorer.py::TestRelevanceScorer::test_query_with_partial_overlap" -q

.                                                                [100%]
1 passed in 0.90s
```

I then reran the complete relevance-scorer unit test file:

```text
python -m pytest tests/unit/test_relevance_scorer.py -q

...................                                              [100%]
19 passed in 0.98s
```

I also attempted the repository-level checks:

```text
make check
make test-unit
```

but GNU Make is not installed in my Windows or Git Bash environment:

```text
make : The term 'make' is not recognized as the name of a cmdlet,
function, script file, or operable program.
```

Git Bash produced the same environment limitation:

```text
bash: make: command not found
```

The targeted test and complete `tests/unit/test_relevance_scorer.py` test file both passed.

## Eval iterations

**Run history**

- Full run 1: 20/20 agreement.

The final run matched every category:

- clear-accept: 7/7
- scope-creep: 4/4
- thread-convention: 2/2
- unbuildable: 3/3
- wrong-cause: 4/4

Final agreement: `20/20 scored items (bar: 18/20: PASS)`.

**Package analysis**

I analyzed `pkg-01`. My rubric returned `reject`, which matched the gold label of `reject`.

The package was in the `wrong-cause` category. My Diagnosis check requires the plan's stated cause to be read against the reproduced observed and expected behavior. Because the proposed diagnosis did not correctly follow from the reproduction evidence, the Diagnosis check failed. Since Diagnosis is a required check, that failure caused the overall package verdict to be `reject`.

This matched the purpose of the rubric: a plan should not be considered ready to build when its proposed fix is based on a cause that is inconsistent with the evidence.

**Check rationale**

> `| Diagnosis | The plan's stated cause read against the repro evidence's observed and expected behavior | Pass if the stated cause is consistent with the reproduced evidence and explains why the observed behavior differs from the expected behavior | required |`

I wrote this check so the grader does not accept a diagnosis merely because it sounds plausible. The stated cause has to be compared directly with the reproduction evidence and must explain the difference between the observed and expected behavior.

I chose this wording instead of a more general requirement such as "the plan explains the bug" because that could allow a confident but unsupported explanation to pass. The check makes evidence agreement part of the decision rule.

**Trade-offs**

I made all six checks required, which makes the rubric intentionally conservative: a plan is rejected when any one required area is not ready, even if the rest of the plan is strong.

This can reject a mostly good plan for one missing requirement, such as an otherwise correct technical plan that ignores a repository convention. I accepted that trade-off because the purpose of this skill is to decide whether a plan is ready to post and build from, not whether it is partially complete.

No rubric revision was required after the full evaluation run. The first and final full run scored 20/20, with every category matched, so I did not need targeted `--only` reruns or canaries.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
