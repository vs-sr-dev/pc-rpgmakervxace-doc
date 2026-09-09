# 07 — the help file: eleven classes of eleven, seventy-five fields of seventy-five, and the same refusal one product later with the grammar fixed

*Measure: `python tools/itsf.py header rpgvxace-steam/RPGVXAce.chm`, in
`notes/itsf-header.txt`; `python tools/chmx.py check rpgvxace-steam/RPGVXAce.chm`,
in `notes/chm-check.txt`; `python tools/chmx.py extract … --out _work/chmx`;
`python tools/rgssjoin.py join --data rpgvxace-steam/SampleMap --docs
_work/chmx/rgss`, in `notes/rgss-join.txt`. `itsf.py`, `chmx.py` and `lzx.py`
were written on the previous object and opened this one without a change.*

---

## Nineteen times bigger, and not one line of the decoder moved

```
python tools/itsf.py header rpgvxace-steam/RPGVXAce.chm
  version 3, header length 96, NINE closures at residue 0
  chunk_count 4, chunk tags PMGL PMGL PMGL PMGI
  listing entries 356, index entries 3, refusals 0
  ResetTable 40 + 226 x 8 = 1848
  compressed 6,610,974   uncompressed 7,398,317, stated twice

python tools/chmx.py check rpgvxace-steam/RPGVXAce.chm
  BYTES PRODUCED        : 7398317      residue : 0
  section-1 entries              : 339
  entries lying inside the output: 339 of 339
  .html entries whose first 400 bytes contain '<' : 172 of 172
```

The previous object's container was 347,218 bytes with 26 reset blocks. This
one is 6,633,819 bytes with **226**. `chmx.py` and `lzx.py` were written for
the first and opened the second unchanged, and the extraction writes **340
files and 7,358,681 bytes**.

**That is a confirmation and it is worth one paragraph, which is what it gets.**
A decoder written against a specification nobody published, tested on one
specimen, that opens a specimen nineteen times larger with an entirely
different reset structure and closes at residue 0 on a figure the container
declares twice — that is the decoder being right rather than lucky, and the
right place to say so is here and briefly.

Inside: **/rgss/ 119 HTML of which 82 are class pages**, **/rpgvxace/ 53** —
the editor's manual, against the previous object's eleven — and **img/ 151
PNG**. `RGSS3` occurs 77 times.

---

## The join, and it closes completely

`pc-rpgmakerxp-doc/docs/06` joined that object's data against its help and got
**28 classes of 28 and 323 field names of 324**. The one field the vendor never
mentioned was `RPG::System`'s `@_`, whose value was `0x777777`.

**This object's join is 11 of 11 and 75 of 75.**

```
python tools/rgssjoin.py join --data rpgvxace-steam/SampleMap --docs _work/chmx/rgss

classes instantiated in the data : 11
classes documented by the .chm   : 82
in both                          : 11
in the data and NOT documented   : 0
documented and NOT in this data  : 71

  class                            data   docs  share  unmat +inherit  unmat
  RPG::BGM                            3      0      0      3       3      0
  RPG::BGS                            3      0      0      3       3      0
  RPG::Event                          5      5      5      0       5      0
  RPG::Event::Page                   13     13     13      0      13      0
  RPG::Event::Page::Condition        13     13     13      0      13      0
  RPG::Event::Page::Graphic           5      5      5      0       5      0
  RPG::EventCommand                   3      3      3      0       3      0
  RPG::Map                           24     24     24      0      24      0
  RPG::MoveCommand                    2      2      2      0       2      0
  RPG::MoveRoute                      4      4      4      0       4      0
  Table                               0      0      0      0       0      0
  TOTAL                              75     69     69      6      75      0
```

**Nothing in the bytes is undocumented.** Zero classes and — once the join
follows inheritance — zero fields.

### The six that looked unmatched were a defect in the join, not a gap in the manual

`RPG::BGM` and `RPG::BGS` document **nothing of their own**, and a join that
compares each class against its own page reports six missing fields. They are
not missing. `RPG::AudioFile`'s page opens:

> *A superclass of BGM, BGS, ME, and SE.*
> **Attributes** — `name` The sound file name. `volume` The sound's volume
> (0..100). The default values are 100 for BGM and ME and 80 for BGS and SE.
> `pitch` The sound's pitch (50..150). The default value is 100.

**Three attributes, on the parent, named as the parent of exactly these two
classes.** `rgssjoin.py` now reads the `Superclass` heading it already used to
recognise a class page, and resolves a class's attributes up the chain; five
checks were added, including one that a superclass of `Object` is read as *no*
superclass — because `Object` carries no serialised attributes and following it
would add nothing — and one that a cycle terminates instead of hanging.

**A join that does not follow inheritance reports a vendor as having failed to
document something the vendor documented one page away.** The 69 is what the
tool said before the repair and the 75 is what the object supports, and both
are printed, because the difference between them is the finding.

---

## The same sentence, one product later, with three words changed

`pc-rpgmakerxp-doc/docs/08` quoted that product's help file declining to
specify its encrypted archive format. **The installer here registers
`.rgss3a`, the tree ships none, and the help file mentions it exactly once, in
one file, `/rgss/rgss.html`:**

> Encrypted archives make it difficult for others to analyze and/or **modify**
> the game contents. Normally, all data and graphic files (**but not audio and
> font files**) are stored in `Game.rgss3a`. …
> **Due to its nature, the encrypted archive's internal format has not, and
> will not, be released to the public. Please refrain from analyzing it.**

The previous product's wording:

> …analyze and/or **rebuild** the game contents. Normally all data and graphic
> files (**not audio files**) are stored in `Game.rgssad`. …
> …has not, and will not, **been** released to the public.

**Three edits and the refusal intact.** *Rebuild* became *modify*; the
parenthesis grew a category; and *"will not, been released"* became *"will not,
be released"* — **somebody fixed the grammar of the sentence in which a vendor
declines to publish a format, and left the decline exactly where it was.**

For an index whose entries are sorted by whether anybody published a format,
that is the boundary marker restated by the boundary's owner, seven years
later, on purpose.

---

## And the help file is one generation behind its own product

The same page, two paragraphs up:

> When there is an encrypted archive in the game folder, the script data
> (normally `Data\Scripts.rvdata`) defined in the Scripts line of `Game.ini`
> will always be read from the archive.

**`Scripts.rvdata`.** The installer registers `.rvdata2`; the 117 data files in
this tree are `.rvdata2`; and the owner's own `Game.ini` — a file Steam did not
write — reads `Scripts=Data\Scripts.rvdata2` ([10](10-whose-bytes.md)).

**The vendor's manual names the previous generation's extension for the
current generation's file**, in a sentence about where that file is read from.
It is the same class of mistake this session's own three readers made, made by
the people who chose the extension, and it is in the document that is otherwise
a complete specification of the object's data model.

---

## What the seventy-one documented and unused classes are

Of the 82 class pages, 71 describe classes this database never instantiates,
and the help file sorts them itself: its file names carry an `sc_` prefix for
the standard Ruby library and a `gc_` prefix for the game classes, so the split
is the vendor's and not this session's.

```
sed -n '/documented and not instantiated/,/^  class /p' notes/rgss-join.txt \
  | grep -oE "sc_[a-z_0-9]+\.html|gc_[a-z_0-9]+\.html" | sed 's/_.*//' \
  | sort | uniq -c
     47 gc          24 sc
```

**Twenty-four are Ruby's own** (`Array`, `Hash`, `String`, `Fixnum`, `Bignum`,
`Proc`, `Regexp`, `Fiber`, `Time`, …). Of the 47 game classes, **35 are
`RPG::`** data classes for the parts of a game this object does not ship —
`RPG::Actor`, `RPG::Enemy`, `RPG::Skill`, `RPG::Weapon`, `RPG::Troop`,
`RPG::System`, `RPG::Tileset`, `RPG::MapInfo` — and **the remaining twelve are
RGSS's graphics layer**: `Bitmap`, `Sprite`, `Viewport`, `Window`, `Tilemap`,
`Plane`, `Font`, `Color`, `Tone`, `Rect`, `RGSSError`, `RGSSReset`.
24 + 35 + 12 = 71, residue 0.

**That last group is the same observation the previous object made, inverted.**
There, the help documented classes the database never used because the database
was one empty map. Here the help documents `RPG::Tileset` and `RPG::Actor`
because **this object ships no database at all** — only 117 maps, with no
`Actors`, no `System`, no `MapInfos`. The previous object shipped the empty
state of a game; this one ships a resource library and does not ship even that.
