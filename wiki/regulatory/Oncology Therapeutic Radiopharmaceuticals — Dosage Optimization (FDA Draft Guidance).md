---
title: "Oncology Therapeutic Radiopharmaceuticals — Dosage Optimization (FDA Draft Guidance)"
type: concept
status: learned
created: 2026-06-20
---

# Oncology Therapeutic Radiopharmaceuticals — Dosage Optimization (FDA Draft Guidance)

FDA **draft guidance** (放射性药物治疗剂量优化指南), Aug 2025, from OCE (Oncology Center of Excellence) + CDER (Center for Drug Evaluation and Research); not binding (nonbinding, 无约束力). It helps sponsors find an **optimized dosage** for **radiopharmaceutical therapies (RPTs, 放射性药物治疗 / 放射配体治疗)** in oncology, *during clinical development, before* a marketing application. It is the RPT-specific partner of the Aug-2024 general oncology dosage-optimization guidance (FDA **Project Optimus**); see [[MTD and RP2D#Optimal treatment regimen]].

- **Scope** — products given systemically, with **α / β / γ decay** (α/β/γ 发射体). It does *not* cover: choosing the starting activity for first-in-human (首次人体) trials (→ the 2019 Nonclinical guidance), the choice of dosimetry software, fixed vs personalized-dosimetry dosing, or theranostic co-development (诊疗一体化联合开发).
- **Key definitions** — *dosage* = **administered activity (给药活度)** + **schedule** (the interval between administrations + the number of cycles). *Administered activity* = the radiation dose of the radiopharmaceutical. **Optimized dosage** = the activity + schedule that gives the best **benefit/risk (获益-风险)** while keeping toxicity as low as possible — *not necessarily the maximum*.

## Background — the core problem

- An RPT is a **hybrid** (混合体): like [[Radiopharmaceutical Therapy (RPT) and External Beam Radiation Therapy (EBRT)|EBRT]] it kills cells with ionizing radiation; like a systemic drug it has **biodistribution (生物分布)** and pharmacologic targeting.
- In the past, RPT activity was capped to stay within **organ absorbed-dose limits that came from EBRT (外照射来源的器官吸收剂量限值)**. But differences in **dose rate (剂量率)** and in how the radiation is distributed mean that EBRT limits fit poorly → the optimized RPT dosage may be **higher *or* lower** than one limited by EBRT; the limits also differ by isotope/product. Capping everything at EBRT tolerances (耐受限值) blocks finding **organ tolerances specific to RPTs** and the full dose-response.
- Standard dose escalation has a limited **[[Dose-Limiting Toxicity (DLT)|DLT]] window** that focuses on acute/subacute (急性/亚急性) toxicity. RPTs cause **long-term / delayed toxicity (长期/迟发毒性)** that depends on the **cumulative administered activity (累积给药活度)** — kidney toxicity, [[Xerostomia|xerostomia]], xerophthalmia (干眼症), bone-marrow failure (骨髓衰竭) — which the DLT window does not capture. So overdose control based on the DLT window cannot prevent **cumulative overdosing**. Long-term toxicity → adverse reactions, being unable to receive later therapy, and harm to endpoints like [[Progression-Free Survival (PFS) and Overall Survival (OS)|OS]].
- A **limit on cumulative exposure** is the standard tool for toxicities from a cumulative dose (EBRT/NTCP models, normal tissue complication probability; platinum 铂类 → kidney/nerve damage/hearing; anthracycline 蒽环类 → heart). Fixed treatment durations + optimization help define RPT organ tolerances while managing the risk.
- **The [[MTD and RP2D|MTD]] is not assumed to be optimal** — chemotherapy used the MTD; targeted drugs are often dosed below it; RPTs share features of both. For many RPTs the MTD is unknown (because they stayed within EBRT tolerances). The dosage for registrational (注册性) trials should rest on the **totality of data across a range of dosages**, not only on the MTD or organ tolerances.

## III. Considerations for dosage optimization

Going beyond EBRT tolerances / earlier RPT dosages **may** be studied, with a good rationale that the optimized dose cannot be found at a lower level; justify it with clinical data; **discuss it with FDA in formal meetings, early**. Build in four safeguards (保障措施):

### A. Participant population

- Trials that define the MTD or go beyond EBRT limits → **participants with limited life expectancy** (预期寿命有限) from cancer, for whom delayed permanent organ failure is an acceptable risk (depends on the disease; discuss with the FDA division).
- **Lower-risk** participants (earlier stage, curable 可治愈, long natural history 自然病程) should *not* receive dosages/organ doses above those described in higher-risk participants with enough follow-up — they have more time to develop long-term toxicity; lower dosages may be right for them, and may need more optimization.
- **Prior EBRT** — decide eligibility by clinical variables (baseline toxicities, organ function); don't exclude someone just for prior EBRT, unless there is a specific toxicity concern in the same location (**co-localization**, 部位重叠).
- **Prior RPT** — decide eligibility by clinical variables + earlier absorbed doses; pre-specify a **maximum cumulative absorbed dose to critical organs** (关键器官; prior + current), and justify going above it; consider **separate cohorts** for patients with prior RPT vs RPT-naïve (未接受过 RPT) patients.

### B. Trial design

- Usually a **fixed number of cycles**; pre-specify a **cap on cumulative administered activity** (and on organ absorbed doses), justified by RPT-specific data; specific to the product/indication, and can be revised. **High uncertainty** (a new product / no data, α-emitters, uneven distribution within an organ, extra toxicity on top of prior RPT) → a lower starting cap; **low uncertainty** (an established product, high-energy β-emitters, even distribution, RPT-naïve) → more flexibility.
- The first-in-human dosage is usually **≤ EBRT limits** (the EBRT literature as the starting point, per the 2019 guidance).
- If the maximum activity shows limited toxicity **and** early efficacy (tumor absorbed dose / clinical) suggests the optimized dosage has not been reached → ask for a meeting to discuss **protocol amendments** for further escalation; bring safety, early efficacy dosimetry, and [[Pharmacokinetics (PK)|PK]] data.
- Choosing the registrational dosage uses **all the data** — safety, early efficacy, PK/PD, PROs; the MTD if known; estimated organ tolerances; tumor + normal-organ dosimetry. Specifically:
  - A **1-cycle DLT period** may be enough for escalating, but the recommended dosage needs longer-term safety data. If several cycles are planned, 1-cycle data is not enough → you need **data from several cycles at several dose levels** for cumulative toxicity; safety follow-up should match the time frame of the expected toxicity and/or the median life expectancy.
  - **Backfill cohorts (回填队列)** — add dose levels or more participants to existing cohorts for extra safety/activity data + longer follow-up.
  - **Compare several dosages, including randomized dose-response trials (随机剂量-反应试验)**, before choosing — the optimized dosage may not be the highest dose. This is especially important when going above EBRT tolerances or at the MTD; size each dose arm for adequate activity/safety/tolerability.
- Consider the cumulative activity from prior RPT when choosing dose levels (lower dosages may suit participants with prior RPT).
- **Informed consent** should explain the risk of long-term / late-onset / cumulative radiation toxicity, and that this risk may not be well described early on.

### C. Safety monitoring

- The onset may be **delayed by months to years** → monitor a pre-specified list of **late radiation adverse events of special interest (rAESI, 放射相关特别关注不良事件)** for **≥ 5 years** after the last dose (or until death if life expectancy is < 5 years). The rAESI list + schedule should reflect the drug-specific dosimetry + a detailed radiation-safety analysis plan; this may become a **postmarketing requirement** (上市后要求). (See [[Adverse Event of Special Interest (AESI)]].)
- For prior radiotherapy (EBRT/RPT): **record the dose to critical organs**; relate organ-specific safety to the prior + cumulative absorbed dose.
- Consider exploratory **early biomarkers** of delayed radiation toxicity; **store (bank)** blood/urine/tissue samples for future validation.

### D. Dosimetry for dosage-optimization trials

- Under **21 CFR 312.23(a)(10)(ii)**, phase 1 studies of radioactive drugs **must** get enough data for **[[Dosimetry|dosimetry]]** calculations. Each novel molecular entity (新分子实体) → dosimetry studies **early**; they give radiobiological context for efficacy/safety. **Direct imaging of the therapeutic product is preferred** (e.g. [[Lutetium-177 (177Lu)|¹⁷⁷Lu]] images itself through its γ); add surrogate analogs (替代类似物) only when direct imaging is not possible.
- An IND (investigational new drug application) built on non-IND data that lacks dosimetry → get dosimetry in the IND trial (a dedicated imaging study or a **lead-in cohort**, 导入队列) to check the dosage assumptions; meet FDA before enrolling large numbers.
- **α-emitters** — direct imaging when possible; otherwise dosimetry from surrogate imaging + PK modelling; consider **micro-scale dosimetry (微剂量学)** because of the short range + uneven deposition → absorbed dose within parts of an organ (sub-organ).
- Dosimetry protocols must describe in detail the image acquisition + processing and every step to the organ absorbed dose: camera/activity calibration (校准), organ/tumor segmentation (分割), time-activity fitting, software, models/assumptions; **bone-marrow dosimetry** per expert consensus (EANM, European Association of Nuclear Medicine); describe the uptake in small organs (salivary, lacrimal 泪腺, pituitary 垂体).
- Organ absorbed doses should come with **estimated uncertainties** (systematic + statistical).
- Justify dose escalation with upper-limit estimates for cumulative activity, optionally through the **biological effective dose (BED, 生物有效剂量)** tied to a defined clinical effect; **report both the absorbed dose and the BED** — a BED-based dose-response helps combine results across studies toward RPT-specific organ tolerances.

---
Part of [[Oncology]]. Related: [[MTD and RP2D]] · [[Dosimetry]] · [[Lutetium-177 (177Lu)]] · [[Dose-Limiting Toxicity (DLT)]] · [[Adverse Event of Special Interest (AESI)]] · [[Xerostomia]] · [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]] · [[PSMA PET-CT]].
