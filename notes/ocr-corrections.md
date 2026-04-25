# OCR corrections log

Audit trail for manual corrections applied during the page-by-page OCR pass that produced [`../sharma-2014/`](../sharma-2014/). The intermediate per-page OCR text (`pages/*.txt`) is preserved in git history; the PDF-page scans (`.ocr_pages/page-NNN.png`) are gitignored and regeneratable from the source PDF via `pdftoppm`.

## Convention

An entry records:

- **Page:** the page number in the source PDF / OCR layer
- **Location:** a brief phrase identifying where on the page the correction sits (verse number, section, or a unique adjacent phrase)
- **Raw OCR:** the exact string the machine transcription produced
- **Corrected:** the exact string we replaced it with
- **Scan evidence:** what the scan shows (the PNG for that page is regeneratable from the source PDF if needed)
- **Rationale:** one sentence on why the correction is warranted

## Entries

### page 074 — Sūtrasthāna 5.12, verse, first pāda

- **Raw OCR:** `आनलकानि`
- **Corrected:** `आमलकानि` (*āmalakāni*, Indian gooseberry, accusative plural neuter)
- **Scan evidence:** the page-074 scan (regeneratable as `.ocr_pages/page-074.png` from the source PDF) clearly shows `आमलकानि` (the Devanagari *म* is unambiguous). OCR confused *म* (ma) with *न* (na), a common Devanagari OCR error.
- **Rationale:** (a) the word is metrically required — 5 syllables, *ā-ma-la-kā-ni* — and *āna-la-kā-ni* would scan identically, but *ānalaka* is not a Sanskrit word; *āmalaka* is the standard name for *Emblica officinalis* (Indian gooseberry), which appears throughout Caraka's dietary verses; (b) the Sharma English translation of this verse reads "āmalaka (fruits)" in the corresponding position, confirming the correct reading is *āmalaka*; (c) the scan itself is clear. This is an unambiguous OCR typo, not a textual variant.
- **Date applied:** 2026-04-23
- **Applied by:** Claude (session with Olivier)
- **Related philology note:** [`philology/sutrasthana-5-12.md`](./philology/sutrasthana-5-12.md)
