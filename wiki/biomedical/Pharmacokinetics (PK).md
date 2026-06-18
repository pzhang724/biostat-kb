---
title: "Pharmacokinetics (PK)"
type: concept
status: learned
tags: [statistics, medical, trial-conduct]
created: 2026-06-11
updated: 2026-06-18
sources: 5
---

# Pharmacokinetics (PK)

**Pharmacokinetics (PK, 药代动力学)** is **"what the body does to the drug"** — the time course of a drug in the body, summarized as **ADME**: Absorption, Distribution, Metabolism, Excretion. (Contrast **pharmacodynamics, PD** = what the drug does to the body.)

Measured by sampling blood (sometimes urine) at set times after dosing to build a **concentration–time curve** (浓度-时间曲线). Parameters are derived from that curve (non-compartmental analysis, **NCA** 非房室分析):

- **Cmax** (峰浓度) — highest observed concentration, read straight off the curve; **Tmax** (达峰时间) — the time at which Cmax occurs.
- **AUC** (曲线下面积) — area under the concentration–time curve = total **exposure** (暴露); integrate concentration over time (trapezoidal). AUC0–t (to last sample) or AUC0–∞ (extrapolated to infinity).
- **t½** (半衰期) — terminal half-life, from the slope of the log-linear elimination phase; **CL** (清除率, clearance) = Dose/AUC; **Vd** (分布容积, volume of distribution).
- **Css** (稳态浓度) — steady-state for repeat dosing; **Ctrough** (谷浓度).

**What the data looks like:**
- **Concentration dataset** — one row per (subject, period/treatment, nominal time 名义时间, actual time 实际时间, analyte, concentration), plus dosing records (dose, dose time); values below the limit of quantification (**LLOQ** 定量下限) handled by rule. In CDISC this is the SDTM **PC** domain (PK concentrations); dosing in **EX**.
- **Parameter dataset** — one row per (subject, profile, parameter) holding Cmax/Tmax/AUC… ; SDTM **PP** domain (PK parameters), analysis-ready as ADaM **ADPC/ADPP**.
- **Plot** — a concentration–time curve per subject, usually shown on both linear and semi-log axes.

**Why in trials:** characterize exposure, check **dose-proportionality**, select the dose/schedule, assess accumulation, evaluate **drug–drug interactions (DDI)** and special populations (renal/hepatic impairment), and drive **exposure–response (PK/PD)** analyses. Phase I is largely PK-driven. **Purpose in one line:** get the dose/schedule right and understand its variability — the quantitative basis for dose selection and benefit-risk (the same goal as [[Dosimetry]], but in concentration rather than radiation-dose terms).

For radioactive drugs the radiation analogue of PK exposure is [[Dosimetry]] (absorbed dose in Gy rather than drug concentration). See also [[PSMA PET-CT]] for the imaging side of radioligand programs.

## PK vs Dosimetry (telling them apart)

Both ask "where does it go in the body over time," but measure different things:

- **PK** counts the **drug molecule** — concentration / exposure over time; unit **concentration (ng/mL)**, AUC. **Any drug** has PK.
- **[[Dosimetry]]** counts the **radiation dose** that the radioactive payload deposits in each tissue; unit **Gray (Gy)**. **Only radioactive drugs** have it.

For radioligands they are a **relay**: PK / biodistribution says where the drug sits and for how long → dosimetry converts that residence + isotope physics into absorbed dose per organ → sets the safe activity (limiting organ = kidney / marrow). **Mnemonic: PK = drug molecule (ng/mL); dosimetry = radiation dose (Gy).**

**What each actually measures:** PK directly measures the **drug molecule's concentration** in blood/plasma (assay, e.g. LC-MS/MS → ng/mL) over time; dosimetry measures the **radioactivity (Bq) per organ** from quantitative imaging, then converts to **absorbed dose (Gy)**.

