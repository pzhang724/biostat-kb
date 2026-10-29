---
title: "Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)"
type: concept
status: learning
created: 2026-06-24
---

# Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)

**Imputation** (填补/插补) — replacing a missing endpoint value with a substitute value, so that the subject stays in the analysis. **Single imputation** (单一填补; one filled value, e.g. carry-forward) vs **multiple imputation** (多重填补). In acute pain (急性疼痛) trials the main causes of missing data are rescue medication (补救镇痛) and early withdrawal; the imputation rule builds in an assumption that is usually **conservative** (保守的).

The carry-forward (结转) family:

- **LOCF** — Last Observation Carried Forward (末次观测结转): fill with the subject's most recent observed value. It assumes the patient stayed frozen at their last state; biased if the pain would have changed.
- **WOCF** — Worst Observation Carried Forward (最差观测结转): fill with the worst (highest) observed pain value. Conservative — it assumes maximum pain. Often used after rescue medication or withdrawal for lack of efficacy. (A close relative: **BOCF** = Baseline Observation Carried Forward, 基线观测结转 — fill with the baseline value before treatment; also conservative and common in pain.)
- **wWOCF** — windowed WOCF (窗口最差观测结转): carry forward the worst observation within a defined **time window** around the missing assessment / before rescue, instead of the single worst value overall — a more local, less extreme conservative imputation.

What gets imputed is usually the [[Pain NRS at Rest and with Movement (NRS-R, NRS-M)]] that feeds the [[Pain Intensity AUC (0-72h)]] endpoint. The triggers (rescue, [[Withdrawal due to AE or Lack of Efficacy]]) are [[Intercurrent Event]]s — the imputation choice puts the estimand's ICE (intercurrent event) strategy into practice. Carry-forward methods build in strong [[Missing Data Mechanisms (MCAR, MAR, MNAR)|MNAR]]-type assumptions, and are now used as conservative sensitivity analyses rather than as the primary analysis. Part of the [[Acute Pain]] thread.
