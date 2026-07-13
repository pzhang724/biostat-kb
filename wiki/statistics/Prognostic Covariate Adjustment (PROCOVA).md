---
title: "Prognostic Covariate Adjustment (PROCOVA)"
type: concept
status: learning
tags: [statistics]
created: 2026-07-13
updated: 2026-07-13
sources: 1
---

# Prognostic Covariate Adjustment (PROCOVA)

Adjusting the primary analysis for a **prognostic score** (预后评分) — a single number predicting a participant's outcome under control from baseline covariates — to gain **precision** (精度) on the treatment-effect estimate without introducing bias, since randomization already balances treatment arms.

- The prognostic score compresses several baseline covariates into one number, so [[ANCOVA (Analysis of Covariance)]] can adjust for it while spending only one degree of freedom.
- **PROCOVA** (PROgnostic COVariate Adjustment) is the best-known implementation: a pre-specified, pre-trained ML model computes each participant's predicted outcome from baseline data; that score enters the ANCOVA as the sole covariate, "locked" before unblinding (解盲) to avoid data-dredging.
- FDA's 2023 covariate-adjustment guidance generally supports the principle: pre-specified prognostic-covariate adjustment raises power / reduces required sample size without unblinding-related bias.
- Open issue: validating the external prognostic model against the trial's own control arm before relying on it.
