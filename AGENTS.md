# Instructions for AI Agents Working on the Caraka Saṃhitā Repository

This file is read by any AI coding/writing agent that recognizes the `AGENTS.md` convention. It records the standing conventions for contributing to this repository.

## The Project

This repository holds the project's working materials for the *Caraka Saṃhitā* — per-page OCR, curated digests by *sthāna*, thematic extractions, philological notes, and translation-provenance tracking. The goal is a repository of verified Caraka textual material that downstream articles (primarily in [`~/git/TheBookOfSol/`](../TheBookOfSol/)) can cite confidently.

## Related repositories

- **`~/git/bibliography/`** — the standalone scholarly library. Book binaries (PDF, EPUB) of printed editions of Caraka live under `~/git/bibliography/en/caraka/` or `~/git/bibliography/sa/caraka/`. This repository does **not** duplicate those binaries; it only contains working extractions.
- **`~/git/TheBookOfSol/`** — where Caraka material is applied to arguments about diet, health, and chloride toxicology. When writing for that repository, cite the verified Caraka material here, not raw translations.

## Working conventions

### 1. The canonical English text per edition lives in `<edition>/`

Each edition of the Caraka Saṃhitā gets its own top-level directory named for the edition (e.g., `sharma-2014/` for the Priya Vrat Sharma Chaukhambha 2014 edition). Inside, the work is split per sthāna into `NN-sthana/MM-name.md` chapter files following [`sharma-2014/CONVENTIONS.md`](./sharma-2014/CONVENTIONS.md).

When a new edition is acquired (e.g., Sharma-Dash 1976, Nirnaya Sagar 1922 with Cakrapāṇi commentary, Angot 2011 French), it gets a sibling directory and its own `CONVENTIONS.md` if its source/format differs.

The intermediate per-page OCR text that produced `sharma-2014/` lived in `pages/*.txt` and is preserved in git history; the PDF-page PNG scans lived in `.ocr_pages/` (gitignored, regeneratable from the source PDF in `~/git/bibliography/en/caraka/` via `pdftoppm`). Manual corrections applied during that OCR pass are logged in [`notes/ocr-corrections.md`](./notes/ocr-corrections.md) for audit.

Do **not** smooth or paraphrase the published English. Fix obvious typos only (the Sharma edition has a few). For any non-typo edit, record it in `notes/ocr-corrections.md` with scan evidence.

### 2. Verified Sanskrit belongs in `notes/philology/`

When we examine a specific verse closely and arrive at a verified reading (with IAST transliteration, multiple-source comparison, and translation), that verse belongs in a dedicated file under `notes/philology/` — organized by sthāna and verse reference, e.g., `notes/philology/sutrasthana-5-12.md`.

A `notes/philology/*.md` file is the authoritative reference for downstream articles that cite that verse.

### 3. Curated digests (`sutrasthana.md`, etc.) summarize without claiming verification

The per-sthāna digests at the repo root (`sutrasthana.md`, `vimanasthana.md`, etc.) are summaries and orientation documents. They point to key passages, give English translations, and organize themes. They do **not** claim to be verified Sanskrit texts. When they quote Sanskrit, the quote must either match the raw OCR faithfully or cite a `notes/philology/` entry.

### 4. Thematic digests at the root use the same rules

Thematic files like `fruit-vegetable-warnings.md` cut across sthāna boundaries. Same rule: orientation documents. If a Sanskrit passage is quoted, its source must be traceable either to raw OCR or to a verified entry in `notes/philology/`.

### 5. IAST, translation, and citation format

Primary-source quote blocks follow the same convention as The Book of Sol:

- Sanskrit in **IAST, bold, no italics** on the opening lines
- A blank `>` blockquote line
- English translation, in double quotes
- Em-dash attribution on the final line, citing edition and chapter-verse

Example:

```
> **sama-doṣaḥ samāgniś ca sama-dhātu-mala-kriyaḥ |**\
> **prasanna-ātmendriya-manāḥ svastha ity abhidhīyate ||**
>
> "Even in the doṣas, even in agni, even in the functioning of tissues and wastes,\
> serene in self, senses, and mind —\
> this is called *svastha*, the healthy one."\
> — *Caraka Saṃhitā*, Sūtrasthāna 15.48, trans. Priya Vrat Sharma
```

No horizontal-rule separators (`---`); structure with headings only.

### 6. When translators disagree, name them

When two English editions render the same Sanskrit verse differently, both renderings belong in the verse's `notes/philology/` entry, attributed by name. The goal is to make translator-intervention visible, not to pick one and hide the other.

### 7. The chloride-vocabulary rule inherits

When referencing discussions of *lavaṇa* or *saindhava* or any dietary salt, **chloride of sodium** (never "sodium chloride," never standalone "sodium") is the required compound name. This inherits from The Book of Sol's *Chloridism* thesis. Exception: verbatim citation of a scholar who used the other term, with the scholar's phrasing preserved and attributed.

## Version control

Jujutsu (`jj`):

```
jj status
jj commit -m "(action, scope, detail) (further-action, scope, detail)" <files>
jj bookmark set main -r @-
jj git push
```

Commit messages follow the comma-grouped parenthetical style from the rest of the ecosystem.

Do not use `git commit` / `git push` directly.

## When in doubt

If a convention is not explicit here, look at recent commits (`jj log --limit 20`) or at the conventions in the companion repositories ([`~/git/TheBookOfSol/AGENTS.md`](../TheBookOfSol/AGENTS.md), [`~/git/bibliography/CLAUDE.md`](../bibliography/CLAUDE.md)). Prefer to preserve existing structure rather than introduce novelty without reason.
