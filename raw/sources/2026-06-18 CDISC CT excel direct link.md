From chat, 2026-06-18

Q: 我觉得 CDISC CT 应该就是一个 Excel，但怎么也找不到 link。

A (summary delivered in chat):

It IS an Excel (.xls) — the reason it's hard to find is that cdisc.org doesn't host the file
itself; it points to NCI-EVS, where the Excel sits in a per-standard folder (one Excel per
standard, not one combined file).

Direct download — SDTM CT Excel (verified, latest 2026-03-31):
https://evs.nci.nih.gov/ftp1/CDISC/SDTM/SDTM Terminology.xls
(same folder also has "SDTM Terminology Changes.xls" = diff vs prior version, and an Archive/
subfolder for older dated versions.)

Same naming pattern per standard (just swap the folder + file name):
- ADaM:  https://evs.nci.nih.gov/ftp1/CDISC/ADaM/ADaM Terminology.xls
- CDASH: https://evs.nci.nih.gov/ftp1/CDISC/CDASH/CDASH Terminology.xls
- SEND:  https://evs.nci.nih.gov/ftp1/CDISC/SEND/SEND Terminology.xls
- Define-XML: https://evs.nci.nih.gov/ftp1/CDISC/Define-XML/

Browse the parent folder to pick a standard/version: https://evs.nci.nih.gov/ftp1/CDISC/
One Excel = all codelists for that standard, with NCI C-codes, submission values, decodes,
and Extensible Yes/No per codelist. Updated ~quarterly.
