---
title: "Estimand"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-22
updated: 2026-06-22
sources: 3
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

## The five intercurrent-event strategies — plain version

Anchor on **one patient**: a control-arm patient who, after progression, **switches** to another cancer drug (a classic ICE), then later dies. Their OS is "polluted" by the switch. Each strategy is just a different answer to *"what do we do with this patient?"*

| Strategy | Plain idea (what you do with the patient) | Typically used for | What the math assumes |
|---|---|---|---|
| **Treatment policy** | Keep their real death time; ignore that they switched — count everything as-is. | Hard regulatory endpoints like [[Progression-Free Survival (PFS) and Overall Survival (OS)\|OS]] where post-ICE reality counts; the default ITT-style primary. | Almost none beyond randomization + administrative censoring — analyze observed data as-is. Robust, but the effect is **diluted** by post-ICE behaviour. |
| **Hypothetical** | Pretend the switch never happened — censor at the switch, reconstruct "what their OS *would* have been." | Stripping out an ICE you don't want to credit/blame on the drug ([[Anti-Cancer Therapy Categories in Oncology Trials\|subsequent therapy]], rescue meds). | Censoring at the ICE is **non-informative (无信息删失) / MAR (随机缺失)** — the censored patient's future looks like comparable patients still at risk. Untestable — the load-bearing assumption. |
| **Composite** | Count the switch *itself* as an event/failure — fold it into the endpoint. | When the ICE is itself a bad outcome (discontinuation for toxicity, needing rescue). | Little statistical assumption — nothing goes missing (the ICE is observed); the real assumption is the **clinical judgment** that the ICE = failure. |
| **While on treatment** | Only use the outcome up to the switch; ignore everything after. | Symptom / PRO / QoL endpoints where only the on-treatment experience matters. | That the (patient-varying) **on-treatment window** *is* the intended quantity — different durations by design, not bias. |
| **Principal stratum** | Only analyze patients who **wouldn't have switched at all** (under either arm). | Effect among adherers/tolerators; complier (依从者) effects; vaccine efficacy among the would-be-infected. | The latent stratum is only partly observed → needs strong identifying assumptions (**monotonicity 单调性** / exclusion-restriction, CACE/IV-style). Most assumption-heavy; often only bounds. |

**Assumption burden rises**: treatment-policy (lightest) → composite / while-on-treatment (modest) → hypothetical (strong, untestable MAR) → principal stratum (strongest, partly unidentified).

## Why it changed practice

Before E9(R1), the analysis hid the real target: "ITT vs per-protocol", how dropouts were imputed, how switches/rescue meds were handled — all buried in the SAP, often inconsistent, decided after the fact. The framework forces these choices **up front** and **into the objective**: state the clinical question precisely, including how complications are handled, before choosing a method. **Same data + different ICE strategy = a genuinely different question**, not just a different analysis.

## Worked oncology example — one endpoint, two estimands

Endpoint: **OS**. ICE of interest: **subsequent anti-cancer therapy** (patients on control often switch to effective drugs after progression).

- **Estimand A (treatment-policy)** — keep following OS no matter what they take next. Answers "real-world effect of *starting* on this drug." Switching dilutes the control arm's apparent disadvantage → effect looks smaller.
- **Estimand B (hypothetical)** — censor OS at the switch. Answers "effect if no one had switched" — closer to the drug's intrinsic effect, but relies on censoring assumptions.

Same patients, same OS data, two different numbers — because the ICE attribute differs. That is the whole point of specifying the estimand.
