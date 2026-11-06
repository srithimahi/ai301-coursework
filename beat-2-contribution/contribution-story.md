# Contribution: MudDataGrid: Add option to expand row on click

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Srithika Mahendran
**GitHub Username:** srithimahi
**Issue:** https://github.com/MudBlazor/MudBlazor/issues/11850
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Issue-scout customization and issue selection (2026-11-05)**

I customized the issue-scout skill with my fit profile, GitHub search
strategies, and a rubric for evaluating open-source issues. My initial
scan revealed problems with language and date filtering, ranking issues
with identical comment counts, and evaluating maintainer activity in
smaller repositories. I corrected the search commands, improved the
ranking and activity criteria, tested the search strategy with live
GitHub queries, and validated the rubric changes against five
evaluation fixtures. I then used the scout to grade MudBlazor #11850,
which passed all required checks and became my selected contribution
issue.

**Unit 6: Voice guard, upstream voice rules, and MudBlazor repo memory (2026-11-05)**

I consolidated the voice rules from repro-check, plan-check, and
pr-precheck into one canonical guide and added upstream rules for claims, questions, and
follow-up pings, then installed the voice guard as a PreToolUse hook on
the Bash tool. My first wiring test failed because the hook only watches
Bash and Claude ran the command through PowerShell, so nothing was
checked. When I reran `gh issue comment --help` through Bash, the guard
fired, blocked it as having no body it could read, and logged the stop;
PowerShell is still outside the guard's protection, so I now post to
GitHub only through Bash with `--body-file`. In my MudBlazor fork I
created a git-excluded `CLAUDE.local.md` from the Unit 6 template that
imports `AGENTS.md` and records my issue and claim link, the DataGrid
files and testing conventions, and the unresolved
`RowClickExpand`/`SelectOnRowClick` design question.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I found MudBlazor #11850 on the official CodePath Issue Selection
website. My own scout scan had already surfaced santoshshinde2012/holdmap
#114, which asks to clear three svelte-check accessibility warnings, so I
ended up with two real candidates. I graded both with my issue-scout
under the patched Unit 6 rubric, and both got ACCEPT: every required
check passed for each. The difference was the new difficulty note.
holdmap #114 came back as straightforward because the issue names the
file and lines and has a clear acceptance list. MudBlazor #11850 came
back as ambitious: no maintainer has settled the design, and it's C# and
Blazor, which are outside the Python/JavaScript/TypeScript in my fit
profile. By fit alone, holdmap ranked first, so choosing MudBlazor means
going against my scout's ranking, though not its verdict. I made that
choice on purpose. MudBlazor has active maintainers (v9.12.0 shipped on
2026-10-30, and the last five commits on `dev` were made in the two days
before I graded it), a mature contributor workflow with a detailed
CONTRIBUTING.md and AGENTS.md, and outside pull requests that actually
get merged, one of them about two hours after it was opened. holdmap is
active too, but it's a solo project, and its one outside PR was folded
into the owner's release PR instead of being merged directly. I want to
learn C#, Blazor, and how UI components are designed, and I want to
learn them by contributing to an established library with real review
standards.

The scout got the facts it can measure right. Repository activity,
maintainer activity and availability were all correct when I checked
them by hand: nobody had claimed the issue, and no PR was linked or
mentioned. Where its ACCEPT fell short was the design question. The
issue proposes a `RowClickExpand` parameter, but `MudDataGrid` already
selects a row when you click it (`SelectOnRowClick` defaults to true),
and in #7982 a maintainer described the expand toggle as deliberately
separate from row selection. A row-click-to-expand option cuts across
that, and the scout's verdict didn't capture it. The ambitious note
pointed me in the right direction, but the important context from
#7982 only surfaced during a deeper investigation of related issues.
I haven't reproduced
anything yet, and no maintainer has approved the design. My claim says
what I plan to investigate first and asks that one design question
before I write any code:
https://github.com/MudBlazor/MudBlazor/issues/11850#issuecomment-6677061973

**Toolkit**

- Tool: issue-scout (my search strategy, my rubric). I ran it in direct
  mode on the two issue URLs (MudBlazor #11850 and holdmap #114) after
  patching the rubric for Unit 6. I didn't run a new scan; holdmap had
  come from my earlier scan, and MudBlazor from the CodePath site.
- What it produced: a regrade appended to `scan-output.md` with seven
  checks per issue, both ACCEPT, and a difficulty note on each: holdmap
  #114 straightforward, MudBlazor #11850 ambitious, naming the open
  design edge (how a row click should interact with `RowClick`,
  `SelectOnRowClick` and the existing hierarchy toggle) and the
  unfamiliar C#/Blazor stack.
- Difficulties: my original *Manageable scope* check was written for
  the sandbox. It failed any issue that left "a required product
  decision… unresolved", and that describes most real issues, including
  this one. Under that check, MudBlazor's grade depended on how strictly
  the grader read the wording. Even after the patch, the scout only
  reads the issue's own thread. It didn't see the maintainer's stance on
  #7982, and it doesn't notice that the `good first issue` label was
  added by a bot rather than a maintainer. The verdict said "safe to
  claim", but the hard question was still open.
- What changed: I replaced *Manageable scope* with the Unit 6
  *scope-feasible* check, which fails only issues that aren't a single
  piece of work, such as umbrella issues, codebase-wide checklists, or
  trackers of many sub-tasks. I also added the difficulty note
  (straightforward / moderate / ambitious), which flags open edges
  without filtering them out. I logged the change in `scan-notes.md`
  on 2026-11-05 and backed up the old rubric. What I would still
  change: have the difficulty note check related issues for
  maintainer statements about the same component, and note whether a
  `good first issue` label was added by a human or a bot. Comparing the
  verdict with my own judgment taught me that ACCEPT means "available
  and alive", not "the design is settled"; that part is still mine to
  read and to ask about.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

I worked on Windows 11 (10.0.26200) in my fork, `srithimahi/MudBlazor`,
cloned to `C:\Srithika\Projects\Codepath\MudBlazor` with `origin` set to
the fork and `upstream` to `MudBlazor/MudBlazor`. I tested on the `dev`
branch at commit `97f33ac` (#14130). MudBlazor's `global.json` pins the
.NET SDK to the 10.0.400 feature band (`rollForward: latestPatch`), but
my machine only had .NET 8.0.203 and 8.0.204, so `dotnet --version`
inside the repo failed with the `global.json` error. I installed the
official .NET SDK 10.0.403 through `winget` (machine-wide, approved
through a UAC prompt) without removing the .NET 8 SDKs, and after that
the repo resolved to 10.0.403. `dotnet tool restore` restored the
repo's local Bun tool (`bundotnet.cli` 3.0.0), and my first existing
test, `DataGridSingleSelectOnRowClick`, passed (1 passed, 0 failed,
0 skipped). For the reproduction I used `MudBlazor.UnitTests.Viewer`,
the test app AGENTS.md recommends for behavior that needs a browser,
and put my component in `TestComponents/Scratch/`, which the repo
gitignores for throwaway repros. My first Viewer build failed with
`CS0246` because `DataGridHierarchyVisibilityToggledEventArgs` lives in
the `MudBlazor.Utilities` namespace, not `MudBlazor`; AGENTS.md warns
about exactly this, and adding `@using MudBlazor.Utilities` fixed it.
To click through the scenarios I installed `playwright-core` 1.56.1
into a temporary folder outside the repo and drove my installed Google
Chrome 157.0.8103.38 headless. My first script run timed out because
`MudSwitch` puts the `data-testid` on the `<input>` itself, not on a
wrapper, so I fixed the selector.

**Steps to Reproduce**

1. Create `src/MudBlazor.UnitTests.Viewer/TestComponents/Scratch/DataGridRowClickRepro.razor`:
   a three-row `MudDataGrid` (Sam, Alicia, Ira) with a `HierarchyColumn`,
   `ChildRowContent`, a `SelectOnRowClick` switch, and an on-page log of
   `RowClick`, `SelectedItemChanged` and `HierarchyVisibilityToggled`.
   The full source is in my reproduction report draft.
2. From the repo root, build the Viewer (a full build, so the Bun
   assets compile):
   `dotnet build src/MudBlazor.UnitTests.Viewer/MudBlazor.UnitTests.Viewer.csproj --nologo`
   (Build succeeded, 0 warnings, 0 errors).
3. Run it:
   `dotnet run --project src/MudBlazor.UnitTests.Viewer/MudBlazor.UnitTests.Viewer.csproj --no-build --urls http://localhost:5199`
   and open `http://localhost:5199/viewer/Scratch/DataGridRowClickRepro?chrome=none&theme=light`
   (the page reached `data-viewer-state="ready"`).
4. In one page load, clearing the log before each click (selection and
   expansion carry over):
   - A. With `SelectOnRowClick` on (the default), click Sam's Name cell.
   - B. Still on, click Ira's expand button.
   - C. Turn `SelectOnRowClick` off, then click Alicia's Name cell.
   - D. Still off, click Alicia's expand button.
5. Observed result: row-body clicks (A, C) never expanded a detail row;
   only the expand button (B, D) did. The clicks were made by my
   Playwright script in headless Chrome, one automated click per
   scenario, not by hand.

**Reproduction Evidence**

- **Commit showing reproduction:** none. The repro component lives in
  the gitignored `Scratch/` folder on purpose and is not committed to
  my fork; its full source is in my reproduction report draft, so
  anyone can recreate it.
- **Screenshots/logs:** the on-page event log from the run:

  | Scenario | Selected after | Detail rows shown after | Events raised |
  |---|---|---|---|
  | A. Row body, Sam (on) | (none) → Sam | none | `RowClick: Sam (row 0)`, `SelectedItemChanged: Sam` |
  | B. Button, Ira (on) | Sam (unchanged) | Ira | `HierarchyVisibilityToggled: Ira expanded=True` |
  | C. Row body, Alicia (off) | Sam (unchanged) | Ira (unchanged) | `RowClick: Alicia (row 1)` |
  | D. Button, Alicia (off) | Sam (unchanged) | Alicia, Ira | `HierarchyVisibilityToggled: Alicia expanded=True` |

  A screenshot after D matched the log (Alicia and Ira expanded, the
  switch off, "Selected: Sam"). I kept it locally and did not upload it.
- **My findings:** this is a missing enhancement, not a broken feature.
  Issue #11850 asks for an option where clicking a row "will expand its
  detail section without requiring to click the explicit expand
  button". On current `dev` there is no such option: a row-body click
  selects the row when `SelectOnRowClick` is on and always raises
  `RowClick`, but never expands it (A, C). Everything I tested matched
  the current API and docs. I also observed that the expand button
  raised neither `RowClick` nor `SelectedItemChanged` (B, D), so
  expansion and selection are fully separate today. That matches the
  maintainer comment on #7982, and it is why my claim asks how a
  `RowClickExpand` option should interact with `SelectOnRowClick`
  before I build anything. No maintainer has answered yet. Not tested:
  - collapsing with a second click
  - `ExpandSingleRow`
  - rows disabled through `ButtonDisabledFunc`
  - keyboard interaction
  - virtualized rows
  - a cell with its own `CellClick` handler
  - anything clicked on dev.mudblazor.com, where I only read the Row
    Detail View docs

  The "no double toggle from the expand button" result rests on one
  click per state, not a full test.

**Toolkit**

- Tool: repro-check (my rubric, evidence guide and voice guide). I ran
  it in live mode on the full package: my posted claim comment plus my
  reproduction report draft (`repro-draft.md`), read against the live
  issue thread.
- What it produced: ACCEPT, with all five required checks passing:
  Environment matches, Steps are reproducible, Behavior matches issue,
  Outcome is supported, and Repository conventions respected. It also
  checked the draft against my voice guide and found no broken rules.
- Difficulties: my rubric is shaped around bugs ("the behavior shown
  matches the issue"), and this issue is a feature request, so there
  is no bug to reproduce. "Behavior matches issue" passes only because
  the issue describes the gap, and the report shows that gap. The
  checks also grade the write-up against the evidence I give them;
  they cannot tell whether the event log came from a real run. So I
  separately compared every event line and the "after" state for each
  scenario with the raw script output, and they matched exactly.
- What changed: the check confirmed the report should say plainly that
  this is a missing option, not a bug, and list what I did not test.
  It also suggested naming the component's full path in the draft. I
  would add a rubric note for feature requests: an evidenced "the
  option doesn't exist today" should count as matching the issue.

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
