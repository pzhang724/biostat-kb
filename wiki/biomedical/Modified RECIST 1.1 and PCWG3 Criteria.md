---
title: "Modified RECIST 1.1 and PCWG3 Criteria"
type: concept
status: learned
tags: [medical, statistics, regulatory]
created: 2026-06-11
updated: 2026-06-11
sources: 1
---

# Modified RECIST 1.1 and PCWG3 Criteria

Full protocol name: **"Modified Response Evaluation Criteria in Solid Tumors Criteria (Version 1.1) and Prostate Cancer Working Group 3 Criteria"** — usually written **modified RECIST 1.1 and PCWG3 criteria**.

This is **one single, named composite criterion** (not two standards applied side by side) — the assessment standard that advanced / metastatic castration-resistant prostate cancer (**mCRPC**) protocols actually cite to define radiographic assessments and hence **rPFS** (radiographic progression-free survival).

- **"Modified RECIST 1.1"** = [[RECIST 1.1]] applied to **soft-tissue / nodal** disease with prostate-specific adaptations (bone disease sits outside the measurable-target framework; nodal and new-lesion handling adapted).
- **PCWG3** = supplies the **bone-scan** progression rule (the 2+2 rule), the PSA rules, and the "still benefiting?" philosophy. See [[PCWG3 Criteria]].
- The two are fused into **one** criterion; the composite is the thing protocols specify.

## How the single criterion decides

The fusion is **asymmetric**: a **bone scan can only contribute *progression*, never *response*** (bone-scan improvement is unreliable, so no CR/PR off bone).

- **Response (CR/PR/SD)** → from the modified-RECIST **soft-tissue** assessment.
- **Radiographic progression** → **union (OR)**: soft-tissue RECIST PD **or** confirmed bone 2+2 **or** death = rPFS event. Earliest date; bone progression is **back-dated** to the first scan showing the initial 2 new lesions. A bone scan with ≥2 new lesions **not yet confirmed** is **not PD yet** (hold the soft-tissue category pending the confirmatory scan).
- **CR** requires **zero bone disease** (any bone lesions ⇒ best achievable is PR).
- **PSA and symptoms are NOT inputs** to this radiographic criterion — they are separate endpoints.

Fused timepoint matrix (rows = soft-tissue RECIST; cols = bone 2+2 status):

| Soft tissue ↓ \ Bone → | No new bone lesions | ≥2 new, **unconfirmed** | ≥2 new, **confirmed (2+2)** |
|------------------------|---------------------|--------------------------|------------------------------|
| **CR** | CR *(if truly no bone disease)* | PR (await bone confirm) | **PD** |
| **PR** | PR | PR (await confirm) | **PD** |
| **SD** | SD | SD (await confirm) | **PD** |
| **PD** (RECIST) | **PD** | **PD** | **PD** |
| **NE** | NE | NE | **PD** |

Read it as: **any confirmed-2+2 column → PD**; **any RECIST-PD row → PD**; everywhere else the soft-tissue category wins, and "unconfirmed" bone merely defers the call.

This matrix gives the **one status per timepoint**; the best status across all timepoints is the [[Best Overall Response]], from which ORR is derived.

Primary use: defines **rPFS** in mCRPC trials (the composite radiographic progression endpoint); **OS** remains the ultimate endpoint, and [[PSA (Prostate-Specific Antigen)|PSA]] response is reported only as a [[Surrogate Endpoint|surrogate]].

## Official references

The composite is protocol-defined by reference to the two underlying standards:

- Eisenhauer EA, Therasse P, Bogaerts J, et al. **New response evaluation criteria in solid tumours: revised RECIST guideline (version 1.1).** *Eur J Cancer.* 2009;45(2):228–247. doi:10.1016/j.ejca.2008.10.026
- Scher HI, Morris MJ, Stadler WM, et al. **Trial design and objectives for castration-resistant prostate cancer: updated recommendations from the Prostate Cancer Clinical Trials Working Group 3.** *J Clin Oncol.* 2016;34(12):1402–1418. doi:10.1200/JCO.2015.64.2702

