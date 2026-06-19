From chat, 2026-06-19

Q: WHODrug 呢? (mapping 发生在 raw 还是 SDTM?)

A: Same as MedDRA — WHODrug coding (verbatim drug name → standardized drug) is a
data-management / medical-coding activity done UPSTREAM at the raw / collected-data stage,
during the trial in the EDC / coding tool by coders. SDTM does not do the coding; it carries
the result.

- WHODrug (WHO Drug Global / WHO-DD) is the dictionary for coding MEDICATIONS — concomitant,
  prior, subsequent meds, and substances. Counterpart to MedDRA, which codes EVENTS/conditions
  (AE, medical history).
- Coder maps the verbatim reported drug name (e.g. CMTRT) to a standardized Drug Name + ATC
  classification (ATC = Anatomical Therapeutic Chemical classification, 解剖治疗化学分类).
- In SDTM (CM domain): verbatim in CMTRT, standardized drug name in CMDECOD, drug class
  (e.g. ATC text) in CMCLAS, plus the WHODrug version recorded.
- So: WHODrug mapping happens in raw; SDTM is just the standardized representation.
