# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer alive | Repo facts: "last 5 default-branch commits" and "maintainer first-response sample" | At least one of the last 5 default-branch commits is human-authored (not just bot-merged) within 90 days of the capture date, OR the response sample shows at least one first response from an Owner/Member/Collaborator within 60 days | required |
| Not archived | Repo line: "archived:" | Field reads false/absent | required |
| Recent activity on default branch or a release | Repo facts: "latest release" and "last push to any branch" | Latest release or last push is within 45 days of the capture date | required |
| Bounded scope | Issue body and Comments section | Pass unless the issue is explicitly framed as an umbrella/tracking issue meant to be split into separate work items, is a pure usage/support question, a maintainer comment shows the design is unsettled, a maintainer states the fix requires core-internals changes, OR the issue's own description leaves key implementation details undetermined (e.g. "TBD", "possibly X if needed", asset/design not yet decided) with no maintainer confirmation that the request is accepted and scoped. Length, level of detail, or number of files touched does not by itself fail this check. | required |
| No unresolved design debate | Comments section | Thread shows no open disagreement about approach that a maintainer has left unsettled | required |
| Not assigned | Repo facts: "this issue: assignees:" | Field is empty | required |
| No active linked PR | Repo facts: "linked PRs:" with state, plus PRs mentioned in Comments | No PR in either source is in an open state | required |
| No unanswered claim in thread | Comments section | No comment claims the issue ("I'll take this", "working on this") without later abandonment evidence (e.g., a closed unmerged PR from that person) | required |
| Contribution policy allows AI-assisted work | Repo facts: "contribution policy" line | Line is silent, or states conditions (disclosure/testing/review) rather than an outright ban on AI-generated contributions | required |
| Newcomer label present | Issue labels | Issue carries "good first issue" or "help wanted" | preferred |
| Low context needed | Issue body | Understanding the ask requires reading only the issue itself, not a separate subsystem | preferred |

## Verdict rule

Accept only if every `required` check passes. `unclear` on a `required` check counts as fail. `preferred` checks never affect accept/reject — they only rank accepted issues, more passes ranking higher; `unclear` on a `preferred` check counts as a non-pass for ranking but does not touch acceptance.

