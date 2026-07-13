---
title: "ANCOVA (Analysis of Covariance)"
type: concept
status: learning
tags: [statistics]
created: 2026-06-24
updated: 2026-06-24
sources: 1
---

# ANCOVA (Analysis of Covariance)

**Analysis of Covariance** (协方差分析) — a linear model for a continuous endpoint that adjusts for **baseline covariates** (基线协变量) and stratification factors (分层因素).

- In acute pain (急性疼痛) trials it's the standard primary-analysis model for the continuous pain endpoint (the [[Pain Intensity AUC (0-72h)]] / SPID), adjusting chiefly for **baseline pain intensity** (基线疼痛强度).
- Removing baseline variability gains **precision** (精度); the treatment effect is the adjusted between-arm difference, reported as **LS means** (最小二乘均值, least-squares means).

Runs on whatever endpoint values survive the [[Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)]] step. Part of the [[Acute Pain]] thread.

- Instead of a raw baseline value, the covariate can be a **prognostic score** predicting outcome under control — see [[Prognostic Covariate Adjustment (PROCOVA)]].
