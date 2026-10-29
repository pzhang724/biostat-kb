---
title: "Pharmacokinetics (PK)"
type: concept
status: learned
created: 2026-06-11
---

# Pharmacokinetics (PK)

**Pharmacokinetics (PK, 药代动力学)** is **"what the body does to the drug"** — how drug levels in the body change over time, summarized as **ADME**: Absorption (吸收), Distribution (分布), Metabolism (代谢), Excretion (排泄). (Compare **pharmacodynamics, PD** 药效学 = what the drug does to the body.)

Measured by taking blood (sometimes urine) samples at set times after dosing, to build a **concentration–time curve** (浓度-时间曲线). Parameters are derived from that curve (non-compartmental analysis, **NCA** 非房室分析):

- **Cmax** (峰浓度) — the highest observed concentration, read straight off the curve; **Tmax** (达峰时间) — the time when Cmax happens.
- **AUC** (曲线下面积) — area under the concentration–time curve = total **exposure** (暴露); integrate (积分) concentration over time (trapezoidal rule, 梯形法). AUC0–t (to the last sample) or AUC0–∞ (extrapolated, 外推, to infinity).
- **t½** (半衰期) — terminal half-life, from the slope of the log-linear elimination phase (对数线性消除相); **CL** (清除率, clearance) = Dose/AUC; **Vd** (分布容积, volume of distribution).
- **Css** (稳态浓度) — steady state for repeat dosing; **Ctrough** (谷浓度).

**What the data looks like:**

- **Concentration dataset** — one row per (subject, period/treatment, nominal time 名义时间, actual time 实际时间, analyte 分析物, concentration), plus dosing records (dose, dose time). Values below the limit of quantification (**LLOQ**, lower limit of quantification, 定量下限) are handled by a rule. In CDISC this is the SDTM **PC** domain (PK concentrations); dosing is in **EX**.
- **Parameter dataset** — one row per (subject, profile, parameter) holding Cmax/Tmax/AUC…; SDTM **PP** domain (PK parameters), analysis-ready as ADaM **ADPC/ADPP**.
- **Plot** — a concentration–time curve per subject, usually shown on both linear and semi-log (半对数) axes.

**Why in trials:** describe exposure, check **dose-proportionality** (剂量比例性), select the dose/schedule, assess accumulation (蓄积), evaluate **drug–drug interactions (DDI, 药物相互作用)** and special populations (renal/hepatic impairment, 肾/肝功能损害), and drive **exposure–response (PK/PD, 暴露-效应)** analyses. Phase I is mostly driven by PK. **Purpose in one line:** get the dose/schedule right and understand how it varies — the numbers behind dose selection and benefit-risk (获益-风险) (the same goal as [[Dosimetry]], but in concentration terms instead of radiation-dose terms).

For radioactive drugs, the radiation counterpart of PK exposure is [[Dosimetry]] (absorbed dose in Gy instead of drug concentration). See also [[PSMA PET-CT]] for the imaging side of radioligand programs.

## PK vs Dosimetry (telling them apart)

Both ask "where does it go in the body over time", but they measure different things:

- **PK** counts the **drug molecule** — concentration / exposure over time; unit **concentration (ng/mL)**, AUC. **Every drug** has PK.
- **[[Dosimetry]]** counts the **radiation dose** that the radioactive payload (载荷) deposits in each tissue; unit **Gray (Gy, 戈瑞)**. **Only radioactive drugs** have it.

For radioligands they work as a **relay** (接力): PK / biodistribution (生物分布) says where the drug sits and for how long → dosimetry turns that residence time + isotope physics into absorbed dose per organ → this sets the safe activity (limiting organ = kidney / marrow). **Mnemonic: PK = drug molecule (ng/mL); dosimetry = radiation dose (Gy).**

**What each actually measures:** PK directly measures the **concentration of the drug molecule** in blood/plasma (血浆) with an assay (检测方法; e.g. LC-MS/MS, liquid chromatography–tandem mass spectrometry 液相色谱-串联质谱 → ng/mL) over time. Dosimetry measures the **radioactivity (Bq, becquerel 贝可) per organ** from quantitative imaging, then converts it to **absorbed dose (Gy)**.
