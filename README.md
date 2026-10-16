# Arabic Heritage Library — مكتبة التراث العربي

Classical Arabic books (literature, language, history, biography, travel) converted to JSON for the
**Adeeb AI** app («الأديب الذكي»). Release **2026.10.16** (catalog_version 1), built from
**OpenITI release 2025.1.9** (`OpenITI/RELEASE`, tag `v2025.1.9`, commit
`cfc4157a3cf2054c0888f133970a4eaa3e22e58c`).

## Attribution
The texts come from the **Open Islamicate Texts Initiative (OpenITI)** corpus
(http://openiti.org/, co-PIs Matthew Thomas Miller, Maxim G. Romanov, Sarah Bowen Savant), supported
by the **KITAB** project (http://kitab-project.org/, ERC Grant Agreement No. 772989) and the Qatar
National Library. For citation of release 2025.1.9, see the OpenITI record at
https://doi.org/10.5281/zenodo.3082463 as OpenITI recommends.

Each book records its exact OpenITI version URI (`src` in the catalog, `source.openiti` in the book).
The conversion (markup cleanup, editor notes removed, paragraph IDs) was done by the Adeeb tools:
five books (kalila, bayan, uyun, kamil, adab) with hand-reviewed recipes, the rest automatically;
books that failed the quality gates or need human review are not published.

## License
Texts and data: **CC BY-NC-SA 4.0** (see `LICENSE`), following OpenITI.

## Layout
- `catalog/v2/catalog.json.gz` — catalog (schema 2): per book `id`, `t` title, `a` author,
  `d` death year (AH), `c` category, `e` era, `v` version, `f` file, `sha` sha256, `sz`/`u`
  compressed/uncompressed bytes, `n` paragraphs, `dia` diacritics, `src` OpenITI version URI.
- `books/<last 2 chars of id>/<id>/<id>.v<N>.json.gz` — the book JSON, written as consecutive gzip
  members (header, one per chapter, trailer); the whole file is a valid gzip stream.
- `books/…/<id>.v<N>.idx.json` — byte offset (`o`), length (`l`) and sha256 of each chapter member,
  for HTTP Range reads of a single chapter.
- `registry.tsv` — permanent mapping OpenITI book URI → book ID (append-only).

Book and paragraph IDs are permanent; changed paragraphs in later versions are mapped through
`redirects`.
