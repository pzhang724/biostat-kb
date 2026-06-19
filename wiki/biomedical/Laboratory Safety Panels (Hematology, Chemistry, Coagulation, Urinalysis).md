---
title: "Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)"
type: concept
status: learned
tags: [medical, trial-conduct]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)

The full lab list from the trial's [[Schedule of Assessments]]. Four panels: **hematology** (marrow output), **blood chemistry** (organ function + electrolytes + metabolic), **coagulation** (bleeding risk + liver synthesis), **urinalysis** (cheap kidney/bladder/infection screen). In a PSMA radioligand trial these are mostly **safety-monitoring** labs repeated each cycle — and three groups (marrow, kidney, bladder) are exactly where the radioligand deposits dose. The entry-threshold *direction* logic (which want high vs low) lives in [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]; this page is the per-parameter catalog.

## Hematology Panel (marrow output)

| Parameter | 中文 | What it tells you |
|---|---|---|
| Hemoglobin | 血红蛋白 | O₂-carrying capacity; low = anemia |
| Red blood cell count | 红细胞计数 | RBC number; pairs with Hgb |
| White blood cell count | 白细胞计数 | total immune cells; low = infection risk, high = infection/inflammation |
| Platelet count | 血小板计数 | clotting cells; low = bleeding risk |
| Reticulocyte percent | 网织红细胞百分比 | % young (immature) RBCs = how fast marrow is **regenerating**; low retic + anemia = marrow not responding (e.g. radiation-suppressed) |

**5-part WBC differential (白细胞分类):**
- **Neutrophil** (中性粒细胞) — bacterial infection / neutropenia (the count with entry floors)
- **Lymphocyte** (淋巴细胞) — viral immunity
- **Monocyte** (单核细胞)
- **Eosinophil** (嗜酸性粒细胞) — allergy / parasite
- **Basophil** (嗜碱性粒细胞)

## Blood Chemistry Panel

**Liver** — AST / ALT (转氨酶, hepatocellular injury; ALT more liver-specific) · Alkaline phosphatase / ALP (碱性磷酸酶, cholestasis **or** bone — note bone mets & osteoblastic activity raise it) · LDH (乳酸脱氢酶, nonspecific cell turnover / tumour burden / hemolysis) · Total & direct bilirubin (总/直接胆红素, direct=conjugated → biliary/excretion problem; indirect → hemolysis/Gilbert) · Total protein (总蛋白) & Albumin (白蛋白, liver synthesis + nutrition/prognosis).

**Kidney** — Creatinine + calculated creatinine clearance (肌酐 + 计算肌酐清除率; CrCl estimates GFR; kidney is dose-limiting for radioligand) · BUN (尿素氮, renal + hydration/protein) · Uric acid (尿酸, also a tumour-lysis marker).

**Electrolytes / acid-base** — Sodium (钠) · Potassium (钾, cardiac-critical) · Chloride (氯) · Bicarbonate (碳酸氢盐, acid-base) · Total calcium (总钙, bone mets → hypercalcemia) · Phosphate (磷酸盐) · Magnesium (镁).

**Pancreas** — Amylase (淀粉酶) · Lipase (脂肪酶, more pancreas-specific); flag pancreatitis.

**Muscle / cardiac** — Creatine kinase / CK (肌酸激酶); if elevated, **fractionate isoenzymes** to separate skeletal muscle (CK-MM) from heart (CK-MB).

**Endocrine / metabolic** — TSH (促甲状腺激素, thyroid screen — on the panel because hyper-/hypothyroidism is a radiation [[Adverse Event of Special Interest (AESI)]]) · Glucose, non-fasted (血糖，非空腹).

## Coagulation

- **INR** (国际标准化比值) — standardized PT; **extrinsic** pathway, sensitive to warfarin and to liver synthesis (clotting factors are made in the liver).
- **PTT / aPTT** (部分凝血活酶时间) — **intrinsic** pathway, sensitive to heparin.

Together a bleeding-risk + liver-function check.

## Urinalysis (Dip Stick)

Cheap screen; **reflex to microscopic examination (镜检) only if the dipstick is abnormal** (casts, crystals, cells, bacteria).

- **Blood** (潜血) — hematuria; kidney/bladder; relevant because the radioligand is renally excreted → cystitis risk.
- **Glucose** (尿糖) — spills when blood glucose exceeds the renal threshold (diabetes).
- **Protein** (尿蛋白) — proteinuria = glomerular/renal damage.
- **Leucocyte test** (白细胞酯酶) — UTI / inflammation.

Note: urinalysis parameters generally have **no [[CTCAE Grade]] term**, so unlike chemistry/hematology analytes they can't be CTCAE-graded.

## Radioligand tie-in

Marrow (hematology + reticulocyte), kidney (creatinine/CrCl/BUN + urine protein/blood), and bladder (urine blood → cystitis) are the dose-deposit organs — see [[Xerostomia]], [[Dosimetry]], [[Pharmacokinetics (PK)]]. TSH, electrolytes, pancreas, and CK are generic safety. Part of [[Oncology]]; collected per the [[Schedule of Assessments]] grid.
