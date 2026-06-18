From chat, 2026-06-18

Q: FDA Validator Rules + CDISC Conformance Rules 等于 Pinnacle 21 吗？

A (summary delivered in chat):

No — different kinds of thing.

- The rules (CDISC Conformance Rules, FDA Validator Rules, FDA Business Rules) are the
  SPECIFICATION: published lists of what must be checked. Documents/spreadsheets, not software.

- Pinnacle 21 (P21) is the TOOL / engine that IMPLEMENTS those rule sets as executable checks
  and runs them against your datasets, producing a findings report (Errors/Warnings/Notices)
  and helping build define.xml. It translates the published rules into code.

So: rules = the law; Pinnacle 21 = the inspector that enforces it. P21 is the de facto industry
+ FDA validation engine (FDA uses P21 internally), which is why "running P21" is shorthand for
"checking conformance" — but P21 may lag a rule version, can have its own interpretation/bugs,
and isn't the only possible implementation. Passing P21 ≈ meeting the rules, not identical to it.
