# open-source-apps-counted

57 open-source web apps, counted from their repositories: how many screens each has, how many API
operations its committed OpenAPI spec describes, and how many end-to-end spec files its maintainers keep.

**14 of the 57 have no end-to-end spec file, and 32 of
the 40 whose screens could be counted have fewer spec files than screens** (the median is
0.25 spec files per screen). Spec files are not tests, and screens are not
features: see [the method](https://featkpr.com/library/counted#method).

The page with the figure, the full table and the method: <https://featkpr.com/library/counted>

## Files

| file | what |
|---|---|
| [`open-source-apps-counted-2026-09-28.csv`](open-source-apps-counted-2026-09-28.csv) | one row per app; the first three lines start with `#` (licence, citation, sources): read with `comment="#"` |
| [`open-source-apps-counted-2026-09-28.json`](open-source-apps-counted-2026-09-28.json) | the same rows, a dictionary of every column, the summary figures and the provenance |

## Columns

| column | meaning |
|---|---|
| `app` | the app |
| `what` | what it is |
| `stack` | its stack: server, then front end |
| `licence` | the licence its LICENSE file names; "+ ee" when a directory is under its own (enterprise) licence |
| `repository` | the repository counted |
| `commit` | the commit counted (full SHA), or the tag; empty where report T2 recorded no commit |
| `commit_date` | the date of that commit or tag |
| `counted_on` | the day it was counted |
| `counted_by` | "report T2, by hand" (17 Sep 2026) or "tools/library_count.py" (28 Sep 2026) |
| `screens` | pages a person can land on: page files or route declarations, never components; empty when they cannot be counted from the files |
| `api_operations` | (path, method) pairs in the OpenAPI or Swagger spec committed to the repository; empty when no spec is committed |
| `e2e_spec_files` | files of the end-to-end suite the project runs against the running app (browser or HTTP); files, not tests |
| `e2e_spec_files_per_screen` | e2e_spec_files divided by screens, to 3 decimals; empty without a screen count |
| `screens_rule` | the rule that produced screens (for the script: the path pattern, the text pattern and the exclusion), or why there is no count |
| `api_rule` | the spec file(s) read and the operations in each, or why there is no count |
| `e2e_rule` | the rule that produced e2e_spec_files |
| `recount_on` | for report T2's apps the script recounted: the day |
| `recount_commit` | the commit recounted (full SHA) |
| `recount_screens` | screens on the recount |
| `recount_api_operations` | API operations on the recount |
| `recount_e2e_spec_files` | end-to-end spec files on the recount |

## How it was counted

- **featkpr research report T2: 14 apps counted by hand**, on 17 Sep 2026: BookStack at its v26.05.5 tag, the others at their default branch
  that day (no commit recorded). Each row carries the rule T2 used.
- **tools/library_count.py: T2's protocol made mechanical; 43 apps counted and 4 of T2's recounted**, on 28 Sep 2026, each repository shallow-cloned at its default branch; the full
  commit and the exact rule (path pattern, text pattern, exclusion) are in each row.
- A **screen** is a page a person can land on: a page file or a route declaration, never a component. An
  **API operation** is a (path, method) pair in the OpenAPI or Swagger spec committed to the repository. An
  **end-to-end spec file** is a file of the suite the project runs against the running app from outside (a
  browser or HTTP). Counts are of files, never of test cases.
- Where both counts exist, the rows keep T2's figures and add the recount in the `recount_*` columns.

What it does not show: a sample of all open-source apps (these were chosen as candidates to map, plus
well-known self-hosted apps), or test quality (unit and integration tests are not counted). The full list
of limits is on [the page](https://featkpr.com/library/counted#limits).

## Count it again

The counting script will be published in this repository. Until then, every rule is written out in
[the method](https://featkpr.com/library/counted#method). To check a row by hand, check out the commit in
that row and apply its rule to `git ls-tree -r --name-only HEAD`.

## A neighbour dataset

E2EGit (Di Meglio, Starace, Pontillo, Opdebeeck, De Roover, Di Martino; MSR 2025, pp. 836-840,
[doi:10.1109/MSR66628.2025.00121](https://doi.org/10.1109/MSR66628.2025.00121); data on
[Zenodo](https://zenodo.org/records/14221860), CC BY 4.0) mines thousands of GitHub repositories for browser
tests and counts the test cases in each file. This dataset is smaller and differs in two ways: it keeps the
apps with no end-to-end suite, and it sets the spec files against each app's screens.

## Licence

- The data (`open-source-apps-counted-2026-09-28.csv`, `open-source-apps-counted-2026-09-28.json`, this README): [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/),
  see [LICENSE](LICENSE). Name featkpr as the source and link to https://featkpr.com/library/counted.

## Cite

> featkpr, 57 open-source web apps counted, 28 Sep 2026, CC BY 4.0, https://featkpr.com/library/counted

```bibtex
@misc{featkpr_counted_20260928,
  author       = {{featkpr}},
  title        = {57 open-source web apps counted: screens, API operations and end-to-end spec files},
  year         = {2026},
  month        = {sep},
  howpublished = {\url{https://featkpr.com/library/counted}},
  note         = {Dataset, CC BY 4.0. Counted 17 Sep 2026 and 28 Sep 2026}
}
```
