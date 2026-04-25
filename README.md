# Caraka Saṃhitā

A working repository for the careful study, translation, and philological verification of the *Caraka Saṃhitā* — the foundational clinical text of Āyurveda, composed c. 100 BCE – 200 CE and revised by Dṛḍhabala (c. 300–500 CE).

The work here supports [*The Book of Sol*](../TheBookOfSol/) and any future project that rests on Caraka's authority. The goal is to move from "translator told me so" to "the Sanskrit says so, with sources and manuscript variants tracked."

## Why a separate repository

The *Caraka Saṃhitā* is long, layered, and philologically contested. Its received Sanskrit shows manuscript variance; modern English translations make interpretive choices that often smooth over grammatical anomalies; traditional commentaries (Cakrapāṇidatta, Gaṅgādhara) resolve some ambiguities and preserve others. Any serious engagement with Caraka needs:

- Per-page OCR of at least one printed edition
- Curated digests organized by *sthāna* (the eight-section structure of the text)
- Thematic digests across *sthāna* boundaries
- Philological notes tracking where the received Sanskrit is ambiguous, where translators disagree, where commentaries decide
- Provenance tracking: which edition, which page, which manuscript variant
- A clean record of every manual OCR correction

Keeping all of this in one dedicated repository makes it easier for a reader to audit the evidence and for future work to build on it incrementally.

## Layout

```
caraka-samhita/
├── README.md              — this file
├── AGENTS.md              — conventions for AI agents contributing
├── .gitignore             — excludes PNG scans, PDFs
│
├── sutrasthana.md         — curated digest, Book 1 (general principles, diet, dravyas)
├── vimanasthana.md        — curated digest, Book 3 (measurement, methodology)
├── sarirasthana.md        — curated digest, Book 4 (embryology, anatomy)
├── indriyasthana.md       — curated digest, Book 5 (prognostic signs)
├── nidanasthana.md        — curated digest, Book 2 (etiology)
│
├── fruit-vegetable-warnings.md
│                          — thematic digest from Sū. 27 on doṣa-aggravating fruits
│                            and the boil-press-add-fat preparation rule for gourds
│
├── sharma-2014/           — chapter-level markdown of the Priya Vrat Sharma
│                            (Chaukhambha Orientalia, 2014) edition. Volume I only:
│                            5 sthānas, 66 chapters. See sharma-2014/README.md and
│                            sharma-2014/CONVENTIONS.md.
│                            Future editions (Sharma-Dash 1976, Nirnaya Sagar 1922,
│                            Angot 2011, Sen-Sen 1894) will live as sibling
│                            edition-named directories.
│
└── notes/
    ├── translation-sources.md
    │                      — what editions we have, what we need, what we've checked,
    │                        what failed, where the scholarly gold standard lives
    │
    ├── ocr-corrections.md
    │                      — historical record of manual corrections applied during
    │                        the page-by-page OCR pass that produced sharma-2014/
    │
    └── philology/
        └── sutrasthana-5-12.md
                           — the saindhavān / lavaṇaṃ / ghṛtam question
                             (the first verse whose received Sanskrit we have examined
                             closely and whose received translation we do not trust)
```

The intermediate `pages/*.txt` per-page OCR (582 files, 5 sthānas) and `.ocr_pages/page-NNN.png` PDF-page scans are no longer in the working tree. The OCR text is preserved in git history; the PNGs are regeneratable from the source PDF via `pdftoppm`.

## Editions on disk

Primary reference edition, already downloaded and indexed in the standalone bibliography repo:

- **Caraka Saṃhitā**, trans. Priya Vrat Sharma (Chaukhambha Orientalia, 2014).\
  Path: `~/git/bibliography/en/caraka/caraka-samhita-priya-vrat-sharma.pdf`.\
  MD5: `93746e6b31e5d0d816e6ac8923b3b634`.\
  Chapter-level English markdown of this edition lives in `sharma-2014/`.

Editions not yet on disk but on the wish-list (see `notes/translation-sources.md`):

- R.K. Sharma & Bhagwan Dash, *Caraka Saṃhitā: Text with English Translation & Critical Exposition Based on Cakrapāṇi Datta's Āyurveda Dīpikā* (Chowkhamba Sanskrit Series, 7 vols) — the commentary-rich gold standard.
- Jādavji Trikamji Āchārya critical Sanskrit edition (Chaukhambha Krishnadas Academy reprint) — for critical apparatus / manuscript variants.
- 1922 Nirnaya Sagar edition with Cakrapāṇi's *Āyurveda Dīpikā* commentary (archive.org, 733 MB PDF) — public domain; needs Devanagari-capable OCR.

## Provenance convention

Two principles:

1. **The chapter-level markdown in `sharma-2014/` is the canonical English-side reference** for the Sharma 2014 edition. Manual corrections applied during the OCR pass are logged in `notes/ocr-corrections.md` with scan evidence.
2. **Every verse reference that ends up in a downstream article** (in TheBookOfSol or elsewhere) should be **verifiable** from this repository: either from the chapter-level markdown, the historical OCR text in git history, or a verified-Sanskrit digest in `notes/philology/`.

## Version control

Jujutsu (`jj`), same as the rest of the sema-ecosystem. Typical flow:

```
jj status
jj commit -m "(action, scope, detail)" <files>
jj bookmark set main -r @-
jj git push
```

Commit messages follow the comma-grouped parenthetical style used across the ecosystem.
