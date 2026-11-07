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

Nothing is broken. `MudDataGrid` has no documented way to expand a
detail row by clicking the row itself: `ChildRowContent` opens only
from the `HierarchyColumn` expand button. The issue proposed a
`RowClickExpand` parameter. On 2026-11-06 danielchalmers (MEMBER)
answered my design question. `RowClick` plus the public
`ToggleHierarchyVisibilityAsync` "should cover this in a few lines",
so he suggested a docs example after the Detail Row section instead,
calling it "a good first PR". versile2 (CONTRIBUTOR) then posted a
working snippet and closed the issue as not planned. What's missing is
documentation, not a feature.

**Expected Behavior**

The DataGrid docs show how to handle `RowClick` and call
`ToggleHierarchyVisibilityAsync(args.Item)`, so that a row-body click
toggles that row's detail. With `SelectOnRowClick` on, the same click
also selects the row; the maintainer said that's fine. The expand
button still toggles once and stays the keyboard path.

**Current Behavior**

In my repro on `dev` at `97f33ac` (Viewer, headless Chrome, one
automated click per scenario), row-body clicks never expanded a row:

- Sam's Name cell with `SelectOnRowClick` on raised `RowClick` and
  `SelectedItemChanged` (A).
- Alicia's with it off raised only `RowClick` (C).

Only the expand button expanded a row. It raised
`HierarchyVisibilityToggled`, with no `RowClick` and no selection
change (B, D). The docs page has no row-click expansion example.

**Affected Components**

- To change: `src/MudBlazor.Docs/Pages/Components/DataGrid/DataGridPage.razor`
  (a new section after "Row Detail View") and a new example in
  `.../DataGrid/Examples/`.
- Read but not changed:
  - `MudDataGrid.razor.cs`: `OnRowClickedAsync`,
    `ActivateRowBehaviorsAsync` and `ToggleHierarchyVisibilityAsync`
  - `HierarchyColumn.razor` and `CellContext.cs`: the expand button
  - `MudBaseButton.cs`: a `<button>` stops click propagation, which
    is why B and D raised no `RowClick`

**Toolkit**

- Tool: Claude Code in my MudBlazor clone, with `CLAUDE.local.md` and
  `AGENTS.md` loaded. It re-read the live #11850 thread with
  `gh issue view --comments` and traced the row-click and hierarchy
  code on `dev` against my A–D event log.
- What it produced: the maintainer's reply and the closure, caught
  before planning. It also produced the code trace above, and an
  explanation for the button result in my repro (`MudBaseButton` stops
  propagation for a `<button>`).
- Difficulties: my own framing. I had read #7982 as "expansion must
  stay separate from selection" and built my claim's question on it.
  The maintainer said it only meant the button shouldn't change
  selection. The thread also now disagrees with my repro: versile2
  says the chevron's click "bubbles up to the row", while my B/D runs
  and `MudBaseButton.GetClickPropagation` say it doesn't. That's not
  settled by a test yet.
- What changed: I dropped `RowClickExpand` and re-scoped the work to
  the docs example. The bubbling question became a check to run in
  the Viewer before the example ships, and I updated `CLAUDE.local.md`
  so my repo memory no longer lists the parameter question as open.

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

This plan builds on my reproduction on `dev` at `97f33ac`: a
`MudBlazor.UnitTests.Viewer` scratch component
(`TestComponents/Scratch/DataGridRowClickRepro.razor`) showing a
three-row grid (Sam, Alicia, Ira) with a `HierarchyColumn`,
`ChildRowContent`, a `SelectOnRowClick` switch and an on-page event
log. I ran one automated click per scenario in headless Chrome:

| Scenario | Events raised | Detail rows after |
|---|---|---|
| A. Row body, Sam (`SelectOnRowClick` on) | `RowClick: Sam (row 0)`, `SelectedItemChanged: Sam` | none |
| B. Expand button, Ira (on) | `HierarchyVisibilityToggled: Ira expanded=True` | Ira |
| C. Row body, Alicia (off) | `RowClick: Alicia (row 1)` | Ira (unchanged) |
| D. Expand button, Alicia (off) | `HierarchyVisibilityToggled: Alicia expanded=True` | Alicia, Ira |

There's no bug behind A and C. Two code paths in
`src/MudBlazor/Components/DataGrid/MudDataGrid.razor.cs` already
exist, and nothing connects them:

- **Row click path.** The `<tr>` click calls
  `OnRowClickedAsync(args, item, rowIndex)`. It raises `RowClick` and
  then calls `ActivateRowBehaviorsAsync(item)`. That method only
  starts editing (with `EditTrigger.OnRowClick`) and calls
  `SetSelectedItemAsync(item)`, which toggles selection and returns
  early when `SelectOnRowClick` is `false`. Nothing here touches
  `_openHierarchies`, so A and C never expand. A cell with its own
  `CellClick` handler goes through `OnCellClickedAsync` instead: it
  raises `CellClick` (not `RowClick`) and then makes the same
  `ActivateRowBehaviorsAsync` call.
- **Hierarchy path.** The public `ToggleHierarchyVisibilityAsync(T)`
  adds or removes the item in `_openHierarchies` (honoring
  `ExpandSingleRow`), raises `HierarchyVisibilityToggled`, and
  re-renders. The default `HierarchyColumn` button reaches it through
  `CellContext.Actions.ToggleHierarchyVisibilityForItemAsync`. That
  button is a `MudIconButton`, and `MudBaseButton` adds
  `onclick:stopPropagation` when it renders as `<button>` without
  `ClickPropagation`. That matches B and D raising no `RowClick`.
- **One trap.** `ToggleHierarchyVisibilityAsync` does not check
  `ButtonDisabledFunc`, although `ExpandAllHierarchy` and
  `CollapseAllHierarchy` do. A row-click handler that calls it
  directly would expand a row whose button is disabled.

One `RowClick` handler that calls `ToggleHierarchyVisibilityAsync`
connects the two paths. The library needs no change. What's missing
is a docs example that shows the pattern.

**Proposed Solution**

I'll add a docs example and make no library change. This follows
danielchalmers' (MEMBER) suggestion on #11850 on 2026-11-06, and it
builds on versile2's snippet in the same thread. I'll add a new
example and a short section to the DataGrid docs page, right after
"Row Detail View". The example uses a `RowClick` handler that calls
`_dataGrid.ToggleHierarchyVisibilityAsync(args.Item)`, keeps the
default expand button, and sets `Hover="true"` and
`RowStyle="cursor: pointer;"` so rows look clickable. The section
description says three things:

- A row click toggles the detail. With `SelectOnRowClick` on (the
  default), the same click also selects the row, and a second click
  collapses it and deselects it. The maintainer said one click
  selecting and expanding is fine.
- The expand button stays. It toggles once and is the keyboard path,
  because a `<tr>` click isn't reachable by keyboard.
- `ToggleHierarchyVisibilityAsync` ignores `ButtonDisabledFunc`, so a
  handler that should skip disabled rows has to check that itself.

What I'm deliberately not changing:

- no `RowClickExpand` parameter (the maintainer pointed to the
  existing API instead)
- no change to `OnRowClickedAsync`, `ActivateRowBehaviorsAsync`,
  `ToggleHierarchyVisibilityAsync`, `HierarchyColumn`, or the
  `RowClick`/`CellClick`/`SelectOnRowClick`/`ExpandSingleRow`
  behavior
- no change to the existing `DataGridDetailRowExample`
- not making the toggle honor `ButtonDisabledFunc` (a behavior change
  that belongs in its own issue)

**Open choices, with my defaults**

The maintainer suggested this direction, so I'm not waiting for
another reply before building. He hasn't reviewed this plan or any
code, though. I'll build with the defaults below and name each choice
in the PR so reviewers can redirect me:

1. *Placement and name.* I read "after the Detail Row section" as
   right after "Row Detail View" and before "Row Detail Renderer". The
   section will be titled "Expand Row on Click", and the example will
   be `DataGridRowClickExpandExample`, following AGENTS.md's
   `<Component><Scenario>Example` pattern.
2. *`ButtonDisabledFunc`.* The example leaves it out, so it teaches one
   thing (AGENTS.md: one concept per example). The caveat goes in one
   sentence of the description.
3. *The `stopPropagation` wrapper.* versile2's snippet wraps the
   chevron in `<span @onclick:stopPropagation="true">` and says the
   default button's click bubbles to the row. My B/D runs and
   `MudBaseButton.GetClickPropagation` say it doesn't. Step 2 tests
   this. If a button click toggles once, the example uses the plain
   default `HierarchyColumn` without the wrapper. If it toggles twice,
   I add the wrapper with a one-line comment and note in the PR why my
   earlier reading was wrong.
4. *A pinning test.* No library logic changes, so CONTRIBUTING.md's
   test requirement doesn't apply. By default I won't add a bUnit
   test, and I'll offer one in the PR (see step 5).

Risks and unknowns:

- versile2 closed #11850 as not planned. Reviewers could still
  decline a docs PR.
- I haven't yet tested a second click, `ExpandSingleRow`,
  disabled-button rows, virtualization, or keyboard use with the
  handler wired.
- The docs page loads `Element` data from `webapi/periodictable`, as
  the existing examples do. I haven't run `MudBlazor.Docs.Server` on
  this machine yet.

**Implementation Plan**

1. **Branch.** In my fork, run `git fetch upstream` and create
   `feature/datagrid-row-click-expand-example` from `upstream/dev`
   (CONTRIBUTING.md: `feature/` for enhancements). The PR targets
   `dev`. To stay current I merge upstream `dev` and never rebase.
2. **Check the pattern in the Viewer first (scratch only, never
   committed).** Add the handler to my gitignored repro:
   `RowClick="OnRowClickAsync"` calling
   `_grid.ToggleHierarchyVisibilityAsync(args.Item)`. Rebuild with
   `dotnet build src/MudBlazor.UnitTests.Viewer/MudBlazor.UnitTests.Viewer.csproj --nologo`,
   run it on `http://localhost:5199`, and re-run each scenario, saving
   the event log:

   | Scenario (handler wired) | Before (table above) | Expected after |
   |---|---|---|
   | A. Row body, Sam (on) | no detail row | `RowClick`, `SelectedItemChanged: Sam`, `HierarchyVisibilityToggled: Sam expanded=True`; Sam's detail shown |
   | A2. Row body, Sam again (on) | not run | `HierarchyVisibilityToggled: Sam expanded=False`; Sam's detail hidden, Sam deselected |
   | B. Expand button, Ira (on) | Ira expanded | exactly one `HierarchyVisibilityToggled: Ira expanded=True`, no `RowClick` |
   | C. Row body, Alicia (off) | no detail row | `RowClick`, `HierarchyVisibilityToggled: Alicia expanded=True`, no selection change |
   | D. Expand button, a closed row (off) | expanded | exactly one toggle, no `RowClick` |
   | E. `ExpandSingleRow` on, row body on a second row | not run | the first row closes and the clicked one opens |
   | F. Row body on a row whose button is disabled | not run | it expands (records the caveat for the description) |

   A and C changing from "no detail row" to "detail shown" is the
   result that proves the pattern works. B and D settle choice 3.
3. **Add the example.** Create
   `src/MudBlazor.Docs/Pages/Components/DataGrid/Examples/DataGridRowClickExpandExample.razor`,
   modeled on `DataGridDetailRowExample.razor`:

   ```razor
   @using System.Net.Http.Json
   @using MudBlazor.Examples.Data.Models
   @namespace MudBlazor.Docs.Examples
   @inject HttpClient httpClient

   <MudDataGrid @ref="_dataGrid" T="Element" Items="@_elements" Hover="true"
                RowStyle="cursor: pointer;" RowClick="OnRowClickAsync">
       <Columns>
           <HierarchyColumn T="Element" />
           <PropertyColumn Property="x => x.Sign" />
           <PropertyColumn Property="x => x.Name" />
           <PropertyColumn Property="x => x.Molar" Title="Molar mass" />
       </Columns>
       <ChildRowContent>
           <MudText>@context.Item.Name is element number @context.Item.Number.</MudText>
       </ChildRowContent>
   </MudDataGrid>

   @code {
       private MudDataGrid<Element> _dataGrid = null!;
       private IEnumerable<Element> _elements = [];

       protected override async Task OnInitializedAsync()
       {
           _elements = await httpClient.GetFromJsonAsync<List<Element>>("webapi/periodictable") ?? [];
       }

       private Task OnRowClickAsync(DataGridRowClickEventArgs<Element> args)
           => _dataGrid.ToggleHierarchyVisibilityAsync(args.Item);
   }
   ```

   If step 2 shows a double toggle, the `HierarchyColumn` gets a
   `CellTemplate` with the wrapper (choice 3).
4. **Add the docs section.** In `DataGridPage.razor`, insert a
   `DocsPageSection` between "Row Detail View" and "Row Detail
   Renderer". Its `SectionHeader Title="Expand Row on Click"` has a
   description making the three points in Proposed Solution, with
   `CodeInline` for `RowClick`, `ToggleHierarchyVisibilityAsync`,
   `SelectOnRowClick` and `ButtonDisabledFunc`. Below it goes
   `<SectionContent DarkenBackground="true" Code="@nameof(DataGridRowClickExpandExample)" Block="true" FullWidth="true">`
   wrapping `<DataGridRowClickExpandExample />`. I'll leave out
   `ShowCode="false"`, because the handler is what's being taught.
   The code panel stays collapsed by default, as AGENTS.md asks for
   examples longer than 15 lines.
5. **Tests.** A fail-first test doesn't apply, since no library
   behavior changes. The proof is step 2's before/after table, re-run
   against the real docs page in step 6.
   - **Render test.** `ExampleDocsTests.generated.cs` yields one render
     test per example (for example, `DataGridDetailRowExample` at
     line 259), so `-p:GenerateDocsTests=true` should add one for
     `DataGridRowClickExpandExample` that fails if it throws. I won't
     edit generated files.
   - **Optional test.** Only if reviewers ask, I'd add one bUnit test
     to `DataGridTests.cs` with a one-sentence `<summary>` citing
     #11850: a row click wired this way expands, a second click
     collapses, and a button click toggles once. I'd say plainly that
     it passes on current `dev`.
6. **Verify.**
   - `dotnet build src/MudBlazor.Docs/MudBlazor.Docs.csproj -p:SkipBunCompile=true`:
     build succeeded, 0 warnings.
   - `dotnet test --project src/MudBlazor.UnitTests.Docs/MudBlazor.UnitTests.Docs.csproj -c Release -p:GenerateDocsTests=true --hangdump --hangdump-timeout 60s`:
     the summary shows a `DataGridRowClickExpandExample` case passing,
     and no failures.
   - Run `dotnet run --project src/MudBlazor.Docs.Server/MudBlazor.Docs.Server.csproj`
     and open the DataGrid page. In the new section, a click on a
     row's Name cell shows its detail text and a second click hides it.
     A click on the chevron toggles once. Capture before (no section
     on `dev`) and after screenshots or a gif for the PR.
   - At the end, from `src`, run
     `dotnet format whitespace --folder --include <changed files>`
     (paths relative to `src`). Then, from the repo root, run
     `dotnet format src --verify-no-changes`, the CI format check in my
     ship manifest.
7. **PR.** Open it as a draft first. Title:
   `MudDataGrid: Add docs example for expanding a row on click (#11850)`.
   The description says `Closes #11850`, as CONTRIBUTING.md asks for
   issues that aren't bugs (the issue is already closed, but the
   keyword links the PR). It also links danielchalmers' comment,
   credits versile2's snippet, and lists choices 1–4. It includes the step 2
   and step 6 evidence and an AI-assistance disclosure in my own
   words (PR template). It goes through ship-gate and pr-precheck
   before `gh pr create`.
8. **Clean up.** Delete the scratch repro once its evidence is saved.

*Deviations:* the plan changed before any code. I had asked about an
opt-in `RowClickExpand` parameter. The maintainer pointed to the
existing API and a docs example, so I dropped the parameter. I'll
record later changes here and in `plan.md`.

*Deviations during the build (2026-11-06; details in Implementation
Notes):*

- With `ExpandSingleRow` on, a second click does not collapse the open
  row, from a row click or the expand button. That's existing behavior
  since #11181, so the docs text says so instead of claiming a second
  click always collapses.
- The example uses `ShowCode="false"`, because `ShowCode` defaults to
  `true`.
- It follows the existing examples' `new List<Element>()` pattern and
  adds a `MudDataGridPager`.
- Choice 3 is settled: the expand button toggled once in every run, so
  there's no `stopPropagation` wrapper.

**Toolkit**

- Tool: Claude Code in my MudBlazor clone, with `CLAUDE.local.md` and
  `AGENTS.md` loaded. It traced the row-click and hierarchy code and
  the docs page, then drafted this section, `plan.md` (a copy of this
  section) and `plan-comment.md`. Then plan-check (my rubric,
  procedure and evidence guide) graded `plan.md` and `plan-comment.md`
  live against #11850.
- What it produced: a docs-only plan with the code paths traced, a
  before/after table built on my A–D scenarios, and four open choices,
  each with a default. It also found the `ButtonDisabledFunc` trap.
  Plan-check's first run (2026-11-06) returned REJECT. Diagnosis,
  Scope, Executability, Test plan and Uncertainty handling passed, but
  Thread and repo alignment failed: my PR step only "linked" #11850,
  while CONTRIBUTING.md says to "Include ... `Closes #<issue nr>` for
  other issues". After that fix and one more (below), the second run
  returned ACCEPT, with all six required checks passing and no
  voice-guide rule broken.
- Difficulties: I first asked Claude to plan `RowClickExpand`. On
  re-reading the live thread, it found the maintainer's reply and the
  closure and stopped to ask. Plan-check also expects my repro to be
  a posted comment, and I've only posted my claim, so the plan and
  the draft comment have to quote the A–D evidence themselves. And
  "fail-first tests" doesn't fit a docs change, so the plan proves
  the change by rerunning my scenarios instead.
- What changed: the plan became a docs example. I stopped treating
  another maintainer reply as a gate, because a MEMBER suggested this
  PR. The repro table moved into the plan itself so the package can
  be graded alone. I added `Closes #11850` to the PR step, and fixed
  the CI format command, which my plan had told me to run from `src`
  even though its path is `src`. My memory file had made the same
  "linking is enough" mistake, so I corrected it there too. Gaps I'd
  fix in plan-check: `procedure.md` doesn't say what to do when the
  repro was never posted to the thread, and it never tells the grader
  to apply `scope.md`'s rules (maintainer direction, someone else's
  plan) or the voice guide.

---

## Testing Strategy

This change is docs only, so no library behavior changes and no test
can fail first. What has to be proven is that the pattern the example
teaches really does what the docs text says, and that the docs still
build and render. I proved that in three layers. The full record,
with every event line, is in `test_evidence.md` in my clone.

1. **Rerun my reproduction against the pattern (Viewer, before and
   after).** I used my scratch component from the reproduction, with
   a switch that wires `RowClick` to
   `ToggleHierarchyVisibilityAsync(args.Item)`.
   - **Before:** with the switch off on the feature branch (A0), a
     row-body click on Sam still only raised `RowClick` and
     `SelectedItemChanged: Sam`, with no detail row. That's the same
     as scenario A on 2026-11-05.
   - **After:**
     - With the switch on, the same click raised
       `HierarchyVisibilityToggled: Sam expanded=True` and showed
       Sam's detail (A). A second click collapsed and deselected it
       (A2).
     - With `SelectOnRowClick` off, the row expanded and collapsed
       with no selection events (C, C2).
     - The expand button toggled exactly once and never raised
       `RowClick` (B, B2, D).
     - With `ExpandSingleRow` on, a second click on the open row
       didn't collapse it, from the row (E4) or the built-in button
       with no handler (E6). That's existing behavior since #11181,
       so I corrected the docs text instead of claiming a second
       click always collapses.
     - A row whose button is disabled still expanded on a row click
       (F), which backs up the `ButtonDisabledFunc` caveat.
2. **The real docs page (Docs.Server, my own run).** I saved three
   screenshots in `C:\Srithika\Projects\Codepath\pr-evidence\11850\`:
   - `before-no-section.png`: unchanged `upstream/dev`, where "Row
     Detail Renderer" follows "Row Detail View" directly
   - `after-section.png`: the new "Expand Row on Click" section with
     its grid collapsed
   - `after-row-expanded.png`: Hydrogen's detail ("Hydrogen is element
     number 1.") shown
   
   A screenshot can't show which part of the row was clicked, so the
   Viewer table is what proves row-click behavior. I didn't capture a
   video or a "before" row click.
3. **The repo's own checks.**
   - Docs build (`dotnet build src/MudBlazor.Docs/MudBlazor.Docs.csproj -p:SkipBunCompile=true`):
     PASS, 0 warnings, both before and after the wording fix.
   - Docs tests (manifest row 2, `-c Release -p:GenerateDocsTests=true`):
     total 1427, succeeded 1427, failed 0, skipped 0. That includes the
     generated `DataGridRowClickExpandExample` render test. The run was
     built before the description-only wording fix.
   - `dotnet format whitespace` doesn't read `.razor` files ("0 of 0
     files"), so I checked BOM, LF and trailing whitespace by hand.
   - Still to run on the committed branch, through the ship-gate:
     manifest row 1 (the full `MudBlazor.UnitTests` suite in Release)
     and row 3 (`dotnet format src --verify-no-changes`). The ship-gate
     re-runs row 2 as well.

Limits:

- The generated test only proves the example renders, not what a
  click does.
- The click behavior was automated in the Viewer, not on the docs
  page.
- Keyboard use, virtualized rows, `CellClick` cells, touch input and
  other browsers aren't tested.

**Toolkit**

- Tool: Claude Code on my feature branch. It drove my gitignored
  Viewer repro with a Playwright script (headless Chrome, outside the
  repo), ran the Docs build and the docs-test row from my ship
  manifest, and wrote `test_evidence.md`. It also checked my
  Docs.Server screenshots against what they claim to show. I took the
  screenshots myself.
- What it produced: before/after event logs for scenarios A0–F, a
  1427/1427 docs-test run, a record of which manifest rows have and
  haven't run, and `test_evidence.md`, which lists only the three
  screenshots that exist.
- Difficulties:
  - My plan predicted that a second click always collapses, and
    `ExpandSingleRow` proved that wrong.
  - `dotnet format` reported success after checking zero files.
  - A screenshot can't prove a row click, so the docs-page evidence
    leans on the Viewer logs.
  - Reading the screenshots caught a number I had made up (118
    elements; the pager says 88).
  - The screenshots show my personal browser tabs.
- What changed: I corrected the docs wording and the row count,
  checked the `.razor` formatting by hand, and wrote down that two
  manifest rows haven't run yet instead of implying all checks pass.
  Before upload, I'll crop the screenshots to the page. Next time I'd
  record a short clip of the click, which proves more than a still
  image.
---

## Implementation Notes

**2026-11-06**

I branched `feature/datagrid-row-click-expand-example` from
`upstream/dev` at `87eec3b`, one commit (a bUnit bump) past the
`97f33ac` I planned against. `git fetch upstream` also brought in a
tag literally named `upstream/dev`, which made the name ambiguous, so
I used `refs/remotes/upstream/dev`. Nothing upstream already showed
the pattern: no docs example calls `ToggleHierarchyVisibilityAsync`,
and no PR mentions #11850.

Before writing any docs, I added switches to my gitignored Viewer
repro for a `RowClick` → `ToggleHierarchyVisibilityAsync` handler,
`ExpandSingleRow`, and a disabled expand button on Ira's row. I
rebuilt the Viewer (Build succeeded, 0 warnings) and drove it with
Playwright in headless Chrome, one automated click per step. These
are the actual results:

| Step | Events raised | Detail rows after |
|---|---|---|
| A0. Row body Sam, no handler | `RowClick`, `SelectedItemChanged: Sam` | none (same as my original repro) |
| A. Row body Sam, handler | `RowClick`, `HierarchyVisibilityToggled: Sam expanded=True`, `SelectedItemChanged: Sam` | Sam |
| A2. Row body Sam again | `RowClick`, `...Sam expanded=False`, `SelectedItemChanged: null` | none, Sam deselected |
| B / B2. Expand button Ira, twice | one `...Ira expanded=True`, then one `...expanded=False`; no `RowClick` | Ira, then none |
| C / C2. Row body Alicia, `SelectOnRowClick` off, twice | `RowClick` + one toggle each; no selection events | Alicia, then none |
| D. Expand button Alicia (off) | one `...Alicia expanded=True` | Alicia |
| E1/E2. `ExpandSingleRow`, row body Sam then Alicia | E2: `...Sam expanded=False`, `...Alicia expanded=True` | Sam, then only Alicia |
| E3. `ExpandSingleRow`, expand button Ira | `...Alicia expanded=False`, `...Ira expanded=True` | only Ira |
| **E4. `ExpandSingleRow`, row body Ira again** | `RowClick`, `SelectedItemChanged: Ira`, **no toggle** | **Ira stays open** |
| **E6. `ExpandSingleRow`, no handler, expand button on open Ira** | **none** | **Ira stays open** |
| F. Ira's button disabled (`isDisabled` true), row body Ira | `RowClick`, `...Ira expanded=True`, `SelectedItemChanged: Ira` | Ira (the caveat is real) |

The expand button toggled exactly once every time and never raised
`RowClick`, so versile2's `stopPropagation` wrapper isn't needed and
the example uses the plain `HierarchyColumn`. E4 was the surprise: my
plan said "a second click collapses it". I checked whether that was
my setup or the library. E6 shows the same thing with no handler at
all, using only the built-in button. `ToggleHierarchyVisibilityAsync`
in `ExpandSingleRow` mode clears every open row and re-adds the
clicked one. Its own comment says so ("clear all open hierarchies,
which will immediately add the item that was clicked"), and it has
worked that way since `ExpandSingleRow` was added in #11181
(`fb88ced94`). No existing test clicks an already-open row in that
mode. So it's existing behavior, and I changed nothing in the library.
I corrected the docs text instead, so it no longer says a second click
always collapses.

Then I added `DataGridRowClickExpandExample.razor` and an "Expand Row
on Click" section between "Row Detail View" and "Row Detail Renderer"
in `DataGridPage.razor`.

Results:

- `dotnet build src/MudBlazor.Docs/MudBlazor.Docs.csproj -p:SkipBunCompile=true`:
  Build succeeded, 0 warnings. I re-ran it after the `ExpandSingleRow`
  wording fix, with the same result.
- `dotnet test --project src/MudBlazor.UnitTests.Docs/MudBlazor.UnitTests.Docs.csproj -c Release -p:GenerateDocsTests=true --hangdump --hangdump-timeout 60s`:
  total 1427, succeeded 1427, failed 0, skipped 0 (2m 03s). The
  generated file has a `DataGridRowClickExpandExample` case
  (`ExampleDocsTests.generated.cs:270`). This run was built before
  the wording fix, which only changed description text on the page;
  the build above covers that change.
- `dotnet format whitespace --folder --include <both files> --verify-no-changes`
  exited 0 but "Formatted 0 of 0 files", because `dotnet format`
  doesn't read `.razor` files. I checked by hand instead: UTF-8 BOM,
  `git ls-files --eol` shows LF, and no trailing whitespace on my
  lines.

Deviations from `plan.md`, each made while building:

- the `ExpandSingleRow` wording above
- `ShowCode="false"`: I had assumed code panels start collapsed, but
  `SectionContent.ShowCode` defaults to `true`, and AGENTS.md and
  every other DataGrid section collapse long examples
- `_elements = new List<Element>()` with a plain `GetFromJsonAsync`
  assignment, matching the existing examples instead of my planned
  `[]`/`?? []`
- a `MudDataGridPager`, as in `DataGridDetailRowExample`, so the grid
  doesn't render all 88 rows the data source returns (the pager reads
  "1-10 of 88" in my Docs.Server screenshots; I first wrote 118 here
  without checking)

Not done yet:

- `MudBlazor.Docs.Server` before/after screenshots
- keyboard and virtualized-row checks
- running the full unit-test suite and the CI format check from my
  manifest

Nothing is committed.

**Toolkit**

- Tool: Claude Code on my feature branch, driving my gitignored
  Viewer repro with a Playwright script (headless Chrome, outside the
  repo), then building Docs and running the docs tests.
- What it produced: the event-log table above, the
  `ExpandSingleRow` finding traced to `fb88ced94`, the example and
  page section, and a 1427/1427 docs-test run.
- Difficulties: my plan predicted that a second click always
  collapses, and it doesn't in `ExpandSingleRow` mode. A clean
  `dotnet format` exit hid that it had checked zero files. And the
  `upstream/dev` tag collision broke the plain branch command.
- What changed: I corrected the docs wording, checked the formatting
  by hand, used the full remote ref, and recorded four deviations here
  and in `plan.md`. Lesson: every row of a plan's expected-results
  table is a prediction until it's run.
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
