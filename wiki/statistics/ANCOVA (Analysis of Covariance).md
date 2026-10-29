---
title: "ANCOVA (Analysis of Covariance)"
type: concept
status: learning
created: 2026-06-24
---

# ANCOVA (Analysis of Covariance)

**Analysis of Covariance** (ANCOVA, 协方差分析) — a linear model for a continuous endpoint that adjusts for **baseline covariates** (基线协变量) and stratification factors (分层因素).

- In acute pain (急性疼痛) trials it is the standard primary-analysis model for the continuous pain endpoint (the [[Pain Intensity AUC (0-72h)]] / SPID, sum of pain intensity differences), adjusting mainly for **baseline pain intensity** (基线疼痛强度).
- Removing baseline variability gives more **precision** (精度). The treatment effect is the adjusted difference between arms, reported as **LS means** (least-squares means, 最小二乘均值).

It runs on whatever endpoint values are left after the [[Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)]] step. Part of the [[Acute Pain]] thread.
