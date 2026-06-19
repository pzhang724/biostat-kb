From chat, 2026-06-19

Q: Does the SDTM IG have separate IGs for different therapeutic areas?

A: No — the SDTMIG is a single therapeutic-area-agnostic foundational document (one IG, versioned v3.x). It is NOT split per disease.

What is TA-specific is a separate CDISC product line: **Therapeutic Area User Guides (TAUGs)**.

- A TAUG is a *User Guide*, not an *Implementation Guide*. It does not replace or fork the SDTMIG.
- Each TAUG sits on top of SDTM + SDTMIG (+ CDASH, controlled terminology) and shows how to represent the data concepts specific to one disease/area — which domains to use, how to model disease-specific assessments, often introducing new test codes / variables / examples for that area.
- CDISC has published 40+ TAUGs: oncology, Alzheimer's, diabetes, COPD/asthma, Parkinson's, breast cancer, prostate cancer, virology, cardiovascular, vaccines, etc.
- TAUGs are guidance/examples; the foundational, conformance-checked spec you build to is still the one SDTMIG. Where a TAUG introduces something not yet in the IG, it may flow into a future IG version or a supplement.

So: one SDTMIG for everyone; therapeutic-area specificity lives in the separate TAUG layer (user guides), not in multiple IGs.
