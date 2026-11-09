# BPD Literature Summary — November 9, 2026

**Window searched:** November 2, 2026 4:01 AM EST – November 9, 2026 3:59 AM EST
**Source:** PubMed (queries: broad terminology OR-query, bare "BPD")

**Note:** Google Scholar was unreachable this run. Both `scholar.google.com`
and the general `www.google.com` domain returned HTTP 403 at the network/
egress-proxy level (confirmed via direct `curl` test and again via one
retry after a 5-second pause; no CAPTCHA page was ever served — the
connection itself was refused), so PubMed E-utilities was used as the
fallback for both required queries per TASK.md. Date-window filtering used
PubMed's own `esearch` with two passes per query — `datetype=pdat`
(formal publication date) and `datetype=edat` (indexing/Entrez date),
both `mindate=2026/11/02&maxdate=2026/11/09` — then exact `History`
timestamps (`entrez`/`pubmed`/`medline`, read as UTC per this log's
established convention) from `efetch` XML to resolve every date-edge case,
consistent with every prior week's method.

## NEW BPD LITERATURE — WEEK OF November 9, 2026

Total new papers identified: 3

Psychometrics:
- 0 high-confidence papers
- 1 possible paper

Psychotherapy:
- 0 high-confidence papers
- 0 possible papers

Adolescent BPD:
- 1 adolescent-focused paper
- 0 papers including adolescents
- 1 possible paper

Pharmacotherapy:
- 0 papers

Other intervention:
- 0 papers

Mentalization & Reflective Functioning:
- 0 papers

Psychodynamic:
- 0 papers (1 additional paper flagged Possible — see Classification notes)

Comorbid with Bipolar Spectrum (I/II):
- 0 papers

Other BPD research:
- 1 paper (theoretical/transdiagnostic neuroscience review, kept at Low relevance)

### Most relevant new papers

1. **Comparisons of psychiatric diagnoses, medication prescription patterns, and psychiatric care utilization in first-degree relatives and spouses of individuals with and without Borderline Personality Disorder** — Category: Epidemiology/phenomenology — Adolescent BPD: Possible — Swedish nationwide register study (n=24,769 vs. 77,728) finds markedly elevated psychiatric morbidity, care use, and psychotropic medication use among the family members of people with BPD.
2. **Diagnosis of personality disorders in youth** — Category: Assessment/Diagnosis — Adolescent BPD: Yes — Adolescent focus — Narrative review of the youth-personality-disorder diagnostic landscape, naming BPD-specific instruments (BPFSC-11, CI-BPD) within the broader categorical-vs-dimensional debate.

### Notable authors/affiliations flagged this week

None this week.

---

## Papers

### 1. Comparisons of psychiatric diagnoses, medication prescription patterns, and psychiatric care utilization in first-degree relatives and spouses of individuals with and without Borderline Personality Disorder

- **Authors:** Vikström Eckevall J, Thacher JD, Capusan AJ, Rylander L, Westling S
- **Year:** 2026
- **Journal:** Comprehensive Psychiatry
- **DOI:** 10.1016/j.comppsych.2026.152755
- **PubMed URL (Google Scholar not used — see header note):** https://pubmed.ncbi.nlm.nih.gov/42998586/

**Abstract:**

Small-scale studies have shown that the next-of-kin of individuals with Borderline Personality Disorder (BPD) face elevated risk of symptoms of mental illness. Little is known about whether these increased symptoms correspond to psychiatric disorders. The aim of this study was to examine the risk of psychiatric disorders, use of psychotropic medication, and utilization of psychiatric care in the next-of-kin of individuals with BPD. Individuals diagnosed with BPD in Sweden, from 2011-01-01 to 2022-12-31, were matched (1:3) by age and sex to individuals without BPD. The study and control cohorts comprised the first-degree relatives and spouses of individuals with BPD and matched controls (n = 24,769 vs n = 77,728). Cox proportional hazards and Poisson regression models assessed associations between having a next-of-kin with BPD and outcome measures during five years post index. After adjustment for potential confounders, the next-of-kin in the BPD cohort exhibited an increased risk of any of the included disorders (HR 2.08; 95% CI 1.94-2.24), as well as higher rates of psychiatric care utilization (IRR 2.21; 95% CI 2.13-2.29), including inpatient care (IRR 2.23; 95% CI 2.02-2.47), and psychotropic medication use (HR 1.75; 95% CI 1.65-1.85), compared with the next-of-kin in the control cohort. In this nationwide study, the next-of-kin of individuals with BPD exhibited increased risk of psychiatric disorders, higher use of psychotropic medication, and greater utilization of psychiatric care. This study highlights the need of adequate care for individuals with BPD and emphasizes the importance of providing support to their next-of-kin.

**Classification**

- **BPD relevance:** High
- **Primary category:** Epidemiology/phenomenology
- **Psychometrics:** No — Confidence: High — Evidence: no measure development, validation, or measurement-property evaluation; BPD diagnosis is used only as the registry-defined grouping variable.
- **Psychotherapy:** No — Confidence: High — Evidence: no psychotherapy delivered or evaluated.
- **Pharmacotherapy:** No — Confidence: High — Evidence: psychotropic medication use in relatives is an outcome variable, not a treatment being evaluated.
- **Other intervention:** No — Confidence: High — Evidence: not an intervention study.
- **Assessment/Diagnosis:** No — Confidence: Moderate — Evidence: BPD diagnosis is the registry-defined exposure variable, but diagnostic methodology itself is not evaluated.
- **Mentalization & Reflective Functioning:** No — Confidence: High — Evidence: not discussed.
- **Psychodynamic:** No — Confidence: High — Evidence: not discussed.
- **Adolescent BPD:** Possible
- **Age range:** Not reported in abstract
- **Population:** First-degree relatives and spouses of individuals diagnosed with BPD in Sweden (2011–2022), matched 1:3 to relatives/spouses of non-BPD controls
- **Developmental focus:** none/unclear
- **Comorbid — Bipolar spectrum (I/II):** No
- **Notable author/affiliation match:** No — Matched on: n/a
- **Other categories:** Epidemiology: Yes (nationwide register-based risk study)
- **Study design:** Register-based retrospective matched-cohort study

**Why it is relevant:** A large Swedish nationwide register study quantifying substantially elevated psychiatric morbidity, psychiatric care utilization, and psychotropic medication use among the family members of people with BPD — new population-level evidence on the family-level burden of BPD.

**Classification notes:** Age range of the index BPD patients (and thus of their relatives/spouses) is not reported in the abstract; marked Adolescent BPD: Possible rather than No because Swedish clinical practice permits BPD diagnosis in older adolescents and the registry period (2011–2022) is not age-restricted in the available text.

### 2. Diagnosis of personality disorders in youth

- **Authors:** Zhou R, Huang A, Zhang T
- **Year:** 2026
- **Journal:** Current Opinion in Psychiatry
- **DOI:** 10.1097/YCO.0000000000001131
- **PubMed URL (Google Scholar not used — see header note):** https://pubmed.ncbi.nlm.nih.gov/42992472/

**Abstract:**

Diagnosis of personality disorders (PDs) in children and adolescents remains clinically controversial, despite revisions in DSM-5-TR Alternative Model for Personality Disorders (AMPD) and ICD-11 removing formal age-limits for PD diagnosis. This review synthesizes recent 12-18-month evidence on conceptual debates, diagnostic frameworks, assessment instruments, cross-cultural considerations, diagnostic risks (over-diagnosis versus under-diagnosis), and clinical-ethical implications for personality pathology among young people. Dimensional severity-centred systems (AMPD Criterion-A/ICD-11 personality-functioning severity) have gained empirical ground for youth populations, yet categorical and dimensional approaches show partial nonoverlap in clinical adolescent cohorts. Validated brief self-report screening tools (LPFS-BF 2.0, BPFSC-11, LoPF-Q 12-18 screener) cannot replace semi-structured clinical interviews (STiP-5.1, CI-BPD). Youth PD presentations vary substantially across cultural contexts; identity-disturbance may be less prominent in nonwestern samples. Longitudinal data confirm substantial plasticity of personality-functioning in adolescence, while sub-threshold personality pathology predicts later psychosocial impairment. Ethical scholarship favours staged-care over stepped-care models, arguing that appropriate early diagnosis reduces rather than amplifies stigma. Contemporary youth-PD diagnosis requires hybrid categorical-dimensional, multiinformant assessment. Clinicians must differentiate normative adolescent developmental turmoil from enduring personality-related functional impairment. Gaps persist in youth-specific cut-offs for dimensional tools, cross-cultural measurement invariance, and longitudinal real-world clinical outcome research.

**Classification**

- **BPD relevance:** Moderate
- **Primary category:** Assessment/Diagnosis
- **Psychometrics:** Possible — Confidence: Low — Evidence: names specific validated screening/interview tools (LPFS-BF 2.0, BPFSC-11 [Borderline Personality Features Scale for Children], LoPF-Q 12-18, STiP-5.1, CI-BPD [Childhood Interview for Borderline Personality Disorder]) but is a narrative synthesis of the diagnostic landscape, not itself a measure-development or validation study.
- **Psychotherapy:** No — Confidence: High — Evidence: no treatment delivered or evaluated.
- **Pharmacotherapy:** No — Confidence: High — Evidence: not discussed.
- **Other intervention:** No — Confidence: High — Evidence: not discussed.
- **Assessment/Diagnosis:** Yes — Confidence: High — Evidence: the entire review is organized around diagnostic frameworks, categorical-vs-dimensional debates, and assessment instruments for personality pathology in youth, including BPD-specific tools (CI-BPD, BPFSC-11).
- **Mentalization & Reflective Functioning:** No — Confidence: High — Evidence: not discussed.
- **Psychodynamic:** No — Confidence: High — Evidence: not discussed.
- **Adolescent BPD:** Yes — Adolescent focus
- **Age range:** Not numerically reported ("children and adolescents," "youth populations," "adolescent cohorts")
- **Population:** Children and adolescents being evaluated for personality disorders/personality pathology, with BPD-specific instruments named among the broader personality-disorder assessment toolkit
- **Developmental focus:** adolescent assessment/adolescent diagnosis
- **Comorbid — Bipolar spectrum (I/II):** No
- **Notable author/affiliation match:** No — Matched on: n/a
- **Other categories:** Review/Meta-analysis: Yes (narrative review)
- **Study design:** Narrative review

**Why it is relevant:** Synthesizes current debates and instruments for diagnosing personality disorders in youth, explicitly naming BPD-specific tools (BPFSC-11, CI-BPD) within the categorical-vs-dimensional assessment debate — directly useful for tracking adolescent BPD assessment practice even though the review's scope is personality disorders broadly rather than BPD alone.

**Classification notes:** BPD relevance set to Moderate rather than High because the paper's organizing subject is youth personality disorders in general, not BPD specifically; BPD content (specific instruments, diagnostic-risk discussion) is substantive enough, however, to warrant inclusion rather than exclusion per rubric §26.

### 3. The Separation-Distress Network as a Transdiagnostic Mechanism Linking Relational Adversity, Social Pain, and Psychopathology

- **Authors:** Glavač T, Nelson E, Zweben D, Jarcho J
- **Year:** 2026
- **Journal:** Neuroscience and Biobehavioral Reviews
- **DOI:** 10.1016/j.neubiorev.2026.107073
- **PubMed URL (Google Scholar not used — see header note):** https://pubmed.ncbi.nlm.nih.gov/42998779/

**Abstract:**

Relational trauma is a major contributor to the development of mental health disorders. This association likely reflects the social nature of humans and other mammals, whose survival depends on maintaining stable social bonds. When these bonds are threatened or disrupted, individuals experience social pain, a distress response mediated by the mammalian separation-distress network. During early development, this network is sensitive to maintaining proximity with caregivers, as independent survival is not yet possible. Converging evidence from ethology, psychodynamic and attachment theory, and social and affective neuroscience supports the function of this network. Because mammalian brains are inherently tuned to form social bonds, adverse relational experiences can disrupt socioemotional development and increase vulnerability to psychopathology. Neural substrates of separation distress include the anterior cingulate cortex, ventral septum, bed nucleus of the stria terminalis, dorsal preoptic area, dorsomedial thalamus, and periaqueductal gray, with endogenous opioids and glucocorticoids serving as key neurochemical modulators in the separation-distress response. Separation distress and adverse relational experiences also alter physiological systems implicated in psychopathology, including the HPA axis, autonomic nervous system activity, inflammation, and brain structure and connectivity. This paper argues that relational trauma and social pain are mediated by an evolutionarily conserved subcortical separation-distress network shared across predominantly mammalian species. Dysregulation of this network may represent one common mechanism underlying depression, social anxiety, suicidality, substance use disorders, borderline personality disorder, and other psychiatric conditions. Understanding the processes linking adverse relational experiences, separation-distress activation, and social pain may provide insights into the etiology and treatment of diverse disorders.

**Classification**

- **BPD relevance:** Low
- **Primary category:** Other (transdiagnostic neurobiological/theoretical review)
- **Psychometrics:** No — Confidence: High — Evidence: no measurement content.
- **Psychotherapy:** No — Confidence: High — Evidence: no treatment evaluated.
- **Pharmacotherapy:** No — Confidence: High — Evidence: not discussed.
- **Other intervention:** No — Confidence: High — Evidence: not discussed.
- **Assessment/Diagnosis:** No — Confidence: High — Evidence: not discussed.
- **Mentalization & Reflective Functioning:** No — Confidence: High — Evidence: not discussed as a measured/analyzed construct.
- **Psychodynamic:** Possible — Confidence: Low — Evidence: cites "psychodynamic and attachment theory" as one strand of converging evidence for the separation-distress network, but the paper is organized around affective neuroscience, not psychodynamic theory or technique.
- **Adolescent BPD:** No
- **Age range:** Not reported
- **Population:** Theoretical/transdiagnostic — no specific empirical patient sample; discusses early-development neurobiology in general terms
- **Developmental focus:** none/unclear (theoretical discussion of early-development attachment neurobiology, not a BPD-specific developmental study)
- **Comorbid — Bipolar spectrum (I/II):** No
- **Notable author/affiliation match:** No — Matched on: n/a
- **Other categories:** Neurobiology/Neuroscience: Yes (reviews separation-distress neural circuitry); Review: Yes (narrative/theoretical review)
- **Study design:** Narrative/theoretical review

**Why it is relevant:** Proposes a shared separation-distress neurocircuitry mechanism across several psychiatric conditions; BPD is named specifically as one of the conditions potentially explained by this mechanism, but it is one of five disorders listed and is not itself analyzed.

**Classification notes:** BPD relevance kept at Low rather than excluded, per rubric §26: "borderline personality disorder" is a specifically named clinical entity in the paper's own list of conditions the proposed mechanism may underlie, not an unrelated keyword collision (e.g., not bronchopulmonary dysplasia) — consistent with this log's established practice of keeping specifically-named-but-secondary BPD mentions at Low relevance rather than excluding them (see e.g. the Nov 2, 2026 run's Oumou/Capruso entries).
