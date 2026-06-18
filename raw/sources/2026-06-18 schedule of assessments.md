From chat, 2026-06-18

Q: 讲讲 Schedule of Assessment 吧。

A (summary delivered in chat):

The Schedule of Assessments / Activities (SoA, 评估计划表 / 流程表) is the master TABLE in a
clinical trial protocol that lays out WHICH procedures/assessments are performed at WHICH
visits/timepoints across the whole study. The operational backbone of the protocol.

Layout (a grid):
- Rows = assessments/procedures: informed consent, eligibility, demographics, medical history,
  vital signs, physical exam, labs (heme/chem), ECG, tumor imaging (RECIST/PCWG3), PK sampling,
  dosing/administration, AE & concomitant-med collection, PRO/QoL questionnaires, survival
  follow-up, etc.
- Columns = visits/timepoints grouped by study period: Screening → Treatment (by cycle/day,
  e.g. C1D1, C1D8…) → EOT → Safety follow-up → Long-term/survival follow-up → EOS.
- Cells = an "X" where that assessment happens at that visit; footnotes carry visit windows
  (±days), conditions, and details.

Why it matters (esp. for a biostatistician):
- It defines the TIMING of every data collection → directly drives analysis windows and endpoint
  measurement (e.g. tumor-assessment frequency affects PFS interval-censoring; PK sampling times
  define the concentration-time curve).
- Maps to the SDTM Trial Design / visit structure (TV/SV, VISIT/VISITNUM) and to define.xml.
- Visit windows give operational flexibility while keeping data comparable across patients.
- ICH M11 (the harmonized protocol template) standardizes the name as "Schedule of Activities (SoA)".

Periods align with the EOT/EOS milestones: the SoA shows exactly which assessments continue
after EOT into follow-up up to EOS.
