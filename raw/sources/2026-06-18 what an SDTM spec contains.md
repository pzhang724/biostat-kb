From chat, 2026-06-18

Q: 一个 SDTM Spec 除了每个 domain 的 mapping，是不是还应该有 controlled terminology / codelist 这些？能把 exact mapping 给我吗？

A (summary delivered in chat):

Yes — CT / codelists are part of it. A full SDTM (mapping) specification is more than
variable→variable; it is essentially the human-readable source that define.xml is generated from.
Typical components / tabs of an SDTM mapping spec (often an Excel workbook):

1. Datasets / Domains metadata — list of domains in the study; per domain: name, description/
   label, class (Interventions/Events/Findings/Special-Purpose), structure (one record per…),
   key variables, location.
2. Variable-level mapping (per domain) — the core tab. Exact columns typically:
   - Domain
   - Variable Name (target SDTM var, e.g. AESTDTC)
   - Variable Label
   - Type (Char / Num)
   - Length
   - Role (Identifier / Topic / Timing / Qualifier-grouping/result/etc.)
   - Core (Req / Exp / Perm)
   - Codelist / CT reference (which codelist the value must come from)
   - Origin (CRF / Derived / Assigned / Protocol / eDT)
   - Source dataset + Source variable(s) (the raw/EDC field)
   - Mapping / Derivation logic (the algorithm or rule in words)
   - Comments
3. Codelists / Controlled Terminology tab — each codelist: codelist name + NCI/CDISC code,
   submission value, decode (display). Covers both CDISC CT and study-/sponsor-specific codelists.
4. Value-Level Metadata (VLM) — for Findings domains keyed by --TESTCD (LB, VS, PC, QS…):
   per test, the type/units/CT/derivation that vary row to row.
5. Computational methods / derivations — named algorithms referenced by the mapping.
6. External dictionaries — MedDRA, WHODrug versions used for coding.
7. SUPPQUAL (supplemental qualifiers SUPP--) and RELREC relationships mapping.
8. Comments / document & study metadata.

So the "exact mapping" is the column set in #2 (target var + metadata + origin + source + logic +
codelist), and the CT/codelists in #3-4 are a required companion, not optional. Spec ≈ define.xml
in human-readable form.
