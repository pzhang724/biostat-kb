---
title: "RECIST 1.1"
type: concept
status: learned
created: 2026-06-11
---

# RECIST 1.1

**RECIST 1.1** (Response Evaluation Criteria In Solid Tumors, version 1.1, 2009; 实体瘤疗效评价标准) is the standard, imaging-based set of rules for judging how solid tumors respond — the common language behind ORR / PFS / DoR in solid-tumor trials (objective response rate 客观缓解率 / progression-free survival 无进展生存期 / duration of response 缓解持续时间).

**Setup:**

- **Measurable lesion** — longest diameter ≥10 mm on CT/MRI (a lymph node is measured by its **short axis**, 短径, ≥15 mm). See [[Measurable vs Non-Measurable Disease (RECIST)]].
- **Target lesions** (靶病灶) — up to **5 in total, at most 2 per organ**; record the **sum of diameters (SoD, 直径总和)** (nodes add their short axis). Every other lesion is a **non-target** lesion (非靶病灶), assessed qualitatively (定性).

**Response categories** (the overall response combines target + non-target + new lesions):

- **CR (complete response, 完全缓解)** — all target lesions are gone; any lymph nodes are <10 mm short axis.
- **PR (partial response, 部分缓解)** — SoD falls by ≥30% compared with baseline.
- **PD (progressive disease, 疾病进展)** — SoD rises by ≥20% compared with the nadir (最低点; the smallest SoD so far) **and** by ≥5 mm in absolute terms; **or** any new lesion; **or** clear (unequivocal, 明确的) progression of non-target lesions.
- **SD (stable disease, 疾病稳定)** — neither PR nor PD.

CR/PR usually need **confirmation** (a repeat scan ≥4 weeks later) in trials where ORR is primary or that are not randomized. Derived endpoints: **ORR, DoR, PFS**.

## Overall response — all combinations

The **overall response** at a timepoint combines target, non-target, and new-lesion status. Rule of thumb: **progression in any one channel → overall PD**, and **CR needs CR everywhere, with no new lesions**.

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

Patients with **non-target disease only** (no measurable target) — note that "Non-CR/Non-PD" replaces "SD":

| Non-target | New lesions | Overall |
|-----------|-------------|---------|
| CR | No | **CR** |
| Non-CR/Non-PD | No | **Non-CR/Non-PD** |
| NE | No | **NE** |
| Unequivocal PD | Yes or No | **PD** |
| Any | Yes | **PD** |

(CR = complete response, PR = partial response, SD = stable disease, PD = progressive disease, NE = not evaluable 不可评估.)

In a [[PCWG3 Criteria]] mCRPC trial, these RECIST calls cover only the **soft-tissue / nodal** channel; bone is judged separately by the 2+2 rule, and the two are combined into the single composite criterion [[Modified RECIST 1.1 and PCWG3 Criteria]] that defines rPFS (radiographic PFS, 影像学无进展生存期).

A limitation that led to [[PCWG3 Criteria]]: RECIST needs measurable disease, so it cannot properly assess prostate cancer that is **mainly in bone** (bone-predominant) — hence the prostate-specific bone/PSA rules. See also [[PSA (Prostate-Specific Antigen)]].

## Step-by-step derivation (for a programmer)

Bottom-up pipeline (自下而上的流程): **lesion measurements → response per channel → overall timepoint response → confirmation → [[Best Overall Response|BOR]]**. Where it lives in CDISC: SDTM **TU**, **TR**, **RS**; ADaM **ADTR** / **ADRS** (BDS, basic data structure 基本数据结构).

**What each domain records** (linked by the lesion id `TULNKID`/`TRLNKID` + RELREC, the related-records dataset 关联记录):

- **TU** (Tumor/Lesion Identification) = the **identity / list (roster, 名册)** of lesions — one row per lesion: location (`TULOC`), method (`TUMETHOD`), classification `TUSTRESC` = **TARGET / NON-TARGET / NEW** (`TUTESTCD = TUMIDENT`). **No measurements.** Target/non-target is set at baseline; new lesions are added when they appear.
  - **`TUMIDENT`** = "**Tumor Identification**" (TUMor IDENTification) — the single topic test of TU, so basically **every** TU row has it; the *answer* (what kind of lesion) is in `TUSTRESC`. Compare **TR**, where `TRTESTCD` **varies** (LDIAM / SAXIS / TUMSTATE…) because TR records different measurements.
- **TR** (Tumor/Lesion Results) = the **measurements / state** of those lesions over time — one row per lesion **per visit**: numbers for targets (`TRTESTCD = LDIAM` longest diameter, or `SAXIS` short axis for nodes), qualitative values for non-targets (`TUMSTATE = PRESENT/ABSENT`).
- **RS** (Disease Response) = the **overall response verdict** (判定) per visit (`RSTESTCD = OVRLRESP`, often derived).

Mnemonic: **TU = which lesions** (identity, set once) · **TR = how big / what state** (results, per visit) · **RS = what response** (verdict).

**Row cardinality per patient** (行数; key: TU is set **once per lesion**; TR & RS **repeat per visit**):

- **TU** ≈ `#lesions × #evaluators` — one row per lesion per reader (new lesions are added when they appear).
- **TR** ≈ `#lesions × #visits × #evaluators` — one row per lesion **per visit** per reader. So "same count as TU" is true **only per visit**; the **total** is TU × #visits — TR is the **largest** domain.
- **RS** ≈ `#response-params × #visits × #evaluators` (+ a BOR record) — the overall (and often target/non-target/new) response **at each visit** per reader; **not** a small fixed 1–3.
- **Evaluators** multiplier (乘数) ≈ ×1–4: investigator + central reader 1 + reader 2 + an adjudicator (裁决者) when they disagree (see [[Local (Investigator) vs Central (BICR) Tumour Assessment]]).

Watch out for the "baseline vs post-baseline" trap: it is tempting to read TU as baseline and TR as post-baseline, but that is not right — **TR has baseline measurements too** (the baseline SoD comes from TR rows at screening), and **TU gets NEW-lesion rows at later visits**. So the split is **identity (TU) vs measurement over time, including baseline (TR) vs verdict (RS)**, not baseline vs post-baseline.

### Step 0 — Baseline lesion setup (TU + TR)

Four sub-steps, all **fixed at baseline**:

1. **Measurability of each lesion.** Non-nodal (非淋巴结): longest diameter **≥10 mm** on CT/MRI (slice thickness 层厚 ≤5 mm, otherwise ≥2× the slice; chest X-ray ≥20 mm; caliper 卡尺 ≥10 mm). Lymph node: by **short axis** — **≥15 mm** = measurable (can be a target), **10–<15 mm** = pathological (病理性) **non-target**, **<10 mm** = normal, not recorded. Non-measurable = lesions <10 mm, nodes 10–<15 mm, and truly non-measurable disease (leptomeningeal 软脑膜, ascites 腹水, effusions 积液, inflammatory breast 炎性乳腺癌, lymphangitic spread 癌性淋巴管炎, cystic 囊性, bone with no soft-tissue part, lesions irradiated before unless they progressed later).
2. **Select target lesions** — up to **5 in total, at most 2 per organ**; pick the **largest** (longest diameter, or short axis for nodes) **that can also be re-measured reliably** (reproducible) on repeat imaging — skip a big lesion you cannot reliably re-measure. The target set is **fixed at baseline** — follow the **same** lesions at every visit; never re-select.
3. **Measurement rule (convention)** — non-nodal target → longest diameter; nodal target → **short axis**. **Baseline SoD** = sum of (non-nodal longest diameters + nodal short axes) — this is the **reference for PR**.
4. **Record non-target** — all other lesions (including pathological nodes 10–<15 mm), qualitatively, as present; they may be grouped (e.g. "multiple liver mets").

*SDTM view:* **TU** = `TULOC` location, `TUSTRESC` = TARGET/NON-TARGET/NEW, lesion link id, `TREVAL` evaluator (**INVESTIGATOR** vs **INDEPENDENT ASSESSOR / BICR**); **TR** = measurement per lesion per visit (`TRLNKID`→TU, `TRTESTCD`=LDIAM…, `TRSTRESN`). Compute baseline SoD only over lesions flagged **TARGET**. *Data checks:* ≤5 targets, ≤2 per organ (by location), each target measurable at baseline, no lesion both target and non-target, lesion ids consistent across visits, **investigator and BICR derived separately**.

### Step 0 mapping example (SDTM TU/TR)

Same lesions (T01 liver / T02 lung TARGET, NT01 bone / NT02 pleura NON-TARGET), baseline `VISIT=SCREENING`.

**TU** — one row per lesion; it identifies and classifies the lesion:

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

- **`TULNKID` is the lesion key**; TR joins to TU via `TRLNKID = TULNKID`. The classification is stored **once** in TU; the measurements repeat per visit in TR.
- **Target** → numeric `TRTESTCD = LDIAM` (longest diameter). **Non-target** → `TRTESTCD = TUMSTATE = PRESENT` (qualitative, no number).
- If T02 were a **lymph node**, `TRTESTCD = SAXIS` (short axis), and only the short axis goes into the sum.
- **`TUEVAL`/`TREVAL = INVESTIGATOR`** here; a **BICR** read is a **parallel** set of rows with `TREVAL = INDEPENDENT ASSESSOR`, derived separately.
- **Baseline SoD (50 + 30 = 80 mm) is NOT a raw TR row** — it is **derived** later, downstream (ADaM ADTR/ADRS, `PARAMCD` like `SUMDIAM`), adding only TARGET lesions. **RS** holds the overall response per visit (Step 2), e.g. `RSTESTCD = OVRLRESP`.

### Step 1 — At each post-baseline visit, evaluate three channels separately

- **Target** — add up the current target diameters = `SoD(t)`; track the **nadir** = the smallest SoD so far.
  - **CR** all targets = 0 (nodal target <10 mm short axis); **PR** `SoD(t) ≤ 0.70 × baseline`; **PD** `SoD(t) ≥ 1.20 × nadir` **and** `(SoD(t) − nadir) ≥ 5 mm`; otherwise **SD**; **NE** if a target was not measured and the call cannot be made.
  - **Key trap:** PR is compared with **baseline**, PD with the **nadir** — two different reference points.
- **Non-target** — CR (all gone + nodes <10 mm + tumour markers normal) / Non-CR/Non-PD / **unequivocal** (明确的) PD / NE.
- **New lesions** — any clear new lesion → flag it (→ PD).
- Note: "unequivocal" non-target progression and new lesions are a **qualitative call by the radiologist/investigator**, not computed from numbers.

### Step 2 — Combine into the overall timepoint response

Use the tables above: progression in **any** channel → **PD**; **CR** needs CR in target **and** non-target **and** no new lesions; otherwise read PR/SD/Non-CR-Non-PD/NE from the matching table.

### Step 3 — Confirmation

In trials where ORR is primary / that are not randomized, a CR/PR must be **confirmed** by a repeat assessment ≥4 weeks later.

### Step 4 — BOR per patient → endpoints

The best overall timepoint response from **baseline → first PD** (with the confirmation + minimum-SD-duration rules) → responder flag (BOR ∈ CR/PR) → **ORR**; DoR/PFS are derived alongside.

**Practical note:** often the investigator or **BICR** gives the target/non-target/overall responses directly in **RS** (collected), and the programmer derives **BOR** from them. Whether you **re-derive** timepoint responses from TR measurements or **use RS as collected** is a **SAP** (statistical analysis plan, 统计分析计划) decision. The nadir is computed over the patient's own history.

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

(Non-target is Non-CR/Non-PD throughout; no new lesions.)

**BOR = PR** (confirmed at Wk16), reached before the first PD (Wk24) → **responder = yes**, counts toward [[Best Overall Response|ORR]].

What it shows: PR is judged against **baseline** (80), PD against the **nadir** (45) — different reference points; the **nadir** only moves down (80→50→45) and then holds; a single PR at Wk8 is not enough until Wk16 **confirms** it; after PD the window **closes**.

## Official reference

Eisenhauer EA, Therasse P, Bogaerts J, et al. **New response evaluation criteria in solid tumours: revised RECIST guideline (version 1.1).** *Eur J Cancer.* 2009;45(2):228–247. doi:10.1016/j.ejca.2008.10.026
