# Dry Run Decisions — August 22, 2026

## Context

Before the first scheduled Monday run (August 24, 2026), a manual dry
run was performed on 2026-08-22 covering a wider window — August 1,
2026 00:00 EST through August 22, 2026 17:00 EST (fixed UTC-5) — to
validate the search → classification → output pipeline end to end
before trusting it to run unattended on a schedule. This follows
standard loop-building practice (see LOOP_INSTRUCTIONS.md "Build order
note"): prove it manually, harden it, then automate it.

The dry run's actual output lives at
`weekly summaries/DRYRUN_0801-0822_summary.md`, formatted to match a
real weekly summary file. This document holds the process
commentary — scoping decisions and findings — that don't belong in that
output file, which is meant to contain only the task's actual output
(title, abstract, and classification per paper), not meta-commentary
about how it was produced.

**Note:** some of the scoping shortcuts described below (the condensed
entries, the hard exclusion of boundary-uncertain papers) were dry-run-
only choices made for cost reasons during this one test. They do **not**
reflect how production runs work — LOOP_INSTRUCTIONS.md was updated
after this dry run was reviewed to close both gaps. See "Changes made
after reviewing the dry run" in LOOP_INSTRUCTIONS.md for what changed.

---

## Scope of this dry run

**Window searched:** August 1, 2026 00:00 EST → August 22, 2026 17:00 EST
(fixed UTC-5)
**Source:** Google Scholar only (no PubMed fallback needed — Scholar was
reachable throughout)
**Queries run:** (1) broad terminology OR-query — `"borderline
personality" OR "borderline patients" OR "borderline pathology" OR
"borderline features" OR "borderline traits" OR "borderline symptoms" OR
"borderline personality pathology"`; (2) bare acronym `BPD`

---

## Dry-run scoping decisions (as originally made — see note above)

1. **Not every paper got a fully-fetched abstract.** Fetching a
   publisher/source page per paper is the expensive step, and this dry
   run surfaced ~50+ raw candidates (see finding #2 below) — fetching all
   of them would have been disproportionate for a validation exercise. I
   fetched full abstracts for a couple of representative papers to prove
   the mechanism works (one succeeded via PMC open access; one was
   blocked by a Springer login wall; a third attempt hit an SSRN 403).
   For the rest, the entry used Google Scholar's own snippet as the
   basis for classification and marked `Abstract:` as not independently
   fetched. **Superseded:** production runs never skip or shorten
   classification because of a fetch failure — see
   LOOP_INSTRUCTIONS.md.
2. **Not every substantively-relevant paper got a full 12-field
   classification block.** 15 representative papers (spanning every
   category: psychotherapy, pharmacotherapy, other intervention,
   adolescent, psychometrics/assessment, neurobiology, comorbidity,
   qualitative, review) got the full block from LOOP_INSTRUCTIONS.md's
   template. The remaining substantively-relevant papers were listed in
   a condensed one-line form instead, purely to bound the cost of a
   22-day (3x normal) test window. **Superseded:** production runs give
   every kept paper the full block, no condensed form exists in the
   real template.
3. **Window boundary is approximate for edge-of-window papers.** Scholar
   shows relative freshness ("22 days ago"), not exact publication dates,
   sorted by *indexing* date, not necessarily pub date. One paper labeled
   "22 days ago" turned out, on fetching the actual source, to have
   published July 31 — one day *before* this window. Boundary-uncertain
   papers were excluded from the dry run's counted results and flagged
   separately rather than guessing. **Superseded:** production runs
   include boundary-uncertain papers rather than excluding them, with a
   check against the prior week's output to avoid double-reporting — see
   LOOP_INSTRUCTIONS.md's VERIFY gate.

---

## Key findings from this dry run

1. **The bare `BPD` query added zero net-new relevant papers.** Checked
   20 results (2 pages) from the bare-acronym search: every genuine BPD
   paper in that sample also appeared in the broad terminology search;
   every paper that used *only* the bare abbreviation (never spelling out
   a "borderline ___" phrase) was about something else entirely
   (bronchopulmonary dysplasia in 6 of the 20, plus unrelated physics,
   Indonesian village governance, etc.). This matches academic writing
   convention — authors virtually always spell out an abbreviation at
   first use. **Recommendation:** keep the bare query per the rubric (§25
   explicitly calls for it, and it's cheap insurance against the rare
   abbreviation-only paper), but expect it to usually contribute nothing,
   and don't be surprised if it's mostly noise every week.
2. **Raw search volume over 22 days: ~56 candidates from the broad
   query** (about 2.5/day). Scaled to a normal 7-day window, that's
   roughly **10–18 raw candidates/week**, of which maybe half survive
   relevance screening — well under the 40-paper "anomalous volume" flag
   in LOOP_INSTRUCTIONS.md. The earlier concern about that threshold was
   based on not yet knowing real volume; it looks appropriately
   calibrated now, not too low.
3. **False-positive patterns confirmed the rubric's design is
   necessary**, not just theoretical:
   - "Borderline symptoms" sometimes means a sub-clinical/cutoff score
     range on an *unrelated* scale (e.g. a COVID-anxiety study reporting
     "8.4% of participants had borderline symptoms" for depression —
     nothing to do with BPD). Pure keyword matching would have wrongly
     included this.
   - Several papers mention BPD once, incidentally, while studying
     something else entirely (a financial-scamming-in-geriatric-patients
     case series, an atypical-depression review, a
     gender-bias-in-clinical-practice review, a neuromodulation field
     piece). Rubric §26's "is this a substantive focus or a passing
     mention?" correctly screens these out.
   - A couple of results were non-academic websites (a counseling blog,
     a yoga-therapy site), not peer-reviewed/preprint/dissertation
     literature — out of scope per TASK.md, and worth an explicit VERIFY
     check (now added).
4. **Abstract fetching works but isn't universal.** Open-access
   (PMC-hosted) sources fetched cleanly with full abstract text.
   Paywalled/gated sources (SSRN returned 403; a Springer article
   redirected to a login page) correctly fall back to "Abstract not
   available" per TASK.md — this path is real and will trigger
   regularly, not just in theory.

---

## Changes made after this dry run was reviewed

See LOOP_INSTRUCTIONS.md's "Changes made after reviewing the dry run
(2026-08-22)" section for the full list. In short: abstract availability
no longer gates classification completeness or inclusion; boundary-
uncertain papers are included (with a cross-week dedup check) rather
than excluded; the output template was reformatted to use bullets/blank
lines so it doesn't render as bunched, hard-to-read text; and
classification_rubric.md gained a Mentalization & Reflective Functioning
category, a highlighted Bipolar spectrum comorbidity flag, and
person-centered/data-driven modeling keywords under Psychometrics.
