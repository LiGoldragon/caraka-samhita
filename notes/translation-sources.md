# Translation sources — inventory, gaps, and research trail

What editions of the *Caraka Saṃhitā* exist, which we have, which we don't, which we've tried to acquire, and what the research so far has shown.

## The primary reference edition on disk

### Caraka Saṃhitā, trans. Priya Vrat Sharma (Chaukhambha Orientalia, 2014)

- **Path:** `~/git/bibliography/en/caraka/caraka-samhita-priya-vrat-sharma.pdf`
- **Registered MD5:** `93746e6b31e5d0d816e6ac8923b3b634`
- **Status:** Primary source for the `pages/*.txt` OCR in this repository. 262 pages covering Sūtrasthāna and commentary.
- **Strengths:** Bilingual Sanskrit–English, widely available, readable English. The English translation is the basis for almost every modern Ayurvedic-studies reference in the Anglophone world.
- **Limits:**
  - The English translation makes interpretive choices that are not always supported by the Sanskrit (see [`philology/sutrasthana-5-12.md`](./philology/sutrasthana-5-12.md) for a worked example: *dhānyaṃ* rendered as "rain water"; *saindhavān lavaṇaṃ* smoothed into a "rock salt" compound despite grammatical non-agreement).
  - Does not include classical commentaries.
  - OCR on Devanagari portions is imperfect; manual corrections tracked in [`ocr-corrections.md`](./ocr-corrections.md).

## Editions we attempted and failed to acquire

### Sen & Sen 1894 (Calcutta, Dhanwantari)

- 19th-century Bengali-tradition edition by Debendra Nath Sen and Upendra Nath Sen.
- **Why wanted:** pre-Chaukhambha editorial tradition; useful for cross-checking received readings against a different manuscript lineage.
- **Anna's Archive MD5:** `c9f5e27a41125f624f66348b3c04d652`
- **Size:** 72.5 MB, PDF
- **Status:** Attempted download via `annas book-download` on 2026-04-23 failed twice due to annas-mcp's built-in HTTP timeout (file got to ~35 MB, then the client killed the connection). The `timeout` wrapper does not override the internal client timeout.
- **Next-try suggestion:** download directly from `annas-archive.gd` landing page via `curl` or `aria2c` with resumable transfer, or retry during a period of better connectivity.

### Michel Angot 2011, Les Belles Lettres (Indika series)

- *Caraka-Samhita. Traité d'Ayurveda — Volume I: Le livre des Principes (Sutrasthana) et le Livre du Corps (Sharirasthana)*.
- **Why wanted:** modern Western critical edition by a serious Sanskritist (French); scholarly apparatus; independent translation.
- **Anna's Archive MD5:** `c20c936d8c948888365a17d577e60280`
- **Size:** 52.5 MB, PDF, French language
- **Status:** Same as above — annas-mcp timeout, got to ~28 MB before failure.
- **Next-try suggestion:** same; also, this is a Les Belles Lettres publication and the French language version is readily available new or used.

## Editions on the wish-list (not attempted)

### R.K. Sharma & Bhagwan Dash — *Caraka Saṃhitā: Text with English Translation & Critical Exposition Based on Cakrapāṇi Datta's Āyurveda Dīpikā*

- Chowkhamba Sanskrit Series, 7 volumes. The scholarly gold standard for Caraka work in English.
- **Why wanted:** includes Cakrapāṇidatta's *Āyurveda Dīpikā* commentary — the canonical traditional commentary that resolves grammatical anomalies in the received Sanskrit. Without this, the philological work in `philology/` cannot reach definitive conclusions for verses where received Sanskrit is ambiguous.
- **Status:** not yet acquired. Anna's Archive has a partial (Śārīra-sthāna only, hash `037f1c66533e9a9701f4c8c2907bbda7`); the Sūtra-sthāna volume would have to be located separately. Available new from Vedic Books / Amazon.
- **Priority:** **HIGH.** This is the single most useful addition to the project library.

### Jādavji Trikamji Āchārya critical Sanskrit edition

- Chaukhambha Krishnadas Academy reprint.
- **Why wanted:** the standard critical Sanskrit text with manuscript apparatus. Pairs well with GRETIL for chapters GRETIL covers.
- **Status:** not yet acquired. Widely available as a physical book.

### 1922 Nirnaya Sagar edition with Cakrapāṇi's Āyurveda Dīpikā

- Edited by Vaman Kesheo Datar, Bombay. Public domain.
- **Why wanted:** free, public-domain edition with the canonical traditional commentary. Functionally equivalent (for verse-level philology) to the Sharma/Dash volume.
- **Status:** available on [Internet Archive](https://archive.org/details/LXpJ_charaka-samhita-sanskrit-with-ayurveda-dipika-commentary-of-chakra-pani-dutta-by) as a 733 MB PDF. The archive.org automatic OCR failed completely on the Devanagari text — the `_djvu.txt` is all "CC-0" metadata stamps, useless. A local run of Devanagari-capable OCR (Tesseract with `san` language data, or Google Cloud Vision) on the downloaded PDF would extract a usable searchable text.
- **Priority:** **MEDIUM.** Free and permanently accessible. A one-time OCR pass would unlock Cakrapāṇi's commentary for the entire project.

## Digital Sanskrit sources checked

### GRETIL (Göttingen Register of Electronic Texts in Indian Languages)

- **Mirror on GitHub:** [INDOLOGY/GRETIL-mirror](https://github.com/INDOLOGY/GRETIL-mirror). Raw file: `gretil.sub.uni-goettingen.de/gretil/1_sanskr/6_sastra/7_ayur/caraka_u.htm`.
- **Coverage:** **partial.** Oliver Hellwig's GRETIL contribution covers only selected *Sūtrasthāna* chapters — specifically 1, 12, 26, 27, 28. **Chapter 5 is not present.**
- **Meaning for verse-level philology:** GRETIL is authoritative Unicode-encoded Sanskrit for the chapters it covers but cannot verify any verse outside those chapters. A snapshot is at [`../tmp/caraka-gretil.htm`](../tmp/caraka-gretil.htm) [not yet committed to this repo] for reference.

### wisdomlib.org — Charaka Samhita (English translation)

- URL pattern: `https://www.wisdomlib.org/hinduism/book/charaka-samhita-english/d/doc<NNNNNN>.html`
- **Coverage:** full text in English, chapter-by-chapter.
- **Edition basis:** unclear from the site; translation style differs from Sharma.
- **Finding:** wisdomlib's translation of Sūtrasthāna 5.12 **adds an item** ("flesh of jangala animals" / *jāṅgala-māṃsa*) not present in Sharma's rendering. This evidences **manuscript variance** within the textual tradition for this verse. See [`philology/sutrasthana-5-12.md`](./philology/sutrasthana-5-12.md).

### CCRAS Online Caraka Saṃhitā

- [PMC article describing it](https://pmc.ncbi.nlm.nih.gov/articles/PMC11782805/) — the Indian government Central Council for Research in Ayurvedic Sciences published a web edition.
- **Status:** not yet accessed directly. Worth checking for another independent English rendering.

### TextGrid / Claudius Teodorescu's GRETIL search interface

- Search interface: `https://claudius-teodorescu.gitlab.io/gretil-corpus-site/`
- Migrated GRETIL home: `https://textgridrep.org/project/TGPR-2ba9cb1b-9602-202d-71ce-67e63a29de55`
- **Status:** not yet explored; may offer better search than the raw GitHub mirror.

## Immediate research priorities

1. Either **acquire the 1922 Nirnaya Sagar PDF + run Devanagari OCR locally** (free path) or **acquire the Sharma/Dash 7-volume set** (fastest path to commentary-verified readings).
2. Resolve the **Sūtrasthāna 5.12 *saindhavān*** question using whichever of the above becomes available first. See [`philology/sutrasthana-5-12.md`](./philology/sutrasthana-5-12.md).
3. Extend the same verification discipline to any other verse we plan to quote authoritatively in a downstream article.

## Sources referenced in this note

- [Anna's Archive](https://annas-archive.org/) via the `annas` CLI in the mentci-tools bundle
- [GRETIL mirror (GitHub)](https://github.com/INDOLOGY/GRETIL-mirror)
- [Internet Archive — Caraka with Ayurveda Dipika 1922](https://archive.org/details/LXpJ_charaka-samhita-sanskrit-with-ayurveda-dipika-commentary-of-chakra-pani-dutta-by)
- [wisdomlib.org — Charaka Samhita English](https://www.wisdomlib.org/hinduism/book/charaka-samhita-english)
