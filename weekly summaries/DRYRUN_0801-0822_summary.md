# BPD Literature Summary — DRY RUN (Aug 1–22, 2026)

> **This is a validation dry run, not an automated weekly output.** It
> exists to test the search → classification → output pipeline before
> Monday's first scheduled run, at the user's request. It intentionally
> covers a 22-day window instead of a normal 7-day window, and it
> intentionally cuts a few corners noted below — see "Dry-run scoping
> decisions" before treating this as a model for real output quality.

**Window searched:** August 1, 2026 00:00 EST → August 22, 2026 17:00 EST
(fixed UTC-5)
**Source:** Google Scholar only (no PubMed fallback needed — Scholar was
reachable throughout)
**Queries run:** (1) broad terminology OR-query — `"borderline
personality" OR "borderline patients" OR "borderline pathology" OR
"borderline features" OR "borderline traits" OR "borderline symptoms" OR
"borderline personality pathology"`; (2) bare acronym `BPD`

---

## Dry-run scoping decisions (read this first)

1. **Not every paper got a fully-fetched abstract.** Fetching a
   publisher/source page per paper is the expensive step, and this dry
   run surfaced ~50+ raw candidates (see finding #2 below) — fetching all
   of them would have been disproportionate for a validation exercise. I
   fetched full abstracts for a couple of representative papers to prove
   the mechanism works (one succeeded via PMC open access; one was
   blocked by a Springer login wall; a third attempt hit an SSRN 403).
   For the rest, the entry below uses Google Scholar's own snippet as the
   basis for classification and marks `Abstract:` as not independently
   fetched. **A real weekly run has ~5–10x fewer candidates** (see
   finding #2), so fetching a real abstract for every kept paper is
   feasible there in a way it wasn't for this 22-day test.
2. **Not every substantively-relevant paper got a full 12-field
   classification block.** 15 representative papers (spanning every
   category: psychotherapy, pharmacotherapy, other intervention,
   adolescent, psychometrics/assessment, neurobiology, comorbidity,
   qualitative, review) got the full block from LOOP_INSTRUCTIONS.md's
   template. The remaining substantively-relevant papers are listed in a
   condensed one-line form instead. A real weekly run (much smaller
   volume) should give every kept paper the full block, as
   LOOP_INSTRUCTIONS.md specifies.
3. **Window boundary is approximate for edge-of-window papers.** Scholar
   shows relative freshness ("22 days ago"), not exact publication dates,
   sorted by *indexing* date, not necessarily pub date. One paper labeled
   "22 days ago" turned out, on fetching the actual source, to have
   published July 31 — one day *before* this window. I've excluded
   papers at the "22+ days ago" edge from the counted results below and
   flagged them separately rather than guessing. **Recommendation:**
   add a VERIFY note that boundary-adjacent papers (first/last 1–2 days
   of the window) get their exact pub date confirmed from the source, not
   just trusted from Scholar's relative label.

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
   in LOOP_INSTRUCTIONS.md. My earlier concern about that threshold was
   based on not yet knowing real volume; it looks appropriately calibrated
   now, not too low.
3. **False-positive patterns confirmed the rubric's design is
   necessary**, not just theoretical:
   - "Borderline symptoms" sometimes means a sub-clinical/cutoff score
     range on an *unrelated* scale (e.g. a COVID-anxiety study reporting
     "8.4% of participants had borderline symptoms" for depression —
     nothing to do with BPD). Pure keyword matching would have wrongly
     included this.
   - Several papers mention BPD once, incidentally, while studying
     something else entirely (a financial-scamming-in-geriatric-patients
     case series, an atypical-depression review, a gender-bias-in-clinical-practice
     review, a neuromodulation field piece). Rubric §26's "is this a
     substantive focus or a passing mention?" correctly screens these
     out.
   - A couple of results were non-academic websites (a counseling blog,
     a yoga-therapy site), not peer-reviewed/preprint/dissertation
     literature — out of scope per TASK.md, and worth an explicit VERIFY
     check.
4. **Abstract fetching works but isn't universal.** Open-access
   (PMC-hosted) sources fetched cleanly with full abstract text.
   Paywalled/gated sources (SSRN returned 403; a Springer article
   redirected to a login page) correctly fall back to "Abstract not
   available" per TASK.md — this path is real and will trigger
   regularly, not just in theory.

---

## NEW BPD LITERATURE — DRY RUN, AUG 1–22, 2026

**Total candidates from search (both queries, deduplicated):** 56
**Excluded — not substantively about BPD, or out of scope:** 22
**Boundary-uncertain (excluded from count pending exact-date check):** 5
**Substantively relevant, included below:** 32
&nbsp;&nbsp;— 15 with full classification blocks
&nbsp;&nbsp;— 17 in condensed form

Psychometrics: 2 high-confidence, 1 possible
Psychotherapy: 7 high-confidence, 2 possible
Adolescent BPD: 4 adolescent-focused/including-adolescents, 2 possible
Pharmacotherapy: 1
Other intervention: 3
Assessment/Diagnosis: 3
Neurobiology: 4
Comorbidity: 5 (secondary category on several of the above)
Qualitative/lived experience: 1
Reviews/meta-analyses: 3

### Most relevant papers this window

1. **Enhancing Therapists' Recognition and Responsiveness to Alliance
   Ruptures in Treatments for Borderline Personality Disorder** —
   Category: Psychotherapy — Adolescent BPD: No — Pilot RCT of two
   therapist-training methods for handling alliance ruptures in BPD
   treatment; directly actionable for clinical training programs.
2. **Adjunctive Memantine for the Treatment of Borderline Personality
   Disorder** — Category: Pharmacotherapy — Adolescent BPD: Possible
   (age range 16–65 in the source protocol) — One of very few BPD
   pharmacotherapy RCTs; NMDA-antagonist mechanism is relatively novel.
3. **The complexity of associations between borderline personality
   features, depression symptoms, anxiety symptoms, and suicidal
   behavior in adolescents** — Category: Epidemiology/phenomenology —
   Adolescent BPD: Yes — Adolescent focus — Network-analysis approach to
   a clinically important adolescent risk pattern.
4. **Borderline personality disorder and Mental Health Services: from
   the diagnostic pathway to the implementation of good practices** —
   Category: Assessment/Diagnosis — Adolescent BPD: No — Real-world
   feasibility data on DBT+GPM+family intervention; **note: on fetching
   the actual source, this paper's true publication date is July 31,
   2026 — one day before this window starts, so it is excluded from the
   counted total above despite Scholar showing "22 days ago."** Included
   here only as the concrete example behind finding #3.
5. **Mechanisms of vulnerability in borderline personality
   psychopathology: The role of childhood maltreatment, social
   cognition, and emotion dysregulation** — Category: Neurobiology —
   Adolescent BPD: No — Integrates three major etiological mechanisms in
   one model.

---

## Full classification blocks (15 representative papers)

### 1. Enhancing Therapists' Recognition and Responsiveness to Alliance Ruptures in Treatments for Borderline Personality Disorder: Protocol for a Pilot Randomised [Controlled Trial]

Authors: T Boritz, AA Di Bartolomeo, U Alter, et al.
Year: 2026
Journal: Counselling and Psychotherapy Research (Wiley)
DOI: not confirmed for this dry run
Google Scholar URL: not captured for this dry run

Abstract: Not independently fetched for this dry run. Scholar snippet:
"The therapeutic alliance in psychotherapy is associated with clinical
outcomes in borderline personality disorder (BPD)." Per web search, the
protocol randomizes 80 psychotherapists to two 4-week alliance-focused
DBT training conditions (reflective practice vs. deliberate practice),
assessing skill acquisition in recognizing/responding to alliance
ruptures.

BPD relevance: High

Primary category: Psychotherapy

Psychometrics: No — Confidence: High — Evidence: uses performance-task
outcome measures but does not evaluate their measurement properties.
Psychotherapy: Yes — Confidence: High — Evidence: directly evaluates a
DBT-based therapist-training intervention for BPD treatment.
Pharmacotherapy: No — Confidence: High — Evidence: no medication
involved.
Other intervention: No — Confidence: High — Evidence: N/A.
Assessment/Diagnosis: No — Confidence: Moderate — Evidence: not a
diagnostic study.
Adolescent BPD: No — Confidence: Moderate — Evidence: sample is
psychotherapists, not BPD patients directly; no adolescent focus
indicated.
Age range: Not reported (subjects are therapists, not patients)
Population: Psychotherapists treating BPD clients
Developmental focus: None/unclear
Other categories: none
Study design: Pilot RCT (training-intervention protocol)

Why it is relevant: Addresses a known clinical challenge (alliance
ruptures) specific to BPD treatment via a structured training RCT, with
direct implications for therapist training programs.
Classification notes: Classified from title + snippet + one web search
result, not full text — full text not fetched for this dry run.

---

### 2. Adjunctive Memantine for the Treatment of Borderline Personality Disorder: A 12-Week, Double-Blind, Randomised, Placebo-Controlled Trial

Authors: J Kulkarni, E Mu, A Cuskelly, C Gurvich, Q Li, et al.
Year: 2026
Journal: preprint (SSRN)
DOI: not confirmed
Google Scholar URL: not captured

Abstract: Not independently fetched — SSRN blocked automated access
(HTTP 403). Scholar snippet: "BPD is a highly prevalent, severe mental
illness with no substantially efficacious pharmacological treatments."

BPD relevance: High

Primary category: Pharmacotherapy

Psychometrics: No — Confidence: High — Evidence: N/A.
Psychotherapy: No — Confidence: High — Evidence: pharmacological trial,
not psychotherapy.
Pharmacotherapy: Yes — Confidence: High — Evidence: RCT of adjunctive
memantine (NMDA receptor antagonist) specifically for BPD.
Other intervention: No — Confidence: High — Evidence: N/A.
Assessment/Diagnosis: No — Confidence: High — Evidence: N/A.
Adolescent BPD: Possible — Confidence: Low — Evidence: not confirmed for
this specific 2026 trial; an earlier related memantine BPD trial from
the same research area used ages 16–65, which would include some
adolescents, but this hasn't been confirmed against this paper's actual
eligibility criteria.
Age range: Not confirmed for this dry run
Population: Adults (and possibly older adolescents) with BPD
Developmental focus: None/unclear
Other categories: none
Study design: RCT (double-blind, placebo-controlled)

Why it is relevant: One of very few pharmacological RCTs in BPD, testing
a mechanistically distinct target (glutamatergic system via NMDA
antagonism) in a field with few evidence-based medication options.
Classification notes: Full text not accessible for this dry run
(paywalled/access-blocked); age range needs verification against the
actual paper before being reported with confidence in a real run.

---

### 3. The complexity of associations between borderline personality features, depression symptoms, anxiety symptoms, and suicidal behavior in adolescents

Authors: C Li, S He, J Wen, S Zhang, L Chen, Y Hu, L Liu, J Gao
Year: 2026
Journal: BMC Psychiatry (Springer)
DOI: 10.1186/s12888-026-08498-9
Google Scholar URL: not captured

Abstract: Not independently fetched — Springer redirected to a login
wall on this attempt. Scholar snippet: "Symptom network analysis may
help clarify the complex interrelations among borderline personality
features."

BPD relevance: High

Primary category: Epidemiology/phenomenology

Psychometrics: No — Confidence: Moderate — Evidence: uses validated
measures but doesn't appear to evaluate their properties (snippet-based;
unconfirmed).
Psychotherapy: No — Confidence: High — Evidence: observational network
study, not a treatment evaluation.
Pharmacotherapy: No — Confidence: High — Evidence: N/A.
Other intervention: No — Confidence: High — Evidence: N/A.
Assessment/Diagnosis: No — Confidence: Moderate — Evidence: N/A from
available snippet.
Adolescent BPD: Yes — Adolescent focus — Confidence: High — Evidence:
title explicitly states "in adolescents."
Age range: Not reported in available snippet
Population: Adolescents with borderline personality features
Developmental focus: Risk factors in adolescence
Other categories: Comorbidity (depression, anxiety), suicide risk
Study design: Observational, symptom network analysis

Why it is relevant: Uses network analysis (rather than simple
correlation) to untangle how BPD features, depression, anxiety, and
suicidality interrelate specifically in adolescents — directly useful
for adolescent risk assessment.
Classification notes: Full text not accessible for this dry run; age
range and psychometrics status should be confirmed against full text in
a real run.

---

### 4. Localizing the structural and functional alteration networks associated with borderline personality disorder

Authors: L Zhang, Y Han, Y Ou, Y Liu, B Lang, W Guo
Year: 2026
Journal: Journal of Affective Disorders (Elsevier)
DOI: not confirmed
Google Scholar URL: not captured

Abstract: Not independently fetched. Scholar snippet: "structural and
functional alterations in borderline personality disorder (BPD) have
been widely reported in neuroimaging studies, the findings remain..."

BPD relevance: High

Primary category: Neurobiology/neuroscience

Psychometrics: No — Confidence: High.
Psychotherapy: No — Confidence: High.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: No — Confidence: Moderate.
Adolescent BPD: No — Confidence: Low — Evidence: not stated in snippet;
unconfirmed.
Age range: Not reported in available snippet
Population: Adults with BPD (likely; unconfirmed)
Developmental focus: None/unclear
Other categories: none
Study design: Neuroimaging meta-analytic/network localization study

Why it is relevant: Neuroimaging findings in BPD have historically been
inconsistent across studies; a localization/network approach aims to
reconcile that.
Classification notes: Snippet-only classification; full text not
fetched for this dry run.

---

### 5. Does impulsivity predict treatment outcomes in PTSD with borderline personality disorder features? Results from a randomized clinical trial

Authors: F Enning, M Bohus, K Priebe, R Steil, N Görg
Year: 2026
Journal: Journal of Psychiatric Research (Elsevier)

Abstract: Not independently fetched. Scholar snippet: study examines
abuse-related PTSD and personality-disorder features as predictors of
treatment outcome.

BPD relevance: Moderate–High
Primary category: Psychotherapy

Psychometrics: No — Confidence: Moderate.
Psychotherapy: Yes — Confidence: High — Evidence: secondary analysis of
an RCT examining treatment outcome predictors in a PTSD+BPD-features
population.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: No — Confidence: Moderate.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Adults with abuse-related PTSD and BPD features
Developmental focus: None/unclear
Other categories: Comorbidity (PTSD)
Study design: RCT (secondary/predictor analysis)

Why it is relevant: Identifies impulsivity as a candidate predictor of
treatment response in a clinically common PTSD+BPD comorbidity picture.
Classification notes: BPD is "features," not confirmed full diagnosis in
this sample — flagged as Moderate–High rather than High relevance.

---

### 6. Complex Post-Traumatic Stress Disorder and Borderline Personality Disorder: A Systematic Review of Diagnostic Distinction and Comorbidity

Authors: A Galvez-Merlin, S Diaz-Gonzalez, E Julian-Montaner, et al.
Year: 2026
Journal: Healthcare (MDPI)

Abstract: Not independently fetched. Scholar snippet: discusses need to
"clarify its boundaries with Borderline Personality Disorder" re: ICD-11.

BPD relevance: High
Primary category: Assessment/Diagnosis (diagnostic distinction is the
central question; also qualifies as Review)

Psychometrics: No — Confidence: Moderate.
Psychotherapy: No — Confidence: High.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: Yes — Confidence: High — Evidence: explicitly
about diagnostic distinction between C-PTSD and BPD.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: General BPD/C-PTSD literature (review)
Developmental focus: None/unclear
Other categories: Comorbidity, Review/meta-analysis
Study design: Systematic review

Why it is relevant: C-PTSD/BPD diagnostic overlap is a live nosological
debate (especially post-ICD-11); this review directly addresses it.
Classification notes: none.

---

### 7. Complex Trauma, Mentalization, Emerging Borderline Personality Features, and Aggressive Behavior in School-Aged Children in Child and Youth Protection Centre

Authors: A Gontero, MM Terradas, O Didier
Year: 2026
Journal: Journal of Infant, Child, and Youth (Taylor & Francis)

Abstract: Not independently fetched.

BPD relevance: High
Primary category: Adolescent BPD / developmental research

Psychometrics: No — Confidence: Moderate.
Psychotherapy: No — Confidence: Moderate — Evidence: setting is a
protection centre but snippet doesn't confirm a treatment evaluation.
Pharmacotherapy: No — Confidence: High.
Other intervention: Possible — Confidence: Low — Evidence: protection-centre
context may involve intervention, unconfirmed from title alone.
Assessment/Diagnosis: No — Confidence: Moderate.
Adolescent BPD: Yes — Adolescent focus — Confidence: High — Evidence:
"school-aged children," emerging BPD features as the explicit subject.
Age range: School-aged children (exact range not reported in snippet)
Population: School-aged children in a child/youth protection setting
Developmental focus: Emergence/development of BPD
Other categories: Comorbidity (trauma), mentalization
Study design: Not confirmed (likely observational/clinical)

Why it is relevant: Studies BPD features at their developmental
emergence point (childhood, not just adolescence), in a high-risk
(protection-centre) population — directly relevant to early-identification
research.
Classification notes: Title-only classification; full text not fetched.

---

### 8. Mechanisms of vulnerability in borderline personality psychopathology: The role of childhood maltreatment, social cognition, and emotion dysregulation

Authors: SMS Ardestani, M Aminaee, V Khosravani, et al.
Year: 2026
Journal: Journal of Affective Disorders (Elsevier)

Abstract: Not independently fetched. Scholar snippet: addresses how
"social cognition, emotion dysregulation, and clinical outcomes
frequently co-occur in borderline personality."

BPD relevance: High
Primary category: Neurobiology/neuroscience (mechanism-focused;
overlaps with Epidemiology/phenomenology)

Psychometrics: No — Confidence: Moderate.
Psychotherapy: No — Confidence: High.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: No — Confidence: Moderate.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Adults with BPD (likely; unconfirmed)
Developmental focus: None/unclear
Other categories: Comorbidity (childhood maltreatment history)
Study design: Not confirmed (likely observational/mediation model)

Why it is relevant: Integrates three major proposed mechanisms
(maltreatment history, social cognition, emotion dysregulation) into one
explanatory model of BPD vulnerability.
Classification notes: Snippet-only classification.

---

### 9. Efficacy of Online Dialectical Behavior Therapy Interventions on Emotional and Behavioral Outcomes: A Systematic Review and Meta-Analysis

Authors: P Anwar, M Zahra, H Javed, S Naveed, et al.
Year: 2026
Journal: Pakistan Journal of Psychology

Abstract: Not independently fetched. Scholar snippet: DBT was
"originally developed for chronic suicidality and borderline personality
disorder."

BPD relevance: Moderate — Confidence caveat: DBT is used for many
conditions beyond BPD; need to confirm whether BPD-specific outcomes are
broken out or whether this is DBT-for-anything broadly.
Primary category: Psychotherapy / Review

Psychometrics: No — Confidence: Moderate.
Psychotherapy: Yes — Confidence: Moderate — Evidence: meta-analysis of a
BPD-associated therapy modality (DBT), though scope may extend beyond
BPD populations specifically.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: No — Confidence: High.
Adolescent BPD: Possible — Confidence: Low — Evidence: online DBT is
commonly studied in youth populations, unconfirmed here.
Age range: Not reported in snippet
Population: Not confirmed — may be broader than BPD specifically
Developmental focus: None/unclear
Other categories: Review/meta-analysis
Study design: Systematic review and meta-analysis

Why it is relevant: Telehealth/online DBT delivery is a growing and
practically important care-access question.
Classification notes: **Flagged for human review** — unclear from the
snippet alone whether this meta-analysis is BPD-specific or DBT-for-
general-populations with BPD as one origin-story mention. This is
exactly the kind of case rubric §22 says should not be forced to a
confident classification.

---

### 10. Borderline Personality Disorder: Assessment from an Integrative Dimensional and Categorical Perspective

Authors: V Morán, L Torres-Rosado, O Lozano-Rojas, et al.
Year: 2026
Journal: Journal of Psychopathology (Springer)

Abstract: Not independently fetched. Scholar snippet: examines
"properties of the Borderline Personality Disorder (BPD)" and assessment
approaches.

BPD relevance: High
Primary category: Assessment/Diagnosis (with likely Psychometrics
overlap)

Psychometrics: Possible — Confidence: Moderate — Evidence: "properties"
language suggests measurement-property evaluation, but title frames it
as assessment/diagnostic-model integration, not instrument validation
specifically — needs full text to confirm.
Psychotherapy: No — Confidence: High.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: Yes — Confidence: High — Evidence: title is
explicitly about assessment from dimensional vs. categorical models.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Not confirmed
Developmental focus: None/unclear
Other categories: none
Study design: Not confirmed

Why it is relevant: The dimensional-vs-categorical debate is central to
how BPD is diagnosed post-DSM-5 alternative model; integrative papers on
this are directly useful for diagnostic-practice tracking.
Classification notes: Psychometrics flag kept at Possible per rubric §4
("distinguish evaluating a measure from using a measure") — not enough
evidence from the snippet to call it High confidence.

---

### 11. Integrative Residential Treatment of Co-Occurring Borderline and Narcissistic Personality Dysfunction: Perspectives from the Gunderson Residence

Authors: KL Jacob, BT Unruh
Year: 2026
Journal: Harvard Review of Psychiatry

Abstract: Not independently fetched.

BPD relevance: High
Primary category: Other clinical intervention (residential treatment
program, not classic psychotherapy-modality or medication evaluation)

Psychometrics: No — Confidence: High.
Psychotherapy: Possible — Confidence: Low — Evidence: residential
programs typically embed psychotherapy, but this appears to be a
program/perspectives piece rather than a therapy-outcome evaluation.
Pharmacotherapy: No — Confidence: High.
Other intervention: Yes — Confidence: Moderate — Evidence: describes an
inpatient/residential program model.
Assessment/Diagnosis: No — Confidence: Moderate.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Adults with co-occurring BPD and NPD
Developmental focus: None/unclear
Other categories: Comorbidity (NPD)
Study design: Not confirmed (perspectives/program-description piece,
possibly not empirical)

Why it is relevant: BPD/NPD co-occurrence is under-studied relative to
either disorder alone, and residential-level care models for it are
rare in the literature.
Classification notes: May be a clinical-perspectives piece rather than
an empirical study — study design unconfirmed without full text.

---

### 12. Treatment of Borderline Personality Disorder: Re-envisioned to Mitigate Stigma and Enhance Treatment Effectiveness

Author: AL Steinkamp
Year: 2026
Journal: University of Kentucky (dissertation repository)

Abstract: Not independently fetched. Scholar snippet: BPD characteristics
are "often viewed negatively by therapists and other mental health
providers."

BPD relevance: High
Primary category: Psychotherapy (treatment-effectiveness framing) —
overlaps with stigma/qualitative themes

Psychometrics: No — Confidence: Moderate.
Psychotherapy: Yes — Confidence: Moderate — Evidence: framed around
enhancing treatment effectiveness, though the stigma angle suggests it
may be more conceptual/qualitative than an outcome trial.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: Moderate.
Assessment/Diagnosis: No — Confidence: Moderate.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Not confirmed
Developmental focus: None/unclear
Other categories: none
Study design: Dissertation — design not confirmed from snippet

Why it is relevant: Clinician stigma toward BPD patients is a documented
barrier to care; this directly targets it.
Classification notes: Dissertation source — worth confirming it's a
completed/available dissertation rather than a proposal.

---

### 13. Transcutaneous auricular vagus nerve stimulation and emotional responding in borderline personality disorder: a randomized single-blind, sham-controlled trial

Authors: G Guerriero, AC Ruocco, HK Carlsen, AR Daros, et al.
Year: 2026
Journal: Borderline Personality Disorder and Emotion Dysregulation
(Springer)

Abstract: Not independently fetched. Scholar snippet: "BPD is
characterized by severe emotional vulnerability, including heightened
sensitivity, exaggerated reactivity, and delayed..."

BPD relevance: High
Primary category: Other clinical intervention (neurostimulation)

Psychometrics: No — Confidence: High.
Psychotherapy: No — Confidence: High.
Pharmacotherapy: No — Confidence: High.
Other intervention: Yes — Confidence: High — Evidence: RCT of
transcutaneous vagus nerve stimulation (a neurostimulation technique) for
emotional responding in BPD.
Assessment/Diagnosis: No — Confidence: High.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Adults with BPD (likely; unconfirmed)
Developmental focus: None/unclear
Other categories: none
Study design: RCT (single-blind, sham-controlled)

Why it is relevant: Neurostimulation for BPD emotion regulation is a
novel, non-pharmacological, non-psychotherapy intervention category —
directly matches rubric §14.
Classification notes: none.

---

### 14. Evaluating the introduction module of Mentalization-Based Treatment: a naturalistic pre-post clinical cohort study

Authors: N Bachrach, S Brugman, R Berkers, et al.
Year: 2026
Journal: Borderline Personality Disorder and Emotion Dysregulation
(Springer)

Abstract: Not independently fetched.

BPD relevance: High
Primary category: Psychotherapy

Psychometrics: No — Confidence: High.
Psychotherapy: Yes — Confidence: High — Evidence: evaluates the
introductory module of MBT (a named BPD psychotherapy) in a cohort study.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: No — Confidence: High.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: BPD patients starting MBT
Developmental focus: None/unclear
Other categories: none
Study design: Naturalistic pre-post cohort study

Why it is relevant: MBT's introduction/psychoeducation module is
under-studied relative to the full treatment; naturalistic cohort data
on it fills a real gap.
Classification notes: none.

---

### 15. The Experience of Emotions in Individuals Diagnosed with Borderline Personality Disorder: Childhood and Present-Day Reflections

Authors: O Ayan, M İnzimermerkaya, et al.
Year: 2026
Journal: AYNA KLINIK (Turkish clinical psychology journal)

Abstract: Not independently fetched. Scholar snippet: qualitative
research examining emotion experiences in individuals with BPD.

BPD relevance: High
Primary category: Qualitative / lived experience

Psychometrics: No — Confidence: High.
Psychotherapy: No — Confidence: High.
Pharmacotherapy: No — Confidence: High.
Other intervention: No — Confidence: High.
Assessment/Diagnosis: No — Confidence: High.
Adolescent BPD: No — Confidence: Low (unconfirmed).
Age range: Not reported in snippet
Population: Adults diagnosed with BPD
Developmental focus: None/unclear (though the "childhood and
present-day" framing does touch developmental history retrospectively)
Other categories: none
Study design: Qualitative

Why it is relevant: First-person accounts of emotional experience,
spanning childhood and present-day, directly serve the rubric's
lived-experience category.
Classification notes: none.

---

## Additional substantively-relevant papers (condensed — not fully classified in this dry run)

| # | Title | Journal | Primary category | Adolescent BPD |
|---|---|---|---|---|
| 16 | AKuT-Ambulanz: sektorenübergreifende Krisenintervention bei Borderline-und Traumafolgestörungen am ZI Mannheim | Der Nervenarzt | Other intervention (crisis care) | No |
| 17 | A profile of occupational therapy practice in Australia for people diagnosed with BPD | Australian Occupational Therapy Journal | Other intervention | No |
| 18 | Impact of Borderline Personality Features on Menstrual Phases and Pain Perception | ProQuest (dissertation) | Epidemiology/phenomenology | Possible |
| 19 | Anxious or Avoidant? Attachment styles moderating PTSD/BPD development after child maltreatment | ProQuest (dissertation) | Epidemiology/phenomenology | Possible |
| 20 | Recurrent Deliberate Foreign Body Ingestion: Psychiatric Comorbidities, Management, Ethics | Current Psychiatry Reports | Comorbidity | No |
| 21 | FROM BORDERLINE PERSONALITY DISORDER TO PARKINSON'S DISEASE (case report) | Am J Geriatric Psychiatry | Comorbidity | No |
| 22 | Internal Processes of a Person with a Borderline Personality Disorder: A Computational Analysis | Springer (book chapter) | Neurobiology (computational) | No |
| 23 | Joy and compassion as prosocial antidotes to aggression | Borderline Personality Disorder and Emotion Dysregulation | Other/psychopathology | No |
| 24 | Borderline-Störung in der hausärztlichen Versorgung | MMW-Fortschritte der Medizin | Assessment/Diagnosis (primary care) | No |
| 25 | Associations Between Dissociation and Childhood Trauma in BPD and Affective Disorders: A Network Analytic Approach | Acta Psychiatrica Scandinavica | Neurobiology/phenomenology | No |
| 26 | Borderline Personality Disorder: An Integrative Biopsychosocial Perspective on Mental Health | Journal Plus Education | Review | No |
| 27 | The effectiveness of the Transitional Age Youth Self-Harm (TaySH) Program | researchsquare.com (preprint) | Other intervention | Possible — "Transitional Age Youth" |
| 28 | Journal of Psychopathology and Clinical Science [131 women with BPD vs. 134 controls] | J Psychopathology and Clinical Science | Neurobiology/phenomenology | No |
| 29 | Testing the Impact of Sexual Minority Stress on BPD-Related Behaviors Among LGB adults | ProQuest (dissertation) | Epidemiology/phenomenology | No |
| 30 | Computational phenomenology of self and time in borderline and narcissistic personality disorders | escholarship.org | Neurobiology (computational) | No |
| 31 | Exploring the link between attachment, emotion regulation, and brain structure in restrictive anorexia nervosa and borderline personality disorder | researchsquare.com (preprint) | Neurobiology | No |
| 32 | When Psychosis Is Not Psychosis: Transient Psychotic Phenomena in Borderline Personality Disorder | Annals of Indian Psychiatry | Epidemiology/phenomenology | No |

---

## Excluded — not substantively about BPD, or out of scope

| Title | Journal | Reason excluded |
|---|---|---|
| Altered responses to social closeness and rule violations in obsessive-compulsive personality disorder | Borderline Personality Disorder and Emotion Dysregulation | About OCPD, not BPD (published in a BPD-named journal but not itself about BPD) |
| Alexithymia as a determinant of health outcomes | rep.bsmu.by | BPD mentioned once as a comorbidity to prevent; not the paper's focus |
| F2. Financial Scamming Experienced by Patients in a Geriatric Psychiatry Outpatient Program | Am J Geriatric Psychiatry | Single incidental mention ("2 patients had borderline personality traits") in a case series about financial scamming |
| Anxiety and depression among home-quarantined COVID-19 patients | BMC Infectious Diseases | "Borderline symptoms" = sub-threshold score range on an anxiety/depression scale — not about BPD at all |
| Recognizing and Treating Dissociative Identity Disorder | Journal of Health Service Psychology | Incidental symptom-overlap mention; paper is about DID |
| Who Gets Labeled 'Borderline'? What Research Shows | connect-counseling.co | Not peer-reviewed/preprint/dissertation/conference literature — a counseling blog |
| Narcissistic Personality Disorder: Dynamics and Implications in Modern Society | ganeshakreasisemesta.com repository | BPD mentioned only as a comorbidity example; primary topic is NPD; source academic status unclear |
| The Dialogic Method of Yoga Vasistha in Psychoanalytic Therapy | indianyoga.org | Not peer-reviewed/preprint/dissertation/conference literature |
| Distress Intolerance: Dialectical Behavior Therapy Informed Communication for Serious Illness Care | Journal of Palliative Medicine | DBT mentioned as "originally developed for BPD" context only; paper is about palliative-care communication, not a BPD study |
| Village/governance/engineering/obstetric/pediatric results from the bare "BPD" query (bronchopulmonary dysplasia, biparietal diameter, bond-based peridynamics, Indonesian village governance, etc.) | various | Acronym collision — "BPD" means something unrelated; confirmed via false-positive control |

*(This list is abbreviated to the clearest examples; the full 22-item
exclusion set followed the same reasoning — incidental mention rather
than substantive focus, or out-of-scope source type.)*

## Boundary-uncertain (excluded from all counts above pending exact-date verification)

| Title | Scholar freshness label | Note |
|---|---|---|
| Borderline personality disorder and Mental Health Services: from the diagnostic pathway... | "22 days ago" | Confirmed actual pub date: **July 31, 2026** — one day before this window. Excluded. |
| When Psychosis Is Not Psychosis: Transient Psychotic Phenomena in BPD | "22 days ago" | Not individually date-checked; excluded pending verification, per the lesson from the item above. |
| Short-term preliminary results from HIPOCRAT-ESK study (TRD) | "22 days ago" | Same — BPD is a secondary comorbidity mention in this one regardless, likely excludable either way. |
| The colonized psyche: psychoanalytic differentiation between C-PTSD and BPD | "23 days ago" | Outside window based on label; not individually verified. |
| A Path to Suicidal Ideation Through Emotional Intelligence... | "23 days ago" | Outside window based on label; not individually verified. |

---

## PROGRESS.md — not updated

This dry run intentionally did **not** touch PROGRESS.md or get
committed automatically — it's a test artifact for review, not a real
week's run. See the accompanying message for what's recommended before
Monday's first live run.
