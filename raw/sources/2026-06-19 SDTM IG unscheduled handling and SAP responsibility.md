From chat, 2026-06-19. Follow-up. Grounded with a web search (lexjansen/CDISC/Pinnacle21 secondary sources on SDTMIG conventions).

Human asked: (1) how does the SDTM IG handle this; (2) how do I know whether an unscheduled visit can go into a given AVISIT — is it defined in the SAP; (3) if the protocol doesn't write it, does the SAP define it itself?

Answer given (content marker):

(1) SDTM IG handling:
- Planned visits live in the TV (Trial Visits) domain — TV holds SCHEDULED visits only.
- IG rule: VISIT + VISITNUM in subject-level domains must match TV, EXCEPT for unscheduled/unplanned visits (the IG explicitly carves out that exception). So unscheduled visits don't appear in TV; they're recorded in SV + the data domains with sponsor-assigned numbers.
- VISITNUM convention (a convention, not a mandated scheme; sponsor-defined, documented in define.xml / cSDRG):
  * decimal insert between bracketing scheduled visits, keeping chronological order — two unscheduled between visit 3 and 4 → 3.1, 3.2.
  * unplanned on the SAME DATE as a planned visit → planned VISITNUM + 0.01.
  * VISIT for unplanned often left null (or "UNSCHEDULED") per sponsor; VISITDY/SVSTDTC carry actual timing.
- Validators (Pinnacle 21 checks e.g. SD1023 / SD1060) police visit consistency against TV with the unscheduled exception; do it the expected way or justify in cSDRG.

(2) Whether unscheduled can enter a given AVISIT = an ANALYSIS decision, defined in the SAP (operationalized in the ADaM spec / define.xml), NOT in SDTM/IG. The visit-windowing algorithm — which actual/unscheduled assessments map to which analysis visit, plus the tie-break when several land in one window (closest-to-nominal-day, last/worst, etc.) — lives in the SAP.

(3) If the protocol is silent (the usual case): YES, the SAP defines it. The protocol gives the SoA's OPERATIONAL/conduct visit windows (acceptable timing for a scheduled visit); the SAP gives the ANALYSIS visit windows + unscheduled handling + tie-breakers. It is the statistician's responsibility and must be explicit, else the derivation isn't reproducible. Protocol = conduct windows; SAP = analysis windows.

One line: TV 只放计划访视;unscheduled 在 SV/数据域里按 sponsor 约定编号(3.1/3.2,同日 +0.01,VISIT 常留空或 "UNSCHEDULED"),IG 给约定不强制方案、写进 define.xml/cSDRG;而"unscheduled 能否进某 AVISIT"是分析问题,由 SAP 定(ADaM spec 落地),protocol 没写就由 SAP 明确定义——这是统计师的活,必须写清才可复现。

Sources:
- https://www.lexjansen.com/css-us/2016/PP13_Final.pdf (Let's Visit — scheduled/unscheduled VISITNUM)
- https://www.pinnacle21.com/forum/unplanned-visits-and-sdtm-rule-sd1060
- https://www.lexjansen.com/pharmasug-cn/2017/CD/PharmaSUG-China-2017-CD05_ppt.pdf (Assigning VISITNUM and EPOCH)
