---
title: "eCRF Forms (Prostate Cancer Trial)"
type: concept
status: learned
tags: [data-management, trial-conduct]
created: 2026-06-19
updated: 2026-06-19
sources: 2
---

# eCRF Forms (Prostate Cancer Trial)

The set of [[CRF vs Non-CRF (External) Data|eCRF]] forms for a (mCRPC) prostate trial, grouped by timing; SDTM domain in (). Prostate = **male**, so **no subject pregnancy test** (a partner-pregnancy form may still exist). **Central lab / central imaging** usually arrive as **non-CRF feeds**, not keyed on the eCRF.

## Screening / Baseline

- **Informed Consent** (consent date) · **Inclusion/Exclusion** (`IE`) · **Demographics** (`DM`)
- **Medical History** (`MH`) · **Disease History / Characteristics** — diagnosis, **Gleason score**, **TNM** stage, metastatic sites, castration status
- **Prior anti-cancer therapy** — surgery / radiotherapy / systemic (`PR`/`CM`); **Prior & Concomitant Meds** (`CM`)
- **Vital Signs** (`VS`), Height/Weight, [[Physical Examination]] (`PE`), [[ECOG Performance Status]] (`QS`)
- [[12-Lead Resting ECG]] (`EG`)
- Local [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)|labs]] (`LB`); **[[PSA (Prostate-Specific Antigen)|PSA]]** + **Testosterone** (`LB`, confirm castrate level)
- **Tumour assessment baseline** — lesion id (`TU`) + measurements (`TR`) + response (`RS`); CT/MRI + bone scan, ± [[PSMA PET-CT]] (see [[RECIST 1.1]] / [[Modified RECIST 1.1 and PCWG3 Criteria]])

## Treatment (each cycle/visit)

- **Study Drug Administration / Dosing / Exposure** (`EX`) incl. [[Action Taken for an Adverse Event|dose modifications]]; Drug Accountability (often IRT/RTSM, not CRF)
- **[[Adverse Event Ascertainment|Adverse Events]]** (`AE`); Concomitant Meds (`CM`)
- Vital Signs / targeted PE / ECOG; periodic ECG; labs + PSA (`LB`)
- **Tumour assessment** at scheduled imaging visits (`TU`/`TR`/`RS`)
- **PK sampling** (`PC`/`PP`) if applicable (e.g. radioligand)
- **PRO / QoL** (`QS`) — **FACT-P**, **Brief Pain Inventory (BPI)**, EQ-5D, analgesic/opioid use

## End of Treatment

- **EOT form** — date + reason for discontinuation (see [[End of Treatment vs End of Study]]); final tumour / labs / PE / ECG

## Follow-up

- **Safety follow-up** ([[Follow-up of Adverse Events|AE/SAE]] + con-med continuation)
- **Disease/progression follow-up** (if PFS followed off-treatment)
- **Survival follow-up** = OS status + subsequent anti-cancer therapy (see [[Progression-Free Survival (PFS) and Overall Survival (OS)]])

## Triggered / as-needed

- **[[Serious Adverse Event (SAE)|SAE]] report** · **Death** (date + cause) · **Skeletal-related event (SSE/SRE)** — prostate bone mets ([[Clinical Progression]])
- New anti-cancer therapy · **Unscheduled visit** ([[Schedule of Assessments]]) · Protocol deviation · Partner pregnancy (if applicable)

## Gating ("gate") questions

A **gate** = a **gating / gatekeeper / trigger question** on a form — usually a **Yes/No** that controls whether a downstream section/log must be filled.

- e.g. "**Any adverse events? Y/N**" — **No** → the AE log stays empty; **Yes** → the detailed fields open (conditional display).
- CDASH implements these as the **`--YN`** header questions: `AEYN`, `CMYN`, `MHYN`, `PRYN`…
- **Why it matters:** a **"No" is positive confirmation that nothing occurred** — it distinguishes "nothing to report" from a **blank = missing/not asked**. It also drives **EDC edit checks** (e.g. `AEYN=Yes` but no AE records → query). So the gate turns *absence of records* into recorded, verifiable data and conditionally reveals the rest of the form.

Prostate-specific emphasis: **PSA + testosterone** (castrate confirm); **bone scan (PCWG3 2+2)** fused with soft-tissue RECIST; **pain/opioid + SSE**; **FACT-P/BPI** PROs. The visit grid these forms hang on is the [[Schedule of Assessments]]; a cross-cutting data concept in [[Oncology]].
