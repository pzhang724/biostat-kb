---
title: "MedDRA"
type: concept
status: learned
created: 2026-06-18
---

# MedDRA

**Medical Dictionary for Regulatory Activities** (监管活动医学词典) — the standard medical terminology used to **code** adverse events, medical history, indications, etc., for regulatory reporting. Maintained by ICH. It codes **events/conditions**; its medication partner is [[WHODrug]].

Hierarchical (分层) structure:

> **SOC** (System Organ Class, 系统器官分类) → **HLGT** (High Level Group Term) → **HLT** (High Level Term) → **PT** (Preferred Term, 首选术语) → **LLT** (Lowest Level Term, 低位语)

- It lets a term written by the investigator in their own words (verbatim) be coded to a common dictionary, so events can be **tabulated / pooled** (汇总/合并) across patients and studies.
- AE analysis is usually coded at the **PT** level.
- [[CTCAE Grade]] is built on / maps to MedDRA terms.

## Where the mapping happens — raw, not SDTM

MedDRA coding (verbatim term → dictionary term) is a **data-management / medical-coding** (医学编码) activity that happens **upstream (上游), at the raw / collected-data stage** — during the trial, in the EDC (electronic data capture, 电子数据采集) / coding tool, by medical coders (often reviewed by a clinician). **SDTM does not do the mapping; it carries the result.**

- The coder maps the verbatim term (e.g. `AETERM`) to a MedDRA **LLT**, which rolls up (向上归入) to **PT** / **SOC**. These coded values already live in the operational/raw database.
- In SDTM: the verbatim term in `--TERM` (e.g. `AETERM`), the dictionary-derived **PT** in `--DECOD` (`AEDECOD`), the **SOC** in `--BODSYS` (`AEBODSYS`), plus the MedDRA **version** recorded.

The controlled terminology (受控术语) used to code AE/medical-history domains in [[SDTM, SDTM IG, and Conformance Rules]]. A data standard used across [[Oncology]].
