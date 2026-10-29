---
title: "Modified RECIST 1.1 and PCWG3 Criteria"
type: concept
status: learned
created: 2026-06-11
---

# Modified RECIST 1.1 and PCWG3 Criteria

Full protocol name: **"Modified Response Evaluation Criteria in Solid Tumors Criteria (Version 1.1) and Prostate Cancer Working Group 3 Criteria"** — usually written **modified RECIST 1.1 and PCWG3 criteria**.

This is **one single, named composite (复合) criterion** — not two standards used side by side. It is the assessment standard that advanced / metastatic castration-resistant prostate cancer (**mCRPC**) protocols actually cite to define radiographic assessments, and so **rPFS** (radiographic progression-free survival, 影像学无进展生存期).

- **"Modified RECIST 1.1"** = [[RECIST 1.1]] applied to **soft-tissue / nodal** (软组织/淋巴结) disease, with changes for prostate cancer (bone disease is outside the measurable-target framework; the handling of nodes and new lesions is adapted).
- **PCWG3** = gives the **bone-scan** progression rule (the 2+2 rule), the PSA rules, and the "is the patient still benefiting?" thinking. See [[PCWG3 Criteria]].
- The two are combined (fused) into **one** criterion; the composite is what protocols specify.

## How the single criterion decides

The combination is **one-sided** (asymmetric, 不对称): a **bone scan can only add *progression*, never *response*** (improvement on a bone scan is unreliable, so there is no CR/PR from bone).

- **Response (CR/PR/SD)** (complete response 完全缓解 / partial response 部分缓解 / stable disease 疾病稳定) → from the modified-RECIST **soft-tissue** assessment.
- **Radiographic progression** → **union (OR, "或")**: soft-tissue RECIST PD (progressive disease, 疾病进展) **or** confirmed bone 2+2 **or** death = an rPFS event. Use the earliest date; bone progression is **back-dated** (回溯) to the first scan that showed the first 2 new lesions. A bone scan with ≥2 new lesions that are **not yet confirmed** is **not PD yet** (keep the soft-tissue category until the confirmatory scan).
- **CR** requires **no bone disease at all** (any bone lesions ⇒ the best possible is PR).
- **PSA and symptoms are NOT inputs** to this radiographic criterion — they are separate endpoints.

Combined timepoint matrix (rows = soft-tissue RECIST; columns = bone 2+2 status; NE = not evaluable, 不可评估):

| Soft tissue ↓ \ Bone → | No new bone lesions | ≥2 new, **unconfirmed** | ≥2 new, **confirmed (2+2)** |
|------------------------|---------------------|--------------------------|------------------------------|
| **CR** | CR *(if truly no bone disease)* | PR (await bone confirm) | **PD** |
| **PR** | PR | PR (await confirm) | **PD** |
| **SD** | SD | SD (await confirm) | **PD** |
| **PD** (RECIST) | **PD** | **PD** | **PD** |
| **NE** | NE | NE | **PD** |

Read it like this: **any confirmed-2+2 column → PD**; **any RECIST-PD row → PD**; everywhere else the soft-tissue category wins, and "unconfirmed" bone only delays the call.

This matrix gives **one status per timepoint**; the best status across all timepoints is the [[Best Overall Response]], from which ORR (objective response rate, 客观缓解率) is derived.

Main use: defines **rPFS** in mCRPC trials (the composite radiographic progression endpoint). **OS** (overall survival, 总生存期) is still the ultimate endpoint, and [[PSA (Prostate-Specific Antigen)|PSA]] response is reported only as a [[Surrogate Endpoint|surrogate]].

## SDTM data model — one domain, criterion is a category

Using both criteria does **not** split the SDTM domains. You still have **one [[RECIST 1.1#Step-by-step derivation (for a programmer)|TU, one TR, one RS]]** (TU = tumor/lesion identification, TR = tumor/lesion results, RS = disease response). The criterion is a **qualifier/category** inside the domain, not a new domain — the same principle as evaluator: investigator vs BICR are `--EVAL` values within one domain.

- **`TUMETHOD`** — `CT`/`MRI` for soft-tissue/nodal (RECIST), `BONE SCAN`/scintigraphy (闪烁显像) for bone (PCWG3); `TULOC` separates bone vs soft-tissue lesions.
- **`RSCAT`/`RSSCAT`** — the response-criteria category (e.g. "RECIST 1.1", "PCWG3", and the composite). So **RS holds several response rows per visit** — a RECIST one, a bone/PCWG3 one, and the combined composite — and each one also **per evaluator**. Per visit you can have `#criteria × #evaluators` RS rows, all in the one RS domain.
- **PSA is not in TU/TR** — it is a lab test, in **`LB`**.
- The composite **modified-RECIST + PCWG3** overall response and **rPFS** are **derived** later, downstream (下游) (ADaM **ADRS**), combining soft-tissue RECIST + bone 2+2 (union for progression) into the single per-timepoint status above.

Rule of thumb: **SDTM splits by topic** (what is measured), **not by analysis type** — criterion and evaluator are extra category axes inside TU/TR/RS, never extra domains. See [[Local (Investigator) vs Central (BICR) Tumour Assessment]].

## Official references

The composite is defined in protocols by reference to the two underlying standards:

- Eisenhauer EA, Therasse P, Bogaerts J, et al. **New response evaluation criteria in solid tumours: revised RECIST guideline (version 1.1).** *Eur J Cancer.* 2009;45(2):228–247. doi:10.1016/j.ejca.2008.10.026
- Scher HI, Morris MJ, Stadler WM, et al. **Trial design and objectives for castration-resistant prostate cancer: updated recommendations from the Prostate Cancer Clinical Trials Working Group 3.** *J Clin Oncol.* 2016;34(12):1402–1418. doi:10.1200/JCO.2015.64.2702
