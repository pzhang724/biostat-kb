From chat, 2026-06-19

Q: 可以说一下 SDTM Model 吗(不是 IG)?

A: The SDTM **Model** is the abstract, study-agnostic framework — the "grammar." It's separately versioned from the IG (Model v1.x / v2.0 vs SDTMIG v3.x), and it gives you a kit of parts, not named tables. Three pillars:

1. General observation classes — every domain is built from one of three:
   - Interventions — substances/treatments given to or taken by the subject; Topic variable = the treatment (--TRT).
   - Events — things that happen to the subject; Topic = the event term (--TERM).
   - Findings — results of a planned measurement/evaluation; Topic = the test (--TESTCD). Plus a Findings About variant.
   Outside the three classes: special-purpose datasets (e.g. Demographics), trial design, and relationship datasets.

2. Variable roles — every variable plays exactly one role:
   - Identifier — STUDYID, DOMAIN, USUBJID, --SEQ.
   - Topic — the focus of the observation.
   - Timing — --DTC, --STDTC/--ENDTC, VISITNUM, --DY.
   - Qualifier — everything else describing the observation, subdivided into Grouping (--CAT/--SCAT), Result (--ORRES/--STRESC/--STRESN), Synonym (--DECOD/--MODIFY), Record (--SEV, --SER), and Variable (--ORRESU units) qualifiers.

3. Naming + general rules — the `--` two-letter domain-prefix convention (--TESTCD, --ORRES, --STDTC) makes variables predictable across domains; core rules like one record = one observation, and use of controlled terminology.

So Model = parts + grammar (stable); the IG names concrete domains (DM/AE/LB…) by picking a class and filling in the role variables. Model = the kit; IG = the assembled, versioned sentence.
