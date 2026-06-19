From chat, 2026-06-19 (follow-up to CTCAE lab test mapping)

Q: For lab parameters that have no CTCAE term (the "no term" case, e.g. urinalysis), how do you handle them?

A: They simply don't get a CTCAE grade — there is no toxicity grade to derive.
- In ADaM ADLB the toxicity-grade variable (ATOXGR / ATOXGRL / ATOXGRH) is left null/missing for those parameters.
- They are still analyzed, just by reference-range flag instead: LBNRIND / shift NORMAL / LOW / HIGH (and the investigator's "clinically significant" flag), not by grade.
- The clinical escalation path: if an abnormal ungraded lab is clinically significant, the investigator can record it as an adverse event in the AE domain. That AE term then carries a CTCAE grade in its own right — but the grade lives on the reported AE, not derived from the lab value.

So "no CTCAE term" → leave the grade null, fall back to reference-range/shift analysis, and let true clinical events surface as graded AEs.

(Note: calcium itself does have terms — Hypocalcemia / Hypercalcemia; the genuine no-term case is things like the urinalysis parameters.)
