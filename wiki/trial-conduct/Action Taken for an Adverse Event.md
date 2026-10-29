---
title: "Action Taken for an Adverse Event"
type: concept
status: learned
created: 2026-06-19
---

# Action Taken for an Adverse Event

How an AE was **managed** — recorded on the AE record as **two separate fields** (SDTM AE domain). Don't mix them up with severity, seriousness or outcome.

## 1. Action taken with study treatment — `AEACN`

What was done to the **study drug** because of the AE. Controlled-terminology values:

- **DOSE NOT CHANGED** (剂量未变)
- **DOSE REDUCED** (减量)
- **DOSE INCREASED** (增量)
- **DRUG INTERRUPTED** (暂停 — a temporary hold)
- **DRUG WITHDRAWN** (永久停药 — permanent discontinuation)
- **NOT APPLICABLE**
- **UNKNOWN**

## 2. Other action taken — `AEACNOTH`

Everything done **besides** changing the study drug: concomitant medication / treatment given for the AE (合并用药), non-drug therapy, a procedure / surgery, hospitalization, etc. This is the supportive/corrective (支持/纠正性) management.

## Who decides — the site investigator, in real time

Action taken is the real-time clinical decision of the treating **site investigator** (a physician) at the point of care. They manage the patient and choose hold / reduce / withdraw + any other treatment, then record it on the eCRF (electronic case report form, 电子病例报告表). The protocol's **dose-modification rules** are guardrails (护栏), and some actions (e.g. permanent discontinuation for a defined event) may be required by the protocol — but applying them to the patient in front of them is the investigator's judgment, not the sponsor's or the statistician's. The sponsor / medical monitor (医学监查员) may be consulted for serious cases, but the bedside decision belongs to the investigator. (How the AE got onto the record in the first place is [[Adverse Event Ascertainment]].)

## Separate from other AE axes

Action taken is independent of:

- **Outcome** — [[Adverse Event Outcome|`AEOUT`]]: recovered/resolved, recovering/resolving, not recovered, recovered with sequelae, fatal, unknown.
- **Severity** — the [[CTCAE Grade]] (intensity).
- **Seriousness** — the [[Serious Adverse Event (SAE)]] criteria.
- **Causality** (因果关系) — related vs not.

The **grade usually drives the action**: a grade ≥3 toxicity triggers interrupt / reduce per the protocol's dose-modification rules (the same threshold logic behind a [[Dose-Limiting Toxicity (DLT)]]). AE terms come from [[MedDRA]]; the record lives in the AE domain of [[SDTM, SDTM IG, and Conformance Rules|SDTM]]. A safety-data concept used across [[Oncology]].
