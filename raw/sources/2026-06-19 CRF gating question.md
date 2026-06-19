From chat, 2026-06-19

Q: What is the "GATE" in a CRF form?

A: A "gate" = a GATING question (also gatekeeper / trigger question) on the eCRF — usually a Yes/No question that CONTROLS whether a downstream section / log has to be filled in.

- Example: "Any adverse events? Yes/No". If No, the AE log stays empty; if Yes, the detailed AE fields open up (dynamic/conditional display).
- CDASH implements these as the "--YN" header questions: AEYN ("Any AEs?"), CMYN (con meds), MHYN (medical history), PRYN (procedures), etc.
- Why it matters (data quality): a "No" is POSITIVE confirmation that nothing occurred — it distinguishes "nothing to report" from "missing / not asked" (a blank). It also drives EDC edit checks: if AEYN = Yes but there are no AE records (or = No but records exist), the system raises a query.

So a gating question turns the absence of records into recorded, verifiable information and conditionally reveals the rest of the form.

(If "GATE" referred to a specific EDC vendor's named feature rather than the general gating-question concept, clarify and I'll adjust.)
