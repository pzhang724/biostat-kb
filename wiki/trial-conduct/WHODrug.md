---
title: "WHODrug"
type: concept
status: learned
created: 2026-06-19
---

# WHODrug

**WHO Drug Global** (WHO-DD, WHO Drug Dictionary, WHO 药物词典) — the standard dictionary used to **code medications** (药物编码): concomitant, prior and subsequent drugs, plus other substances. It is the medication partner of [[MedDRA]], which codes **events/conditions** (AE, medical history).

- Coding maps the drug name exactly as reported (verbatim, 原文) to a **standard Drug Name** + **ATC classification** (Anatomical Therapeutic Chemical classification, 解剖治疗化学分类), so medications can be **tabulated / pooled** (汇总/合并) across patients and studies.

## Where the mapping happens — raw, not SDTM

Same as MedDRA: WHODrug coding (verbatim drug name → dictionary drug) is a **data-management / medical-coding** (医学编码) activity done **upstream (上游), at the raw / collected-data stage** — during the trial, in the EDC (electronic data capture, 电子数据采集) / coding tool, by coders. **SDTM does not do the mapping; it carries the result.**

- In SDTM ([[Prior, Concomitant, and Subsequent Treatment|CM domain]]): the verbatim name in `CMTRT`, the standard drug name in `CMDECOD`, the drug class (e.g. ATC text) in `CMCLAS`, plus the WHODrug **version** recorded.

The controlled terminology (受控术语) used to code medication domains in [[SDTM, SDTM IG, and Conformance Rules]]. A data standard used across [[Oncology]].
