# Baires Raffaelli – bibliographic, academic and authority control dataset

Linked Open Data (Schema.org + BIBFRAME 2.0) about the architect, researcher and author **Baires Raffaelli**: authority identifiers, the three *Fast Guide* books (BIS Publishers) and their translations, page-level citation evidence, events, projects, awards and library holdings.

- Version 3.0.1 · 2026-10-26 · DOI [10.5281/zenodo.23647642](https://doi.org/10.5281/zenodo.23647642) (all versions) · [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)
- Home: <https://w3id.org/baires-raffaelli/> · node IRIs `https://w3id.org/baires-raffaelli/id/…` · vocabulary `https://w3id.org/baires-raffaelli/vocab#`
- About 3,600 triples · 47 people · 39 organisations · 23 works · 28 citation evidences

## Repository layout

| Path | Content |
|---|---|
| `docs/data/baires-raffaelli.ttl` | **Core graph** (Turtle) – start here |
| `docs/data/baires-raffaelli.jsonld` | Same graph in JSON-LD (one node per `@id`, good for RAG chunking) |
| `docs/data/baires-raffaelli-provenance.ttl` | Optional layer: editorial notes (`brv:dataQualityNote`, mostly Italian) and source ids |
| `docs/vocab/vocab.ttl` | Local vocabulary `brv:` (18 terms) |
| `docs/index.html` | Landing page served by GitHub Pages (includes Schema.org `Dataset` markup) |
| `queries/*.rq` | 8 ready-made SPARQL queries (editions, translations, citations with page, holdings, identifiers, events, unverified nodes, deprecated URLs) |
| `shapes/baires-raffaelli.shacl.ttl` | SHACL rules (names, Work/Instance/Item reciprocity, ISBN, evidence fields, status values) |
| `docs/data/baires-raffaelli.nt` | Same core graph as N-Triples (bulk loading) |
| `docs/data/baires-raffaelli-full.ttl` | Core + editorial notes in one file (archiving, Zenodo) |
| `docs/data/baires_raffaelli_dataset.txt` | Key-value text edition, one record per entity (RAG / LLM ingestion; also served at baires.eu) |
| `docs/data/csv/` | Flat tables: editions, person identifiers, events, citation evidence |
| `site/` | Files for the author's website: dataset text, `llms.txt`, home-page JSON-LD snippet |
| `audit/link_register.csv` | Every link with class, persistence, decision, archive URL and `checked_on` date; links present in the graph but not yet re-checked are marked as such |
| `audit/citation_evidence.csv` | Page-level evidence; the cited documents are not redistributed |
| `w3id/` | Redirect rules for the w3id.org pull request |

## Modelling rules

- Person, Work, Instance and Item are separate nodes with reciprocal links (`bf:instanceOf`/`bf:hasInstance`, `bf:itemOf`/`bf:hasItem`, `schema:exampleOfWork`/`schema:workExample`).
- `schema:sameAs` only for identifiers, authority records and profile pages of the same entity; `owl:sameAs` only for Wikidata.
- Broken or unsafe URLs are kept as strings in `brv:deprecatedUrl`; unstable foreign pages carry a web-archive snapshot in `schema:archivedAt`.
- Publisher data prevail for a work (year, pages); library counts are in the provenance notes.
- Records that make a verifiable claim carry `brv:verificationStatus` (`verified-primary`, `verified-secondary`, `self-published`, `unverified`, `archived-only`, …); for question answering use the first two. Each verified record shows either the independent page checked with its access date (`brv:verification`) or the reason why no web page exists (`brv:verificationBasis`).
- Descriptions of citing documents are paraphrases, not quotations.

## How to cite

Raffaelli, B. (2026). *Baires Raffaelli – bibliographic, academic and authority control dataset* (v3.0.1). Zenodo. <https://doi.org/10.5281/zenodo.23647642>

GitHub also offers a ready-made citation (“Cite this repository”) from `CITATION.cff`.

## Quick start

```python
from rdflib import Graph
g = Graph()
g.parse("docs/data/baires-raffaelli.ttl")
g.parse("docs/data/baires-raffaelli-provenance.ttl")   # optional
for row in g.query(open("queries/01-editions.rq").read()):
    print(row)
```

Validate: `pip install pyshacl` then `pyshacl -s shapes/baires-raffaelli.shacl.ttl docs/data/baires-raffaelli.ttl`.

For retrieval-augmented generation, index the JSON-LD `@graph` by `@id` and add the objects one hop away (`bf:instanceOf`, `schema:translator`, `schema:citation`) as context.

## Publishing checklist

1. Create the GitHub repository `baires-raffaelli`, push these files, enable GitHub Pages from `/docs` on the main branch.
2. (Done) The GitHub account `by-res` is already set in `w3id/.htaccess`, `CITATION.cff` and `docs/index.html`; add a maintainer contact in `w3id/README.md`.
3. Open a pull request to [perma-id/w3id.org](https://github.com/perma-id/w3id.org) adding the folder `ids/baires-raffaelli/` with `.htaccess` and `README.md`.
4. Each GitHub release is archived on Zenodo; the concept DOI above always resolves to the latest version.
5. On the personal site, link to the landing page or embed the `Dataset` JSON-LD block of `docs/index.html`.

## Notes and limits

- Facts were checked against public sources on 24–25 October 2026; links can change. Foreign catalogues behind anti-bot protection could not be re-checked and are marked.
- The author mentions 2–3 reprints of the English books; none is documented in any catalogue, so they are not modelled. The Persian second printing (1404 SH) is recorded in `schema:bookEdition`, not as a separate Instance.
- Personal data are limited to public professional information (birth year and place only); no addresses, contacts or family relations.
- Built with the assistance of an AI model (Claude, Anthropic) and checked with the author.
