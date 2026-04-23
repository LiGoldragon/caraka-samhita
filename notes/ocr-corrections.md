# OCR corrections log

Every manual correction applied to a file in `pages/` is recorded here, with scan evidence and rationale. This file is the audit trail for deviations between the raw OCR output and the committed `pages/*.txt` content.

## Convention

An entry records:

- **Page:** the page number as it appears in `pages/`
- **Location:** a brief phrase identifying where on the page the correction sits (verse number, section, or a unique adjacent phrase)
- **Raw OCR:** the exact string the machine transcription produced
- **Corrected:** the exact string we replaced it with
- **Scan evidence:** either a paraphrase of what the scan shows, a reference to `.ocr_pages/page-NNN.png`, or both
- **Rationale:** one sentence on why the correction is warranted

## Entries

### page 074 — Sūtrasthāna 5.12, verse, first pāda

- **Raw OCR:** `आनलकानि`
- **Corrected:** `आमलकानि` (*āmalakāni*, Indian gooseberry, accusative plural neuter)
- **Scan evidence:** `.ocr_pages/page-074.png` clearly shows `आमलकानि` (the Devanagari *म* is unambiguous). OCR confused *म* (ma) with *न* (na), a common Devanagari OCR error.
- **Rationale:** (a) the word is metrically required — 5 syllables, *ā-ma-la-kā-ni* — and *āna-la-kā-ni* would scan identically, but *ānalaka* is not a Sanskrit word; *āmalaka* is the standard name for *Emblica officinalis* (Indian gooseberry), which appears throughout Caraka's dietary verses; (b) the Sharma English translation of this verse reads "āmalaka (fruits)" in the corresponding position, confirming the correct reading is *āmalaka*; (c) the scan itself is clear. This is an unambiguous OCR typo, not a textual variant.
- **Date applied:** 2026-04-23
- **Applied by:** Claude (session with Olivier)
- **Related philology note:** [`philology/sutrasthana-5-12.md`](./philology/sutrasthana-5-12.md)
