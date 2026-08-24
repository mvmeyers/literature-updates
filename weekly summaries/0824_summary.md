# BPD Literature Summary — August 24, 2026

**SEARCH INCOMPLETE**

**Window searched (intended):** August 17, 2026 4:01 AM EST – August 24, 2026 3:59 AM EST
**Source:** None successful — see below.

## What was attempted

1. Google Scholar, broad terminology query (`"borderline personality" OR
   "borderline patients" OR "borderline pathology" OR "borderline
   features" OR "borderline traits" OR "borderline symptoms" OR
   "borderline personality pathology"`), sorted by date, year filter
   2026 — **failed**.
2. Google Scholar, bare acronym query (`BPD`), sorted by date, year
   filter 2026 — **failed**.
3. Retry of a plain Google Scholar fetch (no query params) to rule out a
   transient issue — **failed** (same error).
4. PubMed fallback, broad terminology query, sorted by date — **failed**.
5. PubMed fallback, bare acronym query (`BPD`), sorted by date —
   **failed**.

## Why it failed

Every request to both `scholar.google.com` and `pubmed.ncbi.nlm.nih.gov`
was rejected by this environment's network egress proxy with
`EGRESS_BLOCKED` before reaching either site — i.e. this is an
infrastructure/policy block on the sandbox this run executed in, not a
Google Scholar or PubMed rate-limit, CAPTCHA, or outage. Per the proxy's
own troubleshooting guidance, a destination blocked by egress policy
should be reported rather than retried or routed around, since retrying
or substituting another data-fetch path would not fix the underlying
allowlist gap and could mask the real problem from whoever needs to fix
it.

**Action needed:** an administrator needs to add `scholar.google.com`
and `pubmed.ncbi.nlm.nih.gov` to this environment's egress allowlist (or
otherwise confirm intentional access policy) before this job can run
successfully again.

## Papers

No search could be executed this run, so no papers were retrieved or
classified. This does not mean zero new literature exists for the
window above — it means the window was not searched. Once egress is
restored, a manual or make-up run should cover August 17, 2026 4:01 AM
EST onward (extending back to close the gap, per
[LOOP_INSTRUCTIONS.md](../instructions/LOOP_INSTRUCTIONS.md)'s missed-run
handling) rather than resuming from August 24 as if this week were
covered.
