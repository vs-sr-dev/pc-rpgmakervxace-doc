# 05 — the maps: 117 grids, a million cells, and fifty-nine events that instantiate seven classes and contain nothing

*Measure: `python tools/marshal48.py walk rpgvxace-steam/SampleMap`; `python
tools/rvmap.py fields|grid|events rpgvxace-steam/SampleMap`, in
`notes/rvmap-fields.txt`, `notes/rvmap-grid.txt` and `notes/rvmap-events.txt`;
`python tools/rgssdb.py tables|names rpgvxace-steam/SampleMap`, in
`notes/rgssdb-tables.txt`. `rvmap.py` and the magic-based file selection were
written this session; the `Marshal` reader and the `Table` decoder were not.*

---

## The reader was right and the selection was wrong

`marshal48.py` was written one session ago. Handed one of this object's files
it walks it to the last byte. Handed the directory it refused:

```
python tools/marshal48.py walk rpgvxace-steam/SampleMap
marshal48: no .rxdata under 'rpgvxace-steam/SampleMap' -- refusing to report a
clean table over an empty population
```

**`.rxdata` is what the previous object called this format.** This object calls
the same format — same `04 08` version bytes, same grammar, same parser —
`.rvdata2`. Three readers filtered on the literal extension, and a fourth was
found by running it ([12](12-the-tools.md)). `coverage.py`, which selects by
magic, got all 117 right without being touched.

The selection now opens the file:

```python
def is_marshal48(path):
    with open(path, "rb") as fh:
        head = fh.read(3)
    return (len(head) == 3 and head[0] == 0x04 and head[1] == 0x08
            and head[2:3] in TYPE_BYTES)
```

— two version bytes **and the third byte checked against the grammar**, because
one file in 65,536 begins `04 08` by accident. Nine checks were added, four of
which assert a refusal, and one of them requires that a file named `.rvdata2`
whose third byte the grammar cannot start with is **still** refused.

```
python tools/marshal48.py walk rpgvxace-steam/SampleMap

  files 117   bytes 2248383
  the walk lands on the last byte : 117 of 117
```

---

## Twenty-four fields, on every one of the hundred and seventeen

```
python tools/rvmap.py fields rpgvxace-steam/SampleMap

RPG::Map documents : 117
distinct ivar names: 24
every document carries every name : True

  ivar                    count  value types observed
  @parallax_name            117  RString x102, RWithIvars x15
  @height                   117  int x117
  @events                   117  list x117
  @parallax_sx              117  int x117
  @bgm                      117  RObject x117
  @tileset_id               117  int x117
  @encounter_step           117  int x117
  @width                    117  int x117
  @data                     117  RUserDef x117
  @bgs                      117  RObject x117
  @parallax_loop_y          117  bool x117
  @autoplay_bgm             117  bool x117
  @encounter_list           117  list x117
  @autoplay_bgs             117  bool x117
  @parallax_show            117  bool x117
  @scroll_type              117  int x117
  @parallax_loop_x          117  bool x117
  @disable_dashing          117  bool x117
  @parallax_sy              117  int x117
  @display_name             117  RString x105, RWithIvars x12
  @specify_battleback       117  bool x117
  @note                     117  RString x103, RWithIvars x14
  @battleback1_name         117  RWithIvars x114, RString x3
  @battleback2_name         117  RWithIvars x114, RString x3
```

**The previous object's `RPG::Map` had eleven ivars. This one has
twenty-four**, and `RPG::AudioFile` has split into `RPG::BGM` and `RPG::BGS`.
The object model did not grow; it was re-cut.

**And the `RWithIvars` column is the generational difference.** `RWithIvars` is
Marshal's `I` — a value carrying instance variables, which on a String is the
Ruby 1.9 encoding tag. It appears **466 times** across the 117 files and
**zero times in the whole of the previous object**. Five string fields account
for it, and the split is legible: `@battleback1_name` is tagged on 114 of 117
and plain on 3, `@display_name` is tagged on 12 and plain on 105. **A string
carries an encoding tag when it is not ASCII, or when Ruby was told it had
one**; the same field is both kinds in one directory, which is what a
serialiser looks like when the strings it was handed came from different
places.

---

## The grids, and there are four layers where there were three

```
python tools/rvmap.py grid rpgvxace-steam/SampleMap

RPG::Map documents                     : 117
Table payloads closing at residue 0    : 117 of 117
Tables whose x,y equal @width,@height  : 117 of 117
declared shapes (dimensionality, z)    : {(3, 4): 117}
cells over every map                   : 1085288

  layer   cells      non-empty      share of that layer
      0      271322      267255      98.5010 %
      1      271322       32985      12.1571 %
      2      271322       15719       5.7935 %
      3      271322        12671      4.6701 %

  distinct tile ids used (0 excluded)  : 3133
  the empty cell, id 0                 : 756658 of 1085288 cells
  lowest non-zero id                   : 1
  highest id                           : 8156
```

**Two closures, each from a different direction.** The `Table` payload declares
its own dimensions and its own cell count, and `20 + 2n` equals the payload
length on 117 files of 117. Independently, the map object declares `@width` and
`@height` beside the table, and those agree with the table's own x and y on 117
of 117. **Two structures written by different code paths agreeing is a stronger
statement than one structure closing**, and this is the same argument
`rgssdb.py` was built to make one product earlier.

**The layer profile is the shape of a drawn map.** Layer 0 is ground and is
98.5010 % full; layers 1, 2 and 3 are 12.16 %, 5.79 % and 4.67 %. Sixty-nine
per cent of all cells are empty, and they are empty in the three upper layers.
The previous object's `Table` was three-deep; RGSS3's is four.

---

## Fifty-nine events, in eleven maps, and every one of them is empty

`pc-rpgmakerxp-doc/docs/06` listed eight classes that object's help file
documented and its database never instantiated, and explained the absence in
its own words:

> **And eight are `RPG::` data classes that a database with no events cannot
> contain**: `RPG::Event`, `RPG::Event::Page`, `RPG::Event::Page::Condition`,
> `RPG::Event::Page::Graphic`, `RPG::MoveCommand`, `RPG::MoveRoute`,
> `RPG::Sprite`, `RPG::Weather`.
>
> **The first six of those eight are exactly what a map's `@events` holds, and
> this object's one map has `@events` = an Array of zero.** The absence in the
> data and the absence in the map are the same absence, measured twice by
> different routes.

**All six are here, and so is a seventh** — `RPG::EventCommand`, which that
list does not name because it appears in that object's data by another route.

**And the two remaining classes of the eight have stopped existing.** That
object's help file carried `gc_rpg_sprite.html` and `gc_rpg_weather.html`.
**This one carries neither**: `ls _work/chmx/rgss/ | grep -i "sprite\|weather"`
returns `gc_sprite.html` alone, which is the graphics class and not the
`RPG::` data class. So of the eight classes RGSS1 documented and never used,
**seven are instantiated here and two were deleted from the manual** — the
counts overlap because `RPG::EventCommand` is the seventh and is not in that
object's eight.

```
python tools/rvmap.py events rpgvxace-steam/SampleMap

RPG::Map documents               : 117
maps carrying at least one event : 11
maps carrying none               : 106
events in total                  : 59

  Map006  1     Map007  2     Map008  5     Map012  2     Map014  1
  Map018  7     Map020  1     Map022  1     Map033 14     Map038 14
  Map082 11

  classes reached from the events:
    RPG::Event                           59
    RPG::Event::Page                     59
    RPG::Event::Page::Condition          59
    RPG::Event::Page::Graphic            59
    RPG::EventCommand                    59
    RPG::MoveCommand                     59
    RPG::MoveRoute                       59
```

**Seven classes at fifty-nine instances each, and the pre-briefing's "59 events
across the sample maps" turns out to be 59 events across eleven of them.** A
hundred and six of the 117 maps carry none.

**And then the interesting part.**

```
  pages per event        : {1: 59}
  commands per page      : {1: 59}
  event command codes    : {0: 59}
  page @trigger values   : {0: 59}
  event @name values     : {'EV001': 9, 'EV002': 7, 'EV003': 5, 'EV004': 5, …}
  page graphics (@character_name, @tile_id):
    '!Other2'      tile_id 0      x 37
    ''             tile_id 262    x 14
    ''             tile_id 7 / 9 / 4 / 3    x 1 each
```

Every event has **one page**. Every page's command list holds **one command**,
and its code is **0**. The help file's own definition of that class reads

> `def initialize(code = 0, indent = 0, parameters = [])`

— **so code 0 is the default-constructed command, the terminator a page ends
with.** A page whose list is `[code 0]` is a page holding nothing.

Every event's name is `EV001`, `EV002`, `EV003` — the editor's automatic
numbering, per map. Thirty-seven of the 59 draw themselves with a character
sheet called `!Other2`; twenty-two draw themselves as a tile.

**So the six classes the previous object documented and never used are all
instantiated here, fifty-nine times each — and every one of the fifty-nine is a
picture with no behaviour.** The absence of yesterday and the presence of today
are the same fact measured twice, and the second measurement adds something the
first could not: **the object model is exercised and the scripting is not.**
These are sample maps. Somebody placed decorations on them and wrote no logic,
which is exactly what a resource library's demonstration maps should contain,
and it is a claim you can only make by opening the events rather than counting
the classes.

*And it is worth saying what would have happened if this chapter had stopped at
the class census. It would have reported seven classes at 59 instances each,
scored the previous session's open question as answered, and been entirely
wrong about what the object contains.*

---

## What is left

The `@encounter_list` of every map, the `@note` field's contents, and what the
117 maps are *of* — which is a question about pictures and not about bytes
([14](14-leftovers.md)). And the grids' tile ids join to something, which is
[06](06-the-tile-vocabulary.md).
