---
title: "Dosimetry"
type: concept
status: learned
tags: [medical, statistics, trial-conduct]
created: 2026-06-11
updated: 2026-06-18
sources: 2
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

