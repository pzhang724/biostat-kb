---
title: "Oncology Therapeutic Radiopharmaceuticals — Dosage Optimization (FDA Draft Guidance)"
type: concept
status: learned
tags: [regulatory, medical, statistics]
created: 2026-06-20
updated: 2026-06-20
sources: 1
---

# Oncology Therapeutic Radiopharmaceuticals — Dosage Optimization (FDA Draft Guidance)

FDA **draft guidance** (放射性药物治疗剂量优化指南), Aug 2025, OCE + CDER; nonbinding. Helps sponsors identify an **optimized dosage** for **radiopharmaceutical therapies (RPTs, 放射性药物治疗 / 放射配体治疗)** in oncology, *during clinical development, before* a marketing application. The RPT-specific counterpart to the Aug-2024 general oncology dosage-optimization guidance (FDA **Project Optimus**); see [[MTD and RP2D#Optimal treatment regimen]].

- **Scope** — systemically administered products with **α / β / γ decay** (α/β/γ 发射体). *Does not* cover: first-in-human starting-activity selection (→ 2019 Nonclinical guidance), dosimetry-software choice, fixed-vs-personalized-dosimetry dosing, theranostic co-development.
- **Key definitions** — *dosage* = **administered activity (给药活度)** + **schedule** (interval between administrations + number of cycles). *Administered activity* = the radiation dose of the radiopharmaceutical. **Optimized dosage** = the activity+schedule that maximizes **benefit/risk (获益-风险)** while minimizing toxicity — *not necessarily the maximum*.

## Background — the core problem

- An RPT is a **hybrid**: like [[Radiopharmaceutical Therapy (RPT) and External Beam Radiation Therapy (EBRT)|EBRT]] it kills via ionizing radiation, like a systemic drug it has **biodistribution (生物分布)** and pharmacologic targeting.
- Historically RPT activity was capped to respect **EBRT-derived organ absorbed-dose limits (外照射来源的器官吸收剂量限值)**. But differences in **dose rate (剂量率)** and radiation distribution make EBRT limits poorly applicable → the optimized RPT dosage may be **greater *or* less** than an EBRT-limited one; limits also differ by isotope/product. Capping everything at EBRT tolerances blocks determining **RPT-specific organ tolerances** and the full dose-response.
- Standard dose-escalation has a finite **[[Dose-Limiting Toxicity (DLT)|DLT]] window** focused on acute/subacute toxicity. RPTs cause **long-term / delayed toxicity (长期/迟发毒性)** that depends on **cumulative administered activity (累积给药活度)** — renal toxicity, [[Xerostomia|xerostomia]], xerophthalmia (干眼), bone-marrow failure — not captured in the DLT window, so DLT-window overdose control can't prevent **cumulative overdosing**. Long-term tox → adverse reactions, inability to receive later therapy, harm to endpoints like [[Progression-Free Survival (PFS) and Overall Survival (OS)|OS]].
- A **cumulative-exposure limit** is the standard tool for cumulative-dose toxicities (EBRT/NTCP models, platinum → renal/neuropathy/hearing, anthracycline → cardiac). Fixed treatment durations + optimization help define RPT organ tolerances while managing risk.
- **[[MTD and RP2D|MTD]] not assumed optimal** — chemo used MTD; targeted drugs often dose below it; RPTs share both. Many RPTs' MTD is unknown (from EBRT-tolerance adherence). Dosage for registrational trials should rest on the **totality of data across a range of dosages**, not solely MTD or organ tolerances.

## III. Considerations for dosage optimization

Exceeding EBRT tolerances / prior RPT dosages **may** be studied with adequate rationale that the optimized dose can't be found lower; justify with clinical data; **discuss with FDA in formal meetings, early**. Build in four safeguards:

### A. Participant population
- MTD-defining or EBRT-exceeding trials → **participants with limited life expectancy** from cancer, for whom delayed permanent organ failure is an acceptable risk (disease-specific; discuss with division).
- **Lower-risk** participants (earlier-stage, curable, long natural history) should *not* receive dosages/organ doses above those characterized in higher-risk participants with adequate follow-up — they have more time to develop long-term toxicity; lower dosages may be appropriate, may need further optimization.
- **Prior EBRT** — eligibility by clinical variables (baseline toxicities, organ function); don't exclude solely for prior EBRT unless specific **co-localization** of toxicity concern.
- **Prior RPT** — eligibility by clinical variables + prior absorbed doses; prespecify a **max cumulative absorbed dose to critical organs** (prior + current), justify exceedances; consider **separate cohorts** for prior-RPT vs RPT-naïve.

### B. Trial design
- Generally a **fixed number of cycles**; pre-specify a **cap on cumulative administered activity** (and organ absorbed doses), justified by RPT-specific data; product/indication-specific, revisable. **High uncertainty** (novel/no data, α-emitters, heterogeneous sub-organ distribution, prior-RPT additive tox) → lower starting cap; **low uncertainty** (established product, high-energy β-emitters, homogeneous distribution, RPT-naïve) → more flexibility.
- First-in-human dosage generally **≤ EBRT limits** (EBRT literature as the starting point, per 2019 guidance).
- If max activity shows limited toxicity **and** preliminary efficacy (tumor absorbed dose / clinical) suggests the optimized dosage isn't reached → request a meeting to discuss **protocol amendments** for further escalation; bring safety, preliminary efficacy dosimetry, [[Pharmacokinetics (PK)|PK]].
- Registrational dosage selection uses **all data** — safety, preliminary efficacy, PK/PD, PROs; MTD if established; estimated organ tolerances; tumor + normal-organ dosimetry. Specifically:
  - A **1-cycle DLT period** may suffice to escalate, but recommended dosage needs longer-term safety; if multiple cycles intended, 1-cycle data is insufficient → need **multi-cycle, multi-dose-level** data for cumulative tox; safety follow-up should match the anticipated-toxicity timeframe and/or median life expectancy.
  - **Backfill cohorts (回填队列)** — add dose levels or more participants to existing cohorts for extra safety/activity data + longer follow-up.
  - **Compare multiple dosages, incl. randomized dose-response trials (随机剂量-反应试验)** before selecting — the optimized dosage may not be the highest dose; especially important when exceeding EBRT tolerances or at the MTD; size for adequate activity/safety/tolerability per dose.
- Consider cumulative activity from prior RPT when choosing levels (lower dosages may suit prior-RPT participants).
- **Informed consent** should convey the risk of long-term / late-onset / cumulative radiation toxicity and that it may be poorly characterized early.

### C. Safety monitoring
- Onset may be **delayed months–years** → monitor a pre-specified list of **late radiation adverse events of special interest (rAESI, 放射相关特别关注不良事件)** for **≥ 5 years** after last dose (or until death if life expectancy < 5 yr); the rAESI list + schedule should reflect drug-specific dosimetry + a detailed radiation-safety analysis plan; may become a **postmarketing requirement**. (cf. [[Adverse Event of Special Interest (AESI)]])
- For prior radiotherapy (EBRT/RPT): **record dose to critical organs**; correlate organ-specific safety with prior + cumulative absorbed dose.
- Consider exploratory **early biomarkers** of delayed radiation toxicity; **bank** blood/urine/tissue for future validation.

### D. Dosimetry for dosage-optimization trials
- Per **21 CFR 312.23(a)(10)(ii)**, phase 1 studies of radioactive drugs **must** obtain sufficient data for **[[Dosimetry|dosimetry]]** calculations. Each novel molecular entity → dosimetry studies **early**; gives radiobiological context for efficacy/safety. **Direct imaging of the therapeutic product preferred** (e.g. [[Lutetium-177 (177Lu)|¹⁷⁷Lu]] self-images via γ); supplement with surrogate analogs only when direct imaging isn't possible.
- IND built on non-IND data lacking dosimetry → obtain dosimetry in the IND trial (dedicated imaging study or **lead-in cohort**) to verify dosage assumptions; meet FDA before enrolling large numbers.
- **α-emitters** — direct imaging when possible, else surrogate-imaging dosimetry + PK modeling; consider **micro-scale dosimetry (微剂量学)** for short range + heterogeneous deposition → sub-organ absorbed dose.
- Dosimetry protocols must detail imaging acquisition + processing and every step to organ absorbed dose: camera/activity calibration, organ/tumor segmentation, time-activity fitting, software, models/assumptions; **bone-marrow dosimetry** per expert consensus (EANM); describe small-organ uptake (salivary, lacrimal, pituitary).
- Organ absorbed doses should carry **estimated uncertainties** (systematic + statistical).
- Justify dose-escalation with upper-limit estimates for cumulative activity, optionally via **biological effective dose (BED, 生物有效剂量)** tied to a defined clinical effect; **report both absorbed dose and BED** — BED-based dose-response aids cross-study aggregation toward RPT-specific organ tolerances.

---
Part of [[Oncology]]. Related: [[MTD and RP2D]] · [[Dosimetry]] · [[Lutetium-177 (177Lu)]] · [[Dose-Limiting Toxicity (DLT)]] · [[Adverse Event of Special Interest (AESI)]] · [[Xerostomia]] · [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]] · [[PSMA PET-CT]].
