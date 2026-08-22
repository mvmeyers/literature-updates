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
3. **The agent can do the work itself, end to end** — yes: search, parse,
   format, write the file, update state, commit. No step needs a human
   in the loop to complete.
4. **"Done" is objective** — yes for structure and completeness-of-process
   (every required field present, window correct, both keywords searched,
   dedup done). It is *not* fully objective for "found literally every
   paper that exists" — no automated search can guarantee that. The gate
   below verifies the *process* was followed correctly, not that recall
   is 100%. That gap is called out explicitly in the output rather than
   hidden.

## Protocol (run every Monday)

**1. DISCOVER**
- Read [TASK.md](TASK.md) for the current task spec.
- Read [PROGRESS.md](PROGRESS.md) for the last completed run's window-end
  date. If it is more than 7 days before this run's window-start, extend
  the search window back to close the gap (a missed run should not lose
  a week of literature).

**2. PLAN**
- Compute this run's date window in EST (see TASK.md).
- State the two searches to run (`"borderline personality disorder"`,
  `"BPD" "borderline"` — never the bare acronym `BPD` alone, see TASK.md
  for why) and the source (Google Scholar, PubMed as fallback only).

**3. EXECUTE**
- Run both searches against Google Scholar for the computed window.
- If Google Scholar is unreachable or blocks the request after a
  reasonable retry, fall back to PubMed for both searches and note the
  fallback in the output file's header.
- Merge results from both keyword searches; deduplicate by title/DOI.
- For each unique paper, pull title, author(s), journal/source,
  publication date, abstract, and link.
- Write `weekly summaries/MMDD_summary.md` using the template below.
- Update [PROGRESS.md](PROGRESS.md) with a new row for this run.

**4. VERIFY** — every item below must pass before the run is marked
complete. This is the gate; do not mark a run successful by feel.

- [ ] Output file exists at `weekly summaries/MMDD_summary.md` with the
      correct date (the Monday this task ran).
- [ ] File header states the exact date window searched (start and end,
      in EST).
- [ ] File header states which source was used (Google Scholar, or
      PubMed if fallback was triggered) and confirms both keyword
      searches were run.
- [ ] Every paper entry has all six fields: title, author(s),
      journal/source, publication date, abstract (or explicit "Abstract
      not available" + link), and link.
- [ ] Every paper entry's publication date falls inside the window.
      Anything outside the window is excluded, not included.
- [ ] No duplicate entries (same title or DOI appearing more than once).
- [ ] If zero papers were found, the file says so explicitly rather than
      being empty or missing.
- [ ] [PROGRESS.md](PROGRESS.md) has a new row for this run's date.

**5. ITERATE / DECIDE**
- If every VERIFY item passes: mark the run **OK** in PROGRESS.md.
- If a specific item fails (e.g. an abstract is missing for one paper),
  fix that specific issue directly (re-fetch, re-search) and re-run
  VERIFY. Cap this at 3 fix attempts per run.
- If Google Scholar *and* the PubMed fallback both fail to return usable
  results: still write the summary file, clearly marked
  `SEARCH INCOMPLETE` at the top with what was attempted and why it
  failed. Mark the run **NEEDS REVIEW** in PROGRESS.md. Do not silently
  report success.
- If the result count is unusually high (>40 papers in one week): still
  deliver the file, but add a one-line note in PROGRESS.md flagging the
  volume for a quick human sanity check — it may mean the keyword scope
  is too broad.
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
- **Anomalous volume** (>40 papers): note only, not a hard failure.

## Output template

```markdown
# BPD Literature Summary — [Month DD, YYYY]

**Window searched:** [Prior Monday] 7:01 AM EST – [This Monday] 6:59 AM EST
**Source:** Google Scholar (keywords: "borderline personality disorder", "BPD" "borderline")
[If fallback used: **Note:** Google Scholar was unreachable; PubMed used as fallback.]

## Papers found: [N]

### 1. [Title]
**Author(s):** ...
**Source:** ...
**Published:** ...
**Link:** ...

**Abstract:**
...

### 2. [Title]
...
```

If zero papers were found, replace the numbered list with a single line:
`No new literature matching these keywords was found in this window.`

## State

Run history and the last-completed window boundary live in
[PROGRESS.md](PROGRESS.md) — read it before computing this run's window,
and update it after every run, success or failure.

## Build order note

Per standard loop-building practice: this task was proven with one manual
run before being wrapped in a schedule. If the search method (Scholar
selectors, fallback behavior, etc.) ever needs to change, re-validate
with a manual run before trusting the scheduled version again.
