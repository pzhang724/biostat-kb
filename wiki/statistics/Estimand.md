---
title: "Estimand"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-22
updated: 2026-06-22
sources: 1
---

# Estimand

An **estimand (估计目标)** is a precise description of **what is being estimated** — the target of estimation that makes the trial **objective** and the statistical **analysis** line up. It answers "what treatment effect, in whom, on what outcome, handling complications how" *before* a method is chosen or any analysis is run. Formalized by **ICH E9(R1)** (the addendum to E9) and pre-specified in the protocol/SAP, giving a clear chain: objective → **estimand** → estimator → estimate.

It is defined by **five attributes**:

1. **Treatment** — the treatment condition(s) being compared.
2. **Population** — the target patients (via inclusion/exclusion).
3. **Variable / endpoint** — the outcome measured on each patient.
4. **Intercurrent event handling** — for each [[Intercurrent Event|ICE]] type, one of the five strategies (treatment policy / hypothetical / composite / while-on-treatment / principal stratum).
5. **Population-level summary measure** — e.g. hazard ratio, difference in means, odds ratio.

The intercurrent-event attribute is the central new piece: the **same endpoint can yield different estimands** purely by changing how ICEs are handled — e.g. **OS** with a treatment-policy strategy for [[Anti-Cancer Therapy Categories in Oncology Trials|subsequent therapy]] vs. a hypothetical strategy censoring at the switch.

Why it matters: it forces alignment of the clinical question and the analysis, removing ambiguity that used to hide inside "the analysis" (ITT vs per-protocol, how dropouts/switches were treated).
