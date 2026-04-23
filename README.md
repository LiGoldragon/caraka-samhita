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
├── pages/                 — per-page OCR text, 262 pages
│                            Source: Priya Vrat Sharma, Chaukhambha Orientalia, 2014
│                            edition. Machine-transcribed; manually corrected entries
│                            tracked in notes/ocr-corrections.md.
│
├── .ocr_pages/            — PNG scans of the same pages (gitignored; regeneratable
│                            from the source PDF in ~/git/bibliography/en/caraka/)
│
└── notes/
    ├── translation-sources.md
    │                      — what editions we have, what we need, what we've checked,
    │                        what failed, where the scholarly gold standard lives
    │
    ├── ocr-corrections.md
    │                      — every manual correction applied to pages/, with before,
    │                        after, and scan evidence
    │
    └── philology/
        └── sutrasthana-5-12.md
                           — the saindhavān / lavaṇaṃ / ghṛtam question
                             (the first verse whose received Sanskrit we have examined
                             closely and whose received translation we do not trust)
```

## Editions on disk

Primary reference edition, already downloaded and indexed in the standalone bibliography repo:

- **Caraka Saṃhitā**, trans. Priya Vrat Sharma (Chaukhambha Orientalia, 2014).\
  Path: `~/git/bibliography/en/caraka/caraka-samhita-priya-vrat-sharma.pdf`.\
  MD5: `93746e6b31e5d0d816e6ac8923b3b634`.\
  OCR of this edition is the source of the `pages/` directory.

Editions not yet on disk but on the wish-list (see `notes/translation-sources.md`):

- R.K. Sharma & Bhagwan Dash, *Caraka Saṃhitā: Text with English Translation & Critical Exposition Based on Cakrapāṇi Datta's Āyurveda Dīpikā* (Chowkhamba Sanskrit Series, 7 vols) — the commentary-rich gold standard.
- Jādavji Trikamji Āchārya critical Sanskrit edition (Chaukhambha Krishnadas Academy reprint) — for critical apparatus / manuscript variants.
- 1922 Nirnaya Sagar edition with Cakrapāṇi's *Āyurveda Dīpikā* commentary (archive.org, 733 MB PDF) — public domain; needs Devanagari-capable OCR.

## Provenance convention

Two principles:

1. **The raw `pages/*.txt` OCR is preserved as-is** except where a scan-verified correction is recorded in `notes/ocr-corrections.md` with the specific diff and the reason.
2. **Every verse reference that ends up in a downstream article** (in TheBookOfSol or elsewhere) should be **verifiable** from this repository: either from the raw OCR, a corrected OCR entry, or a verified-Sanskrit digest in `notes/philology/`.

## Version control

Jujutsu (`jj`), same as the rest of the sema-ecosystem. Typical flow:

```
jj status
jj commit -m "(action, scope, detail)" <files>
jj bookmark set main -r @-
jj git push
```

Commit messages follow the comma-grouped parenthetical style used across the ecosystem.
