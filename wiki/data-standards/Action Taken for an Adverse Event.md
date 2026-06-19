---
title: "Action Taken for an Adverse Event"
type: concept
status: learned
tags: [data-management, trial-conduct]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# Action Taken for an Adverse Event

How an AE was **managed** — recorded on the AE record as **two separate fields** (SDTM AE domain). Don't conflate them with severity, seriousness, or outcome.

## 1. Action taken with study treatment — `AEACN`

What was done to the **study drug** because of the AE. Controlled-terminology values:

- **DOSE NOT CHANGED** (剂量未变)
- **DOSE REDUCED** (减量)
- **DOSE INCREASED** (增量)
- **DRUG INTERRUPTED** (暂停 — temporary hold)
- **DRUG WITHDRAWN** (永久停药 — permanent discontinuation)
- **NOT APPLICABLE**
- **UNKNOWN**

## 2. Other action taken — `AEACNOTH`

Everything done **besides** adjusting the study drug: concomitant medication / treatment given for the AE (合并用药), non-drug therapy, a procedure / surgery, hospitalization, etc. This is the supportive/corrective management.

## Separate from other AE axes

Action taken is independent of:

- **Outcome** — `AEOUT`: recovered/resolved, recovering/resolving, not recovered, recovered with sequelae, fatal, unknown.
- **Severity** — the [[CTCAE Grade]] (intensity).
- **Seriousness** — the [[Serious Adverse Event (SAE)]] criteria.
- **Causality** — related vs not.

The **grade typically drives the action**: a grade ≥3 toxicity triggers interrupt / reduce per the protocol's dose-modification rules (the same threshold logic behind a [[Dose-Limiting Toxicity (DLT)]]). AE terms come from [[MedDRA]]; the record lives in the AE domain of [[SDTM, SDTM IG, and Conformance Rules|SDTM]]. A cross-cutting safety-data concept in [[Oncology]].
