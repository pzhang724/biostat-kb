---
title: "CRF vs Non-CRF (External) Data"
type: concept
status: learned
tags: [data-management, standards]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# CRF vs Non-CRF (External) Data

eCRF and central-lab data are **not the same stream** — they are two separate sources that get merged later.

## Two streams

- **CRF data** — the **electronic Case Report Form (eCRF)** in the **EDC** (Electronic Data Capture) system: what **site staff key in** — AEs, con-meds, vitals, [[Physical Examination|physical exam]], dosing, local assessments, the investigator's interpretations.
- **Non-CRF / external / third-party data** — vendor data sent as an **electronic data transfer** straight into the clinical database, **not re-typed by the site**. **Central lab** is the prime example; the same applies to **PK/bioanalytical**, **imaging / ECG core lab**, and **ePRO / eDiary**.

## Why central labs are separate

- **One central lab = one standardized assay + one reference range across all sites** → comparability (local labs vary site to site). Sponsors use central labs for **key / efficacy** labs; **local labs** (entered in the eCRF) for quick safety checks.
- The feed arrives per a **Data Transfer Agreement / spec** and is loaded, then **reconciled** against the eCRF (match subject ID, visit, sample date).

## Where they converge

At [[SDTM, SDTM IG, and Conformance Rules|SDTM]] both land in the **same `LB` domain** (harmonized) — but operationally they came through different channels and needed reconciliation. Note: the central-lab **value** itself isn't in the eCRF, but if the investigator reviews it and judges it **clinically significant**, the derived **AE is** entered in the eCRF — the data-triggered route in [[Adverse Event Ascertainment]]. The per-parameter lab catalog is [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)]]; a cross-cutting data concept in [[Oncology]].
