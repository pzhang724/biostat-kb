---
title: "Prostate Cancer Diagnosis, Staging, and Grading"
type: concept
status: learned
created: 2026-06-19
---

# Prostate Cancer Diagnosis, Staging, and Grading

The vocabulary of disease history recorded at baseline in a prostate trial (the [[eCRF Forms (Prostate Cancer Trial)|disease-history eCRF]]).

## Disease history vs medical history

The same kind of data (past/current conditions), split by whether it is the **disease under study** or **everything else**:

- **Disease history / characteristics** ("prostate cancer history") = the **index disease** (目标疾病) the trial treats — diagnosis date, histology, Gleason/grade, TNM/stage, sites of metastasis, prior prostate-cancer treatments, PSA/castration status. Drives **eligibility, staging, line of therapy, stratification, efficacy baseline**.
- **Medical history (`MH`)** = the patient's **general** past/current conditions and other diseases (comorbidities, 合并症) that are **not** the study disease — hypertension, diabetes, prior MI (myocardial infarction, 心肌梗死), other surgeries, allergies. **Background health**, for safety context and contraindications (禁忌).

Dividing line: *"is it the cancer we are treating, or background health?"* SDTM: both usually live in the **`MH`** domain, separated by **`MHCAT`/`MHSCAT`** (e.g. "PROSTATE CANCER" vs "GENERAL MEDICAL HISTORY"); disease characteristics are often a **separate CRF**, even when they map back to MH.

## Histologic vs cytologic (how it was confirmed)

- **Histologic** (组织学) = diagnosis from the **structure of the tissue** (tissue architecture) — a core needle biopsy (穿刺活检) / specimen under the microscope that shows gland structure. Prostate cancer is almost always **histologically confirmed adenocarcinoma** (腺癌).
- **Cytologic** (细胞学) = diagnosis from **single cells** (fine-needle aspiration 细针穿刺 / fluid cytology), without tissue structure. Less common for prostate.

## TNM — the staging framework

**T** = extent of the primary **Tumour** · **N** = regional lymph **Nodes** · **M** = distant **Metastasis** — the three are sorted by **how far the cancer has spread from where it started**:

- **Primary tumour** (T, 原发肿瘤) = the **original** tumour where the cancer started — for prostate, in the gland itself. T = how far it extends/invades locally: T1 cannot be felt (not palpable, 不可触及) / found by chance (incidental) · T2 confined to the prostate · T3 beyond the capsule (包膜) / into the seminal vesicle (精囊) · T4 invades nearby structures.
- **Regional lymph nodes** (N, 区域淋巴结) = the nodes that **drain** (引流) the primary site (the first spread through the lymph system) — for prostate, the **pelvic** (盆腔) nodes (below the aortic bifurcation, 主动脉分叉). N0 none · N1 regional involvement. Still **locoregional** (局部区域性).
- **Distant metastases** (M, 远处转移) = spread to **faraway** organs beyond the drainage region, usually **through the blood** (hematogenous, 血行) — M0 none · M1 distant: M1a non-regional/distant **nodes**, M1b **bone** (most common in prostate), M1c viscera (内脏). **M1 = metastatic = stage IV.**

**Key detail:** a lymph node is **N or M depending on its location** — pelvic (regional) = **N1**; non-regional nodes (para-aortic 主动脉旁 above the bifurcation, supraclavicular 锁骨上) = **distant = M1a**. So spread to a node is not automatically N. Prostate pattern: prostate (T) → pelvic nodes (N) → bone / distant nodes / viscera (M).

## Clinical vs pathological TNM

- **Clinical TNM (cTNM)** = assessed **before** definitive (根治性) treatment, from exam (DRE, digital rectal exam 直肠指检), imaging and biopsy — an estimate before treatment.
- **Radical prostatectomy** (根治性前列腺切除术) = surgery to remove the **whole prostate** (+ seminal vesicles).
- **Pathological TNM (pTNM)** = staging from the **surgical specimen** (手术标本) examined after prostatectomy (margins 切缘, extracapsular extension 包膜外侵犯, seminal-vesicle involvement, nodes). **More accurate** than cTNM. There is no **pT1** for prostate (it needs the specimen) → pT2/pT3/pT4.
- So **cTNM (before, clinical) vs pTNM (after surgery, pathological)** = the same framework, at a different time point and with different accuracy.

## Disease stage

Overall **stage group I–IV**, derived from TNM **+ PSA + grade group**. **Stage IV = M1 = metastatic** — the [[Metastatic Castration-Resistant Prostate Cancer (mCRPC)|mCRPC]] setting.

## Gleason score (grade)

The histologic **grade** (分级) of prostate adenocarcinoma, based on **gland structure**. The pathologist (病理医生) gives the **two most common patterns** (each 1–5); **sum = score** (in practice 6–10), e.g. **3+4=7**. Higher = more **poorly differentiated** (分化差) / aggressive. The modern equivalent = **ISUP Grade Group 1–5** (ISUP = International Society of Urological Pathology, 国际泌尿病理学会) (GG1 ≤6, GG2 = 3+4, GG3 = 4+3, GG4 = 8, GG5 = 9–10).

## Castration

Two meanings:

1. **The intervention** — lowering/removing **testosterone** (androgen, 雄激素) so it can no longer fuel the cancer. **Surgical** = orchiectomy (睾丸切除术; remove the testes, which make ~90–95% of testosterone); **medical** = ADT — **LHRH/GnRH agonists** (激动剂; leuprolide, goserelin) or **antagonists** (拮抗剂; degarelix) that suppress the hypothalamic-pituitary-gonadal axis (下丘脑-垂体-性腺轴) so the testes stop making testosterone (a [[Anti-Cancer Therapy Categories in Oncology Trials|systemic therapy]]). (LHRH = luteinizing hormone-releasing hormone; GnRH = gonadotropin-releasing hormone.)
2. **The state/level** — serum testosterone below a **castrate level**: conventional **<50 ng/dL** (1.7 nmol/L); stricter/modern **<20 ng/dL** (0.7 nmol/L, because true post-orchiectomy levels are ~15). The **protocol sets** the threshold.

Prostate cancer is **driven by androgens**, so castrate testosterone slows it — the backbone of treatment for advanced disease. **Castration-sensitive** vs **castration-resistant**: **CRPC** = the disease **gets worse while testosterone is confirmed at castrate level** (so castrate T must be ongoing to call it CRPC); **mCRPC** = metastatic CRPC.

The disease is then tracked by [[PSA (Prostate-Specific Antigen)|PSA]] + imaging via [[Modified RECIST 1.1 and PCWG3 Criteria]]; part of [[Oncology]].
