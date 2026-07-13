---
title: "Prognostic Covariate Adjustment (PROCOVA)"
type: concept
status: learning
tags: [statistics]
created: 2026-07-13
updated: 2026-07-13
sources: 3
---

# Prognostic Covariate Adjustment (PROCOVA)

Adjusting the primary analysis for a **prognostic score** (预后评分) — a single number predicting a participant's outcome under control from baseline covariates — to gain **precision** (精度) on the treatment-effect estimate without introducing bias, since randomization already balances treatment arms.

- The prognostic score compresses several baseline covariates into one number, so [[ANCOVA (Analysis of Covariance)]] can adjust for it while spending only one degree of freedom.
- **PROCOVA** (PROgnostic COVariate Adjustment) is the best-known implementation: a pre-specified, pre-trained ML model computes each participant's predicted outcome from baseline data; that score enters the ANCOVA as the sole covariate, "locked" before unblinding (解盲) to avoid data-dredging.
- FDA's 2023 covariate-adjustment guidance generally supports the principle: pre-specified prognostic-covariate adjustment raises power / reduces required sample size without unblinding-related bias.
- Open issue: validating the external prognostic model against the trial's own control arm before relying on it.

## Operationalizing in a real trial

- **Planning (pre-trial)**: written into protocol/SAP; assemble historical/external control-arm data (same population, endpoint, covariates); train and **freeze** the prognostic model on that historical data before any new-trial data exist — architecture, covariates, training data, and freeze date/version all documented ahead of time. Sample-size/power planning uses the model's expected predictive accuracy to project the precision gain.
- **Conduct**: the trial collects the same baseline covariates the locked model needs; an independent, blinded team scores each participant with the frozen model before unblinding — walled off from anyone with unblinded-data access.
- **Analysis**: the pre-specified ANCOVA (treatment + locked score, no re-fitting) runs as the primary analysis exactly as written in the SAP, typically alongside a standard/unadjusted analysis as a consistency check.
- The core safeguard regulators care about is this "wall": proof the model was frozen and documented before it ever touched the live trial's data.

## Robustness to model miscalibration

- Yes, the frozen model can drift from reality (e.g. a model trained on an older natural-history cohort systematically over/under-predicts if standard-of-care or the enrolled population has since shifted).
- Key property: because randomization is unaffected, the treatment-effect **point estimate stays unbiased/consistent** even if the covariate (the score) is a bad predictor — this is a classical robustness property of ANCOVA covariate adjustment in RCTs. Only the **precision gain** is at risk — a badly miscalibrated score just yields less variance reduction than planned (worst case, close to an unadjusted analysis), not bias.
- Worked example: a model trained on a historical ALS natural-history registry to predict control-arm functional decline. If the new trial's actual control arm declines slower (e.g. background therapy has changed since the historical data), the frozen model overestimates decline — a trial sized for an expected 30% variance reduction might only realize ~10%, i.e. underpowered relative to plan, but the treatment-effect estimate itself is still correct.
- Mitigation: pre-plan a blinded interim check of the score's correlation with the pooled (unblinded-by-arm) outcome to see if it still tracks reality as expected; if it diverges, a pre-specified contingency (e.g. blinded sample-size re-estimation, fallback to standard covariate adjustment) is triggered — the contingency rule itself must also be pre-specified.
