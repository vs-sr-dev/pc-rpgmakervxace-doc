# pc-rpgmakervxace-doc

**RPG Maker VX Ace** (PC, Windows; Steam app **220700**, `Copyright (C) 2011
Enterbrain, Inc. / Yoji Ojima`) — a live installation copied and verified on
four axes: **2,026 files, 342,722,404 bytes, 45 directories of which none is
empty, 1,935 distinct hashes**, agreeing with the source on size, on mtime to
the 100-nanosecond tick and on sha1, 2,026 times each.

**The fifth object of one product family, the second built on RGSS — and the
first in this collection that anybody has used.** `LastPlayed` is not `"0"`,
and two of the 2,026 files were put there by the person who owns the copy.

---

## The short sheet

| | |
|---|---|
| files / bytes | **2,026** / **342,722,404** |
| directories | **45**, 0 empty, 42 carrying files |
| distinct sha1 | **1,935**; 84 repeated hashes, 91 extra copies, residue 0 |
| coverage on arrival | **85.1928 % specified**, 68 files opaque — **and one PDF filed as Shift-JIS text** |
| coverage at publication | **98.0644 % specified, 1.9356 % decoded, 0 files and 0 bytes opaque**, residue 0 |
| the shop | `SizeOnDisk` **342,514,066** against a walked **342,722,404** — **residue −208,338** |
| the second residue | six depots summing 356,092,141 — **residue −13,578,075** |
| mtime waves | **two**: 2,024 files in 45 seconds, then 2 files five months later |
| the data format | **117** Ruby `Marshal` 4.8 documents, 11 classes, **75 field slots** |
| the map grids | **1,085,288 cells**, four layers, **3,133 distinct tile ids** |
| the tile vocabulary | **2,544 rows × 5 languages = 12,720 strings**, in files the classifier called unreadable |
| the join | **residue 0** over all 3,133 ids |
| the help file | 7,398,317 bytes of LZX, **11 classes of 11 and 75 fields of 75 documented** |
| binaries | **8** — PE32 7, PE32+ 1; linker 9.00 × 6, 10.00 × 2; 2 signed |
| against the collection | **26 of 1,935**, all with `pc-rpgmakerxp-doc`, **all Ogg, none under its old name** |
| corrections | **20** — thirteen by a program, seven by reading one |
| selftests | **221 checks over nine tools, 0 failures** |

---

## What is in it

| | |
|---|---|
| [00 — predictions](docs/00-predictions.md) | 64 clauses written before anything was opened, with P17's register of eight figures that had to be measured first |
| [01 — the object](docs/01-the-object.md) | what it is, eight denominators, and the coverage before and after |
| [02 — the technical sheet](docs/02-the-technical-sheet.md) | every figure in this repository with the command that reproduces it |
| [03 — the shop](docs/03-the-shop.md) | two totals that fail to close, and each failure names something exactly |
| [04 — the magic table](docs/04-the-magic-table.md) | a classifier that answered confidently and wrongly, and the ordering rule that is the repair |
| [05 — the maps](docs/05-the-maps.md) | 117 grids, a million cells, and 59 events that instantiate seven classes and contain nothing |
| [06 — the tile vocabulary](docs/06-the-tile-vocabulary.md) | 12,720 strings in five languages, and the join to the maps, which closes |
| [07 — the help file](docs/07-the-help-file.md) | 11 of 11, 75 of 75, and the same refusal one product later with three words changed |
| [08 — the clocks](docs/08-the-clocks.md) | the fifth ITSF specimen kills the zone explanation, and what replaces it is one hour wide |
| [09 — the programs](docs/09-the-programs.md) | a language DLL with no code, a section that names nobody twice, and 310 pictures that are one artist's export tool |
| [10 — whose bytes](docs/10-whose-bytes.md) | nineteen occurrences are three addresses, and the fifth rule is about work that is not the object's |
| [11 — against the collection](docs/11-against-the-collection.md) | twenty-six sound effects survive a generation, none under its own name |
| [12 — the tools](docs/12-the-tools.md) | four readers defeated by an extension, ten by a file name, and a survey whose denominator is the honest part |
| [13 — corrections](docs/13-corrections.md) | nineteen, split twelve to seven |
| [14 — leftovers](docs/14-leftovers.md) | thirteen questions with a reason each, and thirty-three initialisms of which nine the object expands itself |
| [15 — prediction scoring](docs/15-prediction-scoring.md) | 61 hits, 3 halves, 0 misses; P17 works and its author left a clause out of the register |

`notes/` holds the raw output of every command the chapters cite. `tools/` is
562 Python files — 558 inherited, four written here, eleven modified.

---

## The three things worth knowing

**The shop's total does not close, and the residue is the measurement.** Four
objects in a row closed at residue 0 because nobody had ever opened them. This
one is short by exactly `Projects\cd32.zip` plus `Projects\cd32.ini`, and a
timestamp census that has never read a manifest puts exactly those two files in
a second wave five months after the first. **Two instruments partition the same
2,026 files the same way and neither was told about the other.**

**A reader written one session ago opens this object's format and refuses the
object.** The format did not change between the two products; the extension
did, from `.rxdata` to `.rvdata2`. Four readers filtered on the name and one
classifier looked at the bytes, and only the classifier was right. **The reader
was correct and the file selection was wrong**, which is `mzcensus.py`'s
twelve-appearance defect inside tools that were a day old.

**And the classifier was worse than silent about one file.** A 328,733-byte PDF
sat in the SPECIFIED bucket under the name *plain text, Shift-JIS*, because a
cp932 probe read a PDF header and found nothing illegal in it. Adding `%PDF-`
fixes that file; **testing every binary signature before every text codec, and
asserting that ordering in a check that fails when it is broken, fixes the
class.**
