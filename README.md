# Gallica & BnF APIs — Postman Collection (France)

A Postman (v2.1) collection (26 requests) for the **Bibliothèque nationale de France**. It covers search in the [Gallica](https://gallica.bnf.fr) digital library (10M+ books, newspapers, maps and manuscripts), Gallica's document services, its page images (IIIF), and the BnF general catalogue.

**Import link** (Postman → Import → Link):
```
https://raw.githubusercontent.com/mikeyeves/Gallica-API-Postman/main/Gallica_BnF_APIs.postman_collection.json
```
No key or environment file is needed.

## Folders
| Folder | Requests | Notes |
|---|---|---|
| ★ Gallica search (SRU) | 11 | Search all of Gallica or only the scanned (OCR) text; filter to newspapers, maps, images or manuscripts; date ranges; exact phrases; author or title |
| Gallica document services | 7 | Document details, page list, **find a word inside a document**, table of contents, plain text, and a periodical's years and issues |
| Gallica IIIF images | 5 | Image-viewer manifest (IIIF), full page, resized page, cropped area |
| BnF catalogue (SRU) | 3 | General catalogue search, genealogy subjects, name records |

The search requests show a **Visualizer** table with links and thumbnails. Search responses are Dublin Core XML.

## Tested at build time
- `gallica all "Bukovsky"` returned 1,076 records.
- Full-text (`text all`) search returned 3,245.
- Newspapers and periodicals only returned 674.
- Limiting the date to 1890–1920 returned 378.
- Le Figaro has 101 years available, with 368 issues in 1905.
- Find-a-word, page list, image manifest and page images all returned 200.
- BnF catalogue: 35 records for `Bukovsky`; 140 for genealogy (*généalogie*) with Hungary (*Hongrie*).

## CQL cheat-sheet
| Goal | query |
|---|---|
| Any field | `gallica all "Krupl"` |
| OCR text | `text all "Krupl"` |
| Phrase | `gallica adj "Banat de Temesvar"` |
| Type | `dc.type all "fascicule"` (newspapers), `"monographie"` (books), `"carte"` (maps), `"image"` (images), `"manuscrit"` (manuscripts) |
| Date | `dc.date >= "1890" and dc.date <= "1920"` |
| Language | `dc.language all "fre"` |

## Tips
- Gallica is behind Cloudflare. Use only the documented endpoints and keep requests modest. Bulk or undocumented calls can get you **blocked**.
- Search with French forms of names and places. The Banat appears as *Banat*, Timișoara as *Temesvar*, Hungary as *Hongrie*, and Austria-Hungary as *Autriche-Hongrie*.
- To find which pages mention a surname, run **ContentSearch** on the document id from search results, then fetch those pages with IIIF.

## Related collections
[Europeana / DDB (European Archives)](https://github.com/mikeyeves/European-Archives-APIs-Postman) · [Open Archives](https://github.com/mikeyeves/Open-Archives-API-Postman) · [Library of Congress](https://github.com/mikeyeves/Library-of-Congress-API-Postman)

*Unofficial. Not affiliated with the Bibliothèque nationale de France.*
