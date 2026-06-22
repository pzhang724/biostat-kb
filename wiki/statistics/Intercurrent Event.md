---
title: "Intercurrent Event"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-11
updated: 2026-06-11
sources: 1
---

# Intercurrent Event

An **intercurrent event (ICE)** is a core concept of the **ICH E9(R1)** estimand framework: an event occurring *after treatment initiation* that affects either the **interpretation** or the **existence** of the outcome measurement. It is not a plain covariate and not missing data — after an ICE, the quantity you intended to measure changes meaning.

Typical ICEs: treatment discontinuation or switching, use of prohibited/rescue concomitant medication, **subsequent anti-cancer therapy**, and death (for non-survival endpoints). Treatment discontinuation corresponds to [[End of Treatment vs End of Study|End of Treatment]] — the patient goes off-treatment but is usually still followed to [[End of Treatment vs End of Study|End of Study]].

E9(R1) requires pre-specifying, for each ICE type, one of five **handling strategies**:

- **Treatment policy** — ignore the ICE, use the observed outcome regardless (intention-to-treat spirit).
- **Hypothetical** — envisage the outcome had the ICE not occurred (e.g. censor at the event).
- **Composite** — fold the ICE into the endpoint definition (e.g. count it as failure).
- **While on treatment** — use only the outcome up to the ICE.
- **Principal stratum** — estimate within the subpopulation that would not experience the ICE.

The choice of strategy, together with population, endpoint, and summary measure, defines the [[Estimand]]. In oncology, subsequent anti-cancer therapy (see [[Anti-Cancer Therapy Categories in Oncology Trials]]) is the most common ICE in **OS** analysis: a treatment-policy strategy keeps following OS as usual, whereas a hypothetical strategy censors at the switch.

