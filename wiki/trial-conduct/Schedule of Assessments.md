---
title: "Schedule of Assessments"
type: concept
status: learned
created: 2026-06-18
---

# Schedule of Assessments

The **Schedule of Assessments / Activities (SoA, 评估计划表 / 流程表)** is the master **table** in a clinical-trial protocol. It sets out **which** procedures/assessments are done at **which** visits/timepoints across the whole study — the **operational backbone** (操作骨架) of the protocol.

## Layout (a grid)

- **Rows = assessments/procedures**: informed consent, eligibility, demographics, medical history, vital signs, [[Physical Examination|physical exam]], [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)|labs (heme/chem)]], [[12-Lead Resting ECG|ECG]], tumor imaging ([[RECIST 1.1]]/[[PCWG3 Criteria]]), [[Pharmacokinetics (PK)|PK]] sampling, dosing, collection of AEs and concomitant medications, PRO/QoL, survival follow-up…
- **Columns = visits/timepoints**, grouped by study period: Screening → Treatment (by cycle/day, e.g. C1D1 = cycle 1 day 1, C1D8…) → EOT (end of treatment) → Safety follow-up → Long-term/survival follow-up → EOS (end of study).
- **Cells = "X"** where an assessment happens at that visit; **footnotes** (脚注) give the **visit windows** (访视窗; ±days), conditions, and details.

Note: the grid sets the timing of **scheduled findings** (labs, ECG, imaging — taken at a fixed timepoint). **AEs are not on the grid** — they are driven by events and carry their own onset date, even though they are *asked about* (solicited) at every visit. See [[SDTM, SDTM IG, and Conformance Rules#Events vs Findings timing — how an AE's occurrence is timed|Events vs Findings timing]].

```
Assessment        │ Screen │ C1D1 │ C1D8 │ … │ EOT │ F/U │ EOS
Informed consent  │   X    │      │      │   │     │     │
Vital signs       │   X    │  X   │  X   │ … │  X  │  X  │  X
Labs (heme/chem)  │   X    │  X   │  X   │ … │  X  │  X  │
Tumor imaging     │   X    │      │      │ q8wk │ X │     │
PK sampling       │        │  X   │  X   │   │     │     │
Survival status   │        │      │      │   │     │  X  │  X
```

## What to read first (a statistician's lens)

Read it **endpoint first**, not top to bottom. Priority order:

1. **The rows for the primary & key-secondary endpoints — and their timing / frequency.** This is the most important thing: *where and how often* the endpoint is measured (tumor imaging every 8–9 weeks, q8–9 wk; FEV1 at week 24). It drives the **analysis windows**, the **bias from the assessment schedule** (评估时间偏倚), and — for time-to-event endpoints like PFS — the **interval censoring (区间删失)** (you can only detect progression at a scheduled scan).
2. **The period / epoch structure** (阶段结构; the columns): Screening → Treatment → EOT → follow-up (safety + survival) → EOS — the backbone of the timeline and the **follow-up / censoring logic** ([[End of Treatment vs End of Study|EOT/EOS]]).
3. **Baseline definition** — which row/visit is the **last assessment before dosing**; every change-from-baseline endpoint depends on it.
4. **Visit windows (±days)** — they define the **analysis windows** and what counts as on schedule.
5. **Footnotes** — the key rules that change the analysis and are easy to miss: conditions ("only if…"), **method / evaluator** (local vs central, see [[Local (Investigator) vs Central (BICR) Tumour Assessment]]), fasting / **triplicate** / **time-matched to PK**, repeat if abnormal.

**Bottom line**: find the primary / key endpoints; read exactly *when and how often* they are collected, plus the **windows and footnotes** that govern them; then the **period structure** for follow-up and censoring.

## Why it matters (esp. for a biostatistician)

- It defines the **timing** of every data collection → it directly drives the **analysis windows** and how endpoints are measured (e.g. how often tumors are assessed affects the interval censoring of PFS; PK sampling times define the concentration-time curve).
- It maps to the **SDTM Trial Design / visit** structure (TV trial visits / SV subject visits, `VISIT`/`VISITNUM`) and to `define.xml` — see [[SDTM, SDTM IG, and Conformance Rules]].
- **Visit windows** give flexibility in operations while keeping the data comparable across patients.
- **ICH M11** (the harmonized protocol template, 统一方案模板) standardizes the name as *"Schedule of Activities (SoA)"*.

## Why there are unscheduled visits

An **unscheduled visit (计划外访视)** is a visit that is **not** on this planned grid. It is triggered by a clinical need that comes up **between** scheduled visits — because a fixed grid cannot predict every clinical event. Typical reasons:

- **Driven by an AE** — to assess/manage a new or worsening adverse event; extra safety monitoring.
- **Confirm / repeat a finding** — repeat an abnormal lab to confirm a toxicity grade, recheck the [[12-Lead Resting ECG|ECG/QTc]], or a **confirmatory scan** for suspected progression (the confirmation logic in [[PCWG3 Criteria]]).
- **A dose-modification decision** — data needed to hold / reduce / restart.
- **Started by the patient** — the patient feels unwell and comes in off schedule.

The data is **still fully recorded** (not thrown away): in SDTM it goes into the visit structure (**SV**) using the convention for unscheduled visits (`VISIT` = "UNSCHEDULED", a decimal `VISITNUM` like 5.1/5.2) — see [[SDTM, SDTM IG, and Conformance Rules#Visit numbering: VISITNUM (SDTM) vs AVISITN (ADaM)|VISITNUM vs AVISITN]]. In the analysis, unscheduled assessments are brought in through **visit windows** — mapped to the nearest planned analysis timepoint, or used as a confirmation / worst-case value — so they don't break the by-visit summaries built on the scheduled grid. The SoA often has an explicit **"Unscheduled" column** that lists which assessments may be done when needed.

Its periods line up with the [[End of Treatment vs End of Study|EOT/EOS]] milestones: the SoA shows exactly which assessments continue after EOT, into follow-up, up to EOS. A trial-conduct concept in [[Oncology]].
