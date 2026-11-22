# AB9MZ Master Field Reference

The Amateur Radio Field Reference by Gregory David Rosenberg, AB9MZ — Edition 2.0, October 31, 2026. 22 sections, 112 pages, in large print (22 point text, 28 point headings).

This is the reference book for the [Visually Inconvenienced Hams](https://www.facebook.com/groups/742838019382868/) Facebook group, a public group for blind and visually impaired amateur radio operators. The book lives in the group's document library, alongside everything else that used to be in the group's Files section: https://visually-inconvenienced-hams.github.io/vih-library/

## What is here

- `index.html` — the section selector. Tick the sections you want and download a custom edition as PDF or Word, right in your browser. (Also kept as `AB9MZ_Master.html`.)
- `AB9MZ_Amateur_Radio_Field_Reference.pdf` — the full book, all 22 sections, large-print PDF.
- `AB9MZ_Amateur_Radio_Field_Reference.docx` — the full book, all 22 sections, Word document.
- `sections/` — each of the 22 sections on its own, in large-print PDF and Word.
- `tagged/` — the full book and all 22 sections as tagged PDFs, which screen readers navigate by heading.
- `braille/` — each of the 22 sections plus the whole book in contracted Braille (UEB grade 2), as .brf files for Braille displays and embossers. Morse code patterns are spelled out as words ("dit dah") so they read clearly in Braille.
- `txt/` — each of the 22 sections plus the whole book in plain text, matching the Braille files line for line in content.
- `master.json` — the single source the whole book is built from. Edit this, then run `rebuild.py` to regenerate the PDFs, the Word files, and the selector.
- `READ_ME_FIRST.txt` — how the kit is organized and what is in it.
- `ACCESSIBILITY_REVIEW.html` — the accessibility review of the book (axe checks clean; VoiceOver, NVDA, and JAWS not yet tested; no WCAG 2.2 AA claim).
- Build scripts and libraries: `rebuild.py`, `prepare.py`, `render_support.py`, `build_tagged.py`, `build_editions.cjs`, `make_selector.py`, `test_generation.cjs`, `book_engine.js`, `selector.js`, `jszip.min.js`, `pdf-lib.min.js`, `compiled_master.json`, `TAG_CHECKS.json`, `VALIDATION.json`.

## Files in this directory

Every file at the root of this repo, with what it is. Subdirectories are listed at the end of this section.

- `AB9MZ_Amateur_Radio_Field_Reference.docx` — The full book, all 22 sections, as a Word document.
- `AB9MZ_Amateur_Radio_Field_Reference.pdf` — The full book, all 22 sections, as a large-print PDF.
- `AB9MZ_Master.html` — The offline section selector: tick sections and download a custom edition as PDF or Word, right in your browser. (Also served as `index.html`.)
- `ACCESSIBILITY_REVIEW.html` — The accessibility review of the book: axe checks, contrast items, and what is still untested.
- `BUILD-REPORT.md` — Per-file line and page counts and validation results for the plain-text and Braille editions in `txt/` and `braille/`.
- `README.md` — This file: what the repo holds and how to use it.
- `READ_ME_FIRST.txt` — How the kit is organized and what is in it. Start here if you downloaded the whole kit.
- `TAG_CHECKS.json` — Per-section checks on the tagged PDFs: page counts, tagged status, and language.
- `VALIDATION.json` — The kit build's validation record: revision, page counts, and which checks passed.
- `book_engine.js` — Offline assembly shared by the master selector and the command-line rebuild: builds custom PDF and Word editions from the section files.
- `build_editions.cjs` — Node script that assembles the PDF and Word editions using `book_engine.js`.
- `build_field_reference.py` — Regenerates the plain-text and Braille editions (`txt/` and `braille/`) from `master.json` and validates every .brf file.
- `build_tagged.py` — Builds the tagged PDFs from the current Word files. Requires LibreOffice.
- `compiled_master.json` — The compiled form of `master.json` used by the selector and the build scripts.
- `index.html` — A copy of `AB9MZ_Master.html`, so GitHub Pages lands on the section selector.
- `jszip-LICENSE.txt` — The license for the bundled JSZip library.
- `jszip.min.js` — The JSZip library (vendored): builds custom-edition zip files in the browser.
- `make_selector.py` — Builds `AB9MZ_Master.html` from `master.json`.
- `master.json` — The single source the whole book is built from: all 22 sections, their pages, tables, notes, and references.
- `pdf-lib-LICENSE.txt` — The license for the bundled pdf-lib library.
- `pdf-lib.min.js` — The pdf-lib library (vendored): builds custom-edition PDFs in the browser.
- `prepare.py` — Prepares the build inputs from `master.json` for the document build.
- `rebuild.py` — Rebuilds all documents and the standalone selector after editing `master.json`.
- `render_support.py` — Shared rendering helpers for the Python build scripts.
- `selector.js` — The selector page's user-interface logic: checkboxes, edition choices, and downloads.
- `test_generation.cjs` — Generation tests: runs the book engine and checks the PDF and zip output.

Subdirectories:

- `braille/` — The 22 sections plus the whole book in contracted Braille (UEB grade 2), as .brf files.
- `sections/` — Each of the 22 sections on its own, in large-print PDF and Word.
- `tagged/` — The full book and all 22 sections as tagged PDFs for screen readers.
- `txt/` — The 22 sections plus the whole book in plain text, matching the Braille files in content.

## The 22 sections

Using and printing this book; Phonetic alphabet; Morse code and procedural signals; Emergency operating procedures; Voice and repeater operation; CW abbreviations; Q signals and net codes; Signal reporting; US band privileges; Digital modes and linked systems; Antennas, power, and station checks; Accessible deployment; ARES; RACES; MARS; Civil Air Patrol; SHARES; Official Observer and Volunteer Monitor; National Traffic System; Message forms, logs, and PACE plan; Weather radio and storm reports; Glossary and review checklist.

## Accessibility notes

- Large print throughout: 22 point body text, 28 point headings, Morse patterns in 26 point bold.
- Tagged PDFs (in `tagged/`) carry real heading structure for screen readers. The print PDFs are fixed-layout and untagged.
- Braille files (in `braille/`) are contracted UEB grade 2, 40 cells per line, 25 lines per page, built with liblouis and verified by back-translation against the plain-text files.
- Plain-text files (in `txt/`) carry the same content as the Braille files, for screen readers, search, and anything that reads text.
- Morse code in the Braille and plain-text editions is spelled as "dit" and "dah" words, because raw dots and dashes read as punctuation in Braille.

## Rebuilding the Braille and plain-text editions

`build_field_reference.py` regenerates `braille/` and `txt/` from `master.json` and validates every .brf file (40 cells per line, back-translation round-trip). It needs liblouis with the UEB tables (`python3-louis`, `liblouis-bin`, `liblouis-data` on Ubuntu). Run it from this folder:

```
python3 build_field_reference.py
```

See `BUILD-REPORT.md` for the per-file line and page counts from the last build.
