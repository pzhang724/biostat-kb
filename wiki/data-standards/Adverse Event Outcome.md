---
title: "Adverse Event Outcome"
type: concept
status: learned
tags: [data-management, trial-conduct]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# Adverse Event Outcome

The **state of the AE** at the time it is assessed/reported — SDTM **`AEOUT`**. A separate axis from [[Action Taken for an Adverse Event|action taken]], [[CTCAE Grade|grade]], [[Serious Adverse Event (SAE)|seriousness]], and causality. Controlled-terminology values:

- **RECOVERED / RESOLVED** (痊愈/缓解) — back to baseline; the event ended (carries an end date `AEENDTC`).
- **RECOVERING / RESOLVING** (恢复中) — improving but not yet fully resolved.
- **NOT RECOVERED / NOT RESOLVED** (未恢复) — still ongoing at assessment.
- **RECOVERED / RESOLVED WITH SEQUELAE** (痊愈但遗留后遗症) — the event ended but left residual / permanent effects (sequelae 后遗症).
- **FATAL** (致死) — the AE led to death (this AE is the **cause** of death).
- **UNKNOWN** (未知) — outcome not known, e.g. lost to follow-up.

## Notes

- It is **per-AE** and time-stamped to the assessment; **updated as the event evolves** (an AE can move RECOVERING → RECOVERED).
- **FATAL** is reserved for the AE that actually **caused** the death — other AEs ongoing at the time of death are not all "fatal". (Death itself is an outcome / a [[Serious Adverse Event (SAE)|seriousness]] criterion, not an AE term.)
- Resolved outcomes pair with the AE **end date `AEENDTC`**; ongoing / unknown leave it null — ties into the onset/end timing under [[SDTM, SDTM IG, and Conformance Rules#Events vs Findings timing — how an AE's occurrence is timed|Events vs Findings timing]].

AE terms come from [[MedDRA]]; how the AE was found is [[Adverse Event Ascertainment]]. A cross-cutting safety-data concept in [[Oncology]].
