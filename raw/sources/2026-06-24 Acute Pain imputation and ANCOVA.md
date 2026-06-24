From chat, 2026-06-24

Human (Acute Pain thread): "再讲一下 wWOCF, WOCF, LOCF, Imputation, withdrawal due to AE or lack of efficacy, ANCOVA"

Answer captured:

- Imputation: replacing a missing endpoint value with a substituted one so the subject stays
  in the analysis. Single imputation (one filled value, e.g. carry-forward) vs multiple
  imputation. In acute pain trials the main missing-data drivers are rescue medication and
  early withdrawal; the imputation rule encodes a (usually conservative) assumption.

- LOCF (Last Observation Carried Forward): fill missing with the subject's most recent observed
  value. Assumes the patient froze at their last state; biased if pain would have changed.

- WOCF (Worst Observation Carried Forward): fill with the worst (highest) observed pain value.
  Conservative — assumes maximum pain. Often used when a patient takes rescue medication or
  withdraws for lack of efficacy (presumably in pain). (Sibling: BOCF = Baseline OCF, fill with
  pre-treatment baseline, also conservative and common in pain.)

- wWOCF (windowed WOCF): carry forward the worst observation within a defined time window
  (e.g. the hours around the missing assessment / before rescue) rather than the single overall
  worst — a more local, less extreme conservative imputation.

- Withdrawal due to AE or lack of efficacy: two key reasons a subject discontinues early; both
  are intercurrent events but handled differently. Lack of efficacy = drug isn't controlling
  pain -> conservative imputation (WOCF/BOCF) assumes continued/worst pain. AE = withdrawal
  driven by toxicity, not pain -> pain at withdrawal may have been fine, so handling differs.
  Map onto estimand ICE strategies (composite = count as failure, treatment-policy, etc.).

- ANCOVA (Analysis of Covariance): linear model for a continuous endpoint (e.g. the pain
  AUC / SPID) that adjusts for baseline covariates — chiefly baseline pain intensity — and
  stratification factors. Removes baseline variability to gain precision; treatment effect is
  the adjusted between-arm difference (LS means). Standard primary-analysis model for the
  continuous pain endpoint.
