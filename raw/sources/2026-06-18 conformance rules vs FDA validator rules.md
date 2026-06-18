From chat, 2026-06-18

Q: conformance rules 和 validator rules 的关系，以及 validator rules 的地址

A (summary delivered in chat):

Two layers of validation rules, by who issues them:

- CDISC Conformance Rules: published BY CDISC alongside each standard version (SDTMIG, ADaMIG,
  SENDIG). They define what it means to conform to that standard — the authoritative, vendor-
  neutral source of truth. "Does the data follow the standard."

- FDA Validator Rules: FDA's OWN published rule set (e.g. Validator Rules v1.6, Dec 2022),
  used to check submissions to FDA. They largely incorporate / build on CDISC Conformance Rules
  but add FDA-specific business expectations (FDA Business Rules) — what FDA additionally
  requires for a reviewable submission. So: FDA Validator Rules ⊇ CDISC Conformance Rules +
  FDA-specific checks. "Does the data follow the standard AND meet FDA submission expectations."

Tools like Pinnacle 21 run both rule sets; the FDA set is what determines whether a submission
passes FDA's technical screening. Reference: FDA Study Data Technical Conformance Guide,
Section 8 (conformance, validation rules, traceability).

Address (FDA Validator Rules + Business Rules live on the FDA Study Data Standards Resources page):
https://www.fda.gov/industry/fda-data-standards-advisory-board/study-data-standards-resources

CDISC Conformance Rules: https://www.cdisc.org/standards/conformance-rules
