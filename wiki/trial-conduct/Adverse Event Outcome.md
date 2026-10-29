---
title: "Adverse Event Outcome"
type: concept
status: learned
created: 2026-06-19
---

# Adverse Event Outcome

The **state of the AE** at the time it is assessed/reported — SDTM **`AEOUT`**. It is a separate axis from [[Action Taken for an Adverse Event|action taken]], [[CTCAE Grade|grade]], [[Serious Adverse Event (SAE)|seriousness]], and causality (因果关系). Controlled-terminology values:

- **RECOVERED / RESOLVED** (痊愈/缓解) — back to baseline; the event ended (it has an end date, `AEENDTC`).
- **RECOVERING / RESOLVING** (恢复中) — getting better, but not fully resolved yet.
- **NOT RECOVERED / NOT RESOLVED** (未恢复) — still ongoing at the assessment.
- **RECOVERED / RESOLVED WITH SEQUELAE** (痊愈但遗留后遗症) — the event ended but left lasting / permanent effects (sequelae, 后遗症).
- **FATAL** (致死) — the AE led to death (this AE is the **cause** of death).
- **UNKNOWN** (未知) — the outcome is not known, e.g. lost to follow-up (失访).

## Notes

- It is **per AE** and time-stamped to the assessment; it is **updated as the event changes** (an AE can move RECOVERING → RECOVERED) — driven by the [[Follow-up of Adverse Events|follow-up]] of the event.
- **FATAL** is only for the AE that actually **caused** the death — the other AEs ongoing at the time of death are not all "fatal". (Death itself is an outcome / a [[Serious Adverse Event (SAE)|seriousness]] criterion, not an AE term.)
- Resolved outcomes go with the AE **end date `AEENDTC`**; ongoing / unknown outcomes leave it empty (null) — this ties into the onset/end timing under [[SDTM, SDTM IG, and Conformance Rules#Events vs Findings timing — how an AE's occurrence is timed|Events vs Findings timing]].

AE terms come from [[MedDRA]]; how the AE was found is [[Adverse Event Ascertainment]]. A safety-data concept used across [[Oncology]].
