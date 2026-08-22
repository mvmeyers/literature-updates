# Task: Weekly BPD Literature Search

## Goal

Every Monday, find every new piece of academic literature on borderline
personality disorder published in the prior 7 days, and produce one
summary file listing the title and abstract of each paper found.

## Trigger

Runs weekly, every Monday at 7:00 AM EST (fixed UTC-5, i.e. 12:00 UTC —
see [LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md) for why this is pinned to
EST rather than floating with EDT).

## Search parameters

- **Primary source:** Google Scholar (`scholar.google.com`).
- **Fallback source:** PubMed (`pubmed.ncbi.nlm.nih.gov`) — use only if
  Google Scholar cannot be reached or blocks the request (CAPTCHA, rate
  limit, etc.), and say so explicitly in the summary file when it happens.
- **Keywords:** run both of the following as separate Google Scholar
  searches, then merge and deduplicate the results:
  - `"borderline personality disorder"` (exact phrase)
  - `"BPD" "borderline"` (both terms required — **do not** search the
    bare acronym `BPD` on its own; validated during setup, it returns
    ~40-60% noise: bronchopulmonary dysplasia, biparietal diameter,
    bond-based peridynamics, and unrelated Indonesian governance
    literature all use the same three letters. Requiring "borderline"
    alongside it eliminates that noise while still catching papers that
    only use the abbreviation.)
- **Date window:** the 7 days ending at this run's scheduled time.
  Specifically: **previous Monday 7:01 AM EST through this Monday 6:59 AM
  EST.**
  Example: for the run on Monday, August 24, 2026, the window is
  Monday, August 17, 2026 7:01 AM EST → Monday, August 24, 2026 6:59 AM
  EST.
  Do not use "last 7 days" relative to when the agent happens to actually
  execute — always compute the window from the scheduled Monday date, and
  check [PROGRESS.md](PROGRESS.md) first in case a prior run was missed
  and the window needs to extend further back to avoid a gap.
- **Scope:** peer-reviewed journal articles, preprints, and conference
  papers indexed by the source. Exclude patents and Scholar's "Cited by"
  listings (those are citation counts, not the papers themselves).

## Output

For each unique paper found in the window, record:

- Title
- Author(s)
- Journal / source
- Publication date
- Abstract (full text as available; if none is available, write
  "Abstract not available" and include a link instead)
- Link (DOI or URL)

Write the results to `weekly summaries/MMDD_summary.md`, where `MMDD` is
the date of the Monday the task is run (e.g. `0824_summary.md` for
Monday, August 24). Use the template in
[LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md).

If zero new papers are found in the window, still create the file and
say so explicitly — never skip creating the file, and never leave it
empty.

## Reference

See [LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md) for the full loop
protocol (verify gate, stop conditions, escalation rules) and
[PROGRESS.md](PROGRESS.md) for run history and state.
