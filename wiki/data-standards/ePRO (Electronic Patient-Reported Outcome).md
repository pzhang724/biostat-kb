---
title: "ePRO (Electronic Patient-Reported Outcome)"
type: concept
status: learned
tags: [data-management, statistics]
created: 2026-06-21
updated: 2026-06-21
sources: 2
---

# ePRO (Electronic Patient-Reported Outcome)

**PRO（患者报告结局）** = any outcome reported **directly by the patient**, without clinician interpretation — symptoms, pain, function, quality of life. **ePRO** = a PRO **captured electronically** (app / tablet / web / handheld device; sometimes **BYOD（自带设备）**). It sits under **eCOA（electronic clinical outcome assessment）**, the umbrella also covering clinician-reported (ClinRO), observer-reported (ObsRO), and performance (PerfO) outcomes.

## The "e" is just the mode

The defining thing is **PRO, not the electronics**. A **paper** patient diary / questionnaire is still a PRO; ePRO only changes the **capture medium** (and improves data quality) — it does not change *whether* something is a PRO. The test for a PRO = the **source is the patient**, reported **without clinician / observer interpretation**.

**Is a questionnaire a PRO?** Only if the patient is the respondent:
- **Patient-completed** (ACQ-6, AQLQ, EQ-5D, FACT-P, BPI) = **PRO**.
- **Clinician-rated / judged** (e.g. [[ECOG Performance Status]]) = **ClinRO**, not a PRO.
- **Caregiver / observer-completed** = **ObsRO**.

Even an interviewer-administered questionnaire stays a PRO if the interviewer only records the patient's own answers verbatim, adding no judgment.

## Why it's needed

- **Only the patient can report it** — subjective experience (symptoms, pain, QoL) the clinician can't measure objectively. Many key endpoints *are* PROs (asthma [[Asthma Patient-Reported Outcomes (Symptom Diary, ACQ-6, AQLQ, EQ-5D)|symptom diary / ACQ / AQLQ / EQ-5D]]; prostate FACT-P / BPI).
- **Electronic beats paper** — timestamps stop after-the-fact backfilling ("parking-lot" entries), real-time compliance reminders, **edit checks（逻辑校验）**, fewer transcription errors, an **audit trail（稽查轨迹）**, and better completeness; FDA PRO / eCOA guidance favors it.
- **Regulatory / patient-experience push（PFDD）** → ePRO is increasingly a **primary / key-secondary endpoint**.

## Does it go into EDC?

**Usually no.** It is **not site-keyed into the EDC / eCRF** — the **patient enters it directly** into a separate **eCOA / ePRO system** (often a specialist vendor). So ePRO is **non-CRF / external data**, in the same bucket as central lab and imaging core-lab feeds (see [[CRF vs Non-CRF (External) Data]]).

- Flows in via a **Data Transfer Agreement（数据传输协议）** → loaded to the clinical database → **reconciled（核对）** → mapped to **SDTM** (questionnaires → the **QS** domain, with QRS supplements). The site does **not** transcribe it.
- Caveat: some EDC platforms bundle an eCOA module, but conceptually ePRO = a **direct-from-patient external feed**, not a site-entered CRF.

Related: [[CRF vs Non-CRF (External) Data]] · [[Asthma Patient-Reported Outcomes (Symptom Diary, ACQ-6, AQLQ, EQ-5D)]] · [[eCRF Forms (Prostate Cancer Trial)]] · [[SDTM, SDTM IG, and Conformance Rules]].
