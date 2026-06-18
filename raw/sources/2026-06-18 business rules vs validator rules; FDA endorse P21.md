From chat, 2026-06-18

Q1: Business Rules 和 Validator Rules 的区别？
Q2: FDA 官方有没有 endorse P21？

A (summary delivered in chat):

Business Rules vs Validator Rules — same intent, two altitudes:
- FDA Business Rules: high-level statements of WHAT FDA expects of study data and WHY (policy /
  requirement level). Conceptual, human-oriented, no severity assigned. ("Data must support
  meaningful review.")
- FDA Validator Rules: the concrete, machine-executable IMPLEMENTATION of those Business Rules —
  the specific checks a validator runs. Published by FDA for transparency; effectively the subset
  of Pinnacle 21 validator rules that implement the FDA Business Rules. This is the operational
  layer.
So: Business Rules = the "what/why" (policy); Validator Rules = the "how" (executable checks that
enforce the policy). Severity note: neither CDISC Conformance Rules nor FDA Business Rules carry
severity, and FDA Validator Rules don't publish severity either; P21 adds its own Type =
Error/Warning/Notice.

Does FDA officially endorse P21?
- No formal public endorsement and no mandate that sponsors must use P21 — FDA guidance
  (Technical Conformance Guide) is written tool-agnostically.
- BUT FDA has licensed and used Pinnacle 21 Enterprise internally to screen incoming submissions
  for over a decade. Because FDA's own screening runs P21, it is the de-facto standard — sponsors
  run the same tool to predict the FDA result.
- So: de-facto standard via FDA's own usage/contract, not a de-jure "you must use this product"
  endorsement.
