# Field Reference build report — .txt and .brf editions

Built from master.json (Edition 2.0, 2026-10-31) by build_field_reference.py. Each .brf is translated from the same paragraph list as its .txt, so the two match exactly. Translation: liblouis contracted grade 2 UEB (en-us-brf.dis + en-ueb-g2.ctb), 40 cells per line, 25 lines per page, form feed between pages.

## Files

| File | .txt lines | .txt bytes | .brf lines | .brf pages | .brf bytes | Validation |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| guide | 37 | 2027 | 70 | 3 | 1670 | OK |
| phonetics | 36 | 410 | 38 | 2 | 480 | OK |
| morse | 163 | 4796 | 210 | 9 | 4570 | OK |
| emergency | 43 | 1882 | 71 | 3 | 1627 | OK |
| voice | 63 | 2803 | 107 | 5 | 2555 | OK |
| cw | 39 | 673 | 40 | 2 | 663 | OK |
| qsignals | 67 | 1732 | 77 | 4 | 1624 | OK |
| reports | 54 | 1320 | 65 | 3 | 1219 | OK |
| bands | 177 | 7119 | 293 | 12 | 6858 | OK |
| digital | 95 | 3980 | 156 | 7 | 3636 | OK |
| station | 105 | 5204 | 189 | 8 | 4523 | OK |
| deployment | 37 | 1863 | 67 | 3 | 1590 | OK |
| ares | 13 | 653 | 25 | 1 | 571 | OK |
| races | 13 | 695 | 26 | 2 | 609 | OK |
| mars | 13 | 766 | 28 | 2 | 665 | OK |
| cap | 13 | 716 | 26 | 2 | 638 | OK |
| shares | 13 | 792 | 28 | 2 | 685 | OK |
| observer | 13 | 689 | 25 | 1 | 599 | OK |
| traffic | 111 | 4932 | 194 | 8 | 4329 | OK |
| forms | 163 | 3677 | 255 | 11 | 4570 | OK |
| weather | 30 | 1128 | 48 | 2 | 976 | OK |
| reference | 28 | 1076 | 40 | 2 | 952 | OK |
| AB9MZ_Amateur_Radio_Field_Reference | 1328 | 48121 | 2037 | 91 | 44776 | OK |

Totals: 23 .txt files, 23 .brf files, 94 Braille pages across the 22 section files.

## Judgment calls

- Tables are linearized one row per line. 2-column tables join cells with a space ("A Alfa"); 3-column tables join cells with ", " so the columns stay apart ("AR, dit dah dit dah dit, End of message"); the two 4-column side-by-side tables (phonetics, Morse letters) are split into their two logical pairs, two lines per row. Header rows render in the same form as data rows.
- Morse dot/dash patterns are spelled as words ("dit dah") wherever they appear as standalone tokens, in tables and in prose (including "SOS is ...---..." in the timing page). A table cell that IS a pattern is spelled out even when it is a single dot (E) or dash (T); in prose only runs of two or more are converted, so real periods and hyphens are left alone. Raw dots and dashes read as punctuation in Braille.
- Page references are expanded from source numbers to source titles ("References: Morse code; Q signals") instead of bare numbers.
- A page title that repeats its section title is not printed twice (7 pages: phonetics, ARES, RACES, MARS, Civil Air Patrol, SHARES, Official Observer).
- Each section file opens with "AB9MZ Master Field Reference, Edition 2.0" so a standalone section still says what book it came from. The whole-book file opens with the full title block and starts each section on a new Braille page.
- Validation: every .brf line at most 40 cells, every character in the Braille ASCII range, and every file back-translates to its .txt. The known liblouis back-translation artifacts repaired in validation (each verified forward-correct by hand — see build_field_reference.py validate_brf) are: the grade-1 + caps-word words "AC" and "RCVR", which the back-translator renders "Ac" and "Rcvr"; seven caps passages the back-translator drops ("ITU R M.1677", "I SAY AGAIN", the spaced capitals "S O S", the traffic preamble "1 R AB9MZ 10 TINLEY PARK IL 0200Z NOV 1", the traffic message text "EXERCISE SHELTER ONE HAS POWER X NO ADDITIONAL BATTERIES NEEDED", its check line, and the "SAY AGAIN WORD AFTER, WORD BEFORE" prowords); the quotation-mark character, whose UEB cell the back-translator reads as the legacy EBAE "his" sign; and underscore runs in the forms section, which wrap across Braille lines (each "_" is two cells) so the line-joining space lands inside the run in the back-translation — spaces between underscores are collapsed on both sides before comparing, so the total count per run is still verified.
- Output filenames follow Gregory's naming scheme (2026-11-16): file-name_v2.0-20261116-2210-AB9MZ.xxx — version 2.0 (the book edition), revision date and 24-hour Central time, author AB9MZ. The scheme applies to these .txt/.brf files only; the kit files keep their names.
