From chat, 2026-06-19. Follow-up to unscheduled-visit question.

Human asked: unscheduled 的 VISITNUM 一般都怎么排呢;还有 AVISITN?

Answer given (content marker):

VISITNUM (SDTM) for unscheduled visits:
- VISITNUM is just a NUMERIC SORT KEY for visit chronology — it is not a calendar date and the SDTMIG does not mandate one fixed scheme; it's sponsor convention, fixed in the SDTM spec.
- Dominant convention = DECIMAL INSERT: an unscheduled visit takes the integer of the most recent scheduled visit + a decimal, so it sorts into the right chronological slot. E.g. unscheduled events after scheduled VISITNUM 5 → 5.1, 5.2, 5.3…; after Cycle2Day1 (say 6) → 6.1, 6.2.
- VISIT (the label) is usually "UNSCHEDULED" (sometimes "UNSCHEDULED 1/2…"); VISITDY/SVSTDTC carry the actual timing.
- Tension to know: many validators expect VISIT↔VISITNUM to be one-to-one. If every unscheduled record is VISIT="UNSCHEDULED" but with different VISITNUM (5.1, 6.1…), that one-to-one expectation breaks → you either give each unscheduled a distinct VISIT label or accept/justify the check. Sponsor SDTM spec decides; document it.
- Some sponsors instead reserve a high block (e.g. 500, 501…) for all unscheduled — works for grouping but loses the chronological-insert nicety; decimal-insert is more common.

AVISITN (ADaM) is a DIFFERENT thing:
- ADaM BDS has its own ANALYSIS visit pair: AVISIT (char) + AVISITN (numeric sort). These are DERIVED for analysis via VISIT WINDOWING per the SAP — they are independent of SDTM VISIT/VISITNUM and do NOT have to equal them.
- AVISITN just orders the analysis timepoints, e.g. Baseline = 0, Week 4 = 4, Week 8 = 8 (or 1,2,3…). The number is chosen to sort the by-visit tables correctly.
- Where do unscheduled SDTM records go in ADaM? Two options per SAP:
  1. Windowed into the nearest nominal analysis visit — the unscheduled value becomes (or competes for) that AVISIT, so it feeds by-visit summaries (often "closest to target" or "worst case" rules pick which record wins the window).
  2. Flagged AVISIT = "Unscheduled" (with its own AVISITN, often a high number) or excluded from by-visit analysis if the SAP only summarizes scheduled timepoints.
- Key mental model: VISITNUM = collection/sort order of what actually happened (SDTM); AVISITN = analysis order after windowing (ADaM). SDTM keeps the raw truth incl. unscheduled; ADaM decides how unscheduled folds into the planned analysis grid.

One line: SDTM 用小数 VISITNUM(如 5.1、5.2)把 unscheduled 插到时间顺序里、VISIT="UNSCHEDULED";AVISITN 是 ADaM 里另起的分析访视序号,按 SAP 的 visit window 派生,unscheduled 要么被窗口归到最近的标称访视、要么标成 "Unscheduled"/排除,二者不必相等。

Ties: [[SDTM, SDTM IG, and Conformance Rules]] (SV/VISIT/VISITNUM, ADaM downstream), [[Schedule of Assessments]] (visit windows).
