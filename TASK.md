# Task: Weekly BPD Literature Search

## Goal

Every Monday, find every new piece of academic literature on borderline
personality disorder published in the prior 7 days, classify each paper
per [classification_rubric.md](classification_rubric.md), and produce one
summary file with the title, abstract, and classification for each paper
found.

## Trigger

Runs weekly, every Monday at 7:00 AM EST (fixed UTC-5, i.e. 12:00 UTC —
see [LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md) for why this is pinned to
EST rather than floating with EDT).

## Search parameters

- **Primary source:** Google Scholar (`scholar.google.com`).
- **Fallback source:** PubMed (`pubmed.ncbi.nlm.nih.gov`) — use only if
  Google Scholar cannot be reached or blocks the request (CAPTCHA, rate
  limit, etc.), and say so explicitly in the summary file when it happens.
- **Queries:** per [classification_rubric.md](classification_rubric.md)
  §25 ("Search Strategy Guidance") and §1 ("BPD terminology to
  recognize"), run these two searches, then merge and deduplicate the
  combined results by title/DOI:

  1. **Broad terminology query** (catches most substantive BPD papers
     regardless of phrasing):
     `"borderline personality" OR "borderline patients" OR "borderline
     pathology" OR "borderline features" OR "borderline traits" OR
     "borderline symptoms" OR "borderline personality pathology"`

  2. **Bare acronym query:** `BPD` — deliberately broad and, on its own,
     noisy. Validated during setup: searched alone, roughly 40–60% of
     results are unrelated (bronchopulmonary dysplasia, biparietal
     diameter, bond-based peridynamics, unrelated Indonesian governance
     literature all use the same three letters). **Do not narrow this
     query** — the rubric's design is to search broad and let
     classification (rubric §26, "could the keyword be referring to
     something else?") filter false positives, rather than filtering at
     the query level. Every result from this query must go through full
     classification before being included in the output; results that
     turn out not to be about borderline personality disorder are
     excluded at that stage, not the search stage.

  This is a deliberate scope decision, not full coverage of every
  combination the rubric's §25 lists (BPD + psychometrics terms, BPD +
  psychotherapy terms, BPD + adolescent terms, etc.) as separate
  searches — running dozens of combinatorial queries every week would be
  expensive and largely redundant, since a paper substantively about
  e.g. DBT for BPD will already surface in query 1 above. The rubric's
  own keyword lists (§2, §6, §9, §13–20) are instead applied as
  *classification* criteria against every paper the two searches return,
  which is what actually determines category membership. If this proves
  to miss real papers over time, revisit and add targeted queries.

- **Date window:** the 7 days ending at this run's scheduled time.
  Specifically: **previous Monday 7:01 AM EST through this Monday 6:59 AM
  EST.**
  Example: for the run on Monday, August 24, 2026, the window is
  Monday, August 17, 2026 7:01 AM EST → Monday, August 24, 2026 6:59 AM
  EST.
  Do not use "last 7 days" relative to when the agent happens to actually
  execute — always compute the window from the scheduled Monday date, and
  check [PROGRESS.md](PROGRESS.md) first in case a prior run was missed
  and the window needs to extend further back.
- **Scope:** peer-reviewed journal articles, preprints, dissertations, and
  conference papers indexed by the source. Exclude patents and Scholar's
  "Cited by" listings (those are citation counts, not the papers
  themselves).

## Classification

For every unique paper found in the window, apply the full screening and
classification system in
[classification_rubric.md](classification_rubric.md): substantive
relevance over keyword matching, every category the rubric defines,
confidence levels, adolescent/age-range rules, primary-category
tie-breaking, and false-positive control (rubric §26). Do not skip
classification for any paper that passes the initial search — every
result gets classified, even if the ultimate answer is "No" across every
category (which is how bare `BPD` false positives get excluded). A
missing or blocked abstract is never a reason to skip or shorten a
paper's classification — see LOOP_INSTRUCTIONS.md.

## Output

Write results to `weekly summaries/MMDD_summary.md`, where `MMDD` is the
date of the Monday the task is run (e.g. `0824_summary.md` for Monday,
August 24). Use the template in
[LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md), which combines:

- the aggregate weekly summary block from classification_rubric.md §24
  (total count, per-category counts, most relevant papers highlighted),
  and
- for every unique paper, the structured classification block from
  classification_rubric.md §23, **plus an `Abstract:` field** (full text
  as available; if none is available, write "Abstract not available" and
  rely on the link) — the rubric's own per-paper template doesn't include
  a full abstract field, but the original point of this file is to give
  a scannable title+abstract record for every paper, so that field is
  added on top of the rubric's classification fields, not in place of
  them.

If zero new papers are found in the window, still create the file and
say so explicitly — never skip creating the file, and never leave it
empty.

## Reference

See [LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md) for the full loop
protocol (verify gate, stop conditions, escalation rules),
[classification_rubric.md](classification_rubric.md) for how to screen
and classify each paper, and [PROGRESS.md](PROGRESS.md) for run history
and state.
