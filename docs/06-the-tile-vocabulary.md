# 06 — the tile vocabulary: 12,720 strings in five languages, in files the classifier called unreadable — and the join to the maps, which closes

*Measure: `python tools/tiletable.py census|langs|dupes
rpgvxace-steam/rtp/Graphics/Tilesets`, in `notes/tiletable-census.txt`,
`notes/tiletable-langs.txt` and `notes/tiletable-dupes.txt`; `python
tools/rvmap.py join rpgvxace-steam/SampleMap --tilesets
rpgvxace-steam/rtp/Graphics/Tilesets`, in `notes/rvmap-join.txt`. Both tools
were written this session.*

---

## Twenty-two pictures and twenty-two lists

`rtp\Graphics\Tilesets\` holds **22 `.png` and 22 `.txt`**, and the text files
were in the OPAQUE bucket because they are UTF-8 and the classifier tested
ASCII and cp932 ([04](04-the-magic-table.md)).

```
python tools/tiletable.py census rpgvxace-steam/rtp/Graphics/Tilesets

tileset tables (.txt) : 22        tileset images (.png) : 22
stems in both         : 22        only .txt : none      only .png : none
RESIDUE on the stem join : 0

encodings, by the first codec that takes the whole file : {'utf-8': 22}

total rows            : 2544      blank lines  : 0
fields per row        : {5: 2544}
strings in total      : 12720   (2544 rows x 5 fields)
empty fields          : 0
```

**A residue-0 join on the names, a residue-0 shape on the rows, and not one
empty field in 12,720.**

The first row of `World_A2.txt` is

```
Grassland|草原|Prairie|Wiese|Prado
```

**No object in this collection has ever shipped a localisation table for its
own vocabulary.** It is the largest completely readable thing in this object
that nobody had read, and it was sitting next to the images it names, in plain
text.

---

## The row counts are not arbitrary — they are the format

```
  Dungeon_A1     16     Inside_A1     16     Outside_A1     16     World_A1     16
  Dungeon_A2     32     Inside_A2     32     Outside_A2     32     World_A2     32
                                             Outside_A3     32
  Dungeon_A4     48     Inside_A4     48     Outside_A4     48
  Dungeon_A5    128     Inside_A5    128     Outside_A5    128
  Dungeon_B     256     Inside_B     256     Outside_B     256     World_B     256
  Dungeon_C     256     Inside_C     256     Outside_C     256
```

**Four families — World, Outside, Inside, Dungeon — and seven page kinds, and
every page kind has exactly one row count wherever it appears.** 16 × 4 + 32 ×
4 + 32 × 1 + 48 × 3 + 128 × 3 + 256 × 4 + 256 × 3 = **2,544**, residue 0.

That regularity is what makes the next section possible.

---

## Which columns are which language, by codepoint and not by position

```
python tools/tiletable.py langs rpgvxace-steam/rtp/Graphics/Tilesets

  column scripts observed, commonest first
  1      ascii x2544
  2      japanese x2544
  3      ascii x1598, latin x946
  4      ascii x1825, latin x719
  5      ascii x2155, latin x389

  columns containing Japanese characters : [2]
  columns that are Latin script only     : [1, 3, 4, 5]
```

**Column 2 is Japanese in all 2,544 rows and no other column is Japanese in
any row.** That is demonstrated from the bytes.

**Which of the four Latin columns is which language is not**, and the tool is
built so that it cannot claim otherwise: `script_of()` returns `ascii`,
`latin`, `japanese`, `mixed` or `empty`, and four of its checks assert that
`Grassland`, `Prairie`, `Wiese` and `Prado` come back as *script* and never as
*English*, *French*, *German* or *Spanish*. A codepoint census cannot tell four
Latin-script languages apart, so the tool is incapable of saying it can.

**The four names are therefore ATTRIBUTED** — from the object's own column
order, from the product's shipped interface languages, and from four words a
reader can check — and are not demonstrated. **And the fifth is not Italian,
while the interface this installation runs in is** ([09](09-the-programs.md)).

---

## It is a translated vocabulary and not a copied one, and that is a count

```
python tools/tiletable.py dupes rpgvxace-steam/rtp/Graphics/Tilesets

rows of exactly 5 fields : 2544

  distinct strings in a row   rows
  2                           8
  3                          21
  4                         115
  5                        2400

  rows where all five fields are byte-identical : 0 of 2544

  column pairs that are byte-identical, commonest first:
    column 1 == column 3     121 rows
    column 1 == column 5      28 rows
    column 1 == column 4      25 rows
    column 3 == column 4      22 rows
    column 3 == column 5      20 rows
    column 4 == column 5      10 rows
```

**Not one row of 2,544 has all five fields the same**, and 2,400 have five
distinct strings. Somebody translated 2,544 tile names into four languages and
did not take a shortcut on any of them.

**And column 2 appears in none of the six identical pairs.** Every pair is
between two Latin columns; the Japanese column is never byte-identical to
anything. That is a second, independent confirmation of the codepoint census —
a column that is Japanese in every row cannot equal a Latin one, and the
duplicate table says it never does.

The 144 rows that repeat a string between Latin columns are what a translator
leaves behind when a word survives translation: 121 of them are column 1
equalling column 3.

---

## The join, which is the point

The maps hold tile ids. The tables hold names. **Nothing in this object states
the mapping between them** — the tables are indexed by position within one
page, a map cell holds a global id, and no file in the tree says which id
belongs to which page. The help file's tileset pages describe the editor's user
interface and not the encoding.

**But the row counts are not arbitrary, and that is enough to derive the
layout and then test it.**

Every page kind has one row count. An autotile page's rows occupy 48
consecutive ids each; a single-tile page's rows occupy one. Lay the pages end
to end and the boundaries fall out — and if the derivation is wrong, ids will
land in the gaps between the bands.

### First, the clusters, from the ids alone and before any layout is proposed

```
python tools/rvmap.py join rpgvxace-steam/SampleMap --tilesets …

    ...    511   then nothing until     1536   (gap of 1024)
    ...   1663   then nothing until     2048   (gap of 384)
    ...   4604   then nothing until     4688   (gap of 83)
    ...   4990   then nothing until     5074   (gap of 83)

    cluster starts observed : [1, 1536, 2048, 4688, 5074]
```

### Then the layout, from the row counts

```
    page   rows  ids/row   id range
    B       256        1        0 ..    255   (256 ids)
    C       256        1      256 ..    511   (256 ids)
    A5      128        1     1536 ..   1663   (128 ids)
    A1       16       48     2048 ..   2815   (768 ids)
    A2       32       48     2816 ..   4351   (1536 ids)
    A3       32       48     4352 ..   5887   (1536 ids)
    A4       48       48     5888 ..   8191   (2304 ids)
```

**What is derived and what is fitted is stated, because the difference is the
whole argument.** The **spans** are derived: 16 × 48 = 768 and 2,048 + 768 =
2,816; 32 × 48 = 1,536 and 2,816 + 1,536 = 4,352; and so on to 8,191. The two
**bases** — where A5 starts and where A1 starts — are *fitted* to the observed
cluster starts, and the tool says so on the page.

**And the fit is confirmed by the data from the other end.** The first cluster
ends at **511**, which is exactly where C's derived span ends. The second ends
at **1663**, which is exactly where A5's derived span ends. Those two
boundaries were not fitted to anything; they came out of the row counts, and
the ids stop there.

### Then the test

```
    distinct ids used                : 3133
    ids inside a derived band        : 3133
    ids OUTSIDE every derived band   : 0
    RESIDUE                          : 0
```

**Every one of the 3,133 distinct tile ids the 117 maps use falls inside a band
derived from the tables' own row counts.** The half of the join that could fail
did not.

**And the half that cannot close is reported as not closing:**

```
    ids covered by the derived bands : 6784
    of those, used by some map       : 3133
    published and never used         : 3651
```

A tile nobody placed is not an error; a sample map does not use every tile in
its tileset. **The residue that matters is the first one, and it is zero.**

*The tool's own blind spot is named in its docstring and checked in its
selftest: a join that matches on COUNTS is not a join that matches on MEANING,
and three checks assert that a count over shuffled names is the same count. So
the closure above is stated as ids-inside-bands, which is what it is, and never
as tile-names-matched, which it is not.*

---

## What the two formats are, together

Two thousand five hundred and forty-four tiles, named in five languages, laid
out in seven page kinds across four families; and a million and eighty-five
thousand cells in a hundred and seventeen maps drawing on 3,133 of them. **The
grids and the vocabulary are one design and they are shipped as two file
formats in two directories, neither of which references the other.** Joining
them cost one arithmetic and it closed at residue 0 the first time it was
tried.
