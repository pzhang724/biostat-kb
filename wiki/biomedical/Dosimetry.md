---
title: "Dosimetry"
type: concept
status: learned
tags: [medical, statistics, trial-conduct]
created: 2026-06-11
updated: 2026-06-18
sources: 6
---

# Dosimetry

**Dosimetry (剂量测定)** quantifies the **absorbed radiation dose** (in **Gray, Gy**) delivered to tumors and to normal/critical organs by a radioactive drug — e.g. ¹⁷⁷Lu-PSMA-617 radioligand therapy. It is the radiation analogue of [[Pharmacokinetics (PK)|PK]] exposure: instead of drug concentration over time, it tracks radioactivity and converts it to absorbed dose.

**How it's done:** serial **quantitative imaging** (SPECT/PET — e.g. of ¹⁷⁷Lu, or a ⁶⁸Ga companion) ± blood sampling at several timepoints → a **time–activity curve** per organ/tumor → integrate to **cumulated activity** → convert to **absorbed dose (Gy)** using dose factors (**MIRD** methodology).

**Organs at risk:** kidneys (often **dose-limiting** for PSMA/peptide radioligand therapies), salivary glands, bone marrow, liver.

**Why in trials:**

- **Safety** — keep each organ under its dose-limit threshold.
- **Efficacy** — confirm the tumor receives a meaningful absorbed dose, and relate **tumor dose → response** (dose–response).
- Supports **personalized activity selection** in radioligand therapy.

**Theranostic link:** the same **PSMA** target imaged on [[PSMA PET-CT]] is what ¹⁷⁷Lu-PSMA binds; dosimetry quantifies the radiation that delivery actually deposits. Shared idea with PK: both answer *"how much reaches where, over time."*

## Dosimetry vs PK (telling them apart)

- **[[Pharmacokinetics (PK)]]** counts the **drug molecule** — concentration / exposure over time; unit **concentration (ng/mL)**, AUC; **any drug** has it.
- **Dosimetry** counts the **radiation dose** the radioactive payload deposits per tissue; unit **Gray (Gy)**; **only radioactive drugs** have it.

They form a **relay** for radioligands: PK/biodistribution (where it sits, how long) → dosimetry (absorbed dose per organ, Gy) → safe activity (limiting organ = kidney/marrow). **Mnemonic: PK = drug molecule (ng/mL); dosimetry = radiation dose (Gy).**

**What each actually measures:** PK directly measures the **drug molecule's concentration** in blood/plasma (assay → ng/mL) over time; dosimetry measures the **radioactivity (Bq) per organ** from quantitative imaging, then converts to **absorbed dose (Gy = J/kg)**.

## Why a drug has radiation, and the organ effect

The drug is a **radioligand / radiopharmaceutical** — a targeting ligand carrying a radioactive isotope (e.g. ¹⁷⁷Lu, ²²⁵Ac). The radiation is **intentional: it is the therapeutic mechanism** — the ligand delivers the isotope to the tumour (e.g. PSMA) and its emitted radiation kills the cells locally ("targeted radiotherapy"), unlike an ordinary small molecule that acts chemically.

**What "radiation" means here:** radiation (辐射) is energy emitted as waves or particles. The relevant kind is **ionizing radiation** (电离辐射) — energetic enough to strip electrons off atoms and so damage DNA / kill cells: the α particles, β particles, and γ rays emitted by radioactive isotopes (contrast **non-ionizing radiation** 非电离辐射 like light or radio waves). That cell-killing is both the therapeutic effect and the source of organ toxicity, and is what dosimetry quantifies (as absorbed dose, Gy).

**Yes — literally radioactive.** The molecule has a **radionuclide** (放射性核素, e.g. ¹⁷⁷Lu, ²²⁵Ac) chemically attached; that atom is unstable and **spontaneously decays inside the body**, emitting radiation until it decays away (set by its **half-life** 半衰期). It is genuine nuclear decay, not a metaphor. Consequences: dosing is by **radioactivity / activity** (放射性活度, in becquerel Bq — clinically MBq/GBq) rather than mass; it's prepared with shielding in a **hot lab**; and the patient is transiently radioactive after administration.

It **does** affect normal organs: the radioactive drug also deposits dose where it accumulates or passes through — kidney (excretion), salivary glands (PSMA), bone marrow, liver — causing off-target toxicity (see [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]: creatinine, xerostomia, MDS). Key wording: **it is the *radiation* that affects organs; *dosimetry* measures that dose** so each organ can be kept under its safe limit (kidney is usually dose-limiting). Dosimetry itself is measurement, not harm.

