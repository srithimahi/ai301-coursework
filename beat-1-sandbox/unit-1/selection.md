# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/64

**Verdict output**

Fit profile in scope.md is still the placeholder — I'll note that at the ranking step. Gathering evidence now.

All three are in the scoped repo (codepath/pathreview-ai301-fa26-s1), so all three are valid candidates. Evidence gathered live via the GitHub API (today: 2026-09-20).

Shared repo facts (decide the two repo-level checks identically for all three):
- Releases: none published → recency falls to the maintainer-response sample. Aburke225 (COLLABORATOR) posted closing comments on #52 and #43 on 2026-09-16, 4 days ago → Maintainer activity: pass.
- Last 5 default-branch commits: 2026-09-16 ×3, 2026-08-24 ×2 → all 5 within 90 days → Repository activity: pass.
- Repo has 0 pull requests (open or closed), so no issue has a linked PR.

Per issue

- #64 — relevance scorer fixture — all required pass. One bounded test-fixture bug, no assignee, no comments at all. Preferred check is the strongest of the three: it carries an actual repro command (pytest tests/unit/test_relevance_scorer.py -q) and the observed failure (assert 1.0 < 0.9). accept
- #72 — verify_password / UnknownHashError — all required pass. One coherent fail-closed bug, both files named, plus the instruction to drop the @pytest.mark.xfail marker. Note: the timeline shows a referenced event from newairforces on 2026-09-19, but it's a commit in their own newairforces/ai301-coursework repo, not a linked PR here and not a thread comment — and the Path Review house rule says classmate activity doesn't block. accept
- #73 — README vs .env.example — all required pass. Two files named, and the desired outcome ("make the two files agree") is determinable because core/config.py already defines both keys, so the reconciliation direction isn't an open product decision. accept

Ranking caveat: the fit-profile section of scope.md is still the placeholder (Write a few sentences here.), so I can't rank these on fit. The order below is by strength of the preferred check (concreteness of the starting point) — fill in your fit profile and I'll re-rank properly.

Per the house rule, claim whichever you pick even if classmates are on it — credit attaches to the PR you open.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/64",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "No releases exist, but COLLABORATOR Aburke225 first-responded on issues #52 and #43 on 2026-09-16, 4 days before today."},
      {"name": "Repository activity", "grade": "pass", "evidence": "Last 5 default-branch commits: 2026-09-16 (x3) and 2026-08-24 (x2) — all within 90 days."},
      {"name": "Manageable scope", "grade": "pass", "evidence": "One bounded fixture bug with a stated resolution: 'Fix the fixture so the overlap is genuinely partial.'"},
      {"name": "Unclaimed issue", "grade": "pass", "evidence": "assignees: [] ; repo has 0 pull requests; comments count: 0 — no claim or work events at all."},
      {"name": "No unresolved formal claim", "grade": "pass", "evidence": "Empty comment thread, so no formal claim command exists."},
      {"name": "Beginner guidance", "grade": "pass", "evidence": "'Steps to reproduce: pytest tests/unit/test_relevance_scorer.py -q — observed: assert 1.0 < 0.9 fails.'"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "No releases exist, but COLLABORATOR Aburke225 first-responded on issues #52 and #43 on 2026-09-16, 4 days before today."},
      {"name": "Repository activity", "grade": "pass", "evidence": "Last 5 default-branch commits: 2026-09-16 (x3) and 2026-08-24 (x2) — all within 90 days."},
      {"name": "Manageable scope", "grade": "pass", "evidence": "One coherent bug with a stated expected outcome: 'Verification against a malformed hash should fail closed (return False), not raise.'"},
      {"name": "Unclaimed issue", "grade": "pass", "evidence": "assignees: [] and no linked PR (repo has 0 PRs); the only timeline event is a 'referenced' commit in newairforces' own ai301-coursework repo, and the house rule says classmate activity does not block."},
      {"name": "No unresolved formal claim", "grade": "pass", "evidence": "Comment thread is empty — no formal claim command was ever issued."},
      {"name": "Beginner guidance", "grade": "pass", "evidence": "Names core/security.py and tests/unit/test_security.py, plus 'remove the marker as part of the fix' for the H-05 xfail."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "No releases exist, but COLLABORATOR Aburke225 first-responded on issues #52 and #43 on 2026-09-16, 4 days before today."},
      {"name": "Repository activity", "grade": "pass", "evidence": "Last 5 default-branch commits: 2026-09-16 (x3) and 2026-08-24 (x2) — all within 90 days."},
      {"name": "Manageable scope", "grade": "pass", "evidence": "One documentation inconsistency with a determinable outcome — 'core/config.py defines both keys. Make the two files agree.' — so no product decision is left open."},
      {"name": "Unclaimed issue", "grade": "pass", "evidence": "assignees: [] ; repo has 0 pull requests; comments count: 0."},
      {"name": "No unresolved formal claim", "grade": "pass", "evidence": "Empty comment thread, so no formal claim command exists."},
      {"name": "Beginner guidance", "grade": "pass", "evidence": "'Relevant files: README.md, .env.example' with the conflict spelled out, though no reproduction command."}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

**Run history**

2/3 → 0/1 → 1/1 → 15/20 → 3/5 → 1/2 → 1/1 → 16/20 → 3/4 → 0/1 → 3/4 → 2/2 → 18/20 → 18/20

**Issue analysis**

`issue-15`: my final rubric decided `reject`, and the gold label was also `reject`. The decisive evidence was the unresolved formal claim in the comment thread. The final claim-related event was `@zulipbot claim` from `souvik150`, with no later bot or maintainer message releasing, rejecting, expiring, or unassigning that claim. My earlier versions sometimes accepted the issue because they treated old claims too loosely, so I separated formal-claim handling into its own required check.

**Check rationale**

| No unresolved formal claim | Comment thread in chronological order: explicit claim commands such as `@zulipbot claim`, followed by any bot/maintainer rejection, unassignment, expiration, release, or abandonment message | Pass if there is no explicit formal claim command, OR every formal claim command is followed later by evidence that the claim was rejected, unassigned, expired, released, or abandoned. Fail if the latest formal claim command has no later clearing message. Do not treat age alone as clearing a claim. Expressions of interest such as "I'd like to work on this" are not formal claims. | required |

I added this check because the broader `Unclaimed issue` check was not consistently distinguishing casual expressions of interest from a formal repository claim. The separate check makes the state transition mechanical: a formal claim remains unresolved until later evidence explicitly clears it.

**Trade-offs**

I re-ran `issue-09` and `issue-15` together as canaries after adding the formal-claim check. `issue-09` still accepted because its contributor only said they would like to work on the issue and never used a formal claim mechanism, while `issue-15` rejected because its latest formal claim had no later clearing message. The trade-off is that this check intentionally treats even an old formal claim as blocking when the snapshot contains no explicit release, rather than assuming that age alone makes the issue available.

---

## Selection rationale

**Selection rationale**

1. Issue #64 fits me because I am comfortable debugging tests and Python, and it is small enough to finish within the time available. It already gives the exact failing test command and assertion, so I have a clear place to start.

2. The skill correctly identified that the issue is bounded, unclaimed, and has strong beginner guidance. It could measure those concrete signals, but it could not really measure whether I personally would enjoy debugging this issue or how comfortable I feel with the code once I open the project.

3. I expect claiming it to be straightforward because there is no assignee, no linked PR, and no comment thread showing another person working on it. I still need to follow the Path Review claiming process in Unit 2 rather than assuming that the issue is mine now.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
