# How this repository was made (Guatemala)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Corte de Constitucionalidad de Guatemala, Constitución Política de la República (edición 2024) | <https://www.cc.gob.gt/index.php/constitucion-politica/> | 2026-10-29 | No licence statement; official publication of the Court. |
| Instituto de la Defensa Pública Penal de Guatemala, Código Penal y sus reformas (Decreto 17-73) | <https://www.idpp.gob.gt/images/Biblioteca-virtual/Leyes_y_Reglamentos/CODIGO_PENAL.pdf> | 2026-10-30 | No licence statement; official legal text published by a State body. |
| Ministerio de Cultura y Deportes de Guatemala, Código Civil (Decreto-Ley 106) | <https://mcd.gob.gt/wp-content/uploads/2013/07/codigo-civil.pdf> | 2026-10-30 | No licence statement; official legal text published by a State body. |
| Ministerio de Economía de Guatemala, Código de Comercio, Decreto 2-70 (ficha de ley) | <https://portal.mineco.gob.gt/sites/default/files/Mineco/ley_-_codigo_de_comercio_decreto_2-70_-_02-11-1970.pdf> | 2026-10-30 | No licence statement; official legal text published by a State body. |
| Oficina Nacional de Servicio Civil, Código de Trabajo (Decreto 1441), edition hosted by the Autoridad para el Manejo Sustentable de la Cuenca y del Lago de Amatitlán (AMSCLAE) | <https://www.amsclae.gob.gt/wp-content/uploads/2026/08/10.-DECRETO-1441-CODIGO-DE-TRABAJO.pdf> | 2026-10-30 | No licence statement; official legal text published by State bodies. |
| Organismo Judicial de Guatemala, Centro Nacional de Análisis y Documentación Judicial (CENADOJ): Código Procesal Penal, actualizado al 30 de abril de 2014 | <https://portal.pnc.edu.gt/wp-content/uploads/2024/02/CODIGO-PROCESAL-PENAL.pdf> | 2026-10-30 | The edition states "Derechos reservados: Organismo Judicial de Guatemala"; only the text of the law is reproduced, as an official legal text with attribution (see LICENSE). |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitucion` | Constitución Política de la República de Guatemala | 1 | 2024-07-18 to 2024-07-18 |
| `codigo-penal` | Código Penal (Decreto 17-73 del Congreso de la República) | 1 | 2022-08-11 to 2022-08-11 |
| `codigo-civil` | Código Civil (Decreto-Ley 106) | 1 | 2024-06-21 to 2024-06-21 |
| `codigo-de-comercio` | Código de Comercio de Guatemala (Decreto 2-70 del Congreso de la República) | 1 | 2021-04-23 to 2021-04-23 |
| `codigo-de-trabajo` | Código de Trabajo (Decreto 1441 del Congreso de la República) | 1 | 2017-04-14 to 2017-04-14 |
| `codigo-procesal-penal` | Código Procesal Penal (Decreto 51-92 del Congreso de la República) | 1 | 2014-04-30 to 2014-04-30 |

The build made 6 commits:

| Commits | Kind |
| ---: | --- |
| 6 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 0 laws in the record.
- 6 tags.

## Dates

Each commit is dated at noon (America/Guatemala) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: The Corte de Constitucionalidad publishes the Constitution in force and gives no per-version dates; the version is dated by the publication date of the PDF edition. https://www.cc.gob.gt/index.php/constitucion-politica/

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `481a7cf3ac22c63d72bf311b89b86075ee9d232a7d802813b967037ac7dd541a` (2684054 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3d00541d258745461ab52b1b0cb4e1716a27a95d`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

6 versions of 6 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

A second build from the same corpus into an empty folder gave identical hashes for all 6 history commits and 6 tags (history tip `f9820f07bcca96588d575ab682986bdfd680f164`).

## Decisions made by hand

- Oldest version available: the Court publishes one edition and no history, so it is one version credited to the publisher. It is dated 2024-07-18, the date of the PDF (HTTP Last-Modified and PDF creation date), not an in-force date: the Constitution came into force on 14 January 1986 and was reformed in 1993.
- About half of the lines of the PDF use a font without a Unicode map. Their glyphs were mapped to characters with a fixed table (Times New Roman in Mac Roman glyph order); this is not OCR, and every word of the result was checked against the words of the PDF normally-encoded lines.
- Footnotes (reform notes), running headers, page numbers, the deputies' signatures and the editor's note are left out. The enacting formula "Dado en el Salón de Sesiones..." is kept as unit cierre.
- Paragraph breaks are read from line spacing; at a page boundary a break is assumed when the previous line ends with a full stop, semicolon or colon.
- Transitional and final provisions (Título VIII) are files disp-01 to disp-27; the PDF omits the word "Artículo" before provision 9 and it was restored.
- Epigraphs (article titles) are kept as printed at the start of each article.
- Código Penal: one version dated 2022-08-11, the HTTP Last-Modified date of the IDPP PDF, credited to the publisher as "oldest version available". It is not the in-force date: the Code entered into force on 15 September 1973, and the PDF holds the text with reforms consolidated up to about 2008.
- Código Penal: one unit per article (art-NNN, with -bis suffixes); the general and final provisions printed as "Artículo I" to "Artículo IV" and "Artículo único" are disp-i to disp-iv and art-unico. Book, title and chapter headings, page numbers and the enacting preamble and signatures are left out; epigraphs are kept at the start of each article.
- Código Penal: three articles are printed in the source with a wrong number and are keyed by their place in the sequence: the "Artículo 337" after 386 is art-387, the second "Artículo 476" is art-478 and the "Artículo 463" after 482 is art-483. The label shows the sequence number; the text is unchanged. The source has no article 463.
- Código Civil: one version dated 2024-06-21, the HTTP Last-Modified date of the MCD PDF, credited to the publisher as "oldest version available". It is not the in-force date: the Code entered into force on 1 July 1964; the PDF holds the text as reformed to an unstated date.
- Código Civil: one unit per article (art-NNN, art-NNNN from 1000; the source has no articles 992, 1000, 1024, 1558 and 2158); articles 229 to 251 are printed as one repealed block and are the single unit art-229-251; the transitional articles at the end are trans-NNN. Headings, page numbers, page footnotes (reform notes) and footnote markers beside article numbers are left out; reform-note markers inside article text, if any, are kept.
- Código de Comercio: one version dated 2021-04-23, the HTTP Last-Modified date of the Ministerio de Economía PDF, credited to the publisher as "oldest version available". It is not the in-force date: the Code entered into force on 20 June 1970; the PDF holds the text with reforms up to Decreto 20-2018 already applied.
- Código de Comercio: one unit per article (art-NNN, art-NNNN from 1000); transitional articles are trans-NN and the final articles of the decree are fin-NN. The source marks reformed and added articles with its own annotation lines in braces (for example "{REFORMADO por el Art. 1 del DECRETO ... el cual queda así:}"); they are kept as printed. The appendix of original texts replaced by reforms ("EL ART. N ORIGINAL DECIA"), the enacting signatures and the portal header and footer are left out.
- Código de Comercio: the source prints no heading for article 280; its text (under a note on the renamed Chapter II) is the unit art-280. Book, title and chapter headings are left out.
- Código de Trabajo: one version, the Oficina Nacional de Servicio Civil consolidation, credited to that office as "oldest version available". It is dated 2017-04-14: its latest reform is Decreto 7-2017, published in the Diario de Centro América on 6 April 2017 (footnotes of the source), in force eight days after publication under the Ley del Organismo Judicial, art. 6, as the decree states no other term. Later reforms and Constitutional Court rulings, if any, are not applied.
- Código de Trabajo: one unit per article (art-NNN, with -bis suffixes); the transitional articles I-II are trans-i and trans-ii and the repealing and final articles I-III are fin-i to fin-iii. Title and chapter headings, the running header, page numbers, the reform footnotes and their markers, the considerandos and the signatures are left out. Paragraphs are rebuilt from the line layout (a line ending in . : or ; followed by a capital starts a new paragraph, as do numbered and lettered items).
- Código Procesal Penal: one version, the CENADOJ (Organismo Judicial) edition, credited to CENADOJ as "oldest version available" and dated 2014-04-30, the date to which the edition states it is updated ("Actualizado al 30 de abril de 2014"); its latest reform note is Decreto 6-2013. Later reforms (for example Decreto 10-2019 on acceptance of charges) are not applied.
- Código Procesal Penal: one unit per article (art-NNN, with bis/ter suffixes); epigraphs are kept at the start of each article. The editor's reform notes printed in small bold italics ("(Reformado por el Artículo 1 del Decreto 7-2011 ...)") and the notes on rulings of unconstitutionality are left out, and each note marks a paragraph break; the text the Court struck down is kept as the edition prints it (underlined there). Headings, page headers and numbers, the considerandos, signatures and the annex of agreements and circulars are left out.
- Código Procesal Penal: the edition goes on printing the former text of repealed provisions after its note "(Derogado por ...)". Where the note opens an article, the unit reads "Derogado." (art-044-bis, art-083, art-084, art-119, art-125, art-126, art-127, art-128, art-129, art-130, art-131, art-132, art-133, art-134, art-324-ter, art-335, art-345-bis, art-345-ter, art-345-quater, art-346, art-347, art-350, art-351, art-352, art-415-bis, art-527, art-528, art-529, art-530, art-531, art-532, art-533, art-534, art-535, art-536, art-537, art-540, art-541, art-542, art-543, art-544, art-546); a paragraph under "(Párrafo derogado por ...)" is left out (art-323); a listed item noted "(Derogada por ...)" keeps its letter and reads "Derogada." (art-024-quater). Article 343 is printed twice, repealed and then re-added by Decreto 18-2010; the re-added text is used.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code wrote the deterministic extraction code; no model wrote or altered any legal text.
- none
- none
