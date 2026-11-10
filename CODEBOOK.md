# Codebook

*The Scholars Got Something To Say: A South-Facing Dataset for Interdisciplinary Hip-Hop Research*, version 1.3 (prepared 2026-11-01; rebuilt 2026-11-03; updated 2026-11-04 and 2026-11-09). Written by AI (Claude, Anthropic) from the dataset and its method; to be checked by the author.

The package holds three tables. All files are UTF-8 CSV with a header row; the same tables are in `dataset.xlsx`. From version 1.1 the works are listed in alphabetical order (see Sort key below).

**Conventions used throughout**

- **"[to confirm]"** (and forms such as "[Year to confirm]") marks a value that rests on a search record, a snippet or an AI lookup and has not been checked against the work itself.
- **A blank tag** means nothing read so far supports a value. It does not mean "none."
- **Several values** in one cell are separated by semicolons or commas.
- **IDs.** "PS-" works were found by the protocol searches, or are chapters of a work the searches found (a few, mostly books known through a review found by a search, are from other sources); "OS-" works were identified from other sources (PRISMA-ScR's term). Six OS works (pieces of the *Southern Cultures* "Hip-Hop" issue, first entered from the issue itself) were later counted under the hand-search HS-04. *Identified via* gives each work's final status (6,353 protocol, 216 other sources, 540 chapters of edited volumes). A chapter that replaced its book keeps the book's ID. Numbers are not reused; gaps are works that were merged as duplicates or removed.
- **Books and chapters (from version 1.3).** Edited volumes mostly about hip-hop have a row for the volume and a row for each chapter; chapter rows name the volume's ID in *Identified via* and have no protocol searches of their own. Books with only one or a few hip-hop chapters are entered as those chapters. See the README.

---

## 1. `dataset.csv` — one row per work (7,109 rows, 27 columns)

### Citation

| Column | What it holds |
|---|---|
| ID | Stable identifier (see above). |
| Author(s) | As in the record found; capitalization normalized. Editors are marked "eds." |
| Year | Year of publication as recorded, with notes where uncertain (e.g., "2026 [from the DOI record; to confirm]", "2021 [2002]" for a reprint, "n.d."). |
| Year (number) | The first four-digit year in *Year*, for sorting and filtering; blank when there is none. |
| Title | As in the record found. |
| Venue / publisher | Journal (with volume and issue where known), book, press or site. |
| Work type | One of 18 standardized types or the placeholder "[Type to confirm]", some with a bracketed qualifier (63 values in all), e.g., Journal article; Book chapter; Book; Edited volume; Book review; Review essay; Review (film, music, exhibition or event); Thesis or dissertation; Conference paper or presentation; Press or web article; Interview; Introduction, foreword or editorial. A value ending "[to confirm]" is uncertain; one ending "[AI-assigned]" was set by AI from an index record (Crossref, OpenAlex, DataCite or Open Library) on 2026-11-03 or later; "OpenAlex agrees" or "[from OpenAlex …]" means the type was checked against or taken from OpenAlex (2026-11-08). |
| Language | Language of the work. |
| Link | One URL: a DOI (as https://doi.org/…) where one was found, otherwise a publisher, repository or database page. Blank for 1,760 works. |
| Link note | Where the link came from and whether it is confirmed. "AI lookup via Crossref (or OpenAlex), 2026-11-01; to confirm" = found by matching title, first author and year in that index; notes dated 2026-11-03 say what was found to agree (2,722 works in all). "from OpenAlex W…, 2026-11-08" marks a link filled from OpenAlex in round 2. Notes such as "[Google Scholar; link to confirm]" = no link yet; the work was seen in that database. |

### How the work was found

| Column | What it holds |
|---|---|
| Identified via | "Protocol: " + the first search (ID and database) that found the work; "Other sources: " + where; or, for chapters of edited volumes, "Chapter of edited volume" + the volume's ID and the source of its table of contents. |
| Protocol searches that found it | The searches that returned the work, by search ID (see `protocol.csv`) and database. Complete for the first round; for round 2 (R2 and round 2 D strings), the search that first found a work is always listed, but a work already in the dataset that a round 2 search found again is listed under that search only in some cases (the Search Log counts all of them as duplicates). |
| Times found in protocol searches | Count of the searches in the previous column. Blank or 0 for most works from other sources and for chapters of edited volumes. |
| Tagged from | What the tags rest on: Search-result excerpt; Abstract; Citation only (title and venue); Table of contents or title only; Review record(s); Publisher description, web page or preview; Full text (part or whole). |
| Search topic | The broad topic of every search that found the work (29 topics, e.g., Artists and labels; Religion and theology; Hauntology; Journal hand-searches; Round 2: research gaps), from the search blocks in `protocol.csv`; "Other sources" for works not found by a search, including chapters of edited volumes. Several separated by semicolons. A fact about how the work was found, not a judgment of its subject. |
| Search subtopic | The specific search, e.g., "Southern artists: Houston", "Christianity", "Necropolitics, Mbembe and Fanon", "Hand-search: Callaloo 29 (3), Summer 2006, ..."; for other sources, where the work came from (e.g., "Other sources: Book known through its reviews"); for round 2, the gap or artist searched (e.g., "Gap: Trap and mental health", "Artist: Trina"). 208 values. In the database, `work_topics` holds one row per work and topic and `work_subtopics` one row per work and subtopic; `work_tags` holds one row per work and tag (Tag type: Style, Region, US region / city, Element, Discipline or Diasporic connection; Tag: the main term, before any parenthesis; Tag as written: the full wording). A place named only in parentheses (e.g., a city after a country) is not a separate tag; use the search box for it. These tables are for browsing. The database's `works` table also has a column, Sort key (alphabetical), used to list the works alphabetically: author's surname as written (prefixes such as "de" or "van" as written), or the title when there is no author (initial articles ignored); organizations as written; names in non-Latin scripts by their romanized form where the record gives one, otherwise after Z; accents and capitals ignored; then year and title. |

### Tags (the coding scheme)

All tags were assigned by AI from the material named in *Tagged from*. Region, style, element and discipline are open lists, standardized on 2026-11-01 for case and form: genre names and topics in lower case (trap, drill, gangsta rap; education, gender), with proper nouns kept (Southern hip-hop, UK drill, SoundCloud rap, Dirty South), and MCing and DJing as written; several values separated by semicolons; detail in parentheses after the main term (e.g., "visual (music video)", "MCing (flow)", "production/composition (sampling)"); "[to confirm]" for an uncertain value. Similar but distinct labels are kept apart (e.g., "Southern rap" and "Southern hip-hop"; "trap" and "trap rap"), since they follow the works' own wording.

| Column | What it holds |
|---|---|
| Region of subject | Where the hip-hop studied is: a country (e.g., "US", "UK", "Cuba"), a US region ("US: South"), a continent or wider area ("Africa", "Caribbean"), or "global" / "general" for works not tied to one place; a city may follow in parentheses. Filled for 5,585 works. |
| US region / city | For US subjects, region or city (e.g., Atlanta, Houston, New Orleans). |
| Style | Sub-genre or style, using the work's own label (e.g., trap, drill, bounce, crunk, chopped and screwed, gangsta rap, Memphis rap). |
| Element | Element of hip-hop: MCing; production/composition (kept separate from DJing); DJing; dance; visual (album covers, music video, fashion, graffiti); and topics such as education, gender or religion. |
| Hip-hop's place in the work | Mainly Central / Substantial / Section or chapter / Partial (a few pages); "Passing (diasporic genre; author's rule of 2026-10-31)" for works kept under the close-ties rule. Not standardized: some cells carry a short note or "[To check]". Blank where not yet judged. |
| Period of publication | 1990s academic founding; 2000s institutionalization; 2010s–2020s journals and global expansion; 1980s and earlier; Undated. Derived from the year. |
| Discipline | Academic discipline, where tagged (2,009 works). |
| Institutional status | One of 11 standardized values, alone or with "[to confirm]", or the placeholder "[To confirm]" (23 values in all, one with a short note), e.g., Peer-reviewed academic; Academic (other); Academic (thesis or dissertation); Student work; Press, journalism or other non-academic; Music criticism; Law or professional journal; Non-peer-reviewed (preprint, working paper or self-published); Interviews. |
| Format | Text, audio, video, images, etc. |
| Source role | Mainly Secondary (scholarship about hip-hop) or Primary (e.g., interviews, oral history, lyrics); some cells say "Both" or add a short note. Not standardized. |
| Diasporic connection | For works on genres with close ties to hip-hop, under the author's rule of 2026-10-31: mainly reggaetón, reggae, dancehall, dub, Afrobeat or Afrobeats, kompa, rara, soca, calypso, Afro-Cuban, Gullah Geechee, Garifuna and boogaloo, plus a few related tags (e.g., dembow, kuduro, zouk, amapiano, Afro-Latin, Afro-Brazilian, Caribbean (general)). 369 works. |

Not published (left in the source sheet): the AI-written summaries; the notes and provenance column; the coding-record column; and tag columns that need the full text and are filled for under 1% of works (region of origin, Southern origin acknowledged, historical lineage, period of subject, method, theoretical framework, the two stance columns, reading of the first-person voice, positionality, speaker). Also not published: the AI's hand-check list and the label wording from before standardization.

---

## 2. `search_log.csv` — one row per search per database (1,454 rows)

| Column | What it holds |
|---|---|
| Search ID | ID from `protocol.csv` (B = original blocks, C = combined strings, D = added strings, including the author's 18 round 2 strings, R2 = round 2 strings drafted by AI, HS = hand-search of a journal or special issue, BL = baseline). |
| Database | SciSpace, Wiley Scholar Gateway, OpenAlex, JSTOR, Google Scholar, Project MUSE, Web search, or "Hand-search" (the journal or issue is named in *Exact string as run* and *Notes*). |
| Searcher | AI, Author, or "Author (contents) and AI (screening)" for five hand-searches of special issues. |
| Date | Date run. |
| Exact string as run | The query as typed, or the question form for SciSpace and Wiley Scholar Gateway. |
| Filters; Sort | As set in the database. |
| Total results | As reported by the database. |
| Screen depth | How many results were screened. |
| Screened | Records screened. |
| Kept | Works new to the dataset. |
| Excl.: not about hip-hop | Excluded: not about hip-hop. |
| Excl.: passing mention | Excluded: hip-hop mentioned only in passing. |
| Duplicates | Works already in the dataset (counted, not entered again). A work is counted as kept under the first search that found it and as a duplicate under every later one. |
| Check (screened = kept + excluded + duplicates) | "OK" when the row adds up. |
| Notes | The screening record: how the search was run, what it was screened from, and which works were kept, excluded or counted as duplicates. |

Totals: 56,071 records screened; 6,340 kept; 12,743 not about hip-hop; 8,539 passing mentions; 28,449 duplicates. The author's searches were screened from the results pages she copied and pasted into documents (text files at first, then Google Docs).

---

## 3. `protocol.csv` — the search strings (487 rows)

| Column | What it holds |
|---|---|
| Search ID | ID used in the Search Log. |
| Block | Topic block of the protocol. |
| Search string | The string as planned. |
| Notes | Dated notes on wording and changes. |
| Wiley: who searches | Who ran the string in Wiley Scholar Gateway, and when. |
| Group | For the original strings, one of the protocol's groups, lettered A to G (A, Trap and Southern rap; B, the field as a whole; C, identities and communities; D, theory; E, disciplines and society; F, hip-hop and other genres; G, music analysis and composition), sometimes with a dated note; "Combined" for the combined strings (C); "Added (D)" and "Added (D, round 2)" for the D strings; "Round 2" for the R2 strings; "Hand-search" or "Hand-search (special issue)" for HS. |
| Replaced by (2026-10-30) | For the original strings, the combined string that replaced them in the author's searches. |

`protocol_notes.txt` holds the explanatory notes that sit outside the table in the source sheet (the search settings, the combined strings, the JSTOR length limit). They are dated: the note of 2026-10-30 counts 45 combined strings, C3-01 to C22-01; the three C23 strings were added on 2026-10-31.
