---
title: "Oncology"
type: therapeutic-area
status: learning
tags: [medical, statistics]
created: 2026-06-12
updated: 2026-06-19
---

# Oncology

Top-level main narrative for the oncology learning thread. Indications are sections within this page (they reuse the same cross-cutting concepts); each links out to its terms.

## Cross-cutting concepts (reused across indications)

**Criteria & rules**
- [[RECIST 1.1]]
- [[Measurable vs Non-Measurable Disease (RECIST)]]
- [[CTCAE Grade]]
- [[Serious Adverse Event (SAE)]]
- [[Dose-Limiting Toxicity (DLT)]]

**Biomedical**
- [[Anti-Cancer Therapy Categories in Oncology Trials]]
- [[ECOG Performance Status]]
- [[12-Lead Resting ECG]]
- [[Radiological Assessment]]
- [[Xerostomia]]
- [[Anti-Emetic Premedication]]
- [[Infusion-Related and Hypersensitivity Reactions]]
- [[Physical Examination]]

**Statistics**
- [[Adverse Event Ascertainment]]
- [[Follow-up of Adverse Events]]
- [[Intercurrent Event]]
- [[Surrogate Endpoint]]
- [[Best Overall Response]]
- [[Progression-Free Survival (PFS) and Overall Survival (OS)]]
- [[Local (Investigator) vs Central (BICR) Tumour Assessment]]
- [[MTD and RP2D]]
- [[Anti-Tumour Activity]]
- [[End of Treatment vs End of Study]]
- [[Schedule of Assessments]]

**Data standards**
- [[MedDRA]]
- [[SDTM, SDTM IG, and Conformance Rules]]
- [[Action Taken for an Adverse Event]]
- [[Adverse Event Outcome]]
- [[CRF vs Non-CRF (External) Data]]
- [[eCRF Forms (Prostate Cancer Trial)]]
- [[Prior, Concomitant, and Subsequent Treatment]]

**Regulatory & trial conduct**
- [[Investigator's Brochure (IB)]]
- [[IRB and IEC (Ethics Committees)]]
- [[Protocol Amendment]]
- [[Financial Disclosure (Clinical Investigators)]]

## Tumour assessment data flow

How an imaging read becomes an efficacy endpoint, end to end:

**Imaging** ([[Radiological Assessment]]) → criterion: [[RECIST 1.1]] for soft-tissue/nodal, fused with bone [[PCWG3 Criteria]] into [[Modified RECIST 1.1 and PCWG3 Criteria]] for mCRPC → recorded in SDTM **[[RECIST 1.1#Step-by-step derivation (for a programmer)|TU → TR → RS]]** (identity → measurements → response verdict), with **local vs central** reads kept as parallel rows ([[Local (Investigator) vs Central (BICR) Tumour Assessment]]; central arrives as a [[CRF vs Non-CRF (External) Data|non-CRF feed]]) → per-visit response collapses to the per-patient [[Best Overall Response]] → endpoints **ORR / DCR / DoR** and the time-to-event [[Progression-Free Survival (PFS) and Overall Survival (OS)|PFS / OS]] (rPFS in prostate). Criterion and evaluator are **category axes inside one set of domains**, not separate domains.

## Prostate cancer

The disease state is [[Metastatic Castration-Resistant Prostate Cancer (mCRPC)|mCRPC]] (metastatic, progressing despite castrate testosterone). How treatment effect is read out in advanced/mCRPC trials: a [[PSA (Prostate-Specific Antigen)|PSA]] biomarker and [[PSMA PET-CT]] imaging measure disease; bone progression follows [[PCWG3 Criteria]], fused with soft-tissue [[RECIST 1.1]] into the [[Modified RECIST 1.1 and PCWG3 Criteria]] criterion; [[PSA (Prostate-Specific Antigen)|PSA]] response is only a [[Surrogate Endpoint]]; radioligand programs add [[Pharmacokinetics (PK)]] / [[Dosimetry]].

Prostate-specific terms: [[Metastatic Castration-Resistant Prostate Cancer (mCRPC)]] · [[PSA (Prostate-Specific Antigen)]] · [[PSMA PET-CT]] · [[PCWG3 Criteria]] · [[Modified RECIST 1.1 and PCWG3 Criteria]] · [[Pharmacokinetics (PK)]] · [[Dosimetry]] · [[Lutetium-177 (177Lu)]] · [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]].
