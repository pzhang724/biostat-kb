From chat, 2026-06-19

Q: Distinguish prior / concomitant / post-treatment for medication, procedure, and therapy — feels like too many.

A: It's not many things — it's TWO axes crossed. One axis = TYPE (which SDTM domain), the other = TIMING (relative to study treatment, derived from dates, NOT a separate domain).

AXIS 1 — TYPE (= the domain):
- Medication / drug -> CM (Concomitant/Prior Medications). All non-study drugs.
- Procedure / surgery / radiotherapy / biopsy -> PR (Procedures).
- The STUDY drug itself -> EX (Exposure), NOT CM. CM = everything else.
- "Anti-cancer THERAPY" is not a separate domain — it's a cancer-directed CUT that spans CM (systemic drugs) + PR (surgery/radiotherapy).

AXIS 2 — TIMING (relative to study treatment, by dates vs the EX window — a flag/derivation, not a new domain):
- PRIOR = started/stopped BEFORE first study dose.
- CONCOMITANT = taken DURING treatment (overlaps the study-drug window) -> "con meds".
- POST-TREATMENT / SUBSEQUENT = after last dose / in follow-up.

So the grid is type x timing:
- Medication (CM): prior meds | con meds | subsequent meds
- Procedure (PR): prior surgery/RT/biopsy | on-study procedures | subsequent procedures
- Anti-cancer therapy (CM+PR cut): prior anti-cancer therapy | (usually prohibited concurrently) | subsequent anti-cancer therapy

Why each matters:
- PRIOR therapy -> eligibility (lines of prior treatment, washout), prognosis/stratification.
- CONCOMITANT meds -> safety, drug interactions, supportive care; prohibited-med checks.
- SUBSEQUENT / post anti-cancer therapy -> confounds OS; it's an INTERCURRENT EVENT (estimand handling / censoring decisions).

Key point: "prior/concomitant/subsequent" is a TIMING relationship derived from dates relative to the study-treatment window; "medication/procedure/therapy" is the TYPE/domain. Only ~2 domains (CM, PR) + EX, sliced by timing — that's why it feels like many but isn't.
