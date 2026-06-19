---
title: "CRF vs Non-CRF (External) Data"
type: concept
status: learned
tags: [data-management, standards]
created: 2026-06-19
updated: 2026-06-19
sources: 2
---

# CRF vs Non-CRF (External) Data

eCRF and central-lab data are **not the same stream** — they are two separate sources that get merged later.

## Two streams

- **CRF data** — the **electronic Case Report Form (eCRF)** in the **EDC** (Electronic Data Capture) system: what **site staff key in** — AEs, con-meds, vitals, [[Physical Examination|physical exam]], dosing, local assessments, the investigator's interpretations.
- **Non-CRF / external / third-party data** — vendor data sent as an **electronic data transfer** straight into the clinical database, **not re-typed by the site**. **Central lab** is the prime example; the same applies to **PK/bioanalytical**, **imaging / ECG core lab**, and **ePRO / eDiary**.

## Why central labs are separate

- **One central lab = one standardized assay + one reference range across all sites** → comparability (local labs vary site to site). Sponsors use central labs for **key / efficacy** labs; **local labs** (entered in the eCRF) for quick safety checks.
- The feed arrives per a **Data Transfer Agreement / spec** and is loaded, then **reconciled** against the eCRF (match subject ID, visit, sample date).

## Local lab — rides in via the eCRF

**Local lab** (the site's own lab) is **not** a separate stream — its results are **entered by the site into the eCRF**, so they are CRF data (often captured only when abnormal / clinically significant, per protocol). Central lab = external feed; local lab = eCRF.

## Other sources feeding the CSR

Beyond eCRF + central lab, many external feeds are loaded and **reconciled** into the clinical database, then mapped [[SDTM, SDTM IG, and Conformance Rules|SDTM]] → ADaM → TLFs → **CSR**:

- **PK / bioanalytical** lab (drug concentrations) → `PC`/`PP` — see [[Pharmacokinetics (PK)]].
- **Biomarker / specialty central labs** — PGx, immunogenicity / anti-drug antibody (ADA), flow cytometry.
- **Imaging / ECG core lab** — centralized reads; includes **BICR** (Blinded Independent Central Review) for tumour response, and central ECG over-read.
- **ePRO / eCOA / eDiary** — patient-reported outcomes via device/app.
- **IRT / RTSM** (IWRS) — randomization assignments, stratification factors, drug dispensing & accountability.
- **Safety / pharmacovigilance database** — [[Serious Adverse Event (SAE)|SAE]] reconciliation against the clinical DB (the PV system holds the regulatory SAE records).
- **Wearables / digital sensors**, and **external death index / registries** — survival-status data for OS follow-up.

## Where they converge

At [[SDTM, SDTM IG, and Conformance Rules|SDTM]] both land in the **same `LB` domain** (harmonized) — but operationally they came through different channels and needed reconciliation. Note: the central-lab **value** itself isn't in the eCRF, but if the investigator reviews it and judges it **clinically significant**, the derived **AE is** entered in the eCRF — the data-triggered route in [[Adverse Event Ascertainment]]. The per-parameter lab catalog is [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)]]; a cross-cutting data concept in [[Oncology]].
