---
title: "Immunogenicity"
type: concept
status: learned
tags: [medical, data-management]
created: 2026-06-20
updated: 2026-06-20
sources: 1
---

# Immunogenicity

**免疫原性** — a therapeutic's ability to provoke an **immune response** in the patient: the body recognizes the drug as foreign and reacts, mainly by producing **anti-drug antibodies (ADA, 抗药抗体)**. Chiefly a concern for **biologics (生物制品)** — large molecules: monoclonal antibodies, fusion proteins, antibody-drug conjugates, enzymes — and more so for non-human/chimeric ones; **small-molecule drugs are rarely immunogenic**.

A subset of ADA are **neutralizing antibodies (NAb, 中和抗体)** that block the drug's active site / function.

## Why it matters

- **Efficacy** — ADA/NAb neutralize the drug or speed its clearance → less exposure, lost activity.
- **Safety** — **hypersensitivity (超敏反应)** / infusion reactions, up to anaphylaxis (see [[Infusion-Related and Hypersensitivity Reactions]]); rarely ADA cross-react with an **endogenous protein** (serious).
- **PK** — ADA alter clearance / half-life, so exposure can drift over time (see [[Pharmacokinetics (PK)]]).

## How it's assessed

A **tiered bioanalytical strategy**: screening assay → confirmatory assay → **titer (滴度)** → neutralizing-antibody assay. Reported as ADA **incidence/prevalence**, titer, **timing** (treatment-emergent / treatment-boosted), and **persistence**. It is a specialty, **[[CRF vs Non-CRF (External) Data|non-CRF]]** (external vendor) lab feed; in CDISC it maps to the **SDTM IS domain** (Immunogenicity Specimen Assessments — see [[SDTM, SDTM IG, and Conformance Rules]]).

**Regulatory** — FDA/EMA/ICH have immunogenicity-assessment guidance; required in biologic development and central to **biosimilars (生物类似药)** (comparative immunogenicity vs the reference product).

Part of [[Oncology]]. Relevant to antibody/ADC agents (see [[Targeted Therapy and Tissue-Agnostic Biomarkers]], [[Anti-Cancer Therapy Categories in Oncology Trials]]).
