From chat, 2026-06-19

Q: If the trial uses both RECIST and PCWG3, does each SDTM domain split into two?

A: No. You still have ONE TU, ONE TR, ONE RS — you do NOT split a domain per criterion. The criterion is a QUALIFIER/CATEGORY within the domain, not a new domain. Same principle as evaluator (investigator vs BICR are --EVAL within one domain, not separate domains).

How the two criteria are distinguished inside the same domains:
- TUMETHOD — CT / MRI for soft-tissue/nodal (RECIST), BONE SCAN / scintigraphy for bone (PCWG3). Plus TULOC (bone vs soft tissue) separates the lesions.
- RSCAT / RSSCAT — the response-criteria category, e.g. "RECIST 1.1", "PCWG3", and the composite overall response. So RS holds several response rows per visit: a RECIST-based one, a bone/PCWG3-based one, and the fused composite — each also per evaluator.
- --EVAL still separates investigator vs central (BICR) reads.

So per visit you can have multiple RS rows = (criteria) x (evaluators), all in the one RS domain.

Other placement:
- PSA is NOT in TU/TR — PSA is a lab, it lives in LB.
- The composite "modified RECIST 1.1 + PCWG3" overall response and rPFS are a DERIVATION downstream (ADaM ADRS), combining soft-tissue RECIST response + bone 2+2 (union for progression) into the single per-timepoint status.

Rule of thumb: SDTM splits by TOPIC (what is measured/identified), not by analysis flavor. Criterion and evaluator are extra category/qualifier axes inside TU/TR/RS, never extra domains.
