From chat, 2026-06-19

Q: MedDRA 的 mapping 一般发生在 raw 还是 SDTM?

A: MedDRA coding (verbatim term → dictionary term) is a data-management / medical-coding
activity that happens UPSTREAM, at the raw / collected-data stage — during the trial, in the
EDC / coding tool, by medical coders (often clinician-reviewed). It is NOT done by SDTM
programming.

- The coder maps the investigator's verbatim term (e.g. AETERM) to a MedDRA LLT, which rolls
  up to PT / SOC, etc. These coded values already live in the operational/raw database.
- SDTM does not perform the mapping; it CARRIES the result: the verbatim term in --TERM
  (e.g. AETERM), the dictionary-derived PT in --DECOD (AEDECOD), the SOC in --BODSYS
  (AEBODSYS), and records the MedDRA dictionary version used.
- So: mapping happens in raw; SDTM is just the standardized representation of an already-coded
  result.
