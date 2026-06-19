From chat, 2026-06-19 (follow-up)

Q: What do TU and TR mainly record?

A:
- TU (Tumor/Lesion Identification) records the IDENTITY of each lesion — one row per lesion: its location (TULOC), imaging method (TUMETHOD), and classification TUSTRESC = TARGET / NON-TARGET / NEW, keyed by TULNKID. It's the lesion ROSTER ("who's who"); topic test TUTESTCD = TUMIDENT. No measurements live here. Target/non-target are set at baseline; new lesions get added at the visit they appear.
- TR (Tumor/Lesion Results) records the MEASUREMENTS / state of those same lesions over time — one row per lesion per visit: numeric for targets (TRTESTCD = LDIAM longest diameter, or SAXIS short axis for nodes), qualitative for non-targets (TUMSTATE = PRESENT/ABSENT). It joins back to TU via TRLNKID = TULNKID. It's the measurement LOG.
- (RS, Disease Response, is the third of the trio — the per-visit overall response verdict, e.g. RSTESTCD = OVRLRESP, often derived.)

Mnemonic: TU = WHICH lesions (identity, set once), TR = HOW BIG / what state (results, per visit), RS = WHAT response (verdict). Linked by the lesion id (TULNKID/TRLNKID) and RELREC.
