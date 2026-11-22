# The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research

**Version 2.0 (2026-11-21)**
**Creator:** Rachel Bomalaski (ORCID: https://orcid.org/0009-0008-6826-5992)
**DOI (all versions; always opens the latest):** https://doi.org/10.5281/zenodo.23933278
**License:** Creative Commons Attribution 4.0 International (CC BY 4.0)

## What this is

A bibliographic dataset of 8,456 works about hip-hop, facing South: it emphasizes Trap and Southern hip-hop while covering hip-hop scholarship across disciplines, regions, and languages. Each work has its citation details, the searches that found it, the topic of those searches, a topic and field for browsing, the artists named in its title, and provisional tags (region, style, element of hip-hop, discipline, and others). The dataset was built for an informal scoping review loosely based on the PRISMA-ScR reporting guideline, and it includes the search protocol and a log of every search run.

New in version 2.0: a third round of searches, two topic columns and two field columns for browsing, and a column of artists named in titles. Topic, field, artist, and language can be browsed by clicking.

**Read "What has and has not been checked" below before relying on any tag, topic, or field.**

A companion concept map, *"These Are More Than Words": An Interdisciplinary Concept Map for Hip-Hop Scholars*, groups the works into clusters: https://doi.org/10.5281/zenodo.24424225 (online at https://rbomalaski.github.io/more-than-words-map).

## Files

| File | Contents |
|---|---|
| `dataset.csv` | One row per work (8,456 rows, 31 columns), in alphabetical order by author (or title when there is no author). |
| `search_log.csv` | One row per search per database (1,641 searches). |
| `protocol.csv` | The planned search strings (518). |
| `protocol_notes.txt` | Notes on the search settings, the combined strings, and the JSTOR length limit. |
| `dataset.xlsx` | The same three tables, plus this README and the codebook, as one spreadsheet. |
| `hiphop_scoping_review.db` | The same tables as a SQLite database (`works`, `search_log`, `protocol`), plus `work_topics` (one row per work and search topic), `work_subtopics` (one row per work and search subtopic), `work_tags` (one row per work and tag: style, region, US region or city, element, discipline, diasporic connection, topic, field, artist, language) for browsing by clicking, and full-text search on titles, authors, venues, tags, and search topics. |
| `CODEBOOK.md` | What every column means and what values it takes. |
| `LICENSE.txt` | License notice. |

*(Decided by the author, 2026-11-18: "click browsing yes." Topic, field, artist, and language are added as tag types in `work_tags`.)*

## How to browse it

**Start here:** https://rbomalaski.github.io/scholars-got-something-to-say (front page with buttons for browsing, searching, downloading, and citing).

**Browse online** (loads in the browser; the first load takes about 20 seconds):
- Works, main columns: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/works?_col=Author(s)&_col=Year&_col=Title&_col=Venue+%2F+publisher&_col=Work+type&_col=Topic+1&_col=Field+1&_col=Region+of+subject&_col=Link&_sort=Sort+key+%28alphabetical%29
- Works by tag, topic, field, artist, or language (click a value in the lists on the left): https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/work_tags?_facet=Tag+type&_facet=Tag
- Works by search topic: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db#/hiphop_scoping_review/work_topics?_facet=Search+topic
- Everything: https://lite.datasette.io/?url=https://raw.githubusercontent.com/rbomalaski/scholars-got-something-to-say/main/hiphop_scoping_review.db

Open `hiphop_scoping_review.db` in Datasette Lite (https://lite.datasette.io) or any SQLite browser. Use the search box for keywords, filter or sort any column (the Link column opens each work's DOI or page), or open `work_tags` and choose a topic (for example "Mental health and wellbeing"), a field, or an artist to see every work given that value. The spreadsheet and CSV work in Excel and similar programs.

## How the dataset was built

- **Searches.** 1,641 searches in SciSpace, Wiley Scholar Gateway, OpenAlex, JSTOR, Google Scholar, Project MUSE, and the web, plus hand-searches of hip-hop journals and special issues. The author ran 587 (198 in Google Scholar, 198 in JSTOR, 191 in Project MUSE): she copied the results pages and pasted them into documents (text files at first, then Google Docs), and the AI screened what she pasted. The AI ran 1,049 (456 in SciSpace, 366 in Wiley Scholar Gateway, 181 in OpenAlex, 41 web searches, and 5 hand-searches). Five hand-searches were shared. A reference manager (Zotero) was tried for the first search only and not used after it, because its exports left out results. The strings are in `protocol.csv`; each run is in `search_log.csv`.
- **Three rounds.**
  - Round 1 (2026-10-26 to 11-03) is the protocol of versions 1.0 to 1.2.
  - Round 2 (2026-11-07 to 11-08), added in version 1.3, searched for research gaps and for 90 artists who had no title in the dataset.
  - Round 3 (2026-11-14 to 11-17), new in version 2.0, ran 31 "E strings" (30 on 2026-11-14, and E12-01, on music therapy, on 2026-11-17), each in six databases: the author in Google Scholar, JSTOR, and Project MUSE, and the AI in OpenAlex, SciSpace, and Wiley Scholar Gateway (187 searches in all). Their subjects were bling and jewelry; conspiracy and antisemitism; resurrection, the afterlife, cyborgs, and outer space; gentrification, housing, and homelessness; alcohol, drugs, and addiction; snitching and codes of silence; Islamophobia and hate speech; authenticity and rags-to-riches stories; nihilism and Afropessimism; John Henryism; racism, colorism, Jim Crow, and minstrelsy; abjection, the carnivalesque, and the gaze; intertextuality; brass bands; music education; poverty and welfare; and music therapy.
- **Screening.** 69,411 search returns screened: 7,668 counted as kept, 14,852 excluded as not about hip-hop, 9,894 excluded as passing mentions, and 36,997 counted as duplicates of works already found. Of the 8,456 works, 7,656 were first identified by a protocol search, 232 came from other sources (mostly AI web and database searches outside the protocol, books known through their reviews, the author's reading, and PDFs she supplied; 6 of them are pieces of a special issue entered from the issue itself), and 568 are chapters entered from edited volumes in the dataset. The Search Log counts search returns, not unique records, and works were later merged, replaced by their chapters, or removed, so these figures are not a strict PRISMA flow diagram.
- **Eligibility.** A work is included when hip-hop is its subject or a substantial part of it. Under the author's rule of 2026-10-31, works on genres with close ties to hip-hop (reggae, dancehall, reggaetón, Afro-Cuban music, Gullah Geechee and Garifuna music, and others) are included even when hip-hop is mentioned only in passing; they are marked in *Diasporic connection*. Works whose own page showed no hip-hop, or left it unclear, were not entered.
- **Books and chapters (the author's rules, 2026-11-08, 11-09, and 11-15).**
  - A book mostly about hip-hop is entered as the book, and so is a book with hip-hop (or a genre with close ties to it) in its title.
  - A book with one or a few chapters on hip-hop is entered as those chapters instead of the book: the first chapter keeps the book's ID and its searches, and further chapters have new IDs. Where hip-hop appears inside a chapter on another subject, that chapter is entered.
  - A single-author book mostly about hip-hop is entered as the book only, not as its chapters.
  - Edited volumes by many authors that are mostly about hip-hop keep their book row, and each chapter also has a row, so that both the book and its essays can be found. A chapter row's *Identified via* names the volume's ID. Chapter rows carry no searches of their own (the searches found the volume), so search counts are not doubled. For an edited volume only partly about hip-hop, only its hip-hop chapters are entered. For *The BreakBeat Poets*, an anthology of poems, the essays have rows and the poems do not.
  - A chapter that reprints a journal article is entered as the original article.
  - Books are entered in their latest edition.
  - New in version 2.0: prefaces, introductions, forewords, and outros with no author named are not entered as their own rows (readers find them with the book); signed front matter stays.
- **Unsigned web reference pages (new in version 2.0).** Wikis and similar pages with no author named are left out; signed entries in published encyclopedias stay.
- **Cleaning.** Duplicates were merged; records too incomplete to identify were removed at the author's decision. IDs are not reused.

## What has and has not been checked

**Checked by machine.** On 2026-11-03 every row then in the dataset was compared with Crossref, OpenAlex, DataCite, and Open Library: links, years, authors, and work types were matched against those indexes, and years were set to the earliest publication date they give. Where an index could not settle a missing author, year, or title, the AI searched the web and read the work's own pages and PDFs; a second, separate AI pass reopened each source to confirm what was found. Years that could not be found are given as "n.d." (100 works); 40 works have no year yet.

**Venues and citation details (version 1.1, 2026-11-04).** The 1,682 works whose venue was then missing or "to confirm" were looked up in Crossref and DataCite by DOI, on the works' own linked pages and PDFs, in OpenAlex and Open Library, and by AI web search; venues were filled for 1,319 of them. The same pages corrected 295 author fields, 60 titles, 86 work types, and 75 years. The author reviewed the doubtful cases and decided them herself.

**Round 2 works (version 1.3).** Each work kept in round 2 was checked by the AI against its own page where one could be found. Blank cells were then filled from OpenAlex and, for chapters, from Crossref; only blank or flagged cells were filled.

**Round 3 works and lookups (version 2.0, 2026-11-15 to 11-18).**
- Round 3 rows were filled from OpenAlex where title, first author, and year agreed, and 433 of them were looked up in Crossref by title (24 books by ISBN); where each value came from is recorded in the source sheet.
- A duplicate sweep merged 37 pairs.
- All 1,797 DOIs that did not come from a Crossref, OpenAlex, or DataCite record were checked at doi.org: 16 did not exist; 8 were replaced with a working DOI and 8 removed. The other DOIs came from registry records and were not rechecked.
- The 1,248 works added since 2026-11-02 that had a lookup note were searched in OpenAlex by title, first author, and year (with the author's own API key). Where all three agreed, links, venues, years, and full author names were filled or confirmed. For works with a DOI and no OpenAlex match, the DOI's own record was read. A looser OpenAlex pass and a Crossref title search were reviewed by the author before anything was written. Records that probably describe a different work were left as they were.
- Every new DOI was checked at doi.org before it was written.
- Links: 6,632 works have one; 1,824 have none. Links found on 2026-11-01 to 11-03 by matching title, first author, and year are counted as accepted (the author's decision, 2026-11-18), as are book links for chapters with no DOI of their own.

**Checked by the author.** The author settled individual records she flagged (corrections, replacements, removals), made the rules above, and reviewed the doubtful lookup results; these are recorded in the source sheet's notes.

**AI-assigned and not yet verified.**
- All tags were assigned by the AI: Region of subject, US region / city, Style, Element, Hip-hop's place in the work, Discipline, Diasporic connection, Institutional status, Format, and Source role.
- So were the topics, the fields, and the artists named in titles (new in version 2.0; see the codebook).
- Most of these rest on a two- or three-line search-result snippet, a table of contents, or the title alone, not the work itself (see *Tagged from*).
- Treat them as a starting point for browsing, not as findings. A blank means nothing seen supported a value, not that the value is absent.

**Factual, not judged.** *Search topic* and *Search subtopic* record which search found each work, not what the work is about. *Period of publication* is derived from the year.

## Use of AI

This dataset was prepared with the AI model Claude (Anthropic).

**The author** designed the protocol, wrote the D strings, and approved the round 2 and 3 strings. She ran 587 of the searches, set the inclusion rules and the rules for books, chapters, front matter, and web pages, decided the topic and field scheme, reviewed the doubtful lookups, and made the decisions recorded in the notes.

**The AI** ran 1,049 of the 1,641 searches and screened every record. It assigned the tags, topics, fields, and artist names, found the links and missing details, drafted the round 2 and round 3 strings other than the author's D strings, found the tables of contents and drafted the chapter rows, and drafted this README and the codebook.

## Limitations

1. **Single screener.** The AI screened every record alone; the author has not checked the screening or the tags.
2. **Tags rest on little text.** See above. Tags that need the full text (method, framework, stance, positionality) were left out of this release.
3. **Some citation details are missing.** 1,824 works have no link and 405 have no venue. Many are theses, press pieces, and records seen only in Google Scholar or JSTOR, which Crossref and OpenAlex do not hold.
4. **Topics and fields are coarse.** Each work has at most two topics, read from title words only; 1,926 titles name no subject and have no topic. Fields come from the Discipline column, the venue, or (for 543 works) discipline words in the title or summary (AI inference); 3,255 works have no field.
5. **Open tag lists.** Region, style, element, and discipline follow the works' own wording, so similar labels are kept apart (e.g., "trap" and "trap rap").
6. **The search is uneven.** The strings center Southern and Trap labels, which raises the Southern share; searches were mostly in English (7,763 works are in English, 693 in other languages or more than one) and not equally deep. Rounds 2 and 3 searched for named gaps, artists, and subjects, so their works cluster on those topics.
7. **Chapters are uneven.** Edited volumes mostly about hip-hop have every chapter entered; single-author books do not, so chapter counts are not comparable across books.
8. **The author is also a subject.** Two of her own works are in the dataset (OS-001, OS-002).

## Changes in version 2.0 (2026-11-21)

- **Round 3:** 187 searches added to the Search Log and 31 E strings to the Protocol; 1,372 new works (1,296 from the 30 strings of 2026-11-14 and 76 from E12-01, music therapy); round 3 search tags added to 1,786 works already in the dataset that the searches found again.
- **Works:** 8,456 (version 1.3.1: 7,109). Besides the round 3 works, rows were added from the contents of books and special issues, and rows were merged or removed: 37 duplicate pairs; chapters of single-author books folded into their books; 8 unsigned front-matter rows and 8 unsigned web pages removed under the new rules. Of the 7,109 works in version 1.3.1, 40 were merged into other rows or removed; 1,387 were added (1,331 first found by round 3 searches, 40 chapters of edited volumes, and 16 from other sources).
- **Titles cut short in search results** (2026-11-21): the author looked up the 49 titles that Google Scholar had cut off with "…" and corrected 41 of them, with their authors, venues, years, and links where she found them; she removed two rows (one not about hip-hop, one not found) and folded one chapter of a single-author book into the book. *Global Hiphopography* (2023) was entered as an edited volume with all its chapters, and Amber Lawson's dissertation (2025) was added.
- **New columns:** Topic 1, Topic 2, Field 1, Field 2, and Artist(s) named in the title, all browsable by clicking (with Language).
- **Cleaner cells:** bracketed notes such as "[to confirm]" or "[from OpenAlex …]" were taken out of the citation and tag columns, so each cell holds only its value; the notes are kept in the source sheet. The Link column holds only the link, and book titles in venues are in quotation marks.
- **Lookups:** OpenAlex, Crossref, and doi.org checks as described above; 16 DOIs that did not exist were fixed or removed.
- **Language:** filled or corrected for the newer works from their titles (AI judgment), and three raw language codes and two blanks fixed.
- **Empty tags filled from titles** (2026-11-15): Region of subject 78, US region / city 141, Style 503, Element 449.

## Earlier versions

- 1.3.1 (2026-11-09): round 2 searches added to the works they found again; three reprint links corrected.
- 1.3 (2026-11-09): round 2; chapters of edited volumes; 7,109 works.
- 1.2 (2026-11-04): 27 duplicate pairs merged; 5,799 works.
- 1.1 (2026-11-04): venues filled and citation details corrected; 5,826 works.
- 1.0 (2026-11-03): https://doi.org/10.5281/zenodo.23933279; 5,826 works.

All versions are on the same Zenodo page under "Versions."

## How to cite

Bomalaski, Rachel. 2026. *The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research*. Version 2.0. Zenodo. https://doi.org/10.5281/zenodo.23933278.

## License

Released under the Creative Commons Attribution 4.0 International License (CC BY 4.0): https://creativecommons.org/licenses/by/4.0/. You may share and adapt it for any purpose, provided you give appropriate credit, link to the license, and indicate whether changes were made.
