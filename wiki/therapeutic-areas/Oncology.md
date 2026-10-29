---
title: "Oncology"
type: therapeutic-area
status: learning
created: 2026-06-12
---

# Oncology

The top-level main narrative for the oncology (肿瘤学) learning thread. Indications (适应证) are sections within this page (they reuse the same cross-cutting concepts); each one links out to its terms.

## Cross-cutting concepts (reused across indications)

**Clinical**
- [[RECIST 1.1]]
- [[Measurable vs Non-Measurable Disease (RECIST)]]
- [[CTCAE Grade]]
- [[Serious Adverse Event (SAE)]]
- [[Dose-Limiting Toxicity (DLT)]]
- [[Anti-Cancer Therapy Categories in Oncology Trials]]
- [[Targeted Therapy and Tissue-Agnostic Biomarkers]]
- [[ECOG Performance Status]]
- [[12-Lead Resting ECG]]
- [[Radiological Assessment]]
- [[Xerostomia]]
- [[Anti-Emetic Premedication]]
- [[Infusion-Related and Hypersensitivity Reactions]]
- [[Physical Examination]]
- [[Immunogenicity]]

**Statistics**
- [[Safety vs Tolerability]]
- [[Intercurrent Event]]
- [[Surrogate Endpoint]]
- [[Best Overall Response]]
- [[Progression-Free Survival (PFS) and Overall Survival (OS)]]
- [[MTD and RP2D]]
- [[Simon's Two-Stage Design]]
- [[Anti-Tumour Activity]]

**Trial conduct**
- [[Adverse Event Ascertainment]]
- [[Follow-up of Adverse Events]]
- [[Local (Investigator) vs Central (BICR) Tumour Assessment]]
- [[End of Treatment vs End of Study]]
- [[Schedule of Assessments]]
- [[MedDRA]]
- [[SDTM, SDTM IG, and Conformance Rules]]
- [[Action Taken for an Adverse Event]]
- [[Adverse Event Outcome]]
- [[CRF vs Non-CRF (External) Data]]
- [[eCRF Forms (Prostate Cancer Trial)]]
- [[Prior, Concomitant, and Subsequent Treatment]]

**Regulatory**
- [[Investigator's Brochure (IB)]]
- [[IRB and IEC (Ethics Committees)]]
- [[Protocol Amendment]]
- [[Financial Disclosure (Clinical Investigators)]]
- [[Oncology Therapeutic Radiopharmaceuticals — Dosage Optimization (FDA Draft Guidance)]]

## Tumour assessment data flow

How an imaging read becomes an efficacy endpoint, from start to end:

**Imaging** ([[Radiological Assessment]]) → criterion: [[RECIST 1.1]] for soft tissue/nodes, combined with bone [[PCWG3 Criteria]] into [[Modified RECIST 1.1 and PCWG3 Criteria]] for mCRPC → recorded in SDTM **[[RECIST 1.1#Step-by-step derivation (for a programmer)|TU → TR → RS]]** (identity → measurements → response verdict), with **local vs central** reads kept as parallel rows ([[Local (Investigator) vs Central (BICR) Tumour Assessment]]; central comes in as a [[CRF vs Non-CRF (External) Data|non-CRF feed]]) → the per-visit response is reduced to the per-patient [[Best Overall Response]] → the endpoints **ORR / DCR / DoR** (objective response rate / disease control rate / duration of response) and the time-to-event [[Progression-Free Survival (PFS) and Overall Survival (OS)|PFS / OS]] (rPFS in prostate). Criterion and evaluator are **category axes inside one set of domains**, not separate domains.

## Prostate cancer

The disease state is [[Metastatic Castration-Resistant Prostate Cancer (mCRPC)|mCRPC]] (metastatic, and getting worse even though testosterone is at castrate level). How the treatment effect is read out in advanced/mCRPC trials: a [[PSA (Prostate-Specific Antigen)|PSA]] biomarker and [[PSMA PET-CT]] imaging measure the disease; bone progression follows [[PCWG3 Criteria]], combined with soft-tissue [[RECIST 1.1]] into the [[Modified RECIST 1.1 and PCWG3 Criteria]] criterion; [[PSA (Prostate-Specific Antigen)|PSA]] response is only a [[Surrogate Endpoint]]; radioligand (放射性配体) programs add [[Pharmacokinetics (PK)]] / [[Dosimetry]].

Prostate-specific terms: [[Metastatic Castration-Resistant Prostate Cancer (mCRPC)]] · [[Prostate Cancer Diagnosis, Staging, and Grading]] · [[PSA (Prostate-Specific Antigen)]] · [[PSMA PET-CT]] · [[PCWG3 Criteria]] · [[Modified RECIST 1.1 and PCWG3 Criteria]] · [[Pharmacokinetics (PK)]] · [[Dosimetry]] · [[Lutetium-177 (177Lu)]] · [[Radiopharmaceutical Therapy (RPT) and External Beam Radiation Therapy (EBRT)]] · [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]].

## Lung cancer

[[Non-Small Cell Lung Cancer (NSCLC)|NSCLC]] is the main class of lung cancer (vs small cell). Trial populations are described in layers: **class → histology (squamous vs non-squamous, 鳞 vs 非鳞) → biomarker** — e.g. *c-Met-overexpressing non-squamous NSCLC*, where **c-Met overexpression** (c-Met 过表达) is the target-selection biomarker for therapy aimed at MET (like how [[PSMA PET-CT|PSMA]] selects patients for ¹⁷⁷Lu-PSMA in prostate).

Lung-specific terms: [[Non-Small Cell Lung Cancer (NSCLC)]].
