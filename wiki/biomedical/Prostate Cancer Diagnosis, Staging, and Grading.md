---
title: "Prostate Cancer Diagnosis, Staging, and Grading"
type: concept
status: learned
tags: [medical]
created: 2026-06-19
updated: 2026-06-19
sources: 2
---

# Prostate Cancer Diagnosis, Staging, and Grading

The disease-history vocabulary captured at baseline for a prostate trial (the [[eCRF Forms (Prostate Cancer Trial)|disease-history eCRF]]).

## Disease history vs medical history

Same kind of data (past/concurrent conditions), split by whether it's the **disease under study** or **everything else**:

- **Disease history / characteristics** ("prostate cancer history") = the **index disease** the trial treats — diagnosis date, histology, Gleason/grade, TNM/stage, metastatic sites, prior prostate-cancer treatments, PSA/castration status. Drives **eligibility, staging, line of therapy, stratification, efficacy baseline**.
- **Medical history (`MH`)** = the patient's **general** past/concurrent conditions / comorbidities **not** the study disease — hypertension, diabetes, prior MI, other surgeries, allergies. **Background health** for safety context and contraindications.

Dividing line: *"is it the cancer we're treating, or background health?"* SDTM: both commonly live in the **`MH`** domain, distinguished by **`MHCAT`/`MHSCAT`** (e.g. "PROSTATE CANCER" vs "GENERAL MEDICAL HISTORY"); disease characteristics are often a **separate CRF** even when they map back to MH.

## Histologic vs cytologic (how it was confirmed)

- **Histologic** (组织学) = diagnosis from **tissue architecture** — a core needle biopsy / specimen under the microscope showing gland structure. Prostate cancer is almost always **histologically confirmed adenocarcinoma**.
- **Cytologic** (细胞学) = diagnosis from **individual cells** (fine-needle aspiration / fluid cytology), no tissue architecture. Less common for prostate.

## TNM — the staging framework

**T** = primary **Tumour** extent · **N** = regional **Nodes** · **M** = distant **Metastasis**.

- **T**: T1 not palpable/incidental · T2 confined to prostate · T3 beyond capsule / seminal vesicle · T4 invades adjacent structures.
- **N**: N0 none · N1 regional node mets. **M**: M0 none · M1 distant (M1a non-regional nodes, M1b **bone**, M1c other).

## Clinical vs pathological TNM

- **Clinical TNM (cTNM)** = assessed **before** definitive treatment from exam (DRE 直肠指检), imaging, biopsy — a pre-treatment estimate.
- **Radical prostatectomy** (根治性前列腺切除) = surgical removal of the **whole prostate** (+ seminal vesicles).
- **Pathological TNM (pTNM)** = staging from the **examined surgical specimen** after prostatectomy (margins, extracapsular extension, seminal-vesicle involvement, nodes). **More accurate** than cTNM. No **pT1** for prostate (needs the specimen) → pT2/pT3/pT4.
- So **cTNM (before, clinical) vs pTNM (after surgery, pathological)** = same framework, different time-point + accuracy.

## Disease stage

Overall **stage group I–IV**, derived from TNM **+ PSA + grade group**. **Stage IV = M1 = metastatic** — the [[Metastatic Castration-Resistant Prostate Cancer (mCRPC)|mCRPC]] setting.

## Gleason score (grade)

Histologic **grade** of prostate adenocarcinoma by **glandular architecture**. The pathologist gives the **two most common patterns** (each 1–5); **sum = score** (practically 6–10), e.g. **3+4=7**; higher = more **poorly differentiated / aggressive**. Modern equivalent = **ISUP Grade Group 1–5** (GG1 ≤6, GG2 = 3+4, GG3 = 4+3, GG4 = 8, GG5 = 9–10).

## Castration

Lowering testosterone to **castrate level** (typically **<50 ng/dL**). Prostate cancer is **androgen-driven**, so this slows it. **Surgical** castration = orchiectomy; **medical** castration = ADT (LHRH agonist/antagonist) — see [[Anti-Cancer Therapy Categories in Oncology Trials|systemic therapy]]. **Castration-sensitive** vs **castration-resistant** (CRPC = progresses despite castrate testosterone); **mCRPC** = metastatic CRPC.

Disease is then tracked by [[PSA (Prostate-Specific Antigen)|PSA]] + imaging via [[Modified RECIST 1.1 and PCWG3 Criteria]]; part of [[Oncology]].
