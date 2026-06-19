From chat, 2026-06-19 (follow-up to CRF vs Non-CRF data)

Q: So for the CSR, one source is EDC (saving eCRF), one is central lab — what about local lab, and are there others?

A: Local lab is NOT a separate stream — local lab results are entered by the SITE into the eCRF, so they ride in as CRF data (EDC). (Often only captured when abnormal / clinically significant, per protocol.) Central lab is the separate external feed; local lab is just eCRF.

Yes, there are many other sources beyond eCRF + central lab. All are loaded and reconciled into the clinical database, then mapped SDTM -> ADaM -> TLFs -> CSR. Common non-CRF / external feeds:

- PK / bioanalytical lab (drug concentrations) -> PC/PP domains.
- Biomarker / specialty central labs — PGx, immunogenicity / anti-drug antibody (ADA), flow cytometry, etc.
- Imaging / ECG core lab — centralized reads; includes BICR (Blinded Independent Central Review) for tumor response, and central ECG over-read.
- ePRO / eCOA / eDiary — patient-reported outcomes via device/app.
- IRT / RTSM (IWRS) — randomization assignments, stratification factors, drug dispensing & accountability.
- Safety / pharmacovigilance database — SAE reconciliation against the clinical DB (the PV system holds the regulatory SAE records).
- Wearables / digital sensors.
- External death index / registries — survival-status data for OS follow-up.

So: EDC/eCRF (incl. local lab) + central lab + this list of external vendor feeds, all integrated → the CSR.
