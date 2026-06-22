---
title: "Estimand"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-22
updated: 2026-06-22
sources: 2
---

# Estimand

An **estimand (估计目标)** is a precise description of **what is being estimated** — the target of estimation that makes the trial **objective** and the statistical **analysis** line up. It answers "what treatment effect, in whom, on what outcome, handling complications how" *before* a method is chosen or any analysis is run. Formalized by **ICH E9(R1)** (the addendum to E9) and pre-specified in the protocol/SAP.

## The estimation chain

E9(R1) makes an explicit chain:

- **Objective** — the clinical question in words ("does drug A prolong survival vs B?").
- **Estimand** — that question made precise via the five attributes: *what* is being estimated.
- **Estimator (估计量)** — the statistical method used to estimate it (e.g. Cox model, MMRM).
- **Estimate (估计值)** — the actual number produced (e.g. HR = 0.72).

Plus **sensitivity analysis (敏感性分析)** — separate analyses under *different assumptions* about the **same** estimand, to test robustness. (Distinct from a **supplementary analysis**, which targets a *different* estimand.)

The key shift: pick the estimand **from** the clinical question, then choose the estimator to match — not "run the standard analysis and see what it estimates."

## The five attributes

1. **Treatment** — the treatment condition(s) compared: not just the drug, but dose, schedule, and what counts as the regimen (e.g. monotherapy vs add-on to standard of care). Defines both arms.
2. **Population** — the target patients, operationalized by [[Inclusion and Exclusion Criteria|inclusion/exclusion]]. Can be the whole trial population or a subgroup (a principal stratum is a special population defined by potential ICE behaviour).
3. **Variable / endpoint** — the outcome measured on each patient (e.g. [[Progression-Free Survival (PFS) and Overall Survival (OS)|OS]], change-from-baseline FEV1), including how/when it's measured.
4. **Intercurrent event handling** — for each [[Intercurrent Event|ICE]] type, one of the five strategies below. This is the attribute E9(R1) **added**; it's where most of the thinking goes.
5. **Population-level summary measure** — how individual outcomes are condensed into one comparison number: hazard ratio, difference in means, risk/odds ratio, etc.

## The five intercurrent-event strategies

- **Treatment policy** — use the observed outcome regardless of the ICE; the ICE is part of the treatment "policy". Effect = effect of being **assigned** the regimen, whatever happens after (ITT spirit). Used for OS (you keep following the patient even after they switch/stop). Can't apply to an endpoint that stops existing after the ICE (e.g. on-treatment tumour size after death).
- **Hypothetical** — the value that *would* have been observed had the ICE not happened. Used when you want the effect in a world without the complication — e.g. censor OS at the start of [[Anti-Cancer Therapy Categories in Oncology Trials|subsequent anti-cancer therapy]], asking "effect if no one switched."
- **Composite** — fold the ICE **into** the endpoint definition, treating its occurrence as part of the outcome (often as failure). Used when the ICE itself is a bad outcome — e.g. "treatment failure" = progression OR rescue-medication use OR discontinuation for toxicity.
- **While on treatment** — use only the outcome up to the ICE: the effect during the time the patient is actually on treatment. Used e.g. for symptom/PRO endpoints where only the on-treatment experience is of interest.
- **Principal stratum** — restrict to the subpopulation that would **not** experience the ICE (under either treatment) — e.g. the effect among patients who would adhere, or never need rescue. Hard to identify in practice (stratum membership is partly unobserved).

## Why it changed practice

Before E9(R1), the analysis hid the real target: "ITT vs per-protocol", how dropouts were imputed, how switches/rescue meds were handled — all buried in the SAP, often inconsistent, decided after the fact. The framework forces these choices **up front** and **into the objective**: state the clinical question precisely, including how complications are handled, before choosing a method. **Same data + different ICE strategy = a genuinely different question**, not just a different analysis.

## Worked oncology example — one endpoint, two estimands

Endpoint: **OS**. ICE of interest: **subsequent anti-cancer therapy** (patients on control often switch to effective drugs after progression).

- **Estimand A (treatment-policy)** — keep following OS no matter what they take next. Answers "real-world effect of *starting* on this drug." Switching dilutes the control arm's apparent disadvantage → effect looks smaller.
- **Estimand B (hypothetical)** — censor OS at the switch. Answers "effect if no one had switched" — closer to the drug's intrinsic effect, but relies on censoring assumptions.

Same patients, same OS data, two different numbers — because the ICE attribute differs. That is the whole point of specifying the estimand.
