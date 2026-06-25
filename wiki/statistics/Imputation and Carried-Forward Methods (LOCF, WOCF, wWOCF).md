---
title: "Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)"
type: concept
status: learning
tags: [statistics, trial-conduct]
created: 2026-06-24
updated: 2026-06-24
sources: 1
---

# Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)

**Imputation** (填补/插补) — replacing a missing endpoint value with a substituted one so the subject stays in the analysis. **Single imputation** (单一填补, one filled value, e.g. carry-forward) vs **multiple imputation** (多重填补). In acute pain (急性疼痛) trials the main missing-data drivers are rescue medication (补救镇痛) and early withdrawal; the imputation rule encodes a usually **conservative** assumption.

The carry-forward (结转) family:

- **LOCF** — Last Observation Carried Forward (末次观测结转): fill with the subject's most recent observed value. Assumes the patient froze at their last state; biased if pain would have changed.
- **WOCF** — Worst Observation Carried Forward (最差观测结转): fill with the worst (highest) observed pain value. Conservative — assumes maximum pain. Often used after rescue medication or withdrawal for lack of efficacy. (Sibling: **BOCF** = Baseline OCF, 基线观测结转 — fill with pre-treatment baseline, also conservative and common in pain.)
- **wWOCF** — windowed WOCF (窗口最差观测结转): carry forward the worst observation within a defined **time window** around the missing assessment / before rescue, rather than the single overall worst — a more local, less extreme conservative imputation.

What gets imputed is typically the [[Pain NRS at Rest and with Movement (NRS-R, NRS-M)]] feeding the [[Pain Intensity AUC (0-72h)]] endpoint. The triggers (rescue, [[Withdrawal due to AE or Lack of Efficacy]]) are [[Intercurrent Event]]s — the imputation choice operationalizes the estimand's ICE strategy. Carry-forward methods encode strong [[Missing Data Mechanisms (MCAR, MAR, MNAR)|MNAR]]-type assumptions, now used as conservative sensitivity rather than primary analysis. Part of the [[Acute Pain]] thread.
