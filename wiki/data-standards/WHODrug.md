---
title: "WHODrug"
type: concept
status: learned
tags: [standards, data-management]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# WHODrug

**WHO Drug Global** (WHO-DD) — the standardized dictionary used to **code medications** (药物编码): concomitant, prior, and subsequent drugs, plus substances. It is the medication counterpart to [[MedDRA]], which codes **events/conditions** (AE, medical history).

- Coding maps a verbatim reported drug name to a **standardized Drug Name** + **ATC classification** (Anatomical Therapeutic Chemical classification, 解剖治疗化学分类), so meds can be **tabulated / pooled** across patients and studies.

## Where the mapping happens — raw, not SDTM

Same as MedDRA: WHODrug coding (verbatim drug name → dictionary drug) is a **data-management / medical-coding** activity done **upstream, at the raw / collected-data stage** — during the trial, in the EDC / coding tool, by coders. **SDTM does not perform the mapping; it carries the result.**

- In SDTM ([[Prior, Concomitant, and Subsequent Treatment|CM domain]]): verbatim in `CMTRT`, standardized drug name in `CMDECOD`, drug class (e.g. ATC text) in `CMCLAS`, plus the WHODrug **version** recorded.

The controlled terminology used to code medication domains in [[SDTM, SDTM IG, and Conformance Rules]]. A cross-cutting data standard in [[Oncology]].
