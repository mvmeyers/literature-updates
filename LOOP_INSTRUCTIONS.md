# Loop Instructions

How this task is run, verified, and escalated. This exists because a
schedule alone is not a loop — a loop needs a goal, a gate that can fail
the work, and a stop condition. This file is that gate.

## Why this task is suitable for a loop

Per the four-part test (does the task repeat weekly, can something
automatically reject bad output, can the agent do the work end to end,
is "done" objective):

1. **Repeats weekly** — yes, every Monday.
2. **Something can automatically reject bad output** — yes, the VERIFY
   checklist below is a hard, mechanical checklist, not a taste call.
3. **The agent can do the work itself, end to end** — yes: search,
   classify, format, write the file, update state, commit. No step needs
   a human in the loop to complete.
4. **"Done" is objective** — yes for structure and completeness-of-process
   (every required field and classification category present, window
   correct, both searches run, dedup done, every result classified). It
   is *not* fully objective for "found literally every paper that
   exists," and classification confidence itself is a judgment call —
   that's exactly why [classification_rubric.md](classification_rubric.md)
   requires explicit confidence levels (High/Moderate/Low/Possible/No)
   instead of forcing a binary Yes/No, and why the gate checks that every
   category has *a* confidence level, not that the level is "correct."
   Anything genuinely uncertain is preserved and marked Possible rather
   than silently dropped (rubric §29).

## Protocol (run every Monday)

**1. DISCOVER**
- Read [TASK.md](TASK.md) for the current task spec,
  [classification_rubric.md](classification_rubric.md) for the
  classification system, and this file for the protocol.
- Read [PROGRESS.md](PROGRESS.md) for the last completed run's window-end
  date. If it is more than 7 days before this run's window-start, extend
  the search window back to close the gap (a missed run should not lose
  a week of literature).

**2. PLAN**
- Compute this run's date window in EST (see TASK.md).
- State the two searches to run — the broad terminology query and the
  bare `BPD` query (see TASK.md "Search parameters" for the exact query
  text and why the bare acronym is intentionally not narrowed) — and the
  source (Google Scholar, PubMed as fallback only).

**3. EXECUTE**
- Run both searches against Google Scholar for the computed window.
- If Google Scholar is unreachable or blocks the request after a
  reasonable retry, fall back to PubMed for both searches and note the
  fallback in the output file's header.
- Merge results from both searches; deduplicate by title/DOI.
- For **every** unique result — including ones that look like they might
  be a bare-`BPD` false positive — apply the full classification system
  in classification_rubric.md: BPD relevance, all category flags with
  confidence + evidence, primary category, adolescent BPD flag + age
  range, population, developmental focus, study design, and a 1–3
  sentence relevance summary. A result that turns out not to be about
  borderline personality disorder at all (e.g. bronchopulmonary
  dysplasia) is excluded from the output at this stage — do not include
  it just because it matched the search.
- For each paper kept, also pull title, author(s), year, journal/source,
  DOI/link, Google Scholar URL, and abstract (fetch the publisher/source
  page if the abstract isn't in the Scholar snippet).
- Write `weekly summaries/MMDD_summary.md` using the template below.
- Update [PROGRESS.md](PROGRESS.md) with a new row for this run.

**4. VERIFY** — every item below must pass before the run is marked
complete. This is the gate; do not mark a run successful by feel.

- [ ] Output file exists at `weekly summaries/MMDD_summary.md` with the
      correct date (the Monday this task ran).
- [ ] File header states the exact date window searched (start and end,
      in EST).
- [ ] File header states which source was used (Google Scholar, or
      PubMed if fallback was triggered) and confirms both searches were
      run.
- [ ] File opens with the aggregate weekly summary block (rubric §24
      format: total count, per-category counts, most relevant papers
      highlighted).
- [ ] Every paper entry has all of: title, author(s), year,
      journal/source, DOI/link, Google Scholar URL, and abstract (or
      explicit "Abstract not available").
- [ ] Every paper entry has been run through full classification: BPD
      relevance, every category (Psychometrics, Psychotherapy,
      Pharmacotherapy, Other intervention, Assessment/Diagnosis,
      Adolescent BPD, plus any of Epidemiology/Neurobiology/
      Comorbidity/Qualitative/Review that apply) with a confidence level
      and supporting evidence, a primary category, an age range (or
      "not reported"), and a 1–3 sentence relevance summary.
- [ ] No paper in the output is there solely because it matched the bare
      `BPD` search without being confirmed as actually about borderline
      personality disorder (rubric §26 false-positive control was
      applied).
- [ ] Every paper entry's publication date falls inside the window.
      Anything outside the window is excluded, not included. For any
      paper whose Scholar-reported freshness ("N days ago") places it
      within 2 days of either window edge, confirm the actual
      publication date from the source page rather than trusting the
      relative label — validated during the Aug 1–22, 2026 dry run:
      Scholar labeled one paper "22 days ago" when its real publication
      date was one day before the window (Scholar's relative freshness
      tracks indexing date, not publication date, and is not precise
      enough alone near an edge).
- [ ] Every included paper is from a peer-reviewed journal, preprint
      server, dissertation repository, or conference proceedings (per
      TASK.md "Scope") — not a blog, counseling-practice website, or
      other non-academic source that happens to rank in Scholar results.
- [ ] No duplicate entries (same title or DOI appearing more than once).
- [ ] If zero qualifying papers were found, the file says so explicitly
      rather than being empty or missing.
- [ ] [PROGRESS.md](PROGRESS.md) has a new row for this run's date.

**5. ITERATE / DECIDE**
- If every VERIFY item passes: mark the run **OK** in PROGRESS.md.
- If a specific item fails (e.g. an abstract or a classification field is
  missing for one paper), fix that specific issue directly (re-fetch,
  re-classify) and re-run VERIFY. Cap this at 3 fix attempts per run.
- If Google Scholar *and* the PubMed fallback both fail to return usable
  results: still write the summary file, clearly marked
  `SEARCH INCOMPLETE` at the top with what was attempted and why it
  failed. Mark the run **NEEDS REVIEW** in PROGRESS.md. Do not silently
  report success.
- If the result count is unusually high (>40 qualifying papers in one
  week): still deliver the file, but add a one-line note in PROGRESS.md
  flagging the volume for a quick human sanity check.
- Hard stop after the fix-attempt cap regardless of outcome — never loop
  indefinitely trying to force a clean pass. Report what's true, including
  a failure, rather than retrying forever.

## Escalation rules

- **NEEDS REVIEW** (search failed on both sources): flag in PROGRESS.md.
  Since this runs unattended, don't rely on someone noticing — if a push
  notification / messaging capability is configured for this routine, use
  it; otherwise this is surfaced the next time the summaries folder or
  PROGRESS.md is checked.
- **Two consecutive NEEDS REVIEW runs**: this likely means Google
  Scholar's access pattern changed (e.g. it started blocking the agent
  outright) and needs a human to look at the search method, not just a
  retry next week.
- **Anomalous volume** (>40 qualifying papers): note only, not a hard
  failure.

## Output template

```markdown
# BPD Literature Summary — [Month DD, YYYY]

**Window searched:** [Prior Monday] 7:01 AM EST – [This Monday] 6:59 AM EST
**Source:** Google Scholar (queries: broad terminology OR-query, bare "BPD")
[If fallback used: **Note:** Google Scholar was unreachable; PubMed used as fallback.]

## NEW BPD LITERATURE — WEEK OF [DATE]

Total new papers identified: XX

Psychometrics:
- X high-confidence papers
- X possible papers

Psychotherapy:
- X high-confidence papers
- X possible papers

Adolescent BPD:
- X adolescent-focused papers
- X papers including adolescents
- X possible papers

Pharmacotherapy:
- X papers

Other intervention:
- X papers

Other BPD research:
- X papers

### Most relevant new papers

1. [Title] — Category: [Primary category] — Adolescent BPD: Yes/No — [1–2 sentence why it matters]
2. [Title] — Category: [Primary category] — Adolescent BPD: Yes/No — [1–2 sentence why it matters]

---

## Papers

### 1. [Title]

Authors:
Year:
Journal:
DOI:
Google Scholar URL:

Abstract:
[full abstract text, or "Abstract not available"]

BPD relevance: High / Moderate / Low

Primary category: [one category]

Psychometrics: Yes / No / Possible — Confidence: — Evidence:
Psychotherapy: Yes / No / Possible — Confidence: — Evidence:
Pharmacotherapy: Yes / No / Possible — Confidence: — Evidence:
Other intervention: Yes / No / Possible — Confidence: — Evidence:
Assessment/Diagnosis: Yes / No / Possible — Confidence: — Evidence:
Adolescent BPD: Yes — Adolescent focus / Yes — Includes adolescents / Possible / No
Age range: [reported age range, or "not reported"]
Population:
Developmental focus:
Other categories:
Study design:

Why it is relevant: [1–3 sentences]
Classification notes: [any ambiguity]

### 2. [Title]
...
```

If zero qualifying papers were found, replace the "Papers" section with
a single line: `No new literature matching these criteria was found in
this window.` — keep the header block (window/source) regardless.

## State

Run history and the last-completed window boundary live in
[PROGRESS.md](PROGRESS.md) — read it before computing this run's window,
and update it after every run, success or failure.

## Provenance: what's from the rubric vs. what was added

[classification_rubric.md](classification_rubric.md) defines *what makes
a paper relevant and how to categorize it*. It does not define the
operational mechanics of running this as a recurring job — those came
from the original task setup and are recorded here so they don't get
mistaken for rubric requirements or silently dropped in a future edit:

- **Time window:** previous Monday 7:01 AM EST → this Monday 6:59 AM EST,
  fixed UTC-5 year-round (not floating Eastern local time — deliberately
  chosen so the cron schedule never needs DST-related adjustment; see
  TASK.md "Trigger"). The rubric doesn't specify a cadence or window at
  all.
- **Output file naming/location:** `weekly summaries/MMDD_summary.md`,
  `MMDD` = the Monday the task runs (e.g. `0824_summary.md`). The rubric's
  §24 shows a summary *format* but says nothing about file naming or
  where output should live.
- **Source:** Google Scholar as primary, PubMed as fallback if Scholar is
  unreachable. The rubric's §25 talks about search *terms*, not which
  engine/database to query.
- **Zero-result behavior:** always create the file and say explicitly
  that nothing was found, rather than skipping the file or leaving it
  empty. Not addressed by the rubric.
- **Full `Abstract:` field per paper:** the rubric's §23 per-paper
  template doesn't include one (it has "Why it is relevant," a 1–3
  sentence summary, instead). Added because the original ask for this
  task was specifically a title+abstract record for every paper found;
  the rubric's classification fields were layered on top of that, not in
  place of it.

## Build order note

Per standard loop-building practice: the search mechanics (Scholar
access, query design) were validated with manual runs before being
wrapped in a schedule — including the finding that a bare `BPD` search is
noisy, which is why classification (not query narrowing) is the
disambiguation layer. If the search method or the classification rubric
ever change materially, re-validate with a manual run before trusting the
scheduled version again.

### Findings from the Aug 1–22, 2026 dry run

A 22-day dry run (3x normal window) validated the pipeline end to end
and produced `weekly summaries/DRYRUN_0801-0822_summary.md`. Worth
knowing for future runs:

- Real weekly raw-candidate volume from the broad query is roughly
  10–18/week, of which perhaps half survive relevance screening — the
  40-paper anomaly threshold above has headroom and doesn't need
  lowering.
- The bare `BPD` query is expected to contribute close to zero net-new
  papers most weeks (confirmed: 0 of 20 sampled results were both
  BPD-relevant and not already caught by the broad query). Keep running
  it anyway — it's the rubric's intended safety net for the rare
  abbreviation-only paper, and it's cheap.
- Abstract fetching succeeds on open-access sources (PMC-hosted content
  fetched cleanly) and fails on some paywalled/gated ones (SSRN returned
  403; a Springer article redirected to a login page) — the "Abstract
  not available" fallback in TASK.md will trigger regularly in practice,
  not just as a theoretical edge case.
