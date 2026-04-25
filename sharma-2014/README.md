# Caraka Saṃhitā — Volume I

P. V. Sharma, *Caraka Saṃhitā*, Chaukhambha Orientalia (Varanasi), 2014.

This directory holds the chapter-level markdown of the Sharma 2014 English translation of the Caraka Saṃhitā, derived from the page-by-page plain-text scans in [`../pages/`](../pages/). Format spec: [CONVENTIONS.md](CONVENTIONS.md).

## Scope

The Caraka Saṃhitā has **eight sthānas (sections)** totalling 120 chapters. Sharma's edition is published in six volumes; this conversion covers **Volume I only** — the first 5 sthānas, 66 chapters. Volumes II-VI (containing Cikitsā, Kalpa, Siddhi sthānas, the clinical-therapeutics half of the canon) are not yet sourced.

| Sthāna | Section | Chapters | Pages | Status |
|---|---|---|---|---|
| 1. Sūtrasthāna | Fundamentals | 30 | 44-289 | ✓ Vol I |
| 2. Nidānasthāna | Diagnosis | 8 | 290-338 | ✓ Vol I |
| 3. Vimānasthāna | Specific Features | 8 | 339-433 | ✓ Vol I |
| 4. Śārīrasthāna | Study of Human Body | 8 | 434-526 | ✓ Vol I |
| 5. Indriyasthāna | Signs of Life and Death | 12 | 527-566 | ✓ Vol I |
| 6. Cikitsāsthāna | Therapeutics | 30 | — | Vol II-IV (not sourced) |
| 7. Kalpasthāna | Pharmaceutics | 12 | — | Vol V-VI (not sourced) |
| 8. Siddhisthāna | Success in Treatment | 12 | — | Vol VI (not sourced) |

## Sthāna indices

- [1. Sūtrasthāna](01-sutrasthana/_index.md) — 30 chapters
- [2. Nidānasthāna](02-nidanasthana/_index.md) — 8 chapters
- [3. Vimānasthāna](03-vimanasthana/_index.md) — 8 chapters
- [4. Śārīrasthāna](04-sharirasthana/_index.md) — 8 chapters
- [5. Indriyasthāna](05-indriyasthana/_index.md) — 12 chapters

## Source notes worth flagging

These are artifacts of the source edition or its OCR, not the conversion. Flagged here for any future philological pass.

- **Sūtra ch 18 (Triśothīya)** has two Sanskrit colophons — one mid-chapter on book p. 170, one at the end on p. 173. Possibly two redactional layers in the printed source.
- **Sūtra ch 22, 23** lack the `CHAPTER XXII` / `CHAPTER XXIII` Roman-numeral marker in the source pages; chapter boundaries detected by Sanskrit ordinal alone.
- **Nidāna ch 4 (Prameha)** has a duplicated paittika-prameha block on book pp. 312-313; the version with introductory framing was kept.
- **Nidāna ch 6 (Śoṣa)** book p. 323 has a misplaced fragment about insanity inside the wasting-causes section; the stray fragment was omitted as a transcription dislocation.
- **Vimāna ch 2 (Trividhakukṣīya)** has overlapping content for verses [12]-[16] across book pp. 350-351 — duplicated *āma* / *alasaka* / *daṇḍālasaka* discussion. Preserved verbatim.
- **Vimāna ch 8** verse marker `[44]` on book p. 432 is likely a typo for `[144]`. Preserved as printed.
- **Śārīra ch 8 (Jātisūtrīya)** has a one-page gap in the OCR source between book pp. 471 and 473 — book p. 472 is missing. Verses [29-31] flow across the gap as a noticeably truncated paragraph.
- **Indriya ch 9** colophon English numbered `(7)` in source; corrected to `(9)` since the Sanskrit reads `॥९॥`. The single Sharma-typo correction in this conversion.
- **Indriya ch 10** colophon-English title "signs of sudden death" contradicts opening-line "signs of imminent death." Both preserved.
- **Indriya ch 8** verses [16-17] precede [13-20] in the source — printing out of sequence. Preserved verbatim.

## Devanagari coverage

The page-level transcription preserves real Devanagari for chapters whose underlying source pages had usable Sanskrit text — predominantly Sūtrasthāna chapters 1 to ~17 (book pp. 1-140 of the OCR). From book p. 141 onwards, dense Sanskrit verses are marked `[Devanagari unclear: …]` in the page transcription and dropped silently in the markdown per [CONVENTIONS.md](CONVENTIONS.md). The English paragraphs stand alone in those chapters. Reconstructing the Sanskrit for the placeholder-only chapters would require either a Devanagari-capable OCR pass over the source PDF (`~/git/bibliography/en/caraka/caraka-samhita-priya-vrat-sharma.pdf`) or cross-referencing against an alternate edition such as the 1922 Nirnaya Sagar text with Cakrapāṇi's *Āyurveda Dīpikā* commentary.

## Back-matter

Pages 568-582 of the source contain an alphabetical subject index (English term → page numbers in Sharma's pagination). Not yet converted to per-letter markdown files; the raw text is in [`../pages/568.txt`](../pages/568.txt) through [`../pages/582.txt`](../pages/582.txt). Conversion to cross-linked anchors would require resolving Sharma's page numbers to chapter+verse references in this markdown — a follow-up task.
