---
title: "PCWG3 Criteria"
type: concept
status: learned
created: 2026-06-11
---

# PCWG3 Criteria

**PCWG3** (Prostate Cancer Working Group 3, 2016; updates PCWG2 from 2008) is the consensus (共识) set of trial-design and endpoint criteria for **advanced / metastatic castration-resistant prostate cancer (mCRPC)**. It exists because [[RECIST 1.1]] alone cannot handle disease that is mainly in bone (bone-predominant) and [[Measurable vs Non-Measurable Disease (RECIST)|non-measurable]].

**How each disease compartment (部位) is assessed:**

- **Bone (bone scan)** — the **"2+2 rule"**: progression = ≥2 new lesions, then **confirmed** by ≥2 *more* new lesions on the next scan. This filters out early bone-scan **flare** (闪烁现象: a short-lived apparent worsening that is actually response).
- **Soft tissue / nodes** — assessed by **RECIST 1.1**.
- **[[PSA (Prostate-Specific Antigen)|PSA]]** — report the kinetics (waterfall plot 瀑布图 of the maximum fall). **PSA progression** = ≥25% increase **and** ≥2 ng/mL above the nadir (最低值), confirmed ≥3 weeks later. Decisions based on PSA alone are discouraged.

**Change in thinking (philosophy shift):** separate "**is the patient still benefiting?**" from "the first sign of change" — keep treating through early PSA/scan changes, and report progression **by mode** (bone vs soft tissue vs PSA vs symptoms) as *separate* endpoints, not as one combined PD (progressive disease, 疾病进展). Both **bone-scan flare** and **PSA flare** can look like (mimic) early progression.

**Preferred efficacy endpoints:** **rPFS** (radiographic progression-free survival, 影像学无进展生存期) and **OS** (overall survival, 总生存期). This framework is why PSA response is reported but treated only as a [[Surrogate Endpoint|surrogate]].

## How RECIST 1.1 and PCWG3 combine into one decision

The two don't compete — each covers a **different compartment**, and they fold into the composite endpoint **rPFS**:

- **Soft tissue / nodes** → [[RECIST 1.1]] (PD = ≥20% rise in SoD, sum of diameters 直径总和, from the nadir + ≥5 mm, or a new soft-tissue lesion).
- **Bone** → the PCWG3 bone-scan **2+2 rule**.

**Combination logic is OR / earliest event:** radiographic progression is declared when **either** soft-tissue PD (RECIST) **or** bone PD (2+2) happens, whichever comes first; death is also an rPFS event. Date detail: when the bone 2+2 rule is met, the progression date is **back-dated to the first scan** that showed the first 2 new lesions, not to the confirmation scan.

**PSA and symptoms stay separate** — PSA progression (≥25% & ≥2 ng/mL above the nadir, confirmed) and symptom endpoints ([[Clinical Progression]]) are reported on their own; you do **not** declare progression on rising PSA alone. The split exists because bone, soft tissue, PSA and symptoms can move independently (mixed response, flare). **OS** stays the ultimate endpoint.

When a protocol combines soft-tissue RECIST and bone PCWG3 into a **single named composite criterion**, that criterion (with its combined timepoint matrix) is described at [[Modified RECIST 1.1 and PCWG3 Criteria]].

## Why progression capture is split (initial vs confirmation)

A progression-tracking table/CRF usually has four columns — **Date Progression Detected (Visit)** · **Criteria for Initial Progression** · **Timing for Confirmation** · **Criteria for Documentation on Confirmatory Scan**. They are the **two-step** confirmed-progression approach × (**when / what**):

| Column | Question | Why separate |
|---|---|---|
| Date detected (visit) | **when** it was first seen | the rPFS date is **back-dated to this first scan**, not the confirmation — so it must be recorded separately |
| Criteria for initial progression | **what** triggered the first call (e.g. ≥2 new bone lesions; RECIST PD) | progression must be **based on criteria and specific to a mode**, not an overall impression (gestalt, 整体印象) |
| Timing for confirmation | **when** the confirmatory scan is due (some interval later) | the **delay** gives a short-lived **flare** / pseudoprogression (假性进展) time to resolve |
| Criteria on confirmatory scan | **what** confirms it (e.g. ≥2 *more* new lesions = the second "2") | only a **confirmed** event becomes the rPFS progression |

**Why two scans (来两次):** one snapshot cannot separate "growing because the cancer is winning" from a false alarm — bone-scan **flare** (healing bone-building cells, osteoblasts 成骨细胞, light up *more* early on when treatment works), immunotherapy **pseudoprogression**, or measurement noise. The only way to tell is the **direction of change over time**: scan again after a delay — if it keeps getting worse → real (confirmed); if it stabilizes/improves → it was flare/pseudo, keep treating. The second visit is the control that filters out these short-lived effects (and the delay must be long enough for flare to resolve).

**Why this way:** a single scan can show *apparent* progression that isn't real — bone-scan **flare**, immunotherapy **pseudoprogression**, measurement noise. Calling PD on the first scan would wrongly take patients off treatment who are actually benefiting. So progression is split into **initial detection → confirmatory scan after an interval**; and because the scored date (initial) is different from the confirmation date, both are recorded. It is the CRF form of the **2+2 rule** (the same shape as iRECIST **iUPD → iCPD**, immune unconfirmed → immune confirmed progressive disease) and it feeds rPFS. See [[Radiological Assessment]] and the combined [[Modified RECIST 1.1 and PCWG3 Criteria]].

## Official reference

Scher HI, Morris MJ, Stadler WM, et al. **Trial design and objectives for castration-resistant prostate cancer: updated recommendations from the Prostate Cancer Clinical Trials Working Group 3.** *J Clin Oncol.* 2016;34(12):1402–1418. doi:10.1200/JCO.2015.64.2702
