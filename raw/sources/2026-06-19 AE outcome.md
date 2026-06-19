From chat, 2026-06-19 (follow-up to Action Taken for an Adverse Event)

Q: Record AE outcome.

A: AE outcome (SDTM AEOUT) = the state of the AE at the time it's assessed/reported — a separate axis from action taken, grade, seriousness, causality. Controlled-terminology values:

- RECOVERED/RESOLVED — back to baseline; the event ended (carries an end date AEENDTC).
- RECOVERING/RESOLVING — improving but not yet fully resolved.
- NOT RECOVERED/NOT RESOLVED — still ongoing at assessment.
- RECOVERED/RESOLVED WITH SEQUELAE — the event ended but left residual / permanent effects (sequelae).
- FATAL — the AE led to death (this AE is the cause of death).
- UNKNOWN — outcome not known (e.g. lost to follow-up).

Notes:
- It's per-AE and time-stamped to the assessment; updated as the event evolves (an AE can move RECOVERING -> RECOVERED).
- FATAL is reserved for the AE that actually caused the death — other AEs ongoing at the time of death are not all "fatal". (Death itself is an outcome/seriousness criterion, not an AE term.)
- Resolved outcomes pair with the AE end date AEENDTC; ongoing/unknown leave it null.
