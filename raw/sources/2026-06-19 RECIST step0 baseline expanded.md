From chat, 2026-06-19 (follow-up — expand Step 0 of RECIST derivation)

Q: Expand Step 0 (baseline lesion setup).

A: Step 0 has four sub-steps: decide measurability -> select target lesions -> set the measurement convention -> record non-target; all fixed at baseline.

1. MEASURABILITY of each lesion:
   - Non-nodal lesion: longest diameter >=10mm on CT/MRI (slice thickness <=5mm; if thicker, >=2x slice). Chest X-ray >=20mm; caliper/clinical >=10mm.
   - Lymph node: measured by SHORT axis. >=15mm = measurable (can be target); 10 to <15mm = pathological NON-target; <10mm = normal, not recorded.
   - Non-measurable: lesions <10mm, nodes 10-<15mm, and truly non-measurable disease (leptomeningeal, ascites, pleural/pericardial effusion, inflammatory breast, lymphangitic spread, cystic, bone with no soft-tissue component, previously irradiated lesions unless later progressed).

2. SELECT target lesions:
   - Up to 5 total, max 2 per organ.
   - Pick the largest (by longest diameter, or short axis for nodes) BUT also representative and REPRODUCIBLE on repeat imaging (skip a big lesion that can't be reliably re-measured).
   - The target set is FIXED at baseline — you follow the SAME lesions every visit; you do not re-select later.

3. MEASUREMENT convention:
   - Non-nodal target -> longest diameter; Nodal target -> short axis.
   - Baseline SoD = sum of (non-nodal longest diameters + nodal short axes). This is the PR reference.

4. NON-target recording:
   - All other lesions (incl. pathological nodes 10-<15mm) recorded qualitatively as present; may be grouped (e.g. "multiple liver mets").

Programmer / SDTM view:
   - TU (identification): TULOC location, TUSTRESC = TARGET / NON-TARGET / NEW, lesion link ID; TREVAL evaluator (INVESTIGATOR vs INDEPENDENT ASSESSOR/BICR).
   - TR (results): per lesion per visit, TRLNKID -> TU, TRTESTCD = LDIAM (longest diameter) / others, TRSTRESN measurement.
   - Compute baseline SoD only over lesions flagged TARGET at baseline.
   - Data checks: <=5 target, <=2 per organ (by location), each target measurable at baseline, no lesion both target & non-target, lesion IDs consistent across visits, evaluator kept separate (investigator vs BICR derived independently).
