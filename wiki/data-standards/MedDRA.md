---
title: "MedDRA"
type: concept
status: learned
tags: [standards, regulatory]
created: 2026-06-18
updated: 2026-06-19
sources: 2
---

# MedDRA

**Medical Dictionary for Regulatory Activities** (监管活动医学词典) — the standardized medical terminology used to **code** adverse events, medical history, indications, etc., for regulatory reporting. Maintained by ICH. Codes **events/conditions**; the medication counterpart is [[WHODrug]].

Hierarchical structure:

> **SOC** (System Organ Class) → **HLGT** → **HLT** → **PT** (Preferred Term) → **LLT** (Lowest Level Term)

- Lets a verbatim investigator term be coded to a common dictionary, so events can be **tabulated / pooled** across patients and studies.
- AE analysis is typically coded to the **PT** level.
- [[CTCAE Grade]] is built on / maps to MedDRA terms.

## Where the mapping happens — raw, not SDTM

MedDRA coding (verbatim term → dictionary term) is a **data-management / medical-coding** (医学编码) activity that happens **upstream, at the raw / collected-data stage** — during the trial, in the EDC / coding tool, by medical coders (often clinician-reviewed). **SDTM does not perform the mapping; it carries the result.**

- The coder maps the verbatim term (e.g. `AETERM`) to a MedDRA **LLT**, which rolls up to **PT** / **SOC**. These coded values already live in the operational/raw database.
- In SDTM: verbatim term in `--TERM` (e.g. `AETERM`), dictionary-derived **PT** in `--DECOD` (`AEDECOD`), **SOC** in `--BODSYS` (`AEBODSYS`), plus the MedDRA **version** recorded.

The controlled terminology used to code AE/medical-history domains in [[SDTM, SDTM IG, and Conformance Rules]]. A cross-cutting data standard in [[Oncology]].
