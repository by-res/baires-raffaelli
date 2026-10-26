# Changelog

## 3.0 – 2026-10-25
- First public release.
- Core graph (Schema.org + BIBFRAME 2.0), local vocabulary, provenance layer with editorial notes.
- 28 page-level citation evidences; link register with persistence class and decision per link.
- Closed open points: Foligno house (sole author, source Tosi & Pistolesi 2022), Perugia webinars 2020 and 2021, Park thesis is a third-party work citing the book, publisher-first rule for years and pages (Form 2016/144 p., Accessibility 2020/160 p., Fundamentals 2023/144 p.), Taiwan edition date 25/02/2022, Persian second printing 1404 SH recorded in `schema:bookEdition`.
- Birth data reduced to year and place (1975, Fabriano).
- IRIs moved to w3id.org (`https://w3id.org/baires-raffaelli/`).
- SHACL shapes and 8 SPARQL queries added.

## 3.0 (2026-10-25) – distribution variants
- Added N-Triples, merged Turtle, key-value text edition, flat CSV tables, llms.txt and a home-page JSON-LD snippet.
- Fixed stale page counts in auto-generated descriptions (editions now 144 / 160 / 144 pages).
- Birth date reduced to year; birth place kept.

## 3.0 (2026-10-25) – final formal validation
- bf:Isbn added for the ISBN-10 of the English *Accessibility Design* edition (schema:isbn and bf:identifiedBy now match for all 7 editions).
- bf:contribution added wherever schema:author was present without it (the two Chinese translations and 16 project/competition works).
- Known and accepted: 5 uses of schema:affiliation inside schema:Role nodes (the Role pattern documented by Schema.org); strict domain checkers flag them, but they are valid.
- Review round: removed the person's WorldCat Entities URI wrongly attached as sameAs to the English *Form* edition (it merged author and book); journal, series, volume and issue nodes now have explicit IRIs (no anonymous nesting); the four remaining libraries are named entities; descriptive pages (Maker Faire, Edilportale, STUBA library home) moved from sameAs to rdfs:seeAlso; added names to all issues and library copies, author/translator on the translated editions, and 40 more properties are now exported in the text edition (producer, funder, members, credentials, ...).
- Verification layer: every record with status verified-primary, verified-secondary or self-published now carries either `brv:verification` (independent source + `brv:accessedOn` date; 75 records), or `brv:verificationBasis` with a short note when no web page exists (author-supplied document, ORCID record, academic record...; 27 records), or `link-not-rechecked` (14 records, recheck pending). A SHACL rule enforces this. The link register gained a `checked_on` column (the date of the last audit pass, 2026-10-25) and 30 graph URLs that were missing from it.
- 2026-10-26 link integration: checked 37 further links against the dataset. Added Wikidata Q138822782 (the PhD thesis, `owl:sameAs`), the Wikiquote page and the Amazon author profile (ID B019OLSVX8) for the person, and an extra source for the Gelfond citation. Corrected the FrancoAngeli series of the Bucchetti volume (it is *Design della comunicazione*, not *Open Access - Saggi*); the volume page now redirects to a login and is kept only as a deprecated URL. The register lists every checked address with its decision (alias, removed search/session/affiliate URLs, dead pages, 7 pending checks).

## 3.0.1 (2026-10-26)
- DOI added (Zenodo concept DOI 10.5281/zenodo.23647642; version 3.0 is 10.5281/zenodo.23647643) in the dataset node, CITATION.cff, README, landing page, text edition, llms.txt and home-page snippet. `.zenodo.json` added so the archive is typed as a dataset.
- Includes the 2026-10-26 link integration described above.
