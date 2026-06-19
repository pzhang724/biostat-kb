From chat, 2026-06-19 (follow-up — wants the Step 0 SDTM mapping example, not the response-flow example)

Q: Show the Step 0 (baseline lesion setup) mapping example as SDTM TU/TR rows.

Same patient/lesions: T01 liver TARGET, T02 lung TARGET, NT01 bone NON-TARGET, NT02 pleura NON-TARGET; baseline VISIT = SCREENING.

TU (Tumor/Lesion Identification) — one row per lesion, identifies & classifies it:
STUDYID DOMAIN USUBJID TUSEQ TULNKID TUTESTCD  TUORRES    TUSTRESC   TULOC  TUMETHOD TUEVAL        VISIT
ABC     TU     01-001  1     T01     TUMIDENT  TARGET     TARGET     LIVER  CT       INVESTIGATOR  SCREENING
ABC     TU     01-001  2     T02     TUMIDENT  TARGET     TARGET     LUNG   CT       INVESTIGATOR  SCREENING
ABC     TU     01-001  3     NT01    TUMIDENT  NON-TARGET NON-TARGET BONE   CT       INVESTIGATOR  SCREENING
ABC     TU     01-001  4     NT02    TUMIDENT  NON-TARGET NON-TARGET PLEURA CT       INVESTIGATOR  SCREENING

TR (Tumor/Lesion Results) — measurements, linked back to TU by TRLNKID = TULNKID:
STUDYID DOMAIN USUBJID TRSEQ TRLNKID TRTESTCD  TRTEST            TRORRES TRSTRESN TRSTRESU TREVAL        VISIT
ABC     TR     01-001  1     T01     LDIAM     Longest Diameter  50      50       mm       INVESTIGATOR  SCREENING
ABC     TR     01-001  2     T02     LDIAM     Longest Diameter  30      30       mm       INVESTIGATOR  SCREENING
ABC     TR     01-001  3     NT01    TUMSTATE  Tumor State       PRESENT .        .        INVESTIGATOR  SCREENING
ABC     TR     01-001  4     NT02    TUMSTATE  Tumor State       PRESENT .        .        INVESTIGATOR  SCREENING

Mapping notes:
- TULNKID is the lesion key; TR rows join to TU via TRLNKID = TULNKID. So lesion classification lives once in TU, measurements repeat per visit in TR.
- Target lesions get a numeric measurement (TRTESTCD = LDIAM, longest diameter). Non-target lesions get TRTESTCD = TUMSTATE = PRESENT (qualitative, no number).
- If T02 were a LYMPH NODE, TRTESTCD would be SAXIS (Short Axis) and only the short axis feeds the sum.
- TREVAL/TUEVAL = INVESTIGATOR here; a BICR read is a parallel set of rows with TREVAL = INDEPENDENT ASSESSOR — derived separately.
- Baseline SoD (50 + 30 = 80 mm) is NOT a raw TR row — it's DERIVED downstream (ADaM ADTR/ADRS, PARAMCD like SUMDIAM), summing only TARGET lesions. RS holds the per-visit overall response (Step 2), e.g. RSTESTCD = OVRLRESP, with RSEVAL investigator vs independent.
