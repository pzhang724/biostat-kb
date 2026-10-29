---
title: "Missing Data Mechanisms (MCAR, MAR, MNAR)"
type: concept
status: learned
created: 2026-06-25
---

# Missing Data Mechanisms (MCAR, MAR, MNAR)

The Rubin/Little three-way classification of **why** data is missing (the **missingness mechanism**, 缺失机制). It describes the *reason* for the missingness, not the data itself, and it decides which analysis method is unbiased.

- **MCAR — Missing Completely At Random (完全随机缺失):** the probability of being missing depends on *nothing* — neither on observed nor on unobserved data. Examples: a centrifuge (离心机) breaks and loses a sample at random; a patient is lost to follow-up because they moved away for reasons that have nothing to do with the disease; a random subsample is picked for an extra assay. Result: complete-case analysis (直接删除) is **unbiased**, just less efficient (smaller n). It is rarely really true.
- **MAR — Missing At Random (随机缺失):** given the *observed* data, missingness does not depend on the unobserved value. Missingness may depend on observed covariates (协变量) or on earlier observed measurements, just not directly on the missing value itself. Examples: sicker patients (high observed baseline score) drop out more; patients with high earlier observed pain readings miss later visits more. Result: likelihood-based methods (基于似然的方法; **MMRM**, mixed model for repeated measures 重复测量混合模型) and **multiple imputation** (多重填补) are valid under MAR — MMRM is valid without explicit imputation.
- **MNAR — Missing Not At Random (非随机缺失):** even given the observed data, missingness still depends on the *unobserved* value itself. Examples: a patient withdraws *because* they got worse at this visit, and that worse value is never measured; pain is too severe → they take rescue medication and leave; patients whose depression gets worse stop filling in the questionnaire. Result: standard MAR methods are **biased**; you need **pattern-mixture** models (模式混合模型), **delta-adjustment / tipping-point** (倾斜点) analyses, and **control-based imputation** (jump-to-reference, copy-reference / 对照组填补) as sensitivity analyses.

## Things worth knowing

1. **MAR vs MNAR cannot be tested** from the observed data — the difference lives exactly in the values you did not observe. So the usual approach is: run the **primary analysis under MAR**, then pre-specify **MNAR sensitivity analyses** to check that the conclusion is robust (稳健).
2. **MCAR can be partly tested** (e.g. Little's MCAR test), but it is rarely believable and rarely really true.
3. **Missing data ≠ [[Intercurrent Event]].** Under ICH E9(R1) you first fix the [[Estimand]] and the ICE handling strategy; the data that is really *absent* is then missing data, handled by the analysis method (MMRM / MI, multiple imputation / sensitivity). The two interact — e.g. a *hypothetical* strategy creates missingness on purpose and then imputes it.
4. **Usual practice:** the primary analysis usually assumes MAR (MMRM or MI); MNAR sensitivity analyses (especially delta-adjusting dropouts in an unfavourable direction, or control-based imputation) show robustness. This is the spirit of FDA / the 2010 NRC (US National Research Council) missing-data report / ICH E9(R1).
5. **Single imputation** ([[Imputation and Carried-Forward Methods (LOCF, WOCF, wWOCF)|LOCF/WOCF/BOCF]]) builds in strong, often unrealistic MNAR-type assumptions — it is now used as a conservative *sensitivity* analysis, not as the primary analysis.

## Plain-language model (confirmed)

- **MCAR** = thrown out at random, no signal (depends on nothing).
- **MAR** = an *observed* characteristic explains who is more likely to go missing — given that characteristic, missing and non-missing values have the same distribution. The catch: the "type of person" must be defined by **measured/observed** variables (covariates, earlier visits). If the feature that separates them was never measured, it shows up as MNAR. (MCAR is the special case of MAR where that observed set is empty.)
- **MNAR** = no observed characteristic explains it — the real driver is the *unobserved value itself*.

## How a SAP justifies the assumption

You cannot *prove* MAR vs MNAR from the data, so the SAP (statistical analysis plan, 统计分析计划) does not prove it. It **states a primary assumption, makes it as believable (plausible) as possible, then stress-tests departures from it**:

1. Fix the [[Estimand]] (ICH E9(R1)) and the [[Intercurrent Event|ICE]] strategy first; only the data that is really *absent* is then handled as missing data.
2. **The primary analysis states MAR explicitly** — MMRM (likelihood-based, uses all observed visits, no explicit imputation) or multiple imputation under MAR. Including strong predictors of *both* the outcome and dropout as covariates makes MAR easier to defend ("given these, missingness is unrelated to the unseen value").
3. **Support from the design** that the SAP relies on: keep missingness as low as possible, keep following patients after they stop treatment (retrieved dropout, 停药后随访), and record the reason for withdrawal — per E9(R1) and the 2010 NRC missing-data report.
4. **Pre-specify MNAR sensitivity analyses** — tipping-point / delta-adjustment, reference/control-based imputation (jump-to-reference, copy-reference), pattern-mixture. The conclusion is **robust** if it holds up under plausible MNAR departures.
5. The SAP text reads roughly like this: *"Primary analysis assumes MAR; given the covariates included and the estimand's ICE strategy this is considered plausible; robustness to MNAR is assessed via tipping-point / reference-based imputation."*

## A worked data example

A longitudinal (纵向) pain trial; outcome Y = pain NRS 0–10 (lower is better); three visits — Baseline, Week-4 (observed), Week-12 (the primary endpoint, where the missingness happens). The **true** data of six patients:

| Patient | Baseline | Week-4 (obs) | TRUE Week-12 |
|---|---|---|---|
| 1 | 8 | 6 | 4 |
| 2 | 7 | 6 | **9** ← rebounds/worsens (moderate Y4, high Y12) |
| 3 | 9 | 8 | 7 |
| 4 | 6 | 3 | 2 |
| 5 | 8 | 7 | 8 |
| 6 | 7 | 4 | 3 |

True Week-12 mean for the full sample = (4+9+7+2+8+3)/6 = **5.5**. Now let Week-12 go missing under each mechanism:

- **MCAR:** drop two patients at random (say patients 2 and 6) — unrelated to any column. Observed = {4,7,2,8}, mean 5.25 ≈ 5.5 → unbiased on average (in expectation), just a smaller n.
- **MAR:** missingness is driven by the *observed* Week-4 — patients with Y4 ≥ 7 drop out → patients 3 (Y4=8) and 5 (Y4=7) are missing. Observed Week-12 = {4,9,2,3}, naive mean 4.5 (biased low). **But** patient 2's bad value 9 is still observed (missingness depends on Y4, and Y4=6 did not trigger it), and Y4 predicts Y12, so MMRM/MI, conditioning on Y4, imputes a high Y12 for the high-Y4 dropouts → **recoverable**.
- **MNAR:** missingness is driven by the *unobserved* Week-12 itself — patients with Y12 ≥ 7 skip the visit *because* they really got worse → patients 2 (9), 3 (7), 5 (8) are missing. Observed = {4,2,3}, mean 3.0 (badly biased low → it looks like a great result). The catch: patient 2's Y4=6 looks like patients 1 and 6, yet its unseen Y12=9 hid itself. Nothing in the observed data signals it, so MMRM/MI **cannot** recover it; you need MNAR sensitivity analyses (delta / control-based).

Same dataset; the difference in one line: **MCAR** — the blank cell relates to no column; **MAR** — the blank is driven by Week-4 (a column you can see), so conditioning on Week-4 gives missing and observed Y12 the same distribution → it can be modelled; **MNAR** — the blank is driven by Week-12 itself (the column you *cannot* see), so even at the same Week-4 the worse Y12 disappears → it cannot be identified (不可识别) from the observed data.

Memory hook (口诀): MCAR = pure random (depends on nothing); MAR = depends only on what you can see; MNAR = depends on the unseen value itself.
