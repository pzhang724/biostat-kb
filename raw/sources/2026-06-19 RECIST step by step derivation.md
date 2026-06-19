From chat, 2026-06-19

Q: As a statistical programmer, using RECIST 1.1, how do I step by step confirm each lesion, each evaluation (timepoint), and the final response?

A: It's a bottom-up pipeline: lesion measurements -> per-category response at each visit -> overall timepoint response -> confirmation -> BOR. CDISC homes: SDTM TU (lesion identification), TR (lesion measurements/results), RS (response assessments); ADaM ADTR (measurements) / ADRS (response, BDS).

STEP 0 — Baseline lesion setup (from TU + TR):
- Classify each lesion: TARGET vs NON-TARGET vs (later) NEW. Target = measurable, up to 5 total and max 2 per organ; non-nodal measured by longest diameter, lymph node by SHORT axis. Data checks: <=5 target, <=2/organ, target measurable at baseline.
- Compute BASELINE SoD = sum of target lesion measurements (non-nodal longest diameter + nodal short axis).
- Non-target lesions recorded qualitatively (present).

STEP 1 — At each post-baseline visit, evaluate the three channels separately:
(a) TARGET response — sum current target diameters = SoD(t); track NADIR = min SoD from baseline..t.
   - CR: all target lesions = 0, and any nodal target <10mm short axis.
   - PR: SoD(t) <= 0.70 x BASELINE SoD (>=30% decrease vs BASELINE).
   - PD: SoD(t) >= 1.20 x NADIR AND (SoD(t) - nadir) >= 5mm absolute.
   - SD: neither PR nor PD.
   - NE: a target lesion not assessed and response can't otherwise be determined.
   KEY TRAP: PR is vs BASELINE, PD is vs NADIR — two different reference points.
(b) NON-TARGET response — CR (all gone + nodes <10mm + markers normal) / Non-CR/Non-PD (>=1 persists) / PD (UNEQUIVOCAL progression) / NE.
(c) NEW lesions — any unequivocal new lesion -> flag (=> PD).
   Note: "unequivocal" NTL progression and new lesions are the radiologist/investigator's qualitative call, not something the programmer computes from numbers.

STEP 2 — Integrate to the OVERALL timepoint response via the RECIST table:
- Progression in ANY channel (target PD, unequivocal non-target PD, or any new lesion) -> overall PD.
- CR requires CR in target AND non-target AND no new lesions.
- Otherwise read PR/SD/Non-CR-Non-PD/NE off the integration table (target-lesion patients vs non-measurable-only patients use different tables).

STEP 3 — Confirmation (if ORR-primary / non-randomized):
- A CR or PR must be CONFIRMED by a repeat assessment >=4 weeks later, else it doesn't count.

STEP 4 — Best Overall Response (per patient) -> endpoints:
- BOR = best overall timepoint response across baseline -> first PD, applying confirmation + SD-minimum-duration rules.
- Responder flag (BOR in CR/PR) -> ORR across patients; DoR/PFS derived alongside.

Practical note: often the investigator or BICR provides target/non-target/overall responses directly in RS (collected), and the programmer derives BOR from those; whether you RE-derive the timepoint responses from TR measurements or consume RS as collected is a SAP decision. Nadir is computed across the patient's own history.
