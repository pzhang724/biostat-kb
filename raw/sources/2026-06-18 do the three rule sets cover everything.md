From chat, 2026-06-18

Q: 所以 Business Rules + Validator Rules + Conformance Rules 理论上应该覆盖所有 rule，只是理解不同会有偏差，能这么理解吗？还是有其他文档可参考？

A (summary delivered in chat):

Mostly right on intent, but two corrections:

1. They are NOT three disjoint sets that add up. They overlap / nest heavily:
   - CDISC Conformance Rules = conformance to the CDISC standards (SDTMIG/ADaMIG/SENDIG/Define).
   - FDA Business Rules = policy (what/why), FDA Validator Rules = executable implementation of
     those, and the Validator Rules already largely INCORPORATE the CDISC conformance checks plus
     FDA-specific ones. So it's overlapping layers, not A+B+C of separate things.
   Union ≈ "essentially all the AUTOMATED checks that matter for a submission," but via overlap,
   not addition.

2. Automated rules ≠ everything you must do. Many requirements live in the standards/IG and
   guidance and are NOT encoded as any machine rule — traceability, data fitness, reviewer
   judgment. Automated rules are a FLOOR, not the whole obligation. Plus other agencies have
   their own rule sets (PMDA Validation Rules for Japan, NMPA for China).

"Interpretation differences cause deviation" — yes: same rule text, different implementations
(P21 vs a home engine vs FDA's internal run) interpret edge cases differently, and versions lag.

Other documents worth referencing (the source-of-truth / governing layer):
- The IGs themselves: SDTMIG, ADaMIG, SENDIG, Define-XML spec — rules DERIVE from these.
- FDA Study Data Technical Conformance Guide — the governing FDA document tying it together.
- FDA Data Standards Catalog — which standard versions FDA currently supports/requires.
- CDISC Controlled Terminology — the codelists the rules check against.
- Reviewer's guides: cSDRG (clinical SDTM) / ADRG (ADaM) — human-facing context.
- PMDA Validation Rules (if submitting to Japan); other regions analogous.
