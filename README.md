# literature-updates

A weekly automated literature-monitoring loop for borderline personality
disorder (BPD) research, with a particular focus on psychometrics and
psychotherapy — especially psychodynamic psychotherapy.

## What this does

Every Monday at 4:00 AM EST, a scheduled agent searches Google Scholar
(PubMed as fallback) for new literature published in the prior week
matching BPD-related terminology, screens out false positives (acronym
collisions like bronchopulmonary dysplasia, incidental one-line
mentions), and classifies every substantively relevant paper against a
detailed rubric before writing a summary file to `weekly summaries/`.

See `instructions/TASK.md` for the task spec, `instructions/LOOP_INSTRUCTIONS.md`
for the search/verify/escalation protocol, and
`instructions/classification_rubric.md` for the full classification rules.

## Classification categories

Every paper found is screened against these categories (a paper can
match more than one — "done" means every category gets a Yes/No/Possible
call with a confidence level, not that every paper fits neatly into one
box):

1. Psychometrics / measurement
2. Psychotherapy
3. Pharmacotherapy
4. Other clinical interventions
5. Assessment / diagnosis
6. Adolescent BPD
7. Mentalization & Reflective Functioning
8. Psychodynamic
9. Epidemiology / phenomenology
10. Neurobiology / neuroscience
11. Comorbidity (with a dedicated highlight for Bipolar spectrum — Bipolar I and II — comorbidity)
12. Qualitative / lived-experience research
13. Reviews / meta-analyses
14. Other BPD-relevant research

## Repo layout

- `instructions/` — the task spec, loop protocol, and classification
  rubric that drive the automated routine
- `weekly summaries/` — one output file per week (`MMDD_summary.md`),
  each with an aggregate summary plus a full classification block per
  paper