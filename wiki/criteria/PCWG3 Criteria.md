---
title: "PCWG3 Criteria"
type: concept
status: learned
tags: [medical, statistics, regulatory]
created: 2026-06-11
updated: 2026-06-19
sources: 4
---

# PCWG3 Criteria

**PCWG3** (Prostate Cancer Working Group 3, 2016; updates PCWG2 2008) is the consensus set of trial-design and endpoint criteria for **advanced / metastatic castration-resistant prostate cancer (mCRPC)**. It exists because [[RECIST 1.1]] alone cannot handle bone-predominant, [[Measurable vs Non-Measurable Disease (RECIST)|non-measurable]] disease.

**How each disease compartment is assessed:**

- **Bone (bone scan)** — the **"2+2 rule"**: progression = ≥2 new lesions, then **confirmed** by ≥2 *additional* new lesions on the next scan. This filters out early bone-scan **flare** (transient apparent worsening that is actually response).
- **Soft tissue / nodes** — assessed by **RECIST 1.1**.
- **[[PSA (Prostate-Specific Antigen)|PSA]]** — report kinetics (waterfall of max decline). **PSA progression** = ≥25% increase **and** ≥2 ng/mL above the nadir, confirmed ≥3 weeks later. PSA-alone decisions are de-emphasized.

**Philosophy shift:** separate "**is the patient still benefiting?**" from "first sign of change" — treat through early PSA/scan changes, and report progression **by mode** (bone vs soft tissue vs PSA vs symptoms) as *separate* endpoints rather than one lumped PD. Both **bone-scan flare** and **PSA flare** can mimic early progression.

**Preferred efficacy endpoints:** **rPFS** (radiographic progression-free survival) and **OS**. This is the framework behind why PSA response is reported but treated only as a [[Surrogate Endpoint|surrogate]].

## How RECIST 1.1 and PCWG3 combine into one decision

The two don't compete — each governs a **different compartment**, and they fold into the composite endpoint **rPFS**:

- **Soft tissue / nodes** → [[RECIST 1.1]] (PD = ≥20% SoD rise from nadir +≥5 mm, or new soft-tissue lesion).
- **Bone** → PCWG3 bone-scan **2+2 rule**.

**Combination logic is OR / earliest-event:** radiographic progression is declared when **either** soft-tissue PD (RECIST) **or** bone PD (2+2) occurs, whichever comes first; death is also an rPFS event. Date nuance: when the bone 2+2 rule is met, the progression date is **back-dated to the first scan** showing the initial 2 new lesions, not the confirmation scan.

**PSA and symptoms stay separate** — PSA progression (≥25% & ≥2 ng/mL above nadir, confirmed) and symptomatic endpoints are reported on their own; you do **not** declare progression on rising PSA alone. The split exists because bone, soft tissue, PSA, and symptoms can move independently (mixed response, flare). **OS** (overall survival) remains the ultimate endpoint.

When a protocol fuses soft-tissue RECIST and bone PCWG3 into a **single named composite criterion**, that criterion (with its fused timepoint matrix) is documented at [[Modified RECIST 1.1 and PCWG3 Criteria]].

## Why progression capture is split (initial vs confirmation)

A progression-tracking table/CRF typically has four columns — **Date Progression Detected (Visit)** · **Criteria for Initial Progression** · **Timing for Confirmation** · **Criteria for Documentation on Confirmatory Scan**. They are the **two-step** confirmed-progression paradigm × (**when / what**):

| Column | Question | Why separate |
|---|---|---|
| Date detected (visit) | **when** first seen | rPFS date is **back-dated to this first scan**, not the confirmation — so it must be recorded distinctly |
| Criteria for initial progression | **what** triggered the first call (e.g. ≥2 new bone lesions; RECIST PD) | progression must be **criteria-based & mode-specific**, not gestalt |
| Timing for confirmation | **when** the confirmatory scan is due (interval later) | the **delay** is what lets transient **flare** / pseudoprogression resolve |
| Criteria on confirmatory scan | **what** confirms it (e.g. ≥2 *additional* new lesions = the second "2") | only a **confirmed** event becomes the rPFS progression |

**Why this way:** a single scan can show *apparent* progression that isn't real — bone-scan **flare**, immunotherapy **pseudoprogression**, measurement noise. Calling PD on the first scan would wrongly pull patients who are actually benefiting. So progression is split into **initial detection → confirmatory scan after an interval**, and because the scored date (initial) differs from the confirmation date, both are captured. It is the CRF form of the **2+2 rule** (same shape as iRECIST **iUPD → iCPD**) and feeds rPFS. See [[Radiological Assessment]] and the fused [[Modified RECIST 1.1 and PCWG3 Criteria]].

## Official reference

Scher HI, Morris MJ, Stadler WM, et al. **Trial design and objectives for castration-resistant prostate cancer: updated recommendations from the Prostate Cancer Clinical Trials Working Group 3.** *J Clin Oncol.* 2016;34(12):1402–1418. doi:10.1200/JCO.2015.64.2702

