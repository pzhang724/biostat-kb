---
title: "Dosimetry"
type: concept
status: learned
created: 2026-06-11
---

# Dosimetry

**Dosimetry (剂量测定)** measures the **absorbed radiation dose** (吸收剂量, in **Gray, Gy**) that a radioactive drug delivers to tumors and to normal/critical organs — e.g. [[Lutetium-177 (177Lu)|¹⁷⁷Lu]]-PSMA-617 radioligand therapy. It is the radiation counterpart of [[Pharmacokinetics (PK)|PK]] exposure: instead of drug concentration over time, it tracks radioactivity and converts it to absorbed dose.

**How it's done:** repeated **quantitative imaging** (定量成像; SPECT/PET — e.g. of ¹⁷⁷Lu, or of a ⁶⁸Ga companion) ± blood sampling at several timepoints → a **time–activity curve** for each organ/tumor → integrate (积分) it to get the **cumulated activity** → convert to **absorbed dose (Gy)** with dose factors (the **MIRD** method, Medical Internal Radiation Dose, 医用内照射剂量).

**What it computes, step by step:** quantitative imaging after the dose at several timepoints (e.g. 1 h / 24 h / 48 h / 96 h / 168 h) → for each organ/tumour, draw a **region/volume of interest** (ROI/VOI, 感兴趣区) → measure the **activity** (Bq, or % of injected activity) at each timepoint → a **time–activity curve (TAC, 时间-活度曲线)** for each organ (just like the PK concentration curve, but the y-axis is radioactivity) → integrate the TAC → **time-integrated / cumulated activity (累积活度)**, often summarized by an **effective half-life (有效半衰期) / residence time (驻留时间)** → convert with **dose factors (S-values, S值 / MIRD)**: organ absorbed dose = cumulated activity × S-value → **Gy per organ**.

**Not only scans — blood & urine too:** together with imaging, dosimetry usually collects **blood** and **urine** samples, each for its own purpose:

- **Imaging (SPECT/PET)** → activity in the **organs / tumour**.
- **Blood samples** → radioactivity in the blood over time → mainly for the absorbed dose of the **red marrow (红骨髓)**. The marrow is hard to image directly, but **low blood counts from marrow damage (myelosuppression, 骨髓抑制) limit the dose**, so blood activity is the standard stand-in (surrogate) — blood-based marrow dosimetry. It also gives the blood clearance curve.
- **Urine samples** → activity that has left the body → measures **excretion through the kidneys** (renal excretion, 经肾排泄) and how fast it happens. From it you get the **whole-body retention** (全身滞留; = given − excreted, a mass balance 质量平衡) and the kidney/bladder exposure. ¹⁷⁷Lu-PSMA is mainly cleared by the kidneys, so urine matters.
- Together: imaging = "how much is *in* each organ/tumour"; blood = "how much the *marrow* gets"; urine = "how much has *left* the body / how much remains".

**What the data looks like:**

- One row per (subject, organ, timepoint) holding the measured **activity**.
- Summary: one row per (subject, organ) with **time-integrated activity, effective half-life, and absorbed dose (Gy)**, often normalized (标准化) as **Gy/GBq**.
- Plots: a time–activity curve per organ; a table of **Gy per organ** (kidney, marrow, salivary glands, tumour).

**Parallel to PK:** PK's **AUC** (concentration·time) ↔ dosimetry's **cumulated activity** (activity·time) — both integrate a time curve. PK reports exposure in concentration units; dosimetry goes one step further and converts the activity–time integral into absorbed dose (Gy).

**Gy vs GBq — two different things:**

- **GBq (gigabecquerel, 吉贝可)** — a unit of **radioactivity / activity** (放射性活度). 1 Bq = 1 nuclear decay (核衰变) per second; 1 GBq = 10⁹ Bq. It is the **input / source** quantity — *how much radioactivity you give*.
- **Gy (gray, 戈瑞)** — a unit of **absorbed dose** (吸收剂量). 1 Gy = 1 joule of energy deposited per kilogram of tissue (J/kg). It is the **received** quantity — *how much radiation energy a given tissue actually absorbs*.
- **Relation:** you give activity (GBq); dosimetry converts it — using where the drug sits, for how long, and the physics of the isotope — into absorbed dose (Gy) per organ, often normalized as **Gy/GBq**. The same GBq gives different Gy in different organs; working that out is exactly the job of dosimetry. **In one line: GBq = how much radioactivity you gave (source); Gy = how much a tissue absorbed (received).**

**How patients receive it & precautions after the dose:** targeted radioligands (e.g. ¹⁷⁷Lu-PSMA) are given by **IV infusion** (静脉输注), not by mouth — the ligand must reach the blood intact, and the activity must be dosed precisely. (Some radiopharmaceuticals *are* oral, e.g. radioactive iodine ¹³¹I as a capsule/drink for the thyroid.) Because the patient is radioactive for a short time, precautions follow, scaled to the isotope / activity / local regulations. With ¹⁷⁷Lu, often **outpatient** (门诊) + a few days of keeping distance (stay away from children/pregnant women, sleep separately, flush urine well / wash hands). A strong γ-emitter like high-dose ¹³¹I may need a short **inpatient isolation** in a shielded room (屏蔽病房) until the measured dose rate falls below a release limit.

**Organs at risk:** kidneys (often **dose-limiting**, 剂量限制性, for PSMA/peptide radioligand therapies), salivary glands, bone marrow, liver.

**Why in trials:**

- **Safety** — keep each organ under its dose-limit threshold.
- **Efficacy** — confirm the tumor gets a meaningful absorbed dose, and relate **tumor dose → response** (dose–response, 剂量-效应).
- Supports **choosing the activity for each patient** (personalized activity selection) in radioligand therapy.

**Purpose in one line:** use radiation dose (Gy) to balance "enough dose to the tumour" against "not too much to the organs" — the same dose-selection / benefit-risk goal as [[Pharmacokinetics (PK)|PK]], but in radiation-dose terms instead of concentration terms.

**Theranostic link (诊疗一体化):** the same **PSMA** target imaged on [[PSMA PET-CT]] is what ¹⁷⁷Lu-PSMA binds; dosimetry measures the radiation that this delivery actually deposits. The idea shared with PK: both answer *"how much reaches where, over time."*

**Does it need a separate agent?** It depends on the isotope — dosimetry needs a signal that can be imaged:

- **Self-imaging (no separate agent)** — [[Lutetium-177 (177Lu)|¹⁷⁷Lu]] gives off an imageable γ together with its therapeutic β, so SPECT of the **therapy dose itself** gives the dosimetry. This is the theranostic advantage: you image the very dose you treated with.
- **Needs an imaging companion** — if the therapeutic nuclide (核素) is a pure β or α emitter with no imageable γ (e.g. **²²⁵Ac**), the therapy cannot be imaged directly. So a separate **diagnostic imaging agent** (low activity, *not* another therapy) is used — e.g. ⁶⁸Ga on the same ligand (PET), or a ¹⁷⁷Lu stand-in. This is the **matched / theranostic pair (诊疗配对)**.

## Dosimetry vs PK (telling them apart)

- **[[Pharmacokinetics (PK)]]** counts the **drug molecule** — concentration / exposure over time; unit **concentration (ng/mL)**, AUC; **every drug** has it.
- **Dosimetry** counts the **radiation dose** that the radioactive payload (载荷) deposits in each tissue; unit **Gray (Gy)**; **only radioactive drugs** have it.

For radioligands they work as a **relay** (接力): PK/biodistribution (where it sits, for how long) → dosimetry (absorbed dose per organ, Gy) → safe activity (limiting organ = kidney/marrow). **Mnemonic: PK = drug molecule (ng/mL); dosimetry = radiation dose (Gy).**

**What each actually measures:** PK directly measures the **concentration of the drug molecule** in blood/plasma (by an assay → ng/mL) over time; dosimetry measures the **radioactivity (Bq) per organ** from quantitative imaging, then converts it to **absorbed dose (Gy = J/kg)**.

## Why a drug has radiation, and the organ effect

The drug is a **radioligand / radiopharmaceutical** (放射性配体/放射性药物) — a targeting ligand that carries a radioactive isotope (e.g. ¹⁷⁷Lu, ²²⁵Ac). The radiation is **on purpose: it is how the treatment works** (the therapeutic mechanism). The ligand brings the isotope to the tumour (e.g. to PSMA), and the radiation it gives off kills the cells locally ("targeted radiotherapy", 靶向放疗) — unlike an ordinary small molecule, which acts chemically.

**What "radiation" means here:** radiation (辐射) is energy given off as waves or particles. The relevant kind is **ionizing radiation** (电离辐射) — strong enough to knock electrons off atoms, and so to damage DNA / kill cells: the α particles, β particles and γ rays given off by radioactive isotopes (compare **non-ionizing radiation**, 非电离辐射, like light or radio waves). That cell-killing is both the therapeutic effect and the source of organ toxicity, and it is what dosimetry measures (as absorbed dose, Gy).

**Yes — literally radioactive.** The molecule has a **radionuclide** (放射性核素, e.g. ¹⁷⁷Lu, ²²⁵Ac) chemically attached. That atom is unstable and **decays by itself inside the body** (spontaneously, 自发地), giving off radiation until it has decayed away (set by its **half-life**, 半衰期). It is real nuclear decay, not a metaphor (比喻). What follows from this: the dose is set by **radioactivity / activity** (放射性活度, in becquerel Bq — in the clinic MBq/GBq), not by mass; it is prepared behind shielding (屏蔽) in a **hot lab** (放射性药物实验室); and the patient is radioactive for a short time after the dose.

It **does** affect normal organs: the radioactive drug also deposits dose where it collects or passes through — kidney (excretion), salivary glands (PSMA), bone marrow, liver — causing off-target toxicity (see [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]: creatinine, xerostomia, MDS). Key wording: **it is the *radiation* that affects organs; *dosimetry* measures that dose**, so that each organ can be kept under its safe limit (the kidney usually limits the dose). Dosimetry itself is a measurement, not a harm.
