From chat, 2026-06-18

Q: 能说一下 SDTM, SDTM IG 和 SDTM Conformance Rule 吗

A (summary delivered in chat):
Three tiers of the same CDISC tabulation standard.

- SDTM (Study Data Tabulation Model): the abstract model / framework. Defines the general
  principles for organizing collected clinical-trial data into observations arranged in
  domains (tables), the class structure (Interventions / Events / Findings + special-purpose
  like DM), the standard variable roles (Identifier, Topic, Timing, Qualifier), and rules like
  one record = one observation. It is the "grammar," not a list of tables to build.

- SDTM IG (Implementation Guide): the concrete, versioned how-to that you actually build to.
  Names the specific domains (DM, AE, CM, EX, LB, VS, PC, PP, ...), their variables, variable
  metadata, expected controlled terminology, and assembly/derivation conventions. When people
  say "submit SDTM datasets" they mean datasets built per a given IG version. Model is stable;
  IG is what gets implemented and versioned per therapeutic-area / general use.

- SDTM Conformance Rules: the machine-checkable validation rules that confirm a dataset
  actually conforms to SDTM + the IG (and to controlled terminology / define.xml). Published as
  CDISC Conformance Rules; FDA also publishes its own Validator Rules. Run via tools like
  Pinnacle 21 / CDISC Library. Results are Errors / Warnings / Notices; FDA rejects submissions
  with high-severity violations.

Relationship: Model (abstract framework) → IG (concrete versioned spec you implement) →
Conformance Rules (automated checks that the implementation is valid). SDTM is the submission
tabulation layer; ADaM (analysis-ready) is built downstream from it.
