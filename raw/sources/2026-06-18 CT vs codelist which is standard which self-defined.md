From chat, 2026-06-18

Q: CT 和 codelist 哪个是 self-defined，哪个是标准库？

A (summary delivered in chat):

They aren't parallel opposites — different kinds of thing:

- Controlled Terminology (CDISC CT) = the STANDARD LIBRARY. Maintained by CDISC + NCI-EVS,
  versioned (quarterly), every term/list carries an NCI C-code. This is the authoritative source.
- Codelist = the structural UNIT — one named set of permissible values (a list). It is the
  container, not "standard vs custom" by itself.

The self-defined vs standard split happens WITHIN codelists:
- Standard codelists = CDISC CT codelists (have NCI C-codes), e.g. SEX, RACE, AESEV, NY,
  the --TESTCD lists.
- Sponsor-/study-defined codelists = self-defined: lists CDISC doesn't provide (study-specific),
  you author them yourself.
- Hybrid: CDISC marks each codelist Extensible Yes/No. Extensible = standard base you MAY add
  sponsor terms to (e.g. extend a CT codelist with extra values); Non-extensible = must use only
  the CDISC values, no additions.

In the spec / define.xml each codelist is tagged accordingly: a CDISC-CT codelist references its
NCI code; a sponsor codelist is flagged as sponsor-defined.

So: CT = the standard library; codelist = the unit; a given codelist is either CDISC-standard,
sponsor-self-defined, or standard-but-extended.
