# 01 — the object: a tool with a resource library attached, the first in this collection anybody has used, and the first whose shop's total does not close

*Measure: `python _work/copyverify.py`, in `notes/copyverify.txt`; `python
tools/hashall.py rpgvxace-steam`, in `notes/sha1-all.txt`; `python
tools/treecensus.py rpgvxace-steam`, in `notes/treecensus.txt`; `python
tools/coverage.py tree --root rpgvxace-steam`, in `notes/coverage-tree.txt`
with the run made before this session touched the classifier in
`notes/coverage-tree-before.txt`; `python _work/pcts.py`, in
`notes/percentages.txt`, which recomputes every four-decimal share in exact
decimal.*

---

## What it is

**RPG Maker VX Ace**, Steam app **220700**, `Copyright (C) 2011 Enterbrain,
Inc. / Yoji Ojima`. A live installation, copied from the owner's machine and
verified on four axes.

```
python _work/copyverify.py

source files       : 2026
source directories : 45, of which empty 0
bytes                   : 342722404
size agrees             : 2026 of 2026
mtime agrees to 100 ns  : 2026 of 2026
sha1 agrees             : 2026 of 2026
directories, source     : 45   copy : 45   agree : True
empty directories       : 0    copy : 0    agree : True
size, mtime, sha1 and the directory tree all agree : True
the original was opened read-only and nothing was written to it
```

**It is the fifth object of one product family and the second built on RGSS.**
The previous object ran RGSS1 on Ruby 1.8.1; this one runs **RGSS3 on Ruby
1.9.2**, and the difference is visible in the byte stream and not only in a
version resource ([05](05-the-maps.md)).

**VX is skipped deliberately.** The owner's reasoning is that VX Ace is VX's
definitive version and that documenting both would be redundant. That is a
scoping decision, not a measurement, and it is recorded so that nobody has to
work out later why the family jumps a generation.

```
95     (1999, stolen)        1 file      7,120,053 bytes
2000   (2017, bought)      477 files    23,518,308
2003   (2017, bought)      737 files    33,578,445
XP     (2017, bought)      913 files    26,915,383
VX Ace (bought, USED)    2,026 files   342,722,404
```

**221.91 % of the previous object's files and 1,273.33 % of its bytes.** The
mean file is **169,162** bytes against **29,480**. This is not the same kind of
object as the four before it: it is a resource library with an editor attached,
and 87 % of its weight is PNG and Ogg.

---

## The eight denominators

Rule 3 of this pipeline says every figure names its denominator. This object
has eight, and **the second one is the finding**.

| | denominator | what it counts |
|---|---:|---|
| 1 | **2,026** files / **342,722,404** bytes | the tree, walked |
| 2 | **342,514,066** bytes | **what the shop believes the tree weighs — short by 208,338** |
| 3 | **45** directories, **0** empty | the shape, where the previous object had one empty of 27 |
| 4 | **1,935** distinct sha1 | the pictures, where 2,026 is the files |
| 5 | **8** binaries / 14,807,376 bytes | PE32 **7** and PE32**+** **1** |
| 6 | **117** files / 2,248,383 bytes | the data format |
| 7 | **2,544** rows / **12,720** strings | the tile vocabulary ([06](06-the-tile-vocabulary.md)) |
| 8 | **780** files / 202,842,120 bytes | `rtp\`, which is one depot exactly |

**The second denominator is not a defect of the shop.** It is short by exactly
the two files the shop did not put there, and a timestamp census that knows
nothing about the manifest partitions the same 2,026 files the same way
([03](03-the-shop.md)).

**And the fourth is not the first.** 1,935 distinct hashes over 2,026 files
means **84 hashes appear more than once** and there are **91 extra copies** —
two different numbers, and only the second closes: 1,935 + 91 = 2,026, residue
0. The previous object had no repeated hash at all. The four groups are counted
in [09](09-the-programs.md).

---

## The coverage, before and after

**The classifier arrived reporting 85.1928 % and left reporting 98.0644 %, and
one file it had already classified was classified *wrongly*.**

```
python tools/coverage.py tree --root rpgvxace-steam     (notes/coverage-tree-before.txt)

  specified  1957 files    291974845 bytes    85.1928 %
  decoded       1 files      6633819 bytes     1.9356 %
  derived       0 files            0 bytes     0.0000 %
  opaque       68 files     44113740 bytes    12.8716 %
  SUM        2026 files    342722404 bytes   100.0000 %   RESIDUE 0
```

**That run is committed as it came, before a line of `coverage.py` was
changed**, because a figure describing the state of the equipment before the
session touched it is true only at a moment (§C of [00](00-predictions.md)).

The 68 opaque files were **six published formats** — MP3, sfnt, BMP, PDF, ZIP —
plus 34 text files in **UTF-8 and EUC-JP**, which the probe did not test. And
one further file was worse than opaque: a 328,733-byte PDF sat in the
**specified** bucket under the name *plain text, Shift-JIS*, because a cp932
probe read a PDF header and found nothing illegal in it.

```
python tools/coverage.py tree --root rpgvxace-steam     (notes/coverage-tree.txt)

  specified  2025 files    336088585 bytes    98.0644 %
  decoded       1 files      6633819 bytes     1.9356 %
  derived       0 files            0 bytes     0.0000 %
  opaque        0 files            0 bytes     0.0000 %
  SUM        2026 files    342722404 bytes   100.0000 %   RESIDUE 0
```

**Zero files and zero bytes opaque.** Four binary magics, one more for ZIP, two
text codecs, and an ordering rule that puts every signature before every codec
— [04](04-the-magic-table.md) is what that cost and what it caught.

**The DECODED file is the same one it has always been:** `RPGVXAce.chm`, whose
container format Microsoft has never specified, opened here by a decoder this
collection wrote one session ago and did not have to change
([07](07-the-help-file.md)).

---

## What was in the twelve per cent

| | files | bytes | what it was |
|---|---:|---:|---|
| MPEG-1 Layer III | 23 | 25,354,236 | one DLC pack's music, in a second format |
| sfnt / TrueType | 4 | 15,795,408 | a Japanese open-source font, shipped twice |
| Windows BMP | 5 | 2,400,280 | the editor's project template images |
| UTF-8 text | 28 | 257,961 | **2,544 rows of a five-language tile vocabulary**, and readmes |
| EUC-JP text | 6 | 23,630 | the font's Japanese licence documents |
| ZIP | 1 | 208,185 | **the owner's** |
| PDF | 1 | 74,040 | a licence |

**Every one of those formats is published and two of them already had readers
in this box** — `zaccount.py` for ZIP, `bmp.py` for BMP. The gap was in the
table that decides what is readable and nowhere else, which is the third
appearance of that defect and the first in which it produced a wrong answer
rather than a silence.

---

## Why sixteen documents

The constraint is twenty and the last ten sessions wrote 20, 17, 18, 19, 17,
16, 16, 16, 17 and 18. **This one is sixteen**, and the reason is that the
object has exactly three things in it that had never been read and one piece of
equipment that was lying:

* **the 117 maps** — one chapter, [05](05-the-maps.md), because the grids and
  the events are one measurement and separating them would produce two
  censuses;
* **the 2,544-row tile vocabulary** — one chapter, [06](06-the-tile-vocabulary.md),
  which is also where the join between the two formats lives, because the join
  is the point and it belongs beside the thing being joined;
* **the help file** — one chapter, [07](07-the-help-file.md), which is the
  third format and the one that turns the other two into a specification;
* **the magic table** — one chapter, [04](04-the-magic-table.md), because a
  classifier that answers confidently and wrongly is a different hazard from
  one that stays quiet, and this is the first time this pipeline has caught it
  doing the first thing.

**No chapter in this repository is a census of a resource family for its own
sake.** There are 1,456 PNG, 363 Ogg, 23 MP3 and 4 fonts in this tree; their
figures are rows of [02](02-the-technical-sheet.md) and evidence inside
chapters that make an argument. The 310 interlaced PNG get four paragraphs
inside [09](09-the-programs.md) because they turned out to be a fingerprint of
one third party's export tool, and not because interlacing is interesting.

---

## The one-sentence version

**A Steam installation of a 2011–2012 Japanese game-making tool, running in
Italian, whose data format is still Ruby's `Marshal` and whose interpreter is
now Ruby 1.9.2; which ships 202 MB of resources, 508 character-generator parts,
117 sample maps, a Japanese open-source font with its licence set, and four
packs of downloadable content by three named third parties — and which, alone
among the five objects of this family, has been opened, played for
twenty-seven hours, and carries two files its owner put there.**
