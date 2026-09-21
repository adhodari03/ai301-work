# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/55

**Verdict output**

Accepted, in fit order

#55 — Skill extractor fails to detect JavaScript and TypeScript (accept, 1/2 preferred)
Best fit: Python, in the ingestion pipeline feeding the AI scoring path, and the body names the file, the three functions, and five already-failing xfail tests — the test suite is the spec, so a first-time contributor knows exactly when they're done. Missing only the newcomer label.

[
{
"item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/55",
"checks": [
{"name": "Maintainer alive", "grade": "pass", "evidence": "Last 5 default-branch commits all human-authored by Aburke225 (COLLABORATOR), newest 2026-09-16, 5 days before today"},
{"name": "Not archived", "grade": "pass", "evidence": "Repo API field archived = False"},
{"name": "Recent activity on default branch or a release", "grade": "pass", "evidence": "pushed_at = 2026-09-16T21:48:27Z, 5 days ago (no releases, but push clause satisfies the OR)"},
{"name": "Bounded scope", "grade": "pass", "evidence": "One file named: '_detect_languages (ingestion/parsers/skill_extractor.py)' plus _detect_tools/_detect_databases, with five named failing tests as the spec; not an umbrella issue, no support question"},
{"name": "No unresolved design debate", "grade": "pass", "evidence": "comments count = 0; timeline holds only three 'labeled' events"},
{"name": "Not assigned", "grade": "pass", "evidence": "assignees: []"},
{"name": "No active linked PR", "grade": "pass", "evidence": "No cross-referenced events in the issue timeline; repo's only open PR (#74) targets issue #60"},
{"name": "No unanswered claim in thread", "grade": "pass", "evidence": "Zero comments on the issue, so no claim comment exists"},
{"name": "Contribution policy allows AI-assisted work", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and .github/PULL_REQUEST_TEMPLATE.md contain no AI-contribution clause; no AI_POLICY.md in the tree — silence passes"},
{"name": "Newcomer label present", "grade": "fail", "evidence": "labels: ['bug', 'ingestion', 'tier-1'] — no 'good first issue' or 'help wanted'"},
{"name": "Low context needed", "grade": "pass", "evidence": "Body names the file, the three functions, and the exact repro command 'pytest tests/unit/test_skill_extractor.py -q'"}
],
"verdict": "accept"
}
]


---

## Eval iterations

**Run history**

1. First full run: `agreement: 15/20 scored items (bar: 18/20: below the bar)`
2. `--only issue-01`: `agreement: 0/1 scored items` (rejected; gold said accept)
3. `--only issue-20`: `agreement: 0/1 scored items` (accepted; gold said reject)
4. After merging "Recent maintainer commits" and "Maintainer responds" into one combined "Maintainer alive" check: `--only issue-01` matched gold.
5. After also broadening "Bounded scope" to not fail issues on self-declared uncertainty (e.g. "TBD" details with no maintainer confirmation): `--only issue-09,issue-14,issue-16,issue-20` — all four matched gold.
6. Final full run: `agreement: 18/20 scored items (bar: 18/20: PASS)`, `run written to eval-run.txt`.

**Issue analysis**

issue-01 (conda/conda#16475). Gold label: accept. My rubric's first verdict was reject, on the check "Maintainer responds." The evidence showed a maintainer first-response sample where 3 of 5 sampled issues had no maintainer reply at all, and the one reply that existed took 32.9 days — despite the repo showing 5 human-authored commits the day before capture and a release 5 days prior. My rubric had treated commit activity and response latency as two separate required checks that both had to pass, so a large, high-traffic repo with limited issue-triage bandwidth failed a family it should have passed. I fixed this by merging both signals into one "Maintainer alive" check joined by OR, so either signal can satisfy the family, in line with how the evidence guide frames multiple signals per family rather than independent gates.

**Check rationale**

| Maintainer alive | Repo facts: "last 5 default-branch commits" and "maintainer first-response sample" | At least one of the last 5 default-branch commits is human-authored (not just bot-merged) within 90 days of the capture date, OR the response sample shows at least one first response from an Owner/Member/Collaborator within 60 days | required |

Reasoning: a single response-latency check punished large, active repos where high issue volume outpaces individual triage capacity. Commit activity is an independent, valid signal of maintainer life, so the check now passes on either signal instead of requiring both.

**Trade-offs**

This change is more permissive: a repo with very little commit activity, but a sole maintainer who responds quickly to the few issues it gets, will still pass. I accept this as a narrow edge case likely caught by other required checks (recent push/release activity, not archived). I re-ran `--only issue-01,issue-09,issue-14,issue-16` after the change and all four flipped from reject to accept, matching gold, with no new failures in that run. Separately, I saw grading variance unrelated to this check: issue-01 flipped from accept back to reject on the final full run purely on "Bounded scope" wording interpretation, with no change to that check between runs — a reminder that verdicts aren't fully deterministic even with stable rubric text.

---

## Selection rationale

I chose issue #55 (skill extractor fails to detect JavaScript and TypeScript) over #73 and #67, which my skill also accepted.

1. **Fit and time available:** the issue is scoped in Python, in a pipeline I'm comfortable working in, and comes with five already-failing tests that define "done" — a concrete, time-bounded first task rather than an open-ended one.
2. **What the verdict caught vs. what I weighed myself:** the skill correctly identified strong bounded scope (one file, three named functions, an exact repro command) and an active, responsive maintainer. What it couldn't weigh was that #73 was the objectively safer pick — smaller, labeled "good first issue," lower risk. I chose #55 anyway because I wanted a task with more real code to work through going into Unit 2's reproduce step, trading some safety for a better learning task.
3. **Anticipated difficulty claiming it:** low. The issue has zero comments and no assignee, so there's no competition to navigate. The real work will be understanding the three functions well enough to fix the detection logic, not any claiming friction
