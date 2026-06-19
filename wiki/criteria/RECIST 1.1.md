---
title: "RECIST 1.1"
type: concept
status: learned
tags: [medical, statistics, standards]
created: 2026-06-11
updated: 2026-06-19
sources: 9
---

# RECIST 1.1

**RECIST 1.1** (Response Evaluation Criteria In Solid Tumors, version 1.1, 2009) is the standardized, imaging-based rule set for assessing solid-tumor response — the common language behind ORR / PFS / DoR in solid-tumor trials.

**Setup:**

- **Measurable lesion** — longest diameter ≥10 mm on CT/MRI (lymph node measured by **short axis** ≥15 mm). See [[Measurable vs Non-Measurable Disease (RECIST)]].
- **Target lesions** — up to **5 total, max 2 per organ**; record the **sum of diameters (SoD)** (nodes contribute short axis). Everything else is a **non-target** lesion, assessed qualitatively.

**Response categories** (overall response integrates target + non-target + new lesions):

- **CR (complete response)** — all target lesions gone; any lymph nodes <10 mm short axis.
- **PR (partial response)** — ≥30% decrease in SoD vs baseline.
- **PD (progressive disease)** — ≥20% increase in SoD vs the nadir (smallest SoD so far) **and** ≥5 mm absolute increase; **or** any new lesion; **or** unequivocal non-target progression.
- **SD (stable disease)** — neither PR nor PD.

CR/PR usually require **confirmation** (repeat scan ≥4 weeks later) in ORR-primary or non-randomized trials. Derived endpoints: **ORR, DoR, PFS**.

## Overall response — all combinations

The time-point **overall response** combines target, non-target, and new-lesion status. Rule of thumb: **progression in any one channel → overall PD**, and **CR requires CR everywhere with no new lesions**.

Patients **with target lesions**:

| Target | Non-target | New lesions | Overall |
|--------|-----------|-------------|---------|
| CR | CR | No | **CR** |
| CR | Non-CR/Non-PD | No | **PR** |
| CR | NE | No | **PR** |
| PR | Non-PD or NE | No | **PR** |
| SD | Non-PD or NE | No | **SD** |
| NE | Non-PD | No | **NE** |
| PD | Any | Yes or No | **PD** |
| Any | PD | Yes or No | **PD** |
| Any | Any | Yes | **PD** |

Patients with **non-target disease only** (no measurable target) — note "Non-CR/Non-PD" replaces "SD":

| Non-target | New lesions | Overall |
|-----------|-------------|---------|
| CR | No | **CR** |
| Non-CR/Non-PD | No | **Non-CR/Non-PD** |
| NE | No | **NE** |
| Unequivocal PD | Yes or No | **PD** |
| Any | Yes | **PD** |

(CR = complete response, PR = partial response, SD = stable disease, PD = progressive disease, NE = not evaluable.)

In a [[PCWG3 Criteria]] mCRPC trial these RECIST calls cover only the **soft-tissue/nodal** channel; bone is judged separately by the 2+2 rule, and the two are fused into the single composite criterion [[Modified RECIST 1.1 and PCWG3 Criteria]] that defines rPFS.

Limitation that motivates [[PCWG3 Criteria]]: RECIST needs measurable disease, so it can't properly assess **bone-predominant** prostate cancer — hence the prostate-specific bone/PSA rules. See also [[PSA (Prostate-Specific Antigen)]].

## Step-by-step derivation (for a programmer)

Bottom-up pipeline: **lesion measurements → per-channel response → overall timepoint response → confirmation → [[Best Overall Response|BOR]]**. CDISC homes: SDTM **TU**, **TR**, **RS**; ADaM **ADTR** / **ADRS** (BDS).

**What each domain records** (linked by the lesion id `TULNKID`/`TRLNKID` + RELREC):

- **TU** (Tumor/Lesion Identification) = the lesion **identity / roster** — one row per lesion: location (`TULOC`), method (`TUMETHOD`), classification `TUSTRESC` = **TARGET / NON-TARGET / NEW** (`TUTESTCD = TUMIDENT`). **No measurements.** Target/non-target set at baseline; new lesions added when they appear.
  - **`TUMIDENT`** = "**Tumor Identification**" (TUMor IDENTification) — the single topic test of TU, so essentially **every** TU row carries it; the *answer* (what kind of lesion) is in `TUSTRESC`. Contrast **TR**, where `TRTESTCD` **varies** (LDIAM / SAXIS / TUMSTATE…) because TR records different measurements.
- **TR** (Tumor/Lesion Results) = the **measurements / state** of those lesions over time — one row per lesion **per visit**: numeric for targets (`TRTESTCD = LDIAM` longest diameter, or `SAXIS` short axis for nodes), qualitative for non-targets (`TUMSTATE = PRESENT/ABSENT`).
- **RS** (Disease Response) = the per-visit **overall response verdict** (`RSTESTCD = OVRLRESP`, often derived).

Mnemonic: **TU = which lesions** (identity, set once) · **TR = how big / what state** (results, per visit) · **RS = what response** (verdict).

Watch the "baseline vs post-baseline" trap: it's tempting to read TU as baseline and TR as post-baseline, but that's not clean — **TR carries baseline measurements too** (the baseline SoD comes from TR rows at screening), and **TU gains NEW-lesion rows at later visits**. So the split is **identity (TU) vs measurement-over-time-including-baseline (TR) vs verdict (RS)**, not baseline vs post-baseline.

**Step 0 — Baseline lesion setup** (TU + TR) — four sub-steps, all **fixed at baseline**:

1. **Measurability of each lesion.** Non-nodal: longest diameter **≥10 mm** on CT/MRI (slice ≤5 mm, else ≥2× slice; chest X-ray ≥20 mm; caliper ≥10 mm). Lymph node: by **short axis** — **≥15 mm** = measurable (can be target), **10–<15 mm** = pathological **non-target**, **<10 mm** = normal, not recorded. Non-measurable = lesions <10 mm, nodes 10–<15 mm, and truly non-measurable disease (leptomeningeal, ascites, effusions, inflammatory breast, lymphangitic spread, cystic, bone with no soft-tissue component, previously irradiated lesions unless later progressed).
2. **Select target lesions** — up to **5 total, max 2/organ**; pick the **largest** (longest diameter, or short axis for nodes) **but also reproducible** on repeat imaging (skip a big lesion you can't reliably re-measure). The target set is **fixed at baseline** — follow the **same** lesions every visit, never re-select.
3. **Measurement convention** — non-nodal target → longest diameter; nodal target → **short axis**. **Baseline SoD** = sum of (non-nodal longest diameters + nodal short axes) — this is the **PR reference**.
4. **Record non-target** — all other lesions (incl. pathological nodes 10–<15 mm) qualitatively as present; may be grouped (e.g. "multiple liver mets").

*SDTM view:* **TU** = `TULOC` location, `TUSTRESC` = TARGET/NON-TARGET/NEW, lesion link id, `TREVAL` evaluator (**INVESTIGATOR** vs **INDEPENDENT ASSESSOR / BICR**); **TR** = per-lesion-per-visit measurement (`TRLNKID`→TU, `TRTESTCD`=LDIAM…, `TRSTRESN`). Compute baseline SoD only over **TARGET**-flagged lesions. *Data checks:* ≤5 target, ≤2/organ (by location), each target measurable at baseline, no lesion both target & non-target, lesion ids consistent across visits, **investigator vs BICR derived separately**.

### Step 0 mapping example (SDTM TU/TR)

Same lesions (T01 liver / T02 lung TARGET, NT01 bone / NT02 pleura NON-TARGET), baseline `VISIT=SCREENING`.

**TU** — one row per lesion, identifies & classifies it:

| USUBJID | TUSEQ | TULNKID | TUTESTCD | TUSTRESC | TULOC | TUMETHOD | TUEVAL | VISIT |
|---|---|---|---|---|---|---|---|---|
| 01-001 | 1 | T01 | TUMIDENT | TARGET | LIVER | CT | INVESTIGATOR | SCREENING |
| 01-001 | 2 | T02 | TUMIDENT | TARGET | LUNG | CT | INVESTIGATOR | SCREENING |
| 01-001 | 3 | NT01 | TUMIDENT | NON-TARGET | BONE | CT | INVESTIGATOR | SCREENING |
| 01-001 | 4 | NT02 | TUMIDENT | NON-TARGET | PLEURA | CT | INVESTIGATOR | SCREENING |

**TR** — measurements, joined back to TU by `TRLNKID = TULNKID`:

| USUBJID | TRSEQ | TRLNKID | TRTESTCD | TRORRES | TRSTRESN | TRSTRESU | TREVAL | VISIT |
|---|---|---|---|---|---|---|---|---|
| 01-001 | 1 | T01 | LDIAM | 50 | 50 | mm | INVESTIGATOR | SCREENING |
| 01-001 | 2 | T02 | LDIAM | 30 | 30 | mm | INVESTIGATOR | SCREENING |
| 01-001 | 3 | NT01 | TUMSTATE | PRESENT | · | · | INVESTIGATOR | SCREENING |
| 01-001 | 4 | NT02 | TUMSTATE | PRESENT | · | · | INVESTIGATOR | SCREENING |

Mapping notes:

- **`TULNKID` is the lesion key**; TR joins to TU via `TRLNKID = TULNKID` — classification lives **once** in TU, measurements repeat per visit in TR.
- **Target** → numeric `TRTESTCD = LDIAM` (longest diameter). **Non-target** → `TRTESTCD = TUMSTATE = PRESENT` (qualitative, no number).
- If T02 were a **lymph node**, `TRTESTCD = SAXIS` (short axis) and only the short axis feeds the sum.
- **`TUEVAL`/`TREVAL = INVESTIGATOR`** here; a **BICR** read is a **parallel** set of rows with `TREVAL = INDEPENDENT ASSESSOR`, derived separately.
- **Baseline SoD (50 + 30 = 80 mm) is NOT a raw TR row** — it's **derived** downstream (ADaM ADTR/ADRS, `PARAMCD` like `SUMDIAM`), summing only TARGET lesions. **RS** holds the per-visit overall response (Step 2), e.g. `RSTESTCD = OVRLRESP`.

**Step 1 — At each post-baseline visit, evaluate three channels separately:**

- **Target** — sum current target diameters = `SoD(t)`; track **nadir** = min SoD so far.
  - **CR** all target = 0 (nodal target <10 mm short axis); **PR** `SoD(t) ≤ 0.70 × baseline`; **PD** `SoD(t) ≥ 1.20 × nadir` **and** `(SoD(t) − nadir) ≥ 5 mm`; else **SD**; **NE** if a target unmeasured and undecidable.
  - **Key trap:** PR is vs **baseline**, PD is vs **nadir** — two different reference points.
- **Non-target** — CR (all gone + nodes <10 mm + markers normal) / Non-CR/Non-PD / **unequivocal** PD / NE.
- **New lesions** — any unequivocal new lesion → flag (→ PD).
- Note: "unequivocal" non-target progression and new lesions are the **radiologist/investigator's qualitative call**, not computed from numbers.

**Step 2 — Integrate to the overall timepoint response** via the tables above: progression in **any** channel → **PD**; **CR** needs CR in target **and** non-target **and** no new lesions; otherwise read PR/SD/Non-CR-Non-PD/NE off the matching table.

**Step 3 — Confirmation** (ORR-primary / non-randomized): a CR/PR must be **confirmed** by a repeat assessment ≥4 weeks later.

**Step 4 — BOR per patient → endpoints:** best overall timepoint response across **baseline → first PD** (with confirmation + SD-min-duration rules) → responder flag (BOR ∈ CR/PR) → **ORR**; DoR/PFS derived alongside.

**Practical note:** often the investigator or **BICR** provides target/non-target/overall responses directly in **RS** (collected), and the programmer derives **BOR** from those; whether you **re-derive** timepoint responses from TR measurements or **consume RS as collected** is a **SAP** decision. Nadir is computed across the patient's own history.

## Worked example (sample data)

One patient, 2 target + 2 non-target lesions, four visits.

**TU** (lesion identification): T1 Liver TARGET · T2 Lung TARGET · NT1 Bone NON-TARGET · NT2 Pleura NON-TARGET.

**TR** (longest diameter, mm), `SoD = T1 + T2`:

| Lesion | Wk0 | Wk8 | Wk16 | Wk24 |
|---|---|---|---|---|
| T1 (liver) | 50 | 30 | 28 | 40 |
| T2 (lung) | 30 | 20 | 17 | 25 |
| **SoD** | **80** | **50** | **45** | **65** |

**Derived per visit:**

| Visit | SoD | nadir | vs baseline | vs nadir | Target | Overall |
|---|---|---|---|---|---|---|
| Wk0 | 80 | 80 | — | — | baseline | baseline |
| Wk8 | 50 | 50 | −37.5% | — | **PR** | PR (unconfirmed) |
| Wk16 | 45 | 45 | −43.8% | — | **PR** | **PR — confirms Wk8** |
| Wk24 | 65 | 45 | −18.8% | **+44.4%, +20 mm** | **PD** | **PD** |

(non-target Non-CR/Non-PD throughout; no new lesions.)

**BOR = PR** (confirmed at Wk16), achieved before first PD (Wk24) → **responder = yes**, counts toward [[Best Overall Response|ORR]].

What it shows: PR is judged vs **baseline** (80), PD vs **nadir** (45) — different reference points; **nadir** ratchets down 80→50→45 then holds; a single Wk8 PR isn't enough until Wk16 **confirms** it; after PD the window **closes**.

## Official reference

Eisenhauer EA, Therasse P, Bogaerts J, et al. **New response evaluation criteria in solid tumours: revised RECIST guideline (version 1.1).** *Eur J Cancer.* 2009;45(2):228–247. doi:10.1016/j.ejca.2008.10.026

