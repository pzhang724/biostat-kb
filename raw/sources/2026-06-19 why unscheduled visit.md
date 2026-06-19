From chat, 2026-06-19

Human asked: 为什么会有 unscheduled visit?

Answer given (content marker):

Unscheduled visit (计划外/非预约访视) = a visit NOT on the protocol's planned Schedule-of-Assessments grid, triggered by a clinical need that arises BETWEEN scheduled visits. They exist because a fixed grid can't anticipate every clinical event — medicine has to stay responsive. Typical reasons:

- Adverse-event driven: assess/manage a new or worsening AE, recheck symptoms, extra safety monitoring.
- Confirm/repeat a finding: repeat an out-of-range or abnormal lab to confirm a toxicity grade; recheck ECG/QTc; a CONFIRMATORY scan for suspected progression (ties to the 2+2 / confirmation logic).
- Dose-modification decisions: data needed to decide hold/reduce/resume.
- Patient-initiated: patient feels unwell and comes in off-schedule.

Key points:
- The data is still fully captured (labs, AEs, ECG, etc.) — an unscheduled visit is real data, not discarded. In SDTM it's recorded in the visit structure (SV) with the unscheduled-visit convention (e.g. a non-integer/flagged VISITNUM, VISIT = "UNSCHEDULED").
- Analytically, unscheduled assessments are handled by VISIT WINDOWS: each is mapped to the nearest planned analysis timepoint, or used as a confirmation/worst-case value — so they don't break the by-visit summaries built on the scheduled grid.
- They contrast with the scheduled visits (Screening → Treatment cycles → EOT → follow-up → EOS) that define the planned grid; the SoA usually has an "Unscheduled" column precisely to say which assessments may be done as-needed.

One line: 固定的访视表无法预知每个临床事件(AE、要复查/确认的异常、要做减量决定),所以协议留出 unscheduled visit 让医生按需把病人叫回来;数据照样采集,分析时用 visit window 归到最近的计划时点。

Ties: [[Schedule of Assessments]] (the planned grid + visit windows), [[Adverse Event of Special Interest (AESI)]] / safety monitoring, confirmation logic in [[PCWG3 Criteria]], SDTM SV in [[SDTM, SDTM IG, and Conformance Rules]].
