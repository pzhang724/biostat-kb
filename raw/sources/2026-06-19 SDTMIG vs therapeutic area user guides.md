From chat, 2026-06-19

Q: Does the SDTM IG have separate IGs for different therapeutic areas?

A: No — the SDTMIG is a single therapeutic-area-agnostic foundational document (one IG, versioned v3.x). It is NOT split per disease.

What is TA-specific is a separate CDISC product line: **Therapeutic Area User Guides (TAUGs)**.

- A TAUG is a *User Guide*, not an *Implementation Guide*. It does not replace or fork the SDTMIG.
- Each TAUG sits on top of SDTM + SDTMIG (+ CDASH, controlled terminology) and shows how to represent the data concepts specific to one disease/area — which domains to use, how to model disease-specific assessments, often introducing new test codes / variables / examples for that area.
- CDISC has published 40+ TAUGs: oncology, Alzheimer's, diabetes, COPD/asthma, Parkinson's, breast cancer, prostate cancer, virology, cardiovascular, vaccines, etc.
- TAUGs are guidance/examples; the foundational, conformance-checked spec you build to is still the one SDTMIG. Where a TAUG introduces something not yet in the IG, it may flow into a future IG version or a supplement.

So: one SDTMIG for everyone; therapeutic-area specificity lives in the separate TAUG layer (user guides), not in multiple IGs.

---

Follow-up: which TAUGs map to this wiki's TAs (Oncology/prostate, Asthma)?

Verified against cdisc.org/standards/therapeutic-areas (June 2026):

- There is NO single generic "Oncology" TAUG. Oncology TAUGs are per cancer type: Breast Cancer, Lung Cancer, **Prostate Cancer**, Colorectal Cancer, Pancreatic Cancer. The cross-cutting oncology machinery (tumor identification/results/response — TU / TR / RS domains, RECIST modeling) lives in the SDTMIG itself, not a TAUG.
- Respiratory: **Asthma**, COPD.

Directly relevant to this wiki:
- **Prostate Cancer TAUG** — matches the prostate-cancer indication under Oncology.
- **Asthma TAUG** — matches the Asthma TA.
- Sibling/umbrella context: other oncology TAUGs (Breast/Lung/Colorectal/Pancreatic) sit under the Oncology umbrella but aren't this wiki's indication; COPD is the respiratory sibling to Asthma.

The page itself (SDTMIG) is still one TA-agnostic doc; these TAUGs are the separate user-guide layer for those areas.
