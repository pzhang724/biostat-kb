---
title: "Missing Data Mechanisms (MCAR, MAR, MNAR)"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-25
updated: 2026-06-25
sources: 3
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

## Plain-language model (confirmed)

- **MCAR** = thrown out at random, no signal (depends on nothing).
- **MAR** = an *observed* characteristic explains who is more likely to go missing — conditional on it, missing and non-missing share a distribution. The catch: the "type of person" must be defined by **measured/observed** variables (covariates, earlier visits). If the distinguishing feature was never measured, it surfaces as MNAR. (MCAR is the special case of MAR where that observed set is empty.)
- **MNAR** = no observed characteristic explains it — the real driver is the *unobserved value itself*.

## How a SAP justifies the assumption

You can't *prove* MAR vs MNAR from the data, so the SAP doesn't prove it — it **states a primary assumption, makes it as plausible as possible, then stress-tests departures**:

1. Fix the [[Estimand]] (ICH E9(R1)) and the [[Intercurrent Event|ICE]] strategy first; only the genuinely *absent* data is then handled as missing data.
2. **Primary analysis states MAR explicitly** — MMRM (likelihood-based, uses all observed visits, no explicit imputation) or multiple imputation under MAR. Including strong predictors of *both* outcome and dropout as covariates makes MAR more defensible ("conditional on these, missingness is unrelated to the unseen value").
3. **Design-side support** the SAP leans on: minimize missingness, keep following patients after discontinuation (retrieved dropout / 停药后随访), record reason for withdrawal — per E9(R1) and the 2010 NRC missing-data report.
4. **Pre-specify MNAR sensitivity analyses** — tipping-point / delta-adjustment, reference/control-based imputation (jump-to-reference, copy-reference), pattern-mixture. The conclusion is **robust** if it survives plausible MNAR departures.
5. The SAP narrative reads roughly: *"Primary analysis assumes MAR; given the covariates included and the estimand's ICE strategy this is considered plausible; robustness to MNAR is assessed via tipping-point / reference-based imputation."*

## A worked data example

A longitudinal pain trial, outcome Y = pain NRS 0–10 (lower better), three visits — Baseline, Week-4 (observed), Week-12 (primary endpoint, where missingness happens). Six patients' **true** data:

| Patient | Baseline | Week-4 (obs) | TRUE Week-12 |
|---|---|---|---|
| 1 | 8 | 6 | 4 |
| 2 | 7 | 6 | **9** ← rebounds/worsens (moderate Y4, high Y12) |
| 3 | 9 | 8 | 7 |
| 4 | 6 | 3 | 2 |
| 5 | 8 | 7 | 8 |
| 6 | 7 | 4 | 3 |

True full-sample Week-12 mean = (4+9+7+2+8+3)/6 = **5.5**. Now let Week-12 go missing under each mechanism:

- **MCAR:** drop two at random (say patients 2, 6) — unrelated to any column. Observed = {4,7,2,8}, mean 5.25 ≈ 5.5 → unbiased in expectation, just smaller n.
- **MAR:** missingness driven by *observed* Week-4 — patients with Y4 ≥ 7 drop out → patients 3 (Y4=8) and 5 (Y4=7) missing. Observed Week-12 = {4,9,2,3}, naive mean 4.5 (biased low). **But** patient 2's bad value 9 is still observed (missingness keys on Y4, and Y4=6 didn't trigger), and Y4 predicts Y12, so MMRM/MI conditioning on Y4 imputes high Y12 for the high-Y4 dropouts → **recoverable**.
- **MNAR:** missingness driven by the *unobserved* Week-12 itself — patients with Y12 ≥ 7 skip the visit *because* they truly got worse → patients 2 (9), 3 (7), 5 (8) missing. Observed = {4,2,3}, mean 3.0 (badly biased low → looks like a great result). The catch: patient 2's Y4=6 looks like patients 1/6, yet its unseen Y12=9 hid itself — nothing in the observed data signals it, so MMRM/MI **can't** recover it; you need MNAR sensitivity (delta / control-based).

Same dataset, the one-line difference: **MCAR** — the blank cell relates to no column; **MAR** — the blank is driven by Week-4 (a column you can see), so conditioning on Week-4 makes missing and observed Y12 share a distribution → modellable; **MNAR** — the blank is driven by Week-12 itself (the column you *can't* see), so even at equal Week-4 the worse Y12 disappears → not identifiable from observed data.

Memory hook (口诀): MCAR = pure random (depends on nothing); MAR = depends only on what you can see; MNAR = depends on the unseen value itself.
