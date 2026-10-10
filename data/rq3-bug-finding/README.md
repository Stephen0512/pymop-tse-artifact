# RQ3: How effective is PyMOP for finding real-world bugs?

[`pr_status.csv`](pr_status.csv) records the cumulative manual inspections, so far, of violations found by PyMOP. Each row is one inspected violation.

## Columns

- `project`: GitHub project, written as `owner-repo`.
- `PR/Issue`: `PR` for a pull request and `Issue` for a GitHub issue. Inspections that were not reported are still labeled `PR`.
- `Source`: which paper the inspection was done for.
  - `FSE-Demo` is the FSE tool demo paper: 271 inspections, 157 true bugs (49 pending, 96 accepted, 12 rejected).
  - `TSE` and `Any` are the TSE manuscript: 817 inspections, 237 true bugs (168 pending, 63 accepted, 6 rejected).
  - `ArXiv` is the arXiv preprint, which describes an earlier stage of PyMOP: 80 inspections, 80 true bugs (29 pending, 36 accepted, 15 rejected).
- `type`: where the violation occurs. `test` is in the project's tests, `project` is in the code under test, and `library` is in a third-party library or the Python runtime.
- `status`: outcome of the inspection.
  - `False Alarm`: the spec is violated, but the violation is not a bug in the code under test.
  - `PR Pending`: a pull request or issue is open and awaiting a developer response.
  - `PR Accepted`: developers accepted or fixed the report.
  - `PR Rejected`: developers rejected the report.
  - `Already fixed before we reported`: the bug was fixed before we opened a report. These rows are counted as accepted.
  - `Repo Archived`: the repository was archived.
  - `Not on GitHub`: the code is no longer on GitHub.
  - `No longer publicly available as of Oct 5, 2026`: the project could no longer be accessed.
- `spec_name`: PyMOP specification that signaled the violation.
- `filename`: path of the file where the violation was reported.
- `line`: line number of the violation in that file.
- `PRs`: URL of the pull request or issue. Empty when no report was opened.

The TSE manuscript extends the FSE tool demo paper. The count reported in the paper combines `FSE-Demo`, `TSE`, and `Any`: 1,088 inspections, 394 true bugs (217 pending, 159 accepted, 18 rejected), and 151 pull requests and issues.
