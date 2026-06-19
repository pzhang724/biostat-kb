From chat, 2026-06-19

Q: 一般是不是只有 central lab 才有 CTCAE（分级）？

A: No — CTCAE is not exclusive to the central lab. CTCAE grades *adverse events*, and AEs come from two routes, only one of which is the central lab:

1. Clinical / symptomatic AEs — graded by the **investigator at the site** (nausea, fatigue, pain, etc.), entered in the AE eCRF (CRF data). Nothing to do with the central lab. This is the bulk of CTCAE grading.

2. Lab-derived toxicity grades — here the central lab is the natural source. A quantitative lab value is mapped to its CTCAE term/threshold to produce a toxicity grade (ATOXGR in ADaM ADLB). The grade is usually **derived programmatically in ADaM** from the value (per CTCAE criteria), not "owned" by the lab vendor — though some central labs do deliver grade/flag in the feed.

Why central lab feels like the CTCAE source: central lab gives one standardized assay + reference range + full quantitative panel across all sites, so systematic lab toxicity grading is built off that feed. Local labs (entered in eCRF) are often captured only when abnormal/clinically significant and aren't systematically graded; if a local abnormal value is clinically significant it becomes an AE with its own investigator CTCAE grade.

One line: clinical AEs are CTCAE-graded by the investigator regardless of any lab; the central lab is just the prime source for *lab* toxicity grades, not the only place CTCAE lives.
