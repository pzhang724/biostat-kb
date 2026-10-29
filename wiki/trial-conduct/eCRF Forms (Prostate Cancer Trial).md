---
title: "eCRF Forms (Prostate Cancer Trial)"
type: concept
status: learned
created: 2026-06-19
---

# eCRF Forms (Prostate Cancer Trial)

The set of [[CRF vs Non-CRF (External) Data|eCRF]] (electronic case report form, 电子病例报告表) forms for an mCRPC prostate trial, grouped by timing; the SDTM domain is in (). Prostate = **male**, so there is **no pregnancy test for the subject** (a partner-pregnancy form may still exist). **Central lab / central imaging** usually come in as **non-CRF feeds**, not typed into the eCRF.

## Screening / Baseline

- **Informed Consent** (知情同意; consent date) · **Inclusion/Exclusion** (`IE`) · **Demographics** (人口学, `DM`)
- **Medical History** (`MH`) · **Disease History / Characteristics** — diagnosis, **Gleason score**, **TNM** stage, sites of metastasis, castration status
- **Prior anti-cancer therapy** — surgery / radiotherapy / systemic (`PR`/`CM`); **Prior & Concomitant Meds** (`CM`)
- **Vital Signs** (`VS`), Height/Weight, [[Physical Examination]] (`PE`), [[ECOG Performance Status]] (`QS`)
- [[12-Lead Resting ECG]] (`EG`)
- Local [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)|labs]] (`LB`); **[[PSA (Prostate-Specific Antigen)|PSA]]** + **Testosterone** (`LB`, to confirm the castrate level)
- **Baseline tumour assessment** — lesion id (`TU`) + measurements (`TR`) + response (`RS`); CT/MRI + bone scan, ± [[PSMA PET-CT]] (see [[RECIST 1.1]] / [[Modified RECIST 1.1 and PCWG3 Criteria]])

## Treatment (each cycle/visit)

- **Study Drug Administration / Dosing / Exposure** (`EX`), including [[Action Taken for an Adverse Event|dose modifications]]; Drug Accountability (药物清点; often in IRT/RTSM, the interactive response / trial supply system, not the CRF)
- **[[Adverse Event Ascertainment|Adverse Events]]** (`AE`); Concomitant Meds (`CM`)
- Vital Signs / targeted PE / ECOG; ECG from time to time (periodic); labs + PSA (`LB`)
- **Tumour assessment** at the scheduled imaging visits (`TU`/`TR`/`RS`)
- **PK sampling** (`PC`/`PP`) if needed (e.g. radioligand)
- **PRO / QoL** (`QS`) — **FACT-P** (Functional Assessment of Cancer Therapy–Prostate), **Brief Pain Inventory (BPI)**, EQ-5D, use of pain drugs/opioids

## End of Treatment

- **EOT form** — date + reason for stopping (see [[End of Treatment vs End of Study]]); final tumour / labs / PE / ECG

## Follow-up

- **Safety follow-up** ([[Follow-up of Adverse Events|AE/SAE]] + continuing con-meds)
- **Disease/progression follow-up** (if PFS is followed after treatment ends)
- **Survival follow-up** = OS status + subsequent anti-cancer therapy (see [[Progression-Free Survival (PFS) and Overall Survival (OS)]])

## Triggered / as-needed

- **[[Serious Adverse Event (SAE)|SAE]] report** · **Death** (date + cause) · **Skeletal-related event (SSE/SRE, 骨相关事件)** — prostate bone mets ([[Clinical Progression]])
- New anti-cancer therapy · **Unscheduled visit** (计划外访视; [[Schedule of Assessments]]) · Protocol deviation (方案偏离) · Partner pregnancy (if applicable)

## Gating ("gate") questions

A **gate** = a **gating / gatekeeper / trigger question** (门控问题) on a form — usually a **Yes/No** that controls whether a later section/log must be filled in.

- e.g. "**Any adverse events? Y/N**" — **No** → the AE log stays empty; **Yes** → the detailed fields open (conditional display, 条件显示).
- CDASH (Clinical Data Acquisition Standards Harmonization, 临床数据采集标准) builds these as the **`--YN`** header questions: `AEYN`, `CMYN`, `MHYN`, `PRYN`…
- **Why it matters:** a **"No" is a positive confirmation that nothing happened** — it separates "nothing to report" from a **blank = missing/not asked**. It also drives **EDC edit checks** (逻辑核查; e.g. `AEYN=Yes` but no AE records → a query, 质疑). So the gate turns *no records* into recorded data that can be checked, and it shows the rest of the form only when needed.

Prostate-specific focus: **PSA + testosterone** (to confirm castrate level); **bone scan (PCWG3 2+2)** combined with soft-tissue RECIST; **pain/opioids + SSE**; **FACT-P/BPI** PROs. The visit grid these forms sit on is the [[Schedule of Assessments]]; a data concept used across [[Oncology]].
