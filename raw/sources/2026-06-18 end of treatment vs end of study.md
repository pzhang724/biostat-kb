From chat, 2026-06-18

Q: 说一下 End of Treatment 和 End of Study 的区别，然后 illustrate 一下。

A (summary delivered in chat):

- End of Treatment (EOT, 治疗结束): the point a patient STOPS study treatment (the
  investigational drug) — completed planned cycles, disease progression, unacceptable toxicity,
  withdrawal of consent, death, etc. Triggers an EOT visit/assessment + an EOT disposition record.
- End of Study (EOS, 研究结束): the point a patient's ENTIRE participation ends — i.e. the last
  contact / last data point, after any follow-up that continues post-treatment. Triggers an EOS
  visit + EOS disposition record.

Key difference: EOT = stop the DRUG; EOS = stop EVERYTHING (last contact). A patient is commonly
OFF-treatment but still ON-study, sitting in the follow-up period between EOT and EOS.

Between EOT and EOS there is usually:
- Safety follow-up (~30 days after last dose) — collect AEs/SAEs, subsequent therapy.
- Long-term / survival follow-up — for OS, collect survival status, subsequent anti-cancer therapy.

Two senses of "End of Study": (a) an individual subject's end of participation; (b) the whole
TRIAL's end = Last Subject Last Visit (LSLV) → database lock. Context tells which.

Why a biostatistician cares: OS is measured from randomization to death, censored at the EOS/last
known alive date — so the EOT→EOS follow-up window is exactly what feeds survival endpoints; the
DS (Disposition) domain records BOTH the EOT reason and the EOS reason. Going off treatment is an
intercurrent event for treatment-policy vs other estimands.

Timeline illustration:

  Screening
     │
     ▼
  Treatment period (cycles / dosing)
     │
     ▼  ◀── EOT: stop study drug (progression / toxicity / completed / withdrawal)
  Safety follow-up (~30 days post last dose: AEs, subsequent therapy)
     │
     ▼
  Long-term / survival follow-up (survival status, subsequent anti-cancer therapy)
     │
     ▼  ◀── EOS: last visit / last contact = end of participation
  (study-level: when the LAST subject reaches EOS = LSLV → database lock)

  On-treatment │←———— EOT ————→│  off-treatment but still ON-STUDY  │←—— EOS ——→│ off-study
