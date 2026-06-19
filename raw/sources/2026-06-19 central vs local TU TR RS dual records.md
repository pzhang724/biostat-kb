From chat, 2026-06-19 (follow-up to local vs central / BICR)

Q: For central and local, are there two of each TU/TR/RS? Do they all go into the eCRF?

A:
Two parallel sets — YES, but they are NOT separate domains. The same TU/TR/RS domains hold both reads as doubled rows, distinguished by the EVALUATOR variable:
- TUEVAL / TREVAL / RSEVAL = INVESTIGATOR (local) vs INDEPENDENT ASSESSOR (central/BICR).
- --EVALID further separates multiple central readers when needed (e.g. Reader 1, Reader 2, Adjudicator).
So one lesion can have an investigator TU/TR row AND an independent-assessor TU/TR row; same for RS overall response.

Do they all go into the eCRF? NO — different sources:
- LOCAL / investigator read -> entered into the eCRF / EDC by the site (CRF data).
- CENTRAL / BICR read -> does NOT go through the eCRF. It arrives as a non-CRF external electronic feed from the imaging core-lab vendor (like central lab data), loaded directly into the clinical database and reconciled. The site does not key in the central read.

Both feeds converge into the same SDTM TU/TR/RS, tagged by --EVAL.

Collection scope can also differ: the investigator read is sometimes only the overall response in RS on the eCRF (not full lesion measurements), while the BICR vendor usually supplies full TU/TR/RS (their own lesion selection + measurements + response). What is collected for each is a protocol/SAP decision.
