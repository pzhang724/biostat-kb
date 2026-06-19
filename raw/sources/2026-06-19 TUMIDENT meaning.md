From chat, 2026-06-19 (follow-up)

Q: What does TUMIDENT mean?

A: TUMIDENT = "Tumor Identification" — the value of TUTESTCD (the topic/test variable) in the SDTM TU domain. It's CDISC controlled terminology; TUMIDENT literally = TUMor IDENTification.

- It marks the record as "identify / classify this lesion," and the RESULT of that test — TUORRES / TUSTRESC — carries the classification: TARGET / NON-TARGET / NEW (also values like EQUIVOCAL).
- Because TU's whole job is identifying lesions, essentially EVERY TU row has TUTESTCD = TUMIDENT — it is the domain's single topic test.
- Contrast TR, where TRTESTCD VARIES (LDIAM longest diameter, SAXIS short axis, TUMSTATE present/absent…) because TR records different measurements.

So: TUMIDENT (TU) = "what kind of lesion is this" with the answer in TUSTRESC; the measurements of that lesion live in TR under varying TRTESTCDs.
