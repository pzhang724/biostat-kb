From chat, 2026-06-19

Q: Action taken for management of an adverse event.

A: "Action taken" records how the AE was managed. It is captured on the AE record as TWO separate fields (SDTM AE domain):

1. Action taken WITH STUDY TREATMENT (SDTM AEACN) — what was done to the study drug because of the AE. Controlled-terminology values:
   - DOSE NOT CHANGED
   - DOSE REDUCED
   - DOSE INCREASED
   - DRUG INTERRUPTED (temporary hold)
   - DRUG WITHDRAWN (permanent discontinuation)
   - NOT APPLICABLE
   - UNKNOWN

2. OTHER action taken (SDTM AEACNOTH) — everything done besides adjusting the study drug: concomitant medication / treatment given for the AE, non-drug therapy, a procedure/surgery, hospitalization, etc. Captures the supportive/corrective management.

These are separate axes from:
- AE OUTCOME (AEOUT): recovered/resolved, recovering/resolving, not recovered/not resolved, recovered with sequelae, fatal, unknown.
- Severity (CTCAE grade), seriousness (SAE criteria), and causality.

The CTCAE grade typically drives the action — e.g. a grade >=3 toxicity triggers interrupt/reduce per the protocol's dose-modification rules.
