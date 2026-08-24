# Progress / Run History

State the loop reads before each run and updates after each run. See
[LOOP_INSTRUCTIONS.md](LOOP_INSTRUCTIONS.md) for the protocol this log
supports and [classification_rubric.md](classification_rubric.md) for how
each week's papers get classified (per-category detail lives in the
weekly summary file itself, not here).

## Current state

- **Last completed window end:** August 24, 2026 3:59 AM EST
- **Consecutive NEEDS REVIEW runs:** 0

## Run log

| Run date | Window covered (EST) | Source used | Papers found | Status | Notes |
|---|---|---|---|---|---|
| 2026-08-24 | Aug 17 4:01 AM – Aug 24 3:59 AM | PubMed (fallback; Google Scholar CAPTCHA-blocked on both queries) | 4 | OK | Superseded an earlier same-day attempt that hit `EGRESS_BLOCKED` on both sources (logged as NEEDS REVIEW) — egress was confirmed restored later the same day, so this run redid the full search for the same window rather than skipping it. Google Scholar itself was then reachable for a plain test query but returned a CAPTCHA "sorry" redirect on both of this task's actual queries (broad OR-query and bare `BPD`), including after one retry; fell back to PubMed per TASK.md. Date-window membership was confirmed via PubMed's own `esearch` `[Date - Publication]` range filter rather than inferred from result sort order, resolving three month-only-dated candidates as confirmed out-of-window (see summary file). One false positive (phyllodes tumor "borderline" margin paper) excluded at classification per rubric §26. No notable-author/affiliation matches this week. |
