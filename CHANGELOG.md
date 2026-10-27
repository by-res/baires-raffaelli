# Changelog

## 3.0.2 – 2026-10-27
- Credentials: registration with the Albo of Rome (no. 15256) from 23/04/2003 and qualification date 01/11/2002 verified on the CNAPPC national register (the 17/03/2003 date of earlier versions was the date of the examination record); degree date 23/07/2002 verified; grade 110/110 cum laude and thesis taken from the official degree certificate (not public, not published).
- Thesis "Progetto della nuova Stazione Tuscolana e degli spazi aperti circostanti" (advisor Marta Calzolaretti) linked to the 2003 chapter "Strutture della mobilità".
- Roles corrected from the official award sheets and the studio's documents: small railway stations competition 2007 (Baires Raffaelli lead designer; five consultants/collaborators, Junior under 39 section, mention); Pump It Up House (Paolo Moressoni collaborator, Kappazeta S.p.A. partner); Passignano sports hall (Paolo Luccioni and Baires Raffaelli designers, six collaborators); the two Paolo Moressoni records merged into one person.
- New records from the author's press and studio archive: Bettona Contratto di Quartiere III (2009, commissioned by the Comune di Bettona; Luccioni Archstudio collaborator), San Nicolò civic centre in Spoleto (P. Luccioni; B. Raffaelli collaborator), Assisi PUC masterplan (invited designer), "La ville des anges", "CITY MILL" (Tatlin News #62-2), one competition result (Il camino d'autore).
- HousingLab (Sapienza) membership documented (EAAE/ARCC 2012 volume); press sources for Livingbox and Central Glass recorded, with the differences in participant counts noted.
- Link register: 6 rows added (CNAPPC register checked, IRIS handle, five project pages).

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
