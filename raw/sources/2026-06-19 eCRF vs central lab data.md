From chat, 2026-06-19

Q: Aren't eCRF and central lab data together / the same thing?

A: No — they are usually two SEPARATE data streams that get merged later.

- eCRF (electronic Case Report Form, in the EDC system) = data the SITE staff key in: AEs, con-meds, vitals, physical exam, dosing, local assessments, the investigator's interpretations. This is "CRF data".
- Central lab data = when samples are shipped to a central laboratory, the lab runs the assays and sends results as an electronic data transfer (a vendor feed / dataset) DIRECTLY into the clinical database — the site does NOT re-type them into the eCRF. This is "non-CRF" / external / third-party data. Other non-CRF feeds work the same way: PK/bioanalytical, imaging/ECG core lab, ePRO/eDiary.

Why central (and why separate):
- One central lab = one standardized assay + one reference range across all sites -> comparability (local labs vary site to site). Sponsors use central labs for key/efficacy labs; local labs (entered in eCRF) for quick safety checks.
- The feed arrives per a Data Transfer Agreement / spec and is loaded, then RECONCILED against the eCRF (match subject ID, visit, sample date).

Where they converge: at SDTM both land in the same LB domain (harmonized), but operationally they arrive through different channels and need reconciliation. Note: the central lab value itself isn't in the eCRF, but if the investigator reviews it and judges it clinically significant, the derived AE IS entered in the eCRF (the data-triggered AE route).
