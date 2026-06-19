From chat, 2026-06-19 (follow-up to Action Taken for an Adverse Event)

Q1: Is "action taken" generally the site investigator's on-the-spot decision?

A1: Yes. It is a real-time clinical decision by the treating site investigator (a physician) at the point of care — they manage the patient and decide hold / reduce / withdraw and any other treatment, then record it on the eCRF. The protocol pre-specifies dose-modification rules / criteria as guardrails (and some actions like permanent discontinuation may be protocol-mandated for certain events), but applying them to the patient in front of them is the investigator's judgment, not the sponsor's or statistician's. Sponsor/medical monitor may be consulted for serious cases, but the bedside call is the investigator's.

Q2: Labs have a Schedule of Activities (measured at fixed times). AEs are not measured on a fixed schedule — how is the AE's occurrence time recorded?

A2: AEs are EVENT-driven, not visit-driven. This is the SDTM Events vs Findings split:
- A scheduled lab is a FINDING — taken at a planned timepoint, tagged with VISIT/VISITNUM and the collection date (--DTC). Its timing IS the grid.
- An AE is an EVENT — it carries its own onset date/time AESTDTC (and end date AEENDTC), the actual calendar date the event started, independent of any visit. There is no fixed timepoint for it.

How the AE is ascertained (found), vs when it is timed:
- Ascertainment is continuous across the whole safety reporting period — patient-reported (between or at visits), investigator-observed, or triggered by a scheduled assessment (a scheduled lab comes back abnormal -> that can become an AE).
- At every visit the investigator solicits AEs ("anything new since last visit?"); off-schedule events come in via unscheduled visits / phone calls.
- But however it's found, the RECORDED time is the AE's own onset date (AESTDTC), not the visit it was captured at. Partial/unknown dates are allowed when exact onset isn't known.

So: scheduled labs feed AE detection, but the AE is timestamped by its own onset date, not by the visit schedule.
