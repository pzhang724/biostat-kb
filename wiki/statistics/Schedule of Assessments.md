---
title: "Schedule of Assessments"
type: concept
status: learned
tags: [trial-conduct, statistics, data-management]
created: 2026-06-18
updated: 2026-06-18
sources: 1
---

# Schedule of Assessments

The **Schedule of Assessments / Activities (SoA, 评估计划表 / 流程表)** is the master **table** in a clinical-trial protocol laying out **which** procedures/assessments are performed at **which** visits/timepoints across the whole study — the **operational backbone** of the protocol.

## Layout (a grid)

- **Rows = assessments/procedures**: informed consent, eligibility, demographics, medical history, vital signs, physical exam, labs (heme/chem), [[12-Lead Resting ECG|ECG]], tumor imaging ([[RECIST 1.1]]/[[PCWG3 Criteria]]), [[Pharmacokinetics (PK)|PK]] sampling, dosing, AE & concomitant-med collection, PRO/QoL, survival follow-up…
- **Columns = visits/timepoints**, grouped by study period: Screening → Treatment (by cycle/day, e.g. C1D1, C1D8…) → EOT → Safety follow-up → Long-term/survival follow-up → EOS.
- **Cells = "X"** where an assessment occurs at that visit; **footnotes** carry **visit windows** (±days), conditions, and details.

```
Assessment        │ Screen │ C1D1 │ C1D8 │ … │ EOT │ F/U │ EOS
Informed consent  │   X    │      │      │   │     │     │
Vital signs       │   X    │  X   │  X   │ … │  X  │  X  │  X
Labs (heme/chem)  │   X    │  X   │  X   │ … │  X  │  X  │
Tumor imaging     │   X    │      │      │ q8wk │ X │     │
PK sampling       │        │  X   │  X   │   │     │     │
Survival status   │        │      │      │   │     │  X  │  X
```

## Why it matters (esp. for a biostatistician)

- Defines the **timing** of every data collection → directly drives **analysis windows** and endpoint measurement (e.g. tumor-assessment frequency affects PFS interval-censoring; PK sampling times define the concentration-time curve).
- Maps to the **SDTM Trial Design / visit** structure (TV/SV, `VISIT`/`VISITNUM`) and to `define.xml` — see [[SDTM, SDTM IG, and Conformance Rules]].
- **Visit windows** give operational flexibility while keeping data comparable across patients.
- **ICH M11** (the harmonized protocol template) standardizes the name as *"Schedule of Activities (SoA)"*.

Its periods align with the [[End of Treatment vs End of Study|EOT/EOS]] milestones: the SoA shows exactly which assessments continue after EOT into follow-up up to EOS. A trial-conduct concept in [[Oncology]].
