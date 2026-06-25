---
title: "Missing Data Mechanisms (MCAR, MAR, MNAR)"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-25
updated: 2026-06-25
sources: 1
---

# Missing Data Mechanisms (MCAR, MAR, MNAR)

The Rubin/Little three-way classification of **why** data is missing (the **missingness mechanism** / 缺失机制) — it describes the *reason* for missingness, not the data itself, and it determines which analysis method is unbiased.

- **MCAR — Missing Completely At Random (完全随机缺失):** missingness probability depends on *nothing* — neither observed nor unobserved data. Examples: a centrifuge breaks and randomly loses a sample; a patient is lost to follow-up because they moved away for reasons unrelated to the disease; a random subsample is selected for an extra assay. Consequence: complete-case analysis (直接删除) is **unbiased**, only less efficient (smaller n). Rarely truly holds.
- **MAR — Missing At Random (随机缺失):** given the *observed* data, missingness is independent of the unobserved value. Missingness may depend on observed covariates (协变量) or earlier observed measurements, just not directly on the missing value itself. Examples: sicker patients (high observed baseline score) drop out more; patients with high earlier observed pain readings miss later visits more. Consequence: likelihood-based methods (**MMRM**) and **multiple imputation** (多重填补) are valid under MAR — MMRM is valid without explicit imputation.
- **MNAR — Missing Not At Random (非随机缺失):** even given the observed data, missingness still depends on the *unobserved* value itself. Examples: a patient withdraws *because* they got worse this visit and that worse value is never measured; pain too severe → take rescue and leave; worsening-depression patients stop filling in the questionnaire. Consequence: standard MAR methods are **biased**; need **pattern-mixture** models, **delta-adjustment / tipping-point** (倾斜点) analyses, and **control-based imputation** (jump-to-reference, copy-reference / 对照组填补) as sensitivity analyses.

## Things worth knowing

1. **MAR vs MNAR is untestable** from the observed data — the distinction lives precisely in the values you didn't observe. So the convention is: run the **primary analysis under MAR**, then pre-specify **MNAR sensitivity analyses** to check the conclusion is robust.
2. **MCAR is partly testable** (e.g. Little's MCAR test), but rarely credible and rarely truly true.
3. **Missing data ≠ [[Intercurrent Event]].** Under ICH E9(R1) you first fix the [[Estimand]] and the ICE handling strategy; the genuinely *absent* data is then missing data, handled by the analysis method (MMRM / MI / sensitivity). They interact — e.g. a *hypothetical* strategy deliberately creates missingness and then imputes it.
4. **Convention:** primary analysis usually assumes MAR (MMRM or MI); MNAR sensitivity (especially delta-adjusting dropouts unfavourably, or control-based imputation) provides robustness. This is the spirit of FDA / the 2010 NRC missing-data report / ICH E9(R1).
5. **Single imputation** ([[Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)|LOCF/WOCF/BOCF]]) encodes strong, often unrealistic MNAR-type assumptions — now used as conservative *sensitivity*, not as the primary analysis.

Memory hook (口诀): MCAR = pure random (depends on nothing); MAR = depends only on what you can see; MNAR = depends on the unseen value itself.
