---
title: "Schedule of Assessments"
type: concept
status: learned
tags: [trial-conduct, statistics, data-management]
created: 2026-06-18
updated: 2026-06-19
sources: 2
---

# Schedule of Assessments

The **Schedule of Assessments / Activities (SoA, 评估计划表 / 流程表)** is the master **table** in a clinical-trial protocol laying out **which** procedures/assessments are performed at **which** visits/timepoints across the whole study — the **operational backbone** of the protocol.

## Layout (a grid)

- **Rows = assessments/procedures**: informed consent, eligibility, demographics, medical history, vital signs, [[Physical Examination|physical exam]], [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)|labs (heme/chem)]], [[12-Lead Resting ECG|ECG]], tumor imaging ([[RECIST 1.1]]/[[PCWG3 Criteria]]), [[Pharmacokinetics (PK)|PK]] sampling, dosing, AE & concomitant-med collection, PRO/QoL, survival follow-up…
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

## Why there are unscheduled visits (计划外访视)

An **unscheduled visit** is one **not** on this planned grid, triggered by a clinical need that arises **between** scheduled visits — because a fixed grid can't anticipate every clinical event. Typical reasons:

- **AE-driven** — assess/manage a new or worsening adverse event; extra safety monitoring.
- **Confirm / repeat a finding** — repeat an abnormal lab to confirm a toxicity grade, recheck [[12-Lead Resting ECG|ECG/QTc]], or a **confirmatory scan** for suspected progression (the confirmation logic in [[PCWG3 Criteria]]).
- **Dose-modification decision** — data needed to hold / reduce / resume.
- **Patient-initiated** — patient feels unwell and comes in off-schedule.

The data is **still fully captured** (not discarded): in SDTM it goes in the visit structure (**SV**) with the unscheduled convention (`VISIT` = "UNSCHEDULED", decimal `VISITNUM` like 5.1/5.2) — see [[SDTM, SDTM IG, and Conformance Rules#Visit numbering: VISITNUM (SDTM) vs AVISITN (ADaM)|VISITNUM vs AVISITN]]. Analytically, unscheduled assessments are folded in via **visit windows** — mapped to the nearest planned analysis timepoint, or used as a confirmation / worst-case value — so they don't break the by-visit summaries built on the scheduled grid. The SoA often has an explicit **"Unscheduled" column** listing which assessments may be done as-needed.

Its periods align with the [[End of Treatment vs End of Study|EOT/EOS]] milestones: the SoA shows exactly which assessments continue after EOT into follow-up up to EOS. A trial-conduct concept in [[Oncology]].
