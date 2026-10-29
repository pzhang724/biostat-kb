---
title: "Estimand"
type: concept
status: learned
created: 2026-06-22
---

# Estimand

An **estimand (估计目标)** is an exact description of **what is being estimated** — the target of estimation that makes the trial **objective** and the statistical **analysis** line up. It answers "what treatment effect, in whom, on what outcome, and how complications are handled" *before* a method is chosen or any analysis is run. Formalized by **ICH E9(R1)** (the addendum, 增补, to E9) and pre-specified in the protocol/SAP (statistical analysis plan, 统计分析计划).

## The estimation chain

E9(R1) sets out an explicit chain:

- **Objective** — the clinical question in words ("does drug A make survival longer than B?").
- **Estimand** — that question made exact through the five attributes: *what* is being estimated.
- **Estimator (估计量)** — the statistical method used to estimate it (e.g. Cox model, MMRM).
- **Estimate (估计值)** — the actual number produced (e.g. HR, hazard ratio 风险比, = 0.72).

Plus **sensitivity analysis (敏感性分析)** — separate analyses under *different assumptions* about the **same** estimand, to test robustness (稳健性). (Different from a **supplementary analysis** (补充分析), which targets a *different* estimand.)

The key shift: choose the estimand **from** the clinical question, then choose the estimator to match — not "run the standard analysis and see what it estimates."

## The five attributes

1. **Treatment** — the treatment condition(s) compared: not just the drug, but dose, schedule, and what counts as the regimen (e.g. monotherapy, 单药, vs add-on to standard of care, 在标准治疗上加用). Defines both arms.
2. **Population** — the target patients, put into practice by [[Inclusion and Exclusion Criteria|inclusion/exclusion]]. Can be the whole trial population or a subgroup (a principal stratum is a special population defined by how patients would behave with respect to an ICE).
3. **Variable / endpoint** — the outcome measured on each patient (e.g. [[Progression-Free Survival (PFS) and Overall Survival (OS)|OS]], change from baseline in FEV1), including how/when it is measured.
4. **Intercurrent event handling** — for each type of [[Intercurrent Event|ICE]] (intercurrent event, 伴发事件), one of the five strategies below. This is the attribute that E9(R1) **added**; most of the thinking goes here.
5. **Population-level summary measure** — how the outcomes of individuals are reduced to one comparison number: hazard ratio, difference in means, risk/odds ratio, etc.

## The five intercurrent-event strategies — plain version

Anchor on **one patient**: a control-arm patient who, after progression, **switches** to another cancer drug (a classic ICE), and later dies. Their OS is "polluted" by the switch. Each strategy is just a different answer to *"what do we do with this patient?"*

| Strategy | Plain idea (what you do with the patient) | Typically used for | What the math assumes |
|---|---|---|---|
| **Treatment policy** | Keep their real death time; ignore that they switched — count everything as it is. | Hard regulatory endpoints like [[Progression-Free Survival (PFS) and Overall Survival (OS)\|OS]], where what happens after the ICE counts; the default ITT-style (intention-to-treat) primary. | Almost nothing beyond randomization + administrative censoring (管理性删失) — analyze the observed data as it is. Robust, but the effect is **diluted** (稀释) by what patients do after the ICE. |
| **Hypothetical** | Pretend the switch never happened — censor at the switch, and rebuild "what their OS *would* have been." | Removing an ICE that you don't want to credit/blame on the drug ([[Anti-Cancer Therapy Categories in Oncology Trials\|subsequent therapy]], rescue meds). | Censoring at the ICE is **non-informative (无信息删失) / MAR (随机缺失)** — the censored patient's future looks like that of comparable patients still at risk. It cannot be tested — and everything rests on this assumption. |
| **Composite** | Count the switch *itself* as an event/failure — build it into the endpoint. | When the ICE is itself a bad outcome (stopping for toxicity, needing rescue). | Few statistical assumptions — nothing goes missing (the ICE is observed); the real assumption is the **clinical judgment** that the ICE = failure. |
| **While on treatment** | Only use the outcome up to the switch; ignore everything after it. | Symptom / PRO / QoL (quality of life) endpoints, where only the experience on treatment matters. | That the **on-treatment window** (which differs between patients) *is* the intended quantity — different durations by design, not bias. |
| **Principal stratum** | Only analyze patients who **would not have switched at all** (in either arm). | The effect among adherers/tolerators (依从/耐受者); complier (依从者) effects; vaccine efficacy among people who would get infected. | The hidden (latent, 潜在) stratum is only partly observed → it needs strong identifying assumptions (**monotonicity 单调性** / exclusion restriction, CACE/IV-style: complier average causal effect / instrumental variable 工具变量). The most assumption-heavy; often only gives bounds (界). |

**The assumption burden goes up**: treatment-policy (lightest) → composite / while-on-treatment (modest) → hypothetical (strong, untestable MAR) → principal stratum (strongest, partly not identifiable).

## Why it changed practice

Before E9(R1), the analysis hid the real target: "ITT vs per-protocol" (符合方案), how dropouts were imputed, how switches/rescue meds were handled — all buried in the SAP, often inconsistent, and decided after the fact. The framework forces these choices to be made **up front** and **inside the objective**: state the clinical question exactly, including how complications are handled, before choosing a method. **Same data + a different ICE strategy = a really different question**, not just a different analysis.

## Worked oncology example — one endpoint, two estimands

Endpoint: **OS**. The ICE of interest: **subsequent anti-cancer therapy** (patients on control often switch to effective drugs after progression).

- **Estimand A (treatment-policy)** — keep following OS whatever they take next. It answers "the real-world effect of *starting* on this drug." Switching makes the control arm's disadvantage look smaller → the effect looks smaller.
- **Estimand B (hypothetical)** — censor OS at the switch. It answers "the effect if no one had switched" — closer to the drug's own (intrinsic) effect, but it relies on assumptions about the censoring.

Same patients, same OS data, two different numbers — because the ICE attribute is different. That is the whole point of specifying the estimand.

## One patient, all five strategies

A realistic **synthetic** (合成的) patient (real patient-level data never goes into this wiki). A control-arm mCRPC patient, **OS** endpoint, with a switch ICE:

| Day | Event |
|---|---|
| 0 | Randomized to the control arm, starts treatment |
| 185 | Radiographic progression; **stops** study treatment |
| 210 | Starts [[Anti-Cancer Therapy Categories in Oncology Trials\|subsequent anti-cancer therapy]] — **the switch (ICE)** |
| 540 | Dies |
| 600 | Database cutoff (数据截止) |

OS = time from randomization to death. How each strategy records **this one patient's** `(time, status)`:

| Strategy | This patient's OS record | Why |
|---|---|---|
| **Treatment policy** | `540, event` | The death counts as it is; the switch is ignored — "whatever happens after" is included. |
| **Hypothetical** | `210, censored` | Pretend there was no switch: censor at it; survival after day 210 "without a switch" is rebuilt from comparable patients still at risk. |
| **Composite** | `210, event` | Endpoint = death OR switch, whichever comes first → the switch *is* the failure; dying later does not matter. |
| **While on treatment** | `185, censored` | The death happened **off** treatment (stopped on day 185) → censor at discontinuation. (Artificial for OS — it fits symptom/PRO endpoints better — but it shows how it works.) |
| **Principal stratum** | *excluded* | This patient *did* switch → not in the "would not switch" stratum → dropped from the analysis set. |

**One patient**, but the analysis "sees" `540-event / 210-censored / 210-event / 185-censored / nothing` depending on the strategy — five different inputs that push five different effect estimates. That is why the estimand (especially the ICE attribute) must be fixed *before* any analysis.

## Is the hypothetical estimand really just `210, censored`?

In the dataset, yes — the row *is* `210, censored`. But that is only **bookkeeping** (记账). Feeding it straight into a standard KM/Cox (Kaplan–Meier / Cox model) is the **naive** version, and it quietly assumes the censoring is **non-informative / MAR (随机缺失)**: that patient 07, after day 210, would die at the same rate as comparable patients still at risk who did **not** switch.

Why that is doubtful: patient 07 switched **because** they progressed (day 185). Switching is triggered by worsening disease → switchers are a selected, **sicker** subset, so their true survival without a switch is shorter than that of the average peer still at risk. So the censoring time carries prognostic information = **informative censoring (信息性删失)** — exactly what KM/Cox assume does not happen. Naive censoring is **too optimistic** about the switcher's counterfactual (反事实) survival → biased.

So `210, censored` is only step 1. A credible (可信的) hypothetical estimand needs an estimator that **corrects** for the informative censoring:

- **IPCW (inverse-probability-of-censoring weighting, 逆删失概率加权)** — model P(not yet switched | time-varying covariates); give more weight to similar patients who did not switch, so they stand in for the censored ones. It assumes all the drivers of switching are **measured** (no unmeasured confounding of the switch).
- **RPSFTM / IPE (rank-preserving structural failure time model / iterative parameter estimation)** — structural models that "remove" the survival time that the switch to an effective therapy bought, and rebuild the counterfactual survival without a switch. Standard adjustments for **treatment switching** in oncology.

Because the MAR bet **cannot be tested**, you stress-test it with a **sensitivity analysis (敏感性分析)** — e.g. a **tipping-point / delta-adjustment (delta 调整)**: penalize the assumed survival of the censored patients more and more until the conclusion flips, and report the delta at which it tips. If an implausibly large penalty is needed ⇒ the result is robust.

**Bottom line**: `210, censored` is the data bookkeeping; whether the hypothetical estimand is credible depends entirely on **how you treat that censoring afterwards** — naive KM = a strong MAR bet; IPCW / RPSFTM = adjusted; plus a sensitivity analysis, so the conclusion does not depend on the part that cannot be tested.
