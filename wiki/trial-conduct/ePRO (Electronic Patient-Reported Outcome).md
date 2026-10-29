---
title: "ePRO (Electronic Patient-Reported Outcome)"
type: concept
status: learned
created: 2026-06-21
---

# ePRO (Electronic Patient-Reported Outcome)

**PRO (患者报告结局)** = any outcome reported **directly by the patient**, without a clinician's interpretation — symptoms, pain, function, quality of life. **ePRO** = a PRO **recorded electronically** (app / tablet / web / handheld device; sometimes **BYOD**, bring your own device, 自带设备). It sits under **eCOA (electronic clinical outcome assessment, 电子临床结局评估)**, the umbrella that also covers clinician-reported (ClinRO), observer-reported (ObsRO) and performance (PerfO) outcomes.

## The "e" is just the mode

The defining thing is **PRO, not the electronics**. A **paper** patient diary / questionnaire is still a PRO; ePRO only changes the **way it is recorded** (capture medium) and improves data quality — it does not change *whether* something is a PRO. The test for a PRO = the **source is the patient**, reported **without interpretation by a clinician / observer**.

**Is a questionnaire a PRO?** Only if the patient is the one who answers:

- **Completed by the patient** (ACQ-6, AQLQ, EQ-5D, FACT-P Functional Assessment of Cancer Therapy–Prostate, BPI Brief Pain Inventory) = **PRO**.
- **Rated / judged by a clinician** (e.g. [[ECOG Performance Status]]) = **ClinRO**, not a PRO.
- **Completed by a caregiver / observer** = **ObsRO**.

Even a questionnaire read out by an interviewer stays a PRO if the interviewer only writes down the patient's own answers word for word (verbatim), adding no judgment.

## Why it's needed

- **Only the patient can report it** — subjective (主观) experience (symptoms, pain, QoL) that the clinician cannot measure objectively. Many key endpoints *are* PROs (asthma [[Asthma Patient-Reported Outcomes (Symptom Diary, ACQ-6, AQLQ, EQ-5D)|symptom diary / ACQ / AQLQ / EQ-5D]]; prostate FACT-P / BPI).
- **Electronic is better than paper** — timestamps stop entries filled in later from memory (backfilling; "parking-lot" entries 停车场补填), real-time reminders to complete, **edit checks (逻辑校验)**, fewer copying errors, an **audit trail (稽查轨迹)**, and better completeness; FDA PRO / eCOA guidance favors it.
- **A push from regulators / patient experience (PFDD, patient-focused drug development, 以患者为中心的药物研发)** → ePRO is more and more a **primary / key-secondary endpoint**.

## Does it go into EDC?

**Usually no.** The site does **not key it into the EDC (electronic data capture, 电子数据采集) / eCRF** — the **patient enters it directly** into a separate **eCOA / ePRO system** (often from a specialist vendor). So ePRO is **non-CRF / external data**, in the same group as central lab and imaging core-lab feeds (see [[CRF vs Non-CRF (External) Data]]).

- It comes in under a **Data Transfer Agreement (数据传输协议)** → loaded into the clinical database → **reconciled (核对)** → mapped to **SDTM** (questionnaires → the **QS** domain, with QRS supplements; QRS = questionnaires, ratings and scales). The site does **not** copy it over.
- Caveat: some EDC platforms include an eCOA module, but in concept ePRO = an **external feed that comes straight from the patient**, not a CRF entered by the site.

Related: [[CRF vs Non-CRF (External) Data]] · [[Asthma Patient-Reported Outcomes (Symptom Diary, ACQ-6, AQLQ, EQ-5D)]] · [[eCRF Forms (Prostate Cancer Trial)]] · [[SDTM, SDTM IG, and Conformance Rules]].
