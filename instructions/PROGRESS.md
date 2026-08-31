# Progress / Run History

State the loop reads before each run and updates after each run. See
[LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md) for the protocol this log
supports and [classification_rubric.md](classification_rubric.md) for how
each week's papers get classified (per-category detail lives in the
weekly summary file itself, not here).

## Current state

- **Last completed window end:** August 31, 2026 3:59 AM EST
- **Consecutive NEEDS REVIEW runs:** 0

## Run log

| Run date | Window covered (EST) | Source used | Papers found | Status | Notes |
|---|---|---|---|---|---|
| 2026-08-31 | Aug 24 4:01 AM – Aug 31 3:59 AM | Google Scholar (both queries reachable, no CAPTCHA this week), cross-checked against PubMed E-utilities for dates/abstracts | 19 | OK | Google Scholar itself was fully reachable this run (unlike last week). However, this environment's network egress policy blocked nearly all individual publisher domains (sciencedirect.com, springer, frontiersin, tandfonline, wiley, medrxiv, osf.io, researchgate, etc. all returned `EGRESS_BLOCKED`/403); only scholar.google.com, pubmed.ncbi.nlm.nih.gov, and eutils.ncbi.nlm.nih.gov were reachable. Used PubMed E-utilities as a supplementary (not primary) tool to confirm exact dates and pull abstracts for the subset of papers indexed there (4 of 19); the rest are classified from title/journal/Scholar snippet with "Abstract not available (access blocked)" per LOOP_INSTRUCTIONS.md policy — none excluded or shortened for this reason. Volume (19) is notably higher than last week (4) but well under the 40-paper anomaly threshold, so no special flag beyond this note. Five papers excluded at classification (§26 false-positive control): one BPD-traits-as-secondary-outcome paper (confirmed via full PubMed abstract), one 2022 paper resurfaced by Scholar's re-indexing (out of window on actual pub year), one no-BPD-in-title/unreachable-abstract paper, one MBT-for-eating-disorders review not substantively about BPD, one general inter-subjectivity paper with no confirmed BPD focus. Bare `BPD` query again contributed zero net-new BPD-relevant papers (bronchopulmonary dysplasia / biparietal diameter / Indonesian village-council acronym false positives dominate, consistent with prior weeks). Three papers included despite date uncertainty within ~1 day of the window's opening edge (publisher pages unreachable, not in PubMed); checked against last week's summary and confirmed not duplicates. No notable-author/affiliation matches this week. |
| 2026-08-24 | Aug 17 4:01 AM – Aug 24 3:59 AM | PubMed (fallback; Google Scholar CAPTCHA-blocked on both queries) | 4 | OK | Superseded an earlier same-day attempt that hit `EGRESS_BLOCKED` on both sources (logged as NEEDS REVIEW) — egress was confirmed restored later the same day, so this run redid the full search for the same window rather than skipping it. Google Scholar itself was then reachable for a plain test query but returned a CAPTCHA "sorry" redirect on both of this task's actual queries (broad OR-query and bare `BPD`), including after one retry with simplified parameters. Per TASK.md, PubMed was used as the fallback for both queries. Date-window membership was confirmed via PubMed's own `esearch` `[Date - Publication]` range filter rather than inferred from result sort order, resolving three month-only-dated candidates as confirmed out-of-window (see summary file). One false positive (phyllodes tumor "borderline" margin paper) excluded at classification per rubric §26. No notable-author/affiliation matches this week. |
