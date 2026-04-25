# Conversion conventions

How `pages/NNN.txt` plain-text scans become `book/NN-sthana/MM-name.md` chapters.

## Source

- Input: `pages/001.txt` … `pages/582.txt` — one file per page of P. V. Sharma's *Caraka Saṃhitā* Vol I (Chaukhambha Orientalia, 2014).
- Pages 1-43 are front matter (title, preface, contents). Skip.
- Pages 44-289 = Sūtrasthāna (30 chapters). Pages 290 = section title; 291-338 = Nidāna (8 ch). 339 = title; 340-433 = Vimāna (8 ch). 434 = title; 435-526 = Śārīra (8 ch). 527 blank. 528 = title; 529-566 = Indriya (12 ch). 568-582 = back-matter index.
- Output: one `.md` per chapter inside the appropriate `book/NN-sthana/` directory.

## Chapter boundary detection

Each chapter is bracketed in the source by:

```
प्रथमोऽध्यायः       ← Sanskrit ordinal ("first chapter," "second chapter," …)

CHAPTER N           ← Roman numeral

अथातो [name] व्याख्यास्यामः ॥१॥   ← opening verse names the chapter
```

…and ends with the colophon:

```
इत्यग्निवेशकृते तन्त्रे चरकप्रतिसंस्कृते [sthāna]स्थाने [name]ो नाम N-ोऽध्यायः ॥N॥

Thus ends the [Nth] chapter on [topic] in [Sthāna]sthāna in the treatise composed by
Agniveśa and redacted by Caraka. (N)
```

Use the colophon's English line to extract the chapter's English topic ("longevity," "seeds of apāmārga," etc.).

## File naming

```
book/01-sutrasthana/01-dirghanjivitiya.md
book/01-sutrasthana/02-apamarga-tanduliya.md
…
book/05-indriyasthana/12-gomayachurniya.md
```

- Lowercase, hyphenated, **no diacritics in the filename** (filesystem-friendly: `apamarga` not `apāmārga`)
- Two-digit zero-padded chapter number prefix
- Use the Sanskrit chapter name (the *N-īya* form from the colophon, e.g., *dīrghañjīvitīya* → `dirghanjivitiya`), not the English topic.

## Frontmatter

YAML at the top of each chapter file:

```yaml
---
sthana: Sūtrasthāna
sthana_number: 1
chapter_number: 1
chapter_name: Dīrghañjīvitīya
chapter_topic: longevity
source_pages: 44-55
source_edition: P. V. Sharma, Caraka Saṃhitā (Chaukhambha Orientalia, 2014), Vol. I
---
```

- `sthana` uses proper diacritics
- `chapter_name` is the Sanskrit name with proper diacritics
- `chapter_topic` is a short English gloss from the colophon (lowercase, no period)
- `source_pages` is `start-end` in the input PDF page numbering
- `source_edition` is the same string for every chapter

## Body structure

```markdown
# Sūtrasthāna · Chapter 1 — Dīrghañjīvitīya

*On longevity.*

> [Sanskrit verse(s), one per line, joined into one blockquote per English paragraph]

[English translation paragraph, with verse number(s) at end as **[N]** or **[N-M]**]

> [next Sanskrit block]

[next English paragraph]

…

## Summing-up verses

[the final summary block of verses, if present, gets this H2]

## Colophon

> [Sanskrit colophon]

[English colophon] **(N)**

[footnotes if any]
```

### Sanskrit blockquote rules

- One **blockquote per associated English paragraph**. If three Sanskrit verses share one English translation, put them in one blockquote with line breaks.
- Verse markers `॥N॥` stay inside the blockquote at end of each verse line.
- For pages where the source uses `[Devanagari unclear: ...]` placeholders (pages ~141-582), **drop the placeholder line** — it carries no semantic content. The English paragraph stands alone.
- Where Devanagari is partially garbled in the source (transcription artifacts from OCR), preserve as-is in the blockquote — these are flagged for future philological work, not silent fixes.

### English paragraph rules

- Verse number at end as bold bracketed: `**[3]**` or `**[4-5]**`
- *Italicize* Sanskrit terms when they appear inline: *doṣa*, *prajñāparādha*, *saindhava*. The Sharma translation already does this inconsistently — make it consistent.
- Em dashes for parenthetical asides: use `—` (`—`), not `--` or `-`. The source frequently uses `–` (en-dash); convert to em dash.
- Quoted speech: straight double quotes `"..."`. Convert curly quotes if any.
- Replace ` - ` (hyphenated word splits across PDF page breaks) by joining: `preg-\nnant` → `pregnant`. Watch for this when paragraphs span page boundaries.

### Page-header noise to strip

Each input `.txt` file starts with one of these patterns — drop the line:

```
NN                            CARAKA-SAṂHITĀ                             [CH.
[ROMAN]]                      SŪTRASTHĀNA                                  NN
[ROMAN]]                      ŚĀRĪRASTHĀNA                                 NN
…
```

Also drop:
- Footer lines like `7 C.S.- I` or `67 C.S. - I` (volume + page-number markers)
- Standalone `•` bullets used as section dividers in the source
- Blank "[Blank or transitional page]" placeholder pages

### Footnotes

The Sharma edition has numbered footnotes (¹ ² ³ ⁴ ⁵) for technical Sanskrit terms. Convert these to markdown footnotes `[^1]`, `[^2]`, … with the definitions at the bottom of the chapter file. See [01-dirghanjivitiya.md](01-sutrasthana/01-dirghanjivitiya.md) for the canonical example.

## Per-sthāna `_index.md`

In each `book/NN-sthana/` directory, create an `_index.md`:

```markdown
# Sūtrasthāna — Section on Fundamentals

*Source pages 44-289 of Sharma 2014, Vol. I.*

The Sūtrasthāna ("section on the threads") establishes the foundational doctrine of Āyurveda — its origin, the six *rasas*, the three *doṣas*, the categories of drugs and food, daily and seasonal regimen, and the moral framework of the physician. It contains 30 chapters.

## Chapters

1. [Dīrghañjīvitīya](01-dirghanjivitiya.md) — on longevity (pp. 44-55)
2. [Apāmārga-taṇḍulīya](02-apamarga-tanduliya.md) — on seeds of apāmārga etc. (pp. 56-…)
…
30. [Arthedaśamahāmūlīya](30-arthedasamahamuliya.md) — on the ten heart-rooted vessels (pp. …-289)
```

Each chapter line: number, link to the `.md` file, em dash, English topic gloss, page range in parens.

## Things to avoid

- Don't invent Sanskrit verses where the source has placeholders. Drop the `[Devanagari unclear: …]` lines silently; don't try to reconstruct.
- Don't smooth or paraphrase Sharma's English. Fix obvious typos (e.g., `agni (appetic and digestion)` → `agni (appetite and digestion)`) but preserve the translation.
- Don't add commentary, headings, or section markers that aren't in the source. The Sharma edition has no internal H2s within a chapter; the only H2 to add are `## Summing-up verses` (when the source has `तत्र श्लोकाः—` / "Now the summing up verses") and `## Colophon`.
- Don't add emojis.
- Don't add a `## Notes` or `## See also` section.
- Don't include the front-matter pages (i-xl, PDF pages 1-43) — those become the top-level `book/README.md` separately.

## Reference implementation

[01-sutrasthana/01-dirghanjivitiya.md](01-sutrasthana/01-dirghanjivitiya.md) — the canonical example. Match its frontmatter shape, blockquote/paragraph alternation, footnote handling, and colophon structure exactly.
