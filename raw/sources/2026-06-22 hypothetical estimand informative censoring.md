From chat, 2026-06-22

Q: 你挖一下我看看，不直接用 210, censored 吗？(dig into the hypothetical strategy — don't we just directly use 210, censored?)

A:
- Yes — in the dataset the row IS `210, censored`. That part is just bookkeeping. The catch: feeding that straight into a standard KM/Cox is the NAIVE version, and it silently assumes the censoring is non-informative (MAR): that patient 07, after day 210, would die at the same rate as comparable patients still at risk who did NOT switch.
- Why that's suspect: 07 switched BECAUSE they progressed (day 185). Switching is triggered by worsening disease → switchers are a selected, SICKER subset. Their true "no-switch" survival is shorter than the average still-at-risk peer's. So the censoring time carries prognostic information = informative censoring. KM/Cox's non-informative-censoring assumption is violated → biased estimate (naive censoring is optimistic about the switcher's counterfactual survival).
- So "directly use 210, censored" is only step 1. A proper hypothetical estimand needs an estimator that CORRECTS for the informativeness:
  - IPCW (inverse-probability-of-censoring weighting): model P(not yet switched | time-varying covariates); upweight similar not-switched patients to stand in for the censored ones. Assumes all drivers of switching are measured (no unmeasured confounding of the switch).
  - RPSFTM / IPE (rank-preserving structural failure time model / iterative parameter estimation): structural models that "remove" the survival time the switch-to-effective-therapy bought, reconstructing the counterfactual no-switch survival. Standard oncology treatment-switching adjustments.
- Sensitivity analysis (the MAR assumption is untestable, so you stress-test it):
  - Tipping-point / delta-adjustment: progressively penalize the censored patients' assumed survival (a delta) until the conclusion flips; report the delta at which it tips. If you need an implausibly large penalty to overturn the result, it's robust.
- Bottom line: `210, censored` is the data bookkeeping; the hypothetical estimand's credibility lives entirely in HOW you treat that censoring afterwards — naive KM = a strong MAR bet; IPCW / RPSFTM = adjusted; plus a sensitivity analysis to show the conclusion doesn't hinge on the untestable part.
