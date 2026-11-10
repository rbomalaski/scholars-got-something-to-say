# The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research

**Version 1.3 (2026-11-09)**
**Creator:** Rachel Bomalaski (ORCID: https://orcid.org/0009-0008-6826-5992)
**DOI (all versions; always opens the latest):** https://doi.org/10.5281/zenodo.23933278
**License:** Creative Commons Attribution 4.0 International (CC BY 4.0)

## What this is

A bibliographic dataset of 7,109 works about hip-hop, facing South: it emphasizes Trap and Southern hip-hop while covering hip-hop scholarship across disciplines, regions and languages. Each work has its citation details, the searches that found it, the topic of those searches, and provisional tags (region, style, element of hip-hop, discipline and others). The dataset was built for an informal scoping review loosely based on the PRISMA-ScR reporting guideline, and it includes the search protocol and a log of every search run.

**Read "What has and has not been checked" below before relying on any tag.**

## Files

| File | Contents |
|---|---|
| `dataset.csv` | One row per work (7,109 rows, 27 columns), in alphabetical order by author (or title when there is no author). |
| `search_log.csv` | One row per search per database (1,454 searches). |
| `protocol.csv` | The planned search strings (487). |
| `protocol_notes.txt` | Notes on the search settings, the combined strings and the JSTOR length limit. |
| `dataset.xlsx` | The same three tables, plus this README and the codebook, as one spreadsheet. |
| `hiphop_scoping_review.db` | The same tables as a SQLite database (`works`, `search_log`, `protocol`), plus `work_topics` (one row per work and search topic), `work_subtopics` (one row per work and search subtopic) and `work_tags` (one row per work and tag: style, region, US region or city, element, discipline, diasporic connection), for browsing by clicking and full-text search on titles, authors, venues, tags and search topics. |
| `CODEBOOK.md` | What every column means and what values it takes. |
| `LICENSE.txt` | License notice. |

## How to browse it

**Start here:** https://rbomalaski.github.io/scholars-got-something-to-say (front page with buttons for browsing, searching, downloading and citing).

**Browse online** (loads in the browser; the first load takes about 20 seconds):
- Works, main columns: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/works?_col=Author(s)&_col=Year&_col=Title&_col=Venue+%2F+publisher&_col=Work+type&_col=Region+of+subject&_col=Style&_col=Element&_col=Link&_sort=Sort+key+%28alphabetical%29
- Works by tag (click a tag in the lists on the left): https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/work_tags?_facet=Tag+type&_facet=Tag
- Works by search topic: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/work_topics?_facet=Search+topic
- Everything: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db

Open `hiphop_scoping_review.db` in Datasette Lite (https://lite.datasette.io) or any SQLite browser. Use the search box for keywords, filter or sort any column (the Link column opens each work's DOI or page), or open the `work_topics` (or `work_subtopics`) table and choose a search topic (for example "Hauntology" or "Southern artists: Houston") to see every work that search found. The spreadsheet and CSV work in Excel and similar programs.

## How the dataset was built

- **Searches.** 1,454 searches in SciSpace, Wiley Scholar Gateway, OpenAlex, JSTOR, Google Scholar, Project MUSE and the web, plus hand-searches of hip-hop journals and special issues. The AI ran 955 (425 in SciSpace, 335 in Wiley Scholar Gateway, 149 in OpenAlex, 41 web searches and five hand-searches). The author ran 494 (167 in JSTOR, 167 in Google Scholar, 160 in Project MUSE): she copied the results pages and pasted them into documents (text files at first, then Google Docs), and the AI screened what she pasted. A reference manager (Zotero) was tried for the first search only and not used after it, because its exports left out results. Five hand-searches were shared. The strings are in `protocol.csv`; each run is in `search_log.csv`.
- **Two rounds.** The first round (2026-10-26 to 11-03) is the protocol of versions 1.0 to 1.2. The second round (2026-11-07 to 11-08), new in version 1.3, searched for research gaps (those named in the author's book and new candidate gaps) and for 90 artists named on the author's scan cards or Southern artist list who had no title in the dataset: the AI ran 131 strings in OpenAlex and SciSpace (first 50 results) and, for the gaps, in Wiley Scholar Gateway (up to 20 passages) and on the web; the author wrote 18 further strings ("D strings"), which she ran in Google Scholar (18 searches), JSTOR and Project MUSE (17 each; D14-01b in place of D14-01), first 100 results (Project MUSE 100 to 130, as pasted), and the AI ran in OpenAlex, SciSpace and Wiley Scholar Gateway.
- **Screening.** 56,071 search returns screened: 6,340 works kept as new, 12,743 excluded as not about hip-hop, 8,539 excluded as passing mentions, and 28,449 counted as duplicates of works already found. Of the 7,109 works, 6,353 were first identified by a protocol search, 216 came from other sources (mostly AI web and database searches outside the protocol, books known through their reviews, the author's reading and PDFs she supplied), and 540 are chapters entered from edited volumes in the dataset (see "Books and chapters"). The Search Log counts search returns, not unique records, and works were later merged, replaced by their chapters or removed, so these figures are not a strict PRISMA flow diagram.
- **Eligibility.** A work is included when hip-hop is its subject or a substantial part of it. Under the author's rule of 2026-10-31, works on genres with close ties to hip-hop (reggae, dancehall, reggaetón, Afro-Cuban music, Gullah Geechee and Garifuna music and others) are included even when hip-hop is mentioned only in passing; they are marked in *Diasporic connection*. Works whose own page showed no hip-hop, or left it unclear, were not entered.
- **Books and chapters (the author's rules, 2026-11-08 and 11-09).**
  - A book mostly about hip-hop is entered as the book, and so is a book with hip-hop (or a genre with close ties to it) in its title.
  - A book with one or a few chapters on hip-hop is entered as those chapters instead of the book: the first chapter keeps the book's ID and its searches, and further chapters have new IDs. Where hip-hop appears inside a chapter on another subject, that chapter is entered.
  - A single-author book mostly about hip-hop is entered as the book only, not as its chapters.
  - Edited volumes by many authors that are mostly about hip-hop keep their book row, and each chapter also has a row, so that both the book and its essays can be found (43 volumes, 540 chapter rows). A chapter row's *Identified via* names the volume's ID. Chapter rows carry no searches of their own (the searches found the volume), so search counts are not doubled. For an edited volume only partly about hip-hop, only its hip-hop chapters are entered. For *The BreakBeat Poets*, an anthology of poems, the essays have rows and the poems do not.
  - A chapter that reprints a journal article is entered as the original article.
  - Books are entered in their latest edition.
- **Cleaning.** Duplicates were merged; records too incomplete to identify were removed at the author's decision. IDs are not reused.

## What has and has not been checked

**Checked by machine.** On 2026-11-03 every row then in the dataset was compared with Crossref, OpenAlex, DataCite and Open Library: links, years, authors and work types were matched against those indexes, and years were set to the earliest publication date they give. Where an index could not settle a missing author, year or title, the AI searched the web and read the work's own pages and PDFs; a second, separate AI pass reopened each source to confirm what was found. Years that could not be found are given as "n.d." Links for 2,722 works were found by matching title, first author and year in Crossref or OpenAlex; they have not been opened one by one. 1,760 works have no link.

**Venues and citation details (version 1.1, 2026-11-04).** The 1,682 works whose venue was then missing or "to confirm" were looked up in Crossref and DataCite by DOI, on the works' own linked pages and PDFs, in OpenAlex and Open Library, and by AI web search; venues were filled for 1,319 of them. The same pages corrected 295 author fields, 60 titles, 86 work types and 75 years. The author reviewed the doubtful cases and decided them herself.

**Round 2 works (version 1.3).** Each work kept in round 2 was checked by the AI against its own page where one could be found. Blank cells were then filled from OpenAlex (with the author's own API key; filled links say "from OpenAlex" with the OpenAlex record number in *Link note*, other filled cells "[from OpenAlex …]" or "OpenAlex agrees") and, for chapters, from Crossref; only blank or flagged cells were filled. Most chapter rows rest on a table of contents (see *Tagged from*) and are marked "to confirm" where pages, DOIs or authors were not confirmed.

**Checked by the author.** The author settled individual records she flagged (corrections, replacements, removals) and made the rules above; these are recorded in the source sheet's notes.

**AI-assigned and not yet verified.** All tags (Region of subject, US region / city, Style, Element, Hip-hop's place in the work, Discipline, Diasporic connection, Institutional status, Format, Source role) and work types marked "[AI-assigned]" were assigned by the AI. Most rest on a two- or three-line search-result snippet, a table of contents or the title alone, not the work itself (see *Tagged from*). Treat them as a starting point for browsing, not as findings. A blank tag means nothing seen supported a value, not that the value is absent. The keyword search covers these tags, so a search can miss works that were not tagged and can return works that were tagged wrongly.

**Factual, not judged.** *Search topic* and *Search subtopic* record which search found each work, not what the work is about. *Period of publication* is derived from the year.

## Use of AI

This dataset was prepared with the AI model Claude (Anthropic). The AI ran 955 of the 1,454 searches, screened every record, assigned the tags, found the links and missing details, drafted the round 2 strings other than the author's 18 D strings, found the tables of contents and drafted the chapter rows, and drafted this README and the codebook. The author designed the protocol, ran the other searches, set the inclusion rules and the rules for books and chapters, and made the decisions recorded in the notes.

## Limitations

1. **Single screener.** The AI screened every record alone; the author has not checked the screening or the tags.
2. **Tags rest on little text.** See above. Tags that need the full text (method, framework, stance, positionality) were left out of this release.
3. **"To confirm."** 3,759 rows hold at least one value marked "to confirm" outside the link notes, most often institutional status (2,699 rows), region (847), venue (814), discipline (627), hip-hop's place in the work (395) and work type (299).
4. **Open tag lists.** Region, style, element and discipline follow the works' own wording, so similar labels are kept apart (e.g., "trap" and "trap rap").
5. **The search is uneven.** The strings center Southern and Trap labels, which raises the Southern share; searches were mostly in English and not equally deep. Round 2 searched for named gaps and artists, so its works cluster on those topics. Round 2 searches also returned works already in the dataset (counted as duplicates in the Search Log), but those searches are listed in *Protocol searches that found it* for only some of those works, so search topics undercount round 2.
6. **Chapters are uneven.** Edited volumes mostly about hip-hop have every chapter entered; single-author books do not, so chapter counts are not comparable across books.
7. **The author is also a subject.** Two of her own works are in the dataset (OS-001, OS-002).

## Changes in version 1.3 (2026-11-09)

- 1,328 works added and 18 removed: 7,109 works (version 1.2: 5,799).
- Round 2 searches: 450 searches added to the Search Log and 149 strings to the Protocol (131 round 2 strings and the author's 18 D strings); 751 new works found.
- 577 chapter rows added under the rules for books and chapters (540 from 43 edited volumes; the rest further chapters of books replaced by their chapters). 79 book rows replaced by a chapter of the book, under the same ID.
- 18 rows removed: 8 books whose hip-hop chapter was already in the dataset (their searches moved to the chapter), 2 duplicates merged into the earlier record (their searches moved to it), and 8 books in which no hip-hop chapter was found.
- 11 reprinted chapters entered as their original journal articles; 7 books changed to their latest edition (two of them, young-readers editions, marked to confirm); blank cells filled from OpenAlex and Crossref; 39 corrections to 34 rows (years, authors, work types, titles, venues and links).
- New search topics: "Round 2: research gaps" and "Round 2: artists with no title in the dataset"; chapter rows of edited volumes appear under "Other sources: Chapter of an edited volume in the dataset (the search found the volume)".

## Earlier versions

- 1.2 (2026-11-04): 27 duplicate pairs merged; three wrong links removed; work types corrected; 5,799 works.
- 1.1 (2026-11-04): venues filled and citation details corrected; works listed alphabetically; 5,826 works.
- 1.0 (2026-11-03): https://doi.org/10.5281/zenodo.23933279; 5,826 works.

All versions are on the same Zenodo page under "Versions".

## How to cite

Bomalaski, Rachel. 2026. *The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research*. Version 1.3. Zenodo. https://doi.org/10.5281/zenodo.23933278.

## License

Released under the Creative Commons Attribution 4.0 International License (CC BY 4.0): https://creativecommons.org/licenses/by/4.0/. You may share and adapt it for any purpose, provided you give appropriate credit, link to the license and indicate whether changes were made.
