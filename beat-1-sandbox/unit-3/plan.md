# Plan for Issue #64

## Diagnosis

The failing test is `TestRelevanceScorer::test_query_with_partial_overlap` in `tests/unit/test_relevance_scorer.py`.

When the test is run with the `xfail` marker bypassed, it fails at:

`assert 0.3 < score < 0.9`

because the relevance scorer returns a score of `1.0`.

The current fixture uses the query:

`Python Django web framework`

and the chunk:

`Django is a Python web framework for rapid development`

All four query terms are present in the chunk, so the fixture creates full keyword overlap rather than the partial overlap the test is intended to exercise.

The reproduced evidence therefore points to the test fixture as the cause of the failure, not the relevance-scoring implementation itself.

## Scope

I will update the fixture used by `test_query_with_partial_overlap` so that only some of the query terms appear in the chunk.

I will also remove the strict `@pytest.mark.xfail` marker from this test once the fixture is corrected, because the repository guidance requires the marker to be removed when the test begins passing.

I will keep the change limited to `test_query_with_partial_overlap` in `tests/unit/test_relevance_scorer.py`.

I will not change the relevance scorer implementation unless new evidence during implementation shows that the scorer itself is responsible for incorrect partial-overlap behavior.

## Files to change

- `tests/unit/test_relevance_scorer.py`

## Approach

Update the chunk used by `test_query_with_partial_overlap` so that it represents genuine partial overlap rather than full overlap.

A candidate fixture is:

`Django is a Python framework for rapid development`

With the existing query `Python Django web framework`, this keeps three of the four query terms present and leaves `web` unmatched, producing genuine partial overlap.

After confirming that the corrected fixture produces a score in the expected range, remove the test's strict `@pytest.mark.xfail` marker so the passing test is treated normally rather than as an unexpected pass.

No scorer logic will be changed unless the corrected fixture still exposes incorrect scoring behavior.

## Test plan

First rerun the original reproduction command:

`python -m pytest "tests/unit/test_relevance_scorer.py::TestRelevanceScorer::test_query_with_partial_overlap" -q --runxfail`

Before the fix, this produced a score of `1.0` and failed:

`0.3 < score < 0.9`

After the fixture change, I expect the test to pass with a score inside the expected partial-overlap range.

Then remove the strict `xfail` marker and run:

`python -m pytest tests/unit/test_relevance_scorer.py -q`

I expect all 19 tests in that file to pass normally, with no `xfail` remaining for this issue.

Finally, run the repository-required checks:

`make check && make test-unit`

These should complete without introducing regressions.

## Risks and unknowns

The reproduction proves that the current fixture creates full overlap. The scorer uses query-term overlap, so a three-of-four-term fixture should produce genuine partial overlap, but the exact observed score will still be verified during implementation.

If a genuine partial-overlap fixture still produces an incorrect score, I will investigate the scorer implementation before expanding the scope.

## Deviations

The implementation matched the planned code change: I updated the partial-overlap fixture and removed the strict xfail marker.

The planned repository-level commands `make check` and `make test-unit` could not be run because GNU Make is not installed in my Windows/Git Bash environment. I instead verified the change by rerunning the affected test directly and the full `tests/unit/test_relevance_scorer.py` file.

The affected test passed, and the full file completed with 19 passed.
