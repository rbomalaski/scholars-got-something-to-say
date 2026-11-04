# The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research

**Version 1.0 (2026-11-03)**
**Creator:** Rachel Bomalaski (ORCID: https://orcid.org/0009-0008-6826-5992)
**DOI:** https://doi.org/10.5281/zenodo.23933279
**License:** Creative Commons Attribution 4.0 International (CC BY 4.0)

## What this is

A bibliographic dataset of 5,826 works about hip-hop, facing South: it emphasizes Trap and Southern hip-hop while covering hip-hop scholarship across disciplines, regions and languages. Each work has its citation details, the searches that found it, the topic of those searches, and provisional tags (region, style, element of hip-hop, discipline and others). The dataset was built for an informal scoping review loosely based on the PRISMA-ScR reporting guideline, and it includes the search protocol and a log of every search run.

**Read "What has and has not been checked" below before relying on any tag.**

## Files

| File | Contents |
|---|---|
| `dataset.csv` | One row per work (5,826 rows, 27 columns). |
| `search_log.csv` | One row per search per database (1,004 searches). |
| `protocol.csv` | The planned search strings (338). |
| `protocol_notes.txt` | Notes on the search settings, the combined strings and the JSTOR length limit. |
| `dataset.xlsx` | The same three tables, plus this README and the codebook, as one spreadsheet. |
| `hiphop_scoping_review.db` | The same tables as a SQLite database (`works`, `search_log`, `protocol`), plus `work_topics` (one row per work and search topic) `work_subtopics` (one row per work and search subtopic) and `work_tags` (one row per work and tag: style, region, US region or city, element, discipline, diasporic connection), for browsing by clicking and full-text search on titles, authors, venues, tags and search topics. |
| `CODEBOOK.md` | What every column means and what values it takes. |
| `LICENSE.txt` | License notice. |

## How to browse it

**Browse online** (loads in the browser; the first load takes about 20 seconds):
- Works, main columns: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/works?_col=Author(s)&_col=Year&_col=Title&_col=Venue+%2F+publisher&_col=Work+type&_col=Region+of+subject&_col=Style&_col=Element
- Works by tag (click a tag in the lists on the left): https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/work_tags?_facet=Tag+type&_facet=Tag
- Works by search topic: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/work_topics?_facet=Search+topic
- Everything: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db

Open `hiphop_scoping_review.db` in Datasette Lite (https://lite.datasette.io) or any SQLite browser. Use the search box for keywords, filter or sort any column, or open the `work_topics` (or `work_subtopics`) table and choose a search topic (for example "Hauntology" or "Southern artists: Houston") to see every work that search found. The spreadsheet and CSV work in Excel and similar programs.

## How the dataset was built

- **Searches.** 1,004 searches in SciSpace, Wiley Scholar Gateway, JSTOR, Google Scholar and Project MUSE, plus hand-searches of hip-hop journals and special issues. The AI ran 557 (276 in SciSpace, 276 in Wiley Scholar Gateway and five hand-searches). The author ran 442 (150 in JSTOR, 149 in Google Scholar, 143 in Project MUSE) and passed the results to the AI to screen. Five hand-searches were shared. The strings are in `protocol.csv`; each run is in `search_log.csv`.
- **Screening.** 40,233 search returns screened: 5,616 works kept as new, 6,953 excluded as not about hip-hop, 7,268 excluded as passing mentions, and 20,396 counted as duplicates of works already found. Of the 5,826 works, 5,622 came from the searches (the 5,616 kept, plus six pieces of one special issue first entered from the issue itself and later counted under its hand-search); 204 came from other sources, mostly the author's reading, PDFs she supplied and books known through their reviews. The Search Log counts search returns, not unique records, so these figures are not a strict PRISMA flow diagram.
- **Eligibility.** A work is included when hip-hop is its subject or a substantial part of it. Under the author's rule of 2026-10-31, works on genres with close ties to hip-hop (reggae, dancehall, reggaetón, Afro-Cuban music, Gullah Geechee and Garifuna music and others) are included even when hip-hop is mentioned only in passing; they are marked in *Diasporic connection*.
- **Cleaning.** Duplicates were merged; chapters of single-author books already in the dataset are counted as the book; records too incomplete to identify were removed at the author's decision.

## What has and has not been checked

**Checked by machine.** On 2026-11-03 every row was compared with Crossref, OpenAlex, DataCite and Open Library: links, years, authors and work types were matched against those indexes, and years were set to the earliest publication date they give. Where an index could not settle a missing author, year or title, the AI searched the web and read the work's own pages and PDFs; a second, separate AI pass reopened each source to confirm what was found. Years that could not be found are given as "n.d." Links for 2,793 works were found by matching title, first author and year in Crossref or OpenAlex; they have not been opened one by one. 1,649 works have no link.

**Checked by the author.** The author settled individual records she flagged (corrections, replacements, removals); these are recorded in the source sheet's notes.

**AI-assigned and not yet verified.** All tags (Region of subject, US region / city, Style, Element, Hip-hop's place in the work, Discipline, Diasporic connection, Institutional status, Format, Source role) and work types marked "[AI-assigned]" were assigned by the AI. Most rest on a two- or three-line search-result snippet or the title alone, not the work itself (see *Tagged from*). Treat them as a starting point for browsing, not as findings. A blank tag means nothing seen supported a value, not that the value is absent. The keyword search covers these tags, so a search can miss works that were not tagged and can return works that were tagged wrongly.

**Factual, not judged.** *Search topic* and *Search subtopic* record which search found each work, not what the work is about. *Period of publication* is derived from the year.

## Use of AI

This dataset was prepared with the AI model Claude (Anthropic). The AI ran 557 of the 1,004 searches, screened every record, assigned the tags, found the links and missing details, and drafted this README and the codebook. The author designed the protocol, ran the other searches, set the inclusion rules and made the decisions recorded in the notes.

## Limitations

1. **Single screener.** The AI screened every record alone; the author has not checked the screening or the tags.
2. **Tags rest on little text.** See above. Tags that need the full text (method, framework, stance, positionality) were left out of this release.
3. **"To confirm."** 3,250 rows hold at least one value marked "to confirm" outside the link notes, most often venues, work types, institutional status and regions.
4. **Open tag lists.** Region, style, element and discipline follow the works' own wording, so similar labels are kept apart (e.g., "trap" and "trap rap").
5. **The search is uneven.** The strings center Southern and Trap labels, which raises the Southern share; searches were mostly in English and not equally deep.
6. **The author is also a subject.** Two of her own works are in the dataset (OS-001, OS-002).

## How to cite

Bomalaski, Rachel. 2026. *The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research*. Version 1.0. Zenodo. https://doi.org/10.5281/zenodo.23933279.

## License

Released under the Creative Commons Attribution 4.0 International License (CC BY 4.0): https://creativecommons.org/licenses/by/4.0/. You may share and adapt it for any purpose, provided you give appropriate credit, link to the license and indicate whether changes were made.
