---
title: "CRF vs Non-CRF (External) Data"
type: concept
status: learned
created: 2026-06-19
---

# CRF vs Non-CRF (External) Data

eCRF data and central-lab data are **not the same stream** — they are two separate sources that are merged later.

## Two streams

- **CRF data** — the **electronic Case Report Form (eCRF, 电子病例报告表)** in the **EDC** (Electronic Data Capture, 电子数据采集) system: what **site staff type in** — AEs, con-meds (合并用药), vitals, [[Physical Examination|physical exam]], dosing, local assessments, the investigator's interpretations.
- **Non-CRF / external / third-party data** (外部/第三方数据) — vendor data sent as an **electronic data transfer** straight into the clinical database, **not typed in again by the site**. The **central lab** is the main example; the same applies to **PK/bioanalytical**, **imaging / ECG core lab**, and **ePRO / eDiary**.

## Why central labs are separate

- **One central lab = one standard assay + one reference range for all sites** → results can be compared (local labs differ from site to site). Sponsors use central labs for **key / efficacy** labs, and **local labs** (entered in the eCRF) for quick safety checks.
- The feed arrives according to a **Data Transfer Agreement / spec** (数据传输协议/规范), is loaded, then **reconciled (核对)** against the eCRF (matching subject ID, visit, sample date).

## Local lab — comes in through the eCRF

The **local lab** (the site's own lab) is **not** a separate stream — its results are **entered by the site into the eCRF**, so they are CRF data (often recorded only when abnormal / clinically significant, per the protocol). Central lab = external feed; local lab = eCRF.

## Other sources feeding the CSR

Besides the eCRF + central lab, many external feeds are loaded and **reconciled** into the clinical database, then mapped [[SDTM, SDTM IG, and Conformance Rules|SDTM]] → ADaM → TLFs (tables, listings and figures, 图表清单) → **CSR** (clinical study report, 临床研究报告):

- **PK / bioanalytical** lab (drug concentrations) → `PC`/`PP` — see [[Pharmacokinetics (PK)]].
- **Biomarker / specialty central labs** — PGx (pharmacogenomics, 药物基因组学), immunogenicity / anti-drug antibody (ADA, 抗药抗体), flow cytometry (流式细胞术).
- **Imaging / ECG core lab** — central reads; includes **BICR** (Blinded Independent Central Review, 独立中心盲态阅片) for tumour response, and central ECG over-read (复读).
- **ePRO / eCOA / eDiary** — patient-reported outcomes through a device/app.
- **IRT / RTSM** (IWRS) (interactive response technology / randomization and trial supply management / interactive web response system, 交互式应答系统) — randomization assignments, stratification factors, drug dispensing (发药) & accountability (药物清点).
- **Safety / pharmacovigilance (药物警戒) database** — [[Serious Adverse Event (SAE)|SAE]] reconciliation against the clinical database (the PV, pharmacovigilance, system holds the regulatory SAE records).
- **Wearables / digital sensors** (可穿戴设备/数字传感器), and **external death index / registries** (死亡登记/登记库) — survival-status data for OS follow-up.

## Where they converge

At [[SDTM, SDTM IG, and Conformance Rules|SDTM]] both land in the **same `LB` domain** (harmonized, 统一) — but in operations they came through different channels and needed reconciliation. Note: the central-lab **value** itself is not in the eCRF, but if the investigator reviews it and judges it **clinically significant**, the resulting **AE is** entered in the eCRF — the data-triggered route in [[Adverse Event Ascertainment]]. The list of lab parameters is [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)]]; a data concept used across [[Oncology]].
