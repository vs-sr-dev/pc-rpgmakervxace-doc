# 08 — the clocks: the fifth ITSF specimen kills the zone explanation, and what replaces it is one hour wide

*Measure: `python tools/chmclocks.py rpgvxace-steam/RPGVXAce.chm
../pc-rpgmakerxp-doc/rpgmakerxp-steam/RPGXP.chm
../pc-rpgmaker2003-doc/rpgmaker2003-steam/rpg2003.chm
../pc-rpgmaker2000-doc/rpgmaker2000-steam/rpg2000.chm
../pc-ilmiocomputer0206/…/SLPEI.chm`, in `notes/chmclocks.txt`; `python
tools/stampcheck.py rpgvxace-steam`, in `notes/stampcheck.txt`; `python
tools/pecensus.py rpgvxace-steam --by-magic`, in `notes/pecensus.txt`; `python
tools/uuidscan.py rpgvxace-steam`, in `notes/uuidscan.txt`. `chmclocks.py` was
written on the previous object and was not modified.*

---

## The question the previous object asked, and the specimen it asked for

`pc-rpgmakerxp-doc/docs/09` found that object's two `/#SYSTEM` clocks
**57,603.953125 seconds** apart, decomposed it as *sixteen hours plus a
compile*, and excluded every time zone by arithmetic — no zone in the Windows
or IANA databases lies outside −12:00 … +14:00, so a sixteen-hour term cannot
be one field local and the other UTC. It left two mechanisms standing and wrote
the falsification:

> *a fifth ITSF specimen with a 0x0411 header whose two clocks agree to within
> seconds would show the bias is not a property of Japanese-locale builds.*

**The fifth specimen has a 0x0411 header and its clocks are seventeen hours
apart.**

```
python tools/chmclocks.py <five containers>

  file           bytes    /#SYSTEM code 10       /#SYSTEM code 4 (FILETIME)
  RPGVXAce.chm  6633819   2012-03-12 17:20:34    2012-03-12 00:20:26.108187
  RPGXP.chm      347218   2005-08-30 22:44:00    2005-08-30 06:43:56.046875
  rpg2003.chm   6268124   2017-09-16 19:54:13    2017-09-16 19:53:55.521294
  rpg2000.chm   5503242   2017-09-13 12:06:26    2017-09-13 12:06:17.556084
  SLPEI.chm     2521916   2005-08-29 05:58:56    2005-08-29 05:58:47.842442

  file           header LCID  code-4 LCID  hdr-vs-c4  code10-code4  remainder
  RPGVXAce.chm   0x0411       0x0409        0.062428  61207.891813  17h + 7.891813
  RPGXP.chm      0x0411       0x0409        0.031257  57603.953125  16h + 3.953125
  rpg2003.chm    0x0C07       0x0409        0.007550     17.478706     17.478706
  rpg2000.chm    0x0C07       0x0409        0.007551      8.443916      8.443916
  SLPEI.chm      0x0407       0x0407        0.187466      8.157558      8.157558
```

**So the falsification does not fire, and what it produces instead is better
than what it was looking for.**

---

## Four things the fifth specimen establishes

**One. The whole-hour term is exactly co-extensive with the Japanese header.**
Two specimens of five carry `0x0411` in the ITSF header, and they are the two
with a whole-hour term: **2 of 2 against 0 of 3.** The three without it are two
German (`0x0C07`) and one Swiss-German (`0x0407`), and their gaps are 17.48,
8.44 and 8.16 seconds.

**Two. A fixed zone bias is dead, and it is dead by arithmetic and not by
argument.** The previous object left standing *an eight-hour offset applied
twice*, which would give sixteen hours on every specimen that has one. **The
two hour-counts are sixteen and seventeen.** A constant does not take two
values. Whatever produces the whole-hour term varies between two builds of one
product line.

**Three. The remainder is a compile both times, and it does NOT grow with the
container.** The pre-briefing said it grows with file size. Sorted by size, the
five remainders are

```
   347,218 bytes -> 3.953125 s      2,521,916 -> 8.157558
 5,503,242       -> 8.443916        6,268,124 -> 17.478706
 6,633,819       -> 7.891813
```

**The largest container has the second-smallest remainder and the
second-largest has by far the biggest.** Within the RPG Maker line it happens
to rise — 3.95 s on 347 KB, 7.89 s on 6.6 MB — and across all five it does not.
The honest statement is that all five remainders lie between 3.95 and 17.48
seconds, which is a plausible band for compiling a help project, and that the
band does not order by size. **That is a correction to the pre-briefing**
([13](13-corrections.md)).

**Four. The header-`u32` derivation holds a fifth time.** The ITSF header's
truncated `u32` at +0x10, joined to the code-4 FILETIME's high half, lands
0.062428 s from that FILETIME — beside 0.031257, 0.007550, 0.007551 and
0.187466. **Five specimens over twelve years, four locales and three products,
and a derivation somebody worked out from one container has never missed.**

---

## What varies by exactly one hour, and how to find out

The two hour-counts differ by **one**. That is a small number and it has one
common cause.

**Daylight saving is the only mechanism this pipeline has met that moves a
clock by exactly one hour and not by a whole zone.** The two compile dates are
**2005-08-30** and **2012-03-12**, which fall on opposite sides of the
northern-hemisphere summer-time window for every zone that keeps one: late
August is inside it, mid-March is outside it for European rules.

**And that reading has a problem the object itself supplies.** The header LCID
that these two specimens share is **0x0411, Japanese**, and **Japan has
observed no daylight saving since 1951.** So either the header LCID does not
describe the build machine's clock — it is a *language* identifier, and a
machine can be set to Japanese in a zone that keeps summer time — or the
mechanism is not daylight saving.

**That is a sharper question than the previous object could ask, and it is one
command from being answered.** The measurement that would distinguish them:

> **A sixth ITSF specimen with a `0x0411` header, compiled between late March
> and late October, whose whole-hour term is SIXTEEN. Or one compiled in
> winter whose term is SEVENTEEN.** Either confirms that the hour tracks the
> season and not the product. **A specimen compiled inside the summer window
> with a seventeen-hour term kills the daylight-saving reading outright**, and
> leaves *the machine's clock was moved between the two builds*, which is
> unfalsifiable from inside a container and should be said to be.

The compiler build is `HHA Version 4.74.8702` on **all five specimens over
twelve years**, so the tool is not the variable.

---

## The eight COFF stamps, and the instrument stays quiet for a second time

```
python tools/stampcheck.py rpgvxace-steam

  T1 IMPOSSIBLE (mtime precedes link time)      : 0 of 8
  T2 COLLIDING  (a stamp shared across sizes)   : 0 of 8
  T3 ROUND      (a round binary quantity)       : 0 of 8
  FALSE by at least one test                    : 0 of 8
```

**Eight plausible dates over three years and two months, and no test fires.**
`pc-rpgmakerxp-doc/docs/09` reported that tool's first silence and observed
that an instrument which only ever fires is an instrument nobody has tested.
**This is its second silence, on twice the population.** It is a negative
control and it is reported as one.

Six distinct COFF days, and two pairs of siblings each linked in one sitting:
**the two Valve DLLs 65 seconds apart** and **the two language DLLs 130 seconds
apart**, the Italian one first.

---

## Three UUIDs where the previous object had thirty-three

```
python tools/uuidscan.py rpgvxace-steam
version-1 UUIDs : 3 in 2 files   distinct node fields : 2

  RPGVXAce.chm  x2   1997-03-15 12:41:51.615828   (the LZX transform GUID)
  RPGVXAce.exe  x1   1996-07-08 20:31:25.984376
```

Both of the container's are Microsoft's LZX transform constant and the
editor's is the same 1996 class identifier the previous object's editor
carried. **There is not one Adobe XMP identifier in 1,456 PNG**, where the
previous object's seven sky panoramas carried thirty between them. Whatever
exported the art in this object writes no identifiers, which is a fact about a
tool chain and not about a date.

---

## Fifteen clocks, and two of them belong to the person who owns the copy

```
1996-07-08   a version-1 UUID inside RPGVXAce.exe
1997-03-15   the ITSF LZX transform GUID, a Microsoft constant
2011         'Copyright (C) 2011 Enterbrain, Inc. / Yoji Ojima', x4
2011-01-03   SciLexer.dll, COFF                  (a third party's)
2011-10-06   Projects\Game.exe, COFF             the RGSS3 player
2012-02-22   RGSS301.dll, COFF                   the interpreter
2012-03-12   RPGVXAce.chm, compiled              the manual
2012-03-14   the preorder bonus EULA, in prose
2013-11-05   Tyler Warren's readme, in prose     (a third party's)
2013-11-21   the two Valve DLLs, COFF            (a third party's)
2014-03-05   RPGVXAce.exe, COFF                  the editor
2014-03-06   the two language DLLs, COFF
2014-05-22   the Royal Tiles readme, in prose    (a third party's)
2025-10-16   wave 1: every file Steam wrote
2026-03-20   wave 2: the owner's two files
```

**Three human-written dates in three third parties' documents**, in a tree
where every filesystem date was written by Valve — and no earlier object in
this family had a date in prose at all.

**And the copyright year is four fields and not five.** `verres.py` reports
**eight** version resources over eight binaries, and four of them carry
`Copyright (C) 2011 Enterbrain, Inc. / Yoji Ojima`: `RGSS301.dll`,
`RPGVXAce.exe`, `RPGVXAceENU.dll` and `Projects\Game.exe`. **The Italian
language DLL carries no `LegalCopyright` at all** ([09](09-the-programs.md)),
which is why the count is four. The pre-briefing said five twice
([13](13-corrections.md)).

---

## The year cell is 2012

`pc-gamelist-doc` wants a `Year`, and the previous row took **2005** because
two independent witnesses inside the object — the editor's `LegalCopyright` and
the help file's own compile clock — agreed on the year. **Here they do not**:
the copyright field says **2011** and the help compiles on **2012-03-12**. So
the argument is not the same argument and has to be made rather than repeated.

* **2014-03-05**, the editor's link time, is the wrong kind of date, for
  exactly the reason the previous row gave: `RPGVXAce.exe` carries a fifth
  section called `.bind`, 562,176 bytes at high entropy, whose first
  instructions compare against `MZ` and `PE\0\0`. **Something re-linked the
  whole image after the product was built.** Dating the product by it dates the
  shop. **2014-03-06**, the two language DLLs, is the same date one day later
  and the same objection.
* **19572675** is the Steam build id, a counter.
* **2011** is a copyright year, and a copyright year is a claim about when a
  work was made.
* **2012 is what three structures written by three different tools say, and
  they were not written by the same pass**: `RGSS301.dll` links on
  **2012-02-22**; the help file compiles on **2012-03-12**; and the preorder
  bonus EULA, a document whose whole purpose is to be dated at or before a
  release, says **"Mar. 14th, 2012"** in prose. `Projects\Game.exe`, the player
  template, links on 2011-10-06 — a component, five months before the rest.

**Three artefacts in a twenty-one-day window in March 2012, one of them a
preorder document, against one copyright field.** The cell is **2012**, and the
copyright field's 2011 is reported beside it rather than discarded: a product
whose parts are dated 2011-10 through 2012-03 is a product made in 2011 and
released in 2012, and the cell that an index wants is the second one.

*What this cannot establish from the object is whether 2011 is itself a release
date of a different release. It is not in the bytes, and it is left in
[14](14-leftovers.md) rather than guessed at.*
