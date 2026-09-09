# 00 — predictions: what you measure when a reader written yesterday opens today's format and refuses the file anyway, and when the shop's total misses by exactly the bytes its owner wrote

*Measure: `python tools/predcount.py` — the clause count and the two totals
below are that command's output and not a hand sum; `python tools/predbands.py
--expect-under 0.60 5` for the three bands and for P12's five. This header was
written from the first run, before the first chapter, and regenerated from a
second run after the last chapter; both runs agree. The verdicts are in the last
chapter of this repository.*

```
document      : docs/00-predictions.md
clauses        : 64
  inherited    : 33
  open         : 31
  method       : 5
  content      : 59

the cross-tabulation, which is the one that matters:
  inherited method  : 0
  inherited content : 33
  open      method  : 5
  open      content : 26

TWO TOTALS, NEVER SUMMED TOGETHER:
  inherited predicted : 30.21 of 33
  open      predicted : 25.34 of 31

content share of the open clauses : 26 of 31 = 83.9 %
```

And the three P11 bands, which are the split the scoring chapter has to report:

```
python tools/predbands.py --expect-under 0.60 5

open content   : 26 clauses

lands       n= 7  total  6.21  mean 0.8871   C39 C40 C46 C57 C58 C61 C63
constructs  n=16  total 11.95  mean 0.7469   C41 C42 C43 C44 C45 C47 C48 C49
                                             C52 C53 C54 C55 C56 C59 C60 C64
nonnumeric  n= 3  total  2.66  mean 0.8867   C50 C51 C62

open content clauses priced below 0.60 : 5   C43=0.45 C48=0.55 C52=0.45
                                             C55=0.50 C59=0.50
```

**And the number P18 asks for is not the band mean but the sub-mean.** The five
P12 clauses total **2.45** and sit inside `constructs`; the **eleven
`constructs` clauses P12 does not govern total 9.50 for a mean of 0.8636**,
against last session's whole-band mean of 0.6908. **That is the figure P18's
falsification has to be evaluated against**, and the scoring chapter must report
it separately or the prescription cannot be scored at all.

This document was written after `prompt.txt` and the eight files of `_pre\` were
read; after `pc-rpgmakerxp-doc/docs/17` and its **P17**, **P18** and **P19** were
read in the original, along with `docs/04` for the coverage buckets as applied
and for the `Marshal` argument, `docs/05` and `docs/06` for the reader and the
class join, `docs/09` for the sixteen hours and the `Year` argument, `docs/11`
for the personal-data rule, `docs/14` for the tool defects and the rule-0 hook's
registration, and `docs/15` for its nineteen corrections; after
`pc-rpgmaker2000-doc/docs/09` for the four buckets and `docs/10` for the
personal-data rule's first statement; after the collection's two directory
counts were re-derived with `ls` and `tools\` was counted; and **before** any
`.rvdata2` was opened past the walk the pre-briefing quotes, before any tileset
table was read past its first row, before `RPGVXAce.chm`'s content section was
extracted, before `coverage.py` was touched, and before one byte of
`Projects\cd32.zip` was read — which is a decision and not an omission, and it
is C50.

Everything in §A is the pre-briefing's work and scores nothing. §B is the
calibration series, re-derived here by command. §C is P17's register — the
figures whose truth depends on *when* a command runs, with the commands already
run and their output already in `notes\`. Everything from C01 on is priced from
the brief and is scored in the last chapter whether it was right or not.

---

## The three prescriptions in force

> **P17 — the inherited band's remaining failures are not about the object.**
> Mark every clause whose figure describes a state the session itself will
> change, run those commands FIRST — before the change — and record the output
> in `notes/`. **Falsification: if a clause of that kind still loses points when
> the command has already been run and its output committed, the problem is not
> the timing either.**

**Implemented, and it is §C below.** Eight figures in this brief describe the
state of something this session is about to change: the tool box before a tool
is written, the coverage table before four magics are added, the refusal table
before three readers are repaired, the index before a row is added, the survey
of tools that crash on a directory before any of them is guarded. **All eight
commands were run before this document's first clause was written**, and every
one of their outputs is a file in `notes\` whose name ends `-before`. The
clauses that cite those figures cite the file and not the brief.

**And the first one already disagreed with the brief**, which is what §C is for.

> **P18 — `constructs` has stopped being ambitious and started being priced
> wrong.** Price `constructs` clauses at the observed over-delivery rate — a
> mean at or above 0.80 — and put the ambition where P12 wants it, in five
> clauses priced below 0.60 and nowhere else. **Falsification: if `constructs`
> priced at 0.80 still over-delivers above 75 %, the band is measuring something
> other than confidence.**

**Implemented, and it collides with P12 head-on, so this document reports two
means rather than pretending it does not.** P12 requires five open content
clauses priced below 0.60. The five ambitious claims this object supports are
all `constructs`-shaped — a join, a join, a decomposition, a comparison and a
scope measurement — so all five sit inside the band P18 wants priced up.

**The two prescriptions cannot both be satisfied by one arithmetic mean**, and
the resolution is stated here in advance rather than discovered in scoring:

* the **eleven `constructs` clauses P12 does not govern** are priced at the
  observed rate, a mean of **0.86**, against last session's whole-band mean of
  0.6908. That is P18 obeyed;
* the **five P12 clauses** are priced at a mean of **0.49**. That is P12 obeyed;
* **the band mean is therefore below 0.80 and is reported as such.** The
  scoring chapter must report the sub-mean over the eleven separately, or P18's
  falsification cannot be evaluated at all.

> **P19 — name, for each new tool, the one thing that tool would fail to notice,
> and write the check for it before pointing the tool at the object.**
> **Falsification: if the corrections chapter still splits better than
> three-to-one in favour of programs, the checks were already sufficient.**

**Implemented, and it is a required part of C34.** Every tool written this
session carries, in its docstring, a section headed *what this tool would not
notice*, and a check written against that blind spot **before** the tool was run
on the object. The blind spots are named in the clause.

**And P16 is still in force and is still not a clause.** `tools/rule0hook.py`
was registered in `.claude\settings.local.json` **before the first line of this
document** and its first live test was a `python -c` that it refused, at
`2026-09-09T23:12:28`. There is deliberately no clause about rule 0.

**And the standing rule from `pc-academagia-doc/docs/18` holds:** never quote a
percentage inside a clause; state the byte count and the denominator. Where a
percentage appears below it is a figure the pre-briefing published and the
clause is testing that publication.

---

## §A — the pre-briefing, which is worth zero points

**The object is a live installation, copied, and it is the first one anybody has
used.** `rpgvxace-steam\`, **2,026 files, 342,722,404 bytes, 45 directories of
which NONE is empty**, and **1,935 distinct sha1 over 2,026 files**.
`copyverify.py` closes on four axes: 2,026 of 2,026 on size, 2,026 of 2,026 on
mtime to the 100-nanosecond tick, 2,026 of 2,026 on sha1, and 45 directories
against 45 with 0 empty against 0. **RPG Maker VX Ace**, Steam app **220700**,
`Copyright (C) 2011 Enterbrain, Inc. / Yoji Ojima` in five version resources.
The **fifth** object of one product family and the second built on RGSS —
**RGSS3, Ruby 1.9.2**, where the previous object was RGSS1 and Ruby 1.8.1.
**VX is skipped deliberately**, on the owner's reasoning that VX Ace is VX's
definitive version; that is a scoping decision and not a measurement.

**It is 221.91 % of the previous object's files and 1,273.33 % of its bytes.**
The mean file is 169,162 bytes against 29,480.

**Eighty-four hashes appear more than once**, where the previous object had
none: 1,935 distinct + 91 repeats = 2,026. The 84 sort into four groups — 49
inside `dlc\Tyler Warren…`, 24 inside `Generator\`, 10 between `VLGothic\` and
`rtp\Fonts\VLGothic\`, and 1 in `Projects\`.

**The shop does not close, twice, and each residue names something.**
`SizeOnDisk` **342,514,066** against a counted tree of **342,722,404**, residue
**−208,338**; six installed depots summing **356,092,141**, residue
**−13,578,075**. The first is `Projects\cd32.zip` (208,185) + `Projects\cd32.ini`
(153); the second is depot **220708** (16,523,099) minus `RPGVXAceITA.dll`
(2,945,024). The six depots are **220701 / 62,332,617**, **220702 / 202,842,120**
= `rtp\` exactly, **220708 / 2,945,024 of 16,523,099**, **265461 / 57,491,682**,
**271961 / 15,516,018** and **291473 / 1,386,605**, and **`dlc\Bonus` at
9,357,289 is inside the base depot** — so the depot boundary is not a directory
boundary, which is the opposite of the previous object. Build id **19572675**,
`LastUpdated` **1760616017**, **`LastPlayed` 1774010264 and not `"0"`**,
`BytesToDownload` **321,169,744** against `BytesToStage` 342,514,066 — a ratio of
**1.0665**, the lowest in the family. `UserConfig` says `language "italian"`.

**And a second instrument partitions the same 2,026 files the same way without
being told.** `mtimes.py --waves`: wave 1, **2025-10-16 13:59:10 .. 13:59:55**,
**2,024 files, 342,514,066 bytes**; wave 2, **2026-03-20 13:37:42**, **2 files,
208,338 bytes**. **Wave 1's byte total is `SizeOnDisk` to the byte.**

**By directory**, 42 rows over 45 directories, none empty, with `rtp/Audio/BGM`
largest at 42 / 80,659,139. The six top-level subtrees are `rtp\` **780 /
202,842,120**, `dlc\` **476 / 83,751,594**, `Generator\` **508 / 17,016,940**,
`SampleMap\` **234 / 7,119,608**, `VLGothic\` **10 / 7,940,282**, `Projects\`
**8 / 2,749,418**, and the root **10 / 21,302,442**.

**By extension, nineteen rows** against the previous object's eleven, six of the
kinds new to this pipeline: `.png` 1,456 / 155,470,460; `.ogg` 363 /
119,011,030; `.mp3` 23 / 25,354,236; `.ttf` 4 / 15,795,408; `.dll` 6 /
7,722,320; `.exe` 2 / 7,085,056; `.chm` 1 / 6,633,819; `.bmp` 5 / 2,400,280;
**`.rvdata2` 117 / 2,248,383**; `.pdf` 2 / 402,773; `.txt` 27 / 220,549; `.zip`
1 / 208,185. **There is no `.mid` and no `.jpg` at all**, where the previous
object had 80 and 59.

**The coverage figure the box prints is 85.1928 %.** `coverage.py tree` reports
**1,957 files and 291,974,845 bytes specified, 1 file and 6,633,819 decoded, 0
derived, and 68 files and 44,113,740 bytes OPAQUE (12.8716 %)**, residue **0**.
The three magics the previous session added already carry all 117 `.rvdata2` and
all 363 Ogg. The 68 opaque are **23 MP3, 22 `.txt`, 6 extensionless, 5 BMP, 4
TTF, 4 `.mplus`, 2 `.sazanami`, 1 PDF and 1 ZIP**, and **one further file is
worse than opaque**: a 328,733-byte Japanese-titled PDF is filed **`specified` —
plain text, Shift-JIS**, because the cp932 probe read a PDF header and found
nothing illegal in it. The pre-briefing says four magics and an encoding probe
take the figure to **98.0644 %**.

**Entropy**: 2,026 files, 342,722,404 bytes, **5,916 of 6,528 blocks above
7.5**, nineteen rows, `.CHM` highest at **7.9981** and **`.RVDATA2` lowest at
2.0714 with 0 blocks above 7.5**.

**Eight binaries, all PE32, all linker 9.00**, where the previous object had
four across two linker versions: `RPGVXAce.exe` 6,944,256 / **2014-03-05
06:17:58**; `RPGVXAceITA.dll` 2,945,024 / **2014-03-06 01:32:17**;
`RPGVXAceENU.dll` 2,917,888 / **2014-03-06 01:34:27**; `RGSS301.dll` 1,085,952 /
**2012-02-22 00:14:13**; `SciLexer.dll` 545,280 / **2011-01-03 02:33:26**;
`Projects/Game.exe` 140,800 / **2011-10-06 04:40:34**; `steam_api64.dll` 121,256
and `steam_api.dll` 106,920 / **2013-11-21**. `stampcheck.py` reports **0 of 8
false on all three tests — its second silent run**. `sigcount.py --hex
4d5a5000` gives **0 of 2,026**. `mzcensus.py`, **twelfth appearance**, finds 2
of 8 and misses six DLLs totalling 7,722,320 bytes.

**Six version resources of eight**, and three are findings. `RGSS301.dll` **has**
one where `RGSS104E.dll` had none, and its `ProductName` reads **`Ruby Game
Scripting System`** in a linker-written field. **The Italian DLL declares itself
English**: `InternalName` is **`LangENU`** on both language DLLs, the Italian one
carries **no `LegalCopyright`**, and its `FileVersion` is **`1, 0, 2, 2`** against
the English one's **`1, 0, 3, 0s`** — a version ending in a letter. And Valve's
two DLLs name Valve's build machines, **`winslave04`** and **`winslave05`**, in a
`FileDescription`. `SciLexer.dll` is **Scintilla 2.22, Copyright 1998-2010 by
Neil Hodgson**, against the previous object's 1.58 of 1998-2003.

**`RGSS301.dll` exports 27 functions, 27 by name, 0 forwarded**, against the
previous object's **66** — whose 66 were 23 `RGSS*` plus **43 names of Ruby's
regular-expression engine**, of which RGSS3 exports none. `RGSSInitialize`
became **`RGSSInitialize3`**, **`RGSSSetupFonts`** is new, and the string
accessors gained **UTF-16** forms. It imports **12 DLLs and 14 names**, including
**`ws2_32.dll #116`** where the previous object imported **`#55`**, and
**`advapi32!GetUserNameW`**.

**`RPGVXAce.exe` has five sections and the fifth is `.bind`, 562,176 bytes raw —
exactly the size of `RPGXP.exe`'s.** `bindcmp.py`: not identical, **9,549 bytes
equal of 562,176**, **first differing byte 768**, **longest identical run 6,084
bytes at offset 809**. Both begin `55 8b ec 5d c3` and both compare against `MZ`
and `PE\0\0` in their first sixty-four bytes. The previous session refused to
attribute it because `steam`, `valve` and `SteamStub` occur zero times in that
file.

**The `.chm` is the fifth ITSF specimen and opens unchanged**: version 3, header
length 96, **nine closures at residue 0**, 4 chunks tagged `PMGL PMGL PMGL
PMGI`, **356 listing entries**, 3 index entries, 0 refusals, **226 reset
blocks**, compressed 6,610,974 and uncompressed **7,398,317, stated twice**.
`chmx.py check` produces **7,398,317 bytes at residue 0**, **339 of 339** entries
inside the output and **172 of 172** HTML entries beginning with `<`; `extract`
writes **340 files, 7,358,681 bytes**. Inside: **/rgss/ 119 HTML of which 82 are
class pages**, **/rpgvxace/ 53**, **img/ 151 PNG**, `RGSS3` occurring **77
times**. Compiled **2012-03-12 17:20:34 UTC**, title `RPG MAKER VX Ace`,
compiler **`HHA Version 4.74.8702`** — the same compiler build as all four
earlier specimens.

**And the fifth specimen answers the previous object's open question by
sharpening it.** `chmclocks.py` over five containers: `RPGVXAce.chm` header
**0x0411**, code-4 0x0409, hdr-vs-c4 **0.062428**, code10−code4 **61,207.891813
= 17 h + 7.891813 s**; `RPGXP.chm` **0x0411** and **16 h + 3.953125 s**;
`rpg2003.chm` 0x0C07 and 17.478706 s; `rpg2000.chm` 0x0C07 and 8.443916 s;
`SLPEI.chm` 0x0407 and 8.157558 s. **The two specimens with a Japanese header
LCID are the only two with a whole-hour term, 2 of 2 against 0 of 3 — and the
number of hours is not the same, so a fixed zone bias is dead.**

**1,456 PNG close 1,456 times**, **14,035 of 14,035 CRC-32 verifying**, five
IHDR shapes and **310 files interlaced** — the first interlaced PNG in this
collection. **363 Ogg close 363 times**, **28,585 of 28,585 page CRC**, and
**363 of 363 flag end-of-stream**, where the previous object had 199 of 200 —
which makes that object's one exception a file's defect and not the encoder's.
Channels `{1: 284, 2: 79}`, rates `{22050: 260, 44100: 102, 32000: 1}`, total
**5,522.628 s**.

**The 117 `.rvdata2` all begin `04 08`** — the same Marshal 4.8 as the previous
object's `.rxdata` — and `_work/rvprobe.py` walks all 117 and **lands on the
last byte 117 of 117**, root objects `{'RPG::Map': 117}`, 0 failures. The type
bytes over every value are `'i' 2585, 'F' 1323, '"' 996, 'o' 764, 'T' 729,
**'I' 466**, '[' 412, '{' 117, 'u' 117`, total 7,509. **`I` appeared ZERO times
in the whole of the previous object**: it is Ruby 1.9's encoding-tagged String.
**Eleven classes**: `RPG::Map` 117 with 24 ivars, `RPG::BGM` 117, `RPG::BGS`
117, `Table` 117, and **`RPG::Event`, `RPG::Event::Page`,
`RPG::Event::Page::Condition`, `RPG::Event::Page::Graphic`,
`RPG::EventCommand`, `RPG::MoveCommand` and `RPG::MoveRoute` at 59 each** — six
of which `pc-rpgmakerxp-doc/docs/06` listed as documented and never
instantiated. **68 distinct ivar names, 75 class/field slots.**

**And `marshal48.py`, `rgssdb.py` and `rxscripts.py` refuse this object**, because
they select files by the literal extension `.rxdata`. `coverage.py`, which
selects by magic, gets all 117 right.

**`rtp\Graphics\Tilesets\` holds 22 `.png` and 22 `.txt`**, the stems joining at
**22 with none on either side alone**, **2,544 rows, 0 blank lines, fields per
row `{5: 2544}`** — **12,720 strings** in **English, Japanese, French, German and
Spanish**, the first row of `World_A2.txt` being
`Grassland|草原|Prairie|Wiese|Prado`. **They are filed OPAQUE because they are
UTF-8**, and the probe tests ASCII and cp932. `textprobe.py`: **34 opaque files
are text**, `{'utf-8': 28, 'euc_jp': 6}`.

**Three version-1 UUIDs in 2 files**, against the previous object's 33 in 9 —
two being the ITSF LZX transform GUID and one the 1996 class identifier in the
editor. **Not one Adobe XMP identifier in 1,456 PNG.**

**`sift.py --group personal` reports 19 e-mail shapes in 11 blobs**, where the
previous object had 0 at eight bits and 1 at sixteen; `utf16sift.py` reports
**17 hits only a sixteen-bit pass finds**; `sift.py --group buildpath` reports
**3 hits in 3 files**. Eight of the nineteen are one Japanese open-source font
project's licence set shipped twice, three are three resource packs' readmes,
**and all of them are third parties'**.

**`namescan.py`**: `Kadokawa` **0 of 2,026** in both encodings for the second
object running; `Enterbrain` 24 at eight bits + 17 at UTF-16 in 5 files;
`Degica` 4 in 4; **`Yoji Ojima` 9, UTF-16 only**; **`Yukihiro Matsumoto` 1,
UTF-16 only, `Copyright (C) 1993-2010`**; **`Neil Hodgson` 3, UTF-16 only**;
`Tyler Warren` 8 in 1 file at eight bits. The editor's About block reads
**`Ruby Version 1.9.2`** and **`Scintilla Version 2.22`**.

**`VXAce_install.vdf` is 2,041 bytes** and writes
`HKEY_LOCAL_MACHINE\Software\Enterbrain\RPGVXAce` and
`…\Enterbrain\`**`RGSS3`**`\RTP`, registering **`.rvproj2`, `.rvdata2` and
`.rgss3a`** of which the object ships only the second — **the third product in a
row to register an encrypted archive it does not ship.**

**Four packs of downloadable content by three named third parties**:
`AdventurersJourney_SND` 47 files / 57,491,682, **23 MP3 and 23 OGG**;
`Tyler Warren RPG Battlers 1st 50` 320 / 15,516,018, fifty battlers at five
sizes plus a `Recommended Sizes` set that is `280 Large` copied; `dlc\Bonus` 97
/ 9,357,289 with a preorder EULA dated **Mar. 14th, 2012** that misspells
*Bonus* as **`Bouns`**; `RoyalTileset_GFX` 12 / 1,386,605 dated **2014.05.22**.
**`VLGothic\` and `rtp\Fonts\VLGothic\` hold the same ten files twice** — two
TrueType faces and eight licence documents in UTF-8 and EUC-JP.

**`Projects\` is eight files and 2,749,418 bytes**, six of them the editor's own
template — `Game.exe` 140,800, `game.bmp` 480,056 and four `RMworkshop_0N.bmp`
of which `_01` is byte-identical to `game.bmp` — **and two of them the owner's**:
`cd32.ini` at 153 bytes and `cd32.zip` at 208,185. `cd32.ini` is a `Game.ini`
carrying `RTP=RPGVXAce`, `Library=System\RGSS301.dll`,
`Scripts=Data\Scripts.rvdata2` and `Title=CD32`. **The owner has said these may
be cited without going into detail.**

**`crossall.py` reports 26 crossings of 1,935 distinct sha1** over 106
repositories, 473 list files and 159,482 hash tokens, **all 26 with
`pc-rpgmakerxp-doc` and none with anything else** — **22 Ogg sound effects and 4
ambiences**, whose names changed: `001-System01.ogg` became `Load.ogg`. The
collection's six rates are 1 of 12, 10 of 962, 0 of 477, 368 of 731, 0 of 913
and 26 of 1,935.

**`refusals.py` reports 85 readers pointed**, `refusalclass.py` splitting them
`argparse` **23 for the sixth time**, `oserror` 16, `format` 12, `exception` 1.
**`hashall.py` crashes with `UnicodeEncodeError` without `PYTHONIOENCODING`**, on
a Japanese file name — the first object in this collection with one.
`dirguard.py --survey` found **216 of 557** tools letting a traceback reach the
user on the previous object. **`toolsdiff.py` reports 558 common and 0
differing**, the box being `pc-rpgmakerxp-doc/tools/` copied whole; **twenty-six
tools of 558 were run in the pre-briefing**, which is 4.6595 % of the box.

**The carried defects and their counts**: `namecensus.py` twenty-third,
`dircensus.py` twenty-fourth, `protscan.py` nineteenth, `mzcensus.py` twelfth,
`kfaccount.py` seventh, `refusals.py` sixth, `jstore.py` sixth object,
`ispkg.py` fourth, `buildroot.py` third, `pdbpaths.py` third, `coverage.py`
third **and first as a wrong answer rather than an omission**, `oggtime.py`
second, and **first appearances for `marshal48.py`, `rgssdb.py`, `rxscripts.py`,
`hashall.py` and `depotsplit.py`**.

---

## §B — the calibration series, re-derived

```
python _work/calib3.py                       (notes/calibration.txt)

terms    : 36
sum      : -31.2700
mean     : -0.8686
negative : 24   positive : 11   zero : 1
last10   : -43.4300   mean -4.3430
tail run of consecutive negatives : 5
the last term -5.86 ranks 11 of 36 by absolute value

the brief's eight claims about the series, one at a time : 0 wrong
```

**All eight are right.** The tail run is five, the last ten average −4.3430, and
`pc-rpgmakerxp-doc/docs/17` decomposed the last term as **−2.60 over the five
P12 clauses and −3.26 over the other twenty-six** — the smallest per-clause
residue that band has taken since P12 came into force.

**So this document is priced under two instructions that pull apart.** The
eleven `constructs` clauses P12 does not govern are priced **up**, to a mean of
**0.86** against last session's whole-band 0.6908, because P18 says the band
beat its price five times in six. The five P12 clauses are priced at a mean of
**0.49**, because each asks for something this document does not expect to get.
**The inherited band is priced at a mean near 0.93**, and it is not higher
because P15's three-part test is still in force and **the pre-briefing declares
four of its own statements unverified** — the depot mapping, the count of opaque
text files, the DLC sum against the three depots, and the claim that all 26
crossings are Ogg. Those four are C04, C29, C04 again and C30, and they are
priced below the band.

---

## §C — P17's register: the eight figures whose truth depends on when the command runs

**Every command in this table was run before this document's first clause was
written.** The output is the file named, committed as it came.

| the figure | the state it describes | the file | run at |
|---|---|---|---|
| `toolsdiff.py --expect-differing 0` → **558 / 0** | the box before this session writes a tool | `notes/toolsdiff-before.txt` | 21:12:44 UTC |
| `toolscan.py` → **558 files, 0 forbidden bytes** | the same | `notes/toolscan-before.txt` | 21:13 UTC |
| `dirguard.py --survey` → **216 raised of 557** | the box before any guard is added | `notes/dirguard-survey-before.txt` | 21:13 UTC |
| `coverage.py tree` → **85.1928 %, 68 opaque** | the classifier before four magics | `notes/coverage-tree-before.txt` | 21:14 UTC |
| `refusals.py` + `refusalclass.py` | the readers before three are repaired | `notes/refusals-before.txt`, `notes/refusalclass-before.txt` | 21:14 UTC |
| `rowlen.py` → **78 rows, 0 over budget** | the index before this session adds a row | `notes/rowlen-before.txt` | 21:13 UTC |
| `ls -1d ../*-doc/` → **136**, `../pc-*-doc/` → **67** | the collection including this directory | in C30 | 21:15 UTC |
| `rule0hook.py --report` | a running count that only grows | `notes/rule0.txt` | continuous |

**And the register earned its place on the first row it checked.** The brief
publishes `refusals.py` at **52 of 85** with `exception` **1**. Run here it
reports **54 of 85** with `exception` **3**. The difference is not the object
and is not the moment: it is **`PYTHONIOENCODING`**. With it set the count is 52;
with it unset, `unityfs.py` and `unityarc.py` die of `UnicodeEncodeError` on the
same Japanese file name that kills `hashall.py`. **A figure the brief attributes
to the object is a figure about an environment variable**, and that is C31 and
C59.

---

## §D — the clauses

### Inherited — re-testing the pre-briefing's own figures

*Each of the thirty-three below is P15's three-part test: **the named command is
run; its output is reported; and where the output disagrees with the figure this
clause names, the disagreement is recorded as a correction against the
pre-briefing rather than smoothed over.** The tolerance is stated once and
governs all thirty-three: exact equality for file counts, byte counts, instance
counts and timestamps; **±1 in the last published decimal** for percentages,
means and durations; and where the pre-briefing states a figure in prose rather
than as tool output, the tool's output wins.*

**C01** `content` `inherited` — `copyverify.py` re-run against the live source
closes on **four axes**: **2,026 source files and 2,026 copied**, 2,026 of 2,026
on size, 2,026 of 2,026 on mtime to the 100-nanosecond tick, 2,026 of 2,026 on
sha1, **45 directories against 45** and **0 empty against 0**, with a single
final agreement of `True`. *Predicted: 0.96*

**C02** `content` `inherited` — `hashall.py` reports **2,026 files, 342,722,404
bytes, 1,935 distinct sha1 and 0 unreadable**; **1,935 + 91 = 2,026 at residue
0**; **84 hashes appear more than once**; and the byte total is re-derived by a
command that is not `hashall.py`. *Predicted: 0.94*

**C03** `content` `inherited` — `steamacf.py --check` on
`appmanifest_220700.acf` reports `SizeOnDisk` **342,514,066** against a counted
tree of **342,722,404** at residue **−208,338**; six installed depots
**220701 / 62,332,617**, **220702 / 202,842,120**, **220708 / 16,523,099**,
**265461 / 57,491,682**, **271961 / 15,516,018** and **291473 / 1,386,605**
summing to **356,092,141** at residue **−13,578,075**; build id **19572675**;
`LastUpdated` **1760616017**; **`LastPlayed` 1774010264, which is not `"0"` and
is the first such in this collection**; `BytesToDownload` **321,169,744**;
`UserConfig` `language "italian"`; and `LastOwner` redacted by the program
without this session touching it. *Predicted: 0.93*

**C04** `content` `inherited` — **the depot mapping and the DLC sum, which are
two of the four claims the pre-briefing made once and never checked**: walking
the tree gives `rtp\` at **202,842,120** = depot 220702 exactly,
`dlc\AdventurersJourney_SND` at **57,491,682** = 265461,
`dlc\Tyler Warren RPG Battlers 1st 50` at **15,516,018** = 271961,
`dlc\RoyalTileset_GFX` at **1,386,605** = 291473, **`dlc\Bonus` at 9,357,289
matching no depot and therefore inside 220701**, and everything else except the
Italian DLL and the owner's two files at **62,332,617** = 220701 — every figure
produced by walking and not by subtracting one published number from another,
and the four DLC directories summing to **83,751,594** against the three DLC
depots' **74,394,305**, a difference of **9,357,289** which is `dlc\Bonus`.
*Predicted: 0.86*

**C05** `content` `inherited` — the **−208,338** residue is exactly
`Projects\cd32.zip` at **208,185** plus `Projects\cd32.ini` at **153**, both
sizes taken from the tree and not from the brief, and 208,185 + 153 = 208,338 at
residue 0. *Predicted: 0.95*

**C06** `content` `inherited` — the **−13,578,075** residue is exactly depot
220708's declared **16,523,099** minus `RPGVXAceITA.dll`'s **2,945,024**, and
**no other file in the tree belongs to that depot**, which is checked by
subtracting rather than asserted. *Predicted: 0.90*

**C07** `content` `inherited` — `mtimes.py --waves` reports **two waves**: wave 1
from **2025-10-16 13:59:10 to 13:59:55** carrying **2,024 files and 342,514,066
bytes**, and wave 2 at **2026-03-20 13:37:42** carrying **2 files and 208,338
bytes**; **wave 1's byte total equals `SizeOnDisk` to the byte** and wave 2's two
files are the two files of C05, with the equality checked and not assumed.
*Predicted: 0.93*

**C08** `content` `inherited` — the by-directory census carries **42 rows over 45
directories of which 0 are empty**, the file counts summing to **2,026** and the
bytes to **342,722,404**; the seven top-level totals are `rtp\` **780 /
202,842,120**, `dlc\` **476 / 83,751,594**, `Generator\` **508 / 17,016,940**,
`SampleMap\` **234 / 7,119,608**, `VLGothic\` **10 / 7,940,282**, `Projects\`
**8 / 2,749,418** and the root **10 / 21,302,442**, summing to 2,026 and
342,722,404 at residue 0; **and every four-decimal percentage the pre-briefing
publishes for those rows is recomputed in exact decimal**, because five of
twenty-five were wrong last session and only an exact recomputation caught them.
*Predicted: 0.88*

**C09** `content` `inherited` — the by-extension census carries **nineteen
rows** summing to **2,026** files and **342,722,404** bytes, with `.png`
**1,456 / 155,470,460**, `.ogg` **363 / 119,011,030**, `.mp3` **23 /
25,354,236**, `.ttf` **4 / 15,795,408** and **`.rvdata2` 117 / 2,248,383**, and
**no `.mid` and no `.jpg` at all**. *Predicted: 0.93*

**C10** `content` `inherited` — **P17 clause; the command was run before this
document and its output is `notes/coverage-tree-before.txt`.** `coverage.py
tree` **as the box stood on arrival** prints **1,957 files and 291,974,845 bytes
specified, 1 file and 6,633,819 decoded, 0 derived, and 68 files and 44,113,740
opaque**, residue **0**; and **one of the 1,957 is the 328,733-byte PDF filed as
`plain text, Shift-JIS`**, which is visible in that same output. *Predicted: 0.95*

**C11** `content` `inherited` — `entropy.py --tree --by-ext` reports **2,026
files, 342,722,404 bytes and 5,916 of 6,528 blocks above 7.5**, in **nineteen
rows**, with `.CHM` highest at **7.9981** and **`.RVDATA2` lowest at 2.0714 with
0 blocks above 7.5** — lower than the previous object's `.RXDATA` at 3.8587.
*Predicted: 0.91*

**C12** `content` `inherited` — `pecensus.py --by-magic` reports **8 binaries,
PE32 8, NE 0**, all found by magic, `impossible mtimes : 0 of 8`, **all eight at
linker 9.00**, and the eight byte counts and eight COFF stamps exactly as §A
lists them — including the two Valve DLLs **65 seconds apart** and the two
language DLLs **130 seconds apart**, both intervals computed and not quoted.
*Predicted: 0.92*

**C13** `content` `inherited` — `stampcheck.py` reports **T1 impossible 0 of 8,
T2 colliding 0 of 8, T3 round 0 of 8 and FALSE by at least one test 0 of 8**,
its **second silent run**, on twice the previous population; and the chapter
reports it as a negative control and not as a finding. *Predicted: 0.94*

**C14** `content` `inherited` — `verres.py dump` reports **6 version resources
over 8 PE**, with `RGSS301.dll` at `ProductName` **`Ruby Game Scripting
System`** and `FileDescription` **`RGSS3 Core`**; `RPGVXAce.exe` at
`FileVersion` **`1, 0, 2, 2`** and `LegalCopyright` **`Copyright (C) 2011
Enterbrain, Inc. / Yoji Ojima`**; `RPGVXAceENU.dll` at `FileVersion`
**`1, 0, 3, 0s`** and `InternalName` **`LangENU`**; **`RPGVXAceITA.dll` at
`FileVersion` `1, 0, 2, 2`, `InternalName` `LangENU` and no `LegalCopyright` at
all**; `SciLexer.dll` at **2.22** and `Copyright 1998-2010 by Neil Hodgson`; and
the two Valve DLLs naming **`winslave04`** and **`winslave05`**. *Predicted: 0.92*

**C15** `content` `inherited` — `mzcensus.py`, **twelfth appearance**, reports
**2 of 8**, and the six it misses are the six DLLs totalling **7,722,320
bytes**, because it filters on the `.EXE` extension where a magic exists.
*Predicted: 0.94*

**C16** `content` `inherited` — `sigcount.py --hex 4d5a5000` reports **0 of
2,026**: no `MZP` stub anywhere, at offset 0 or elsewhere. *Predicted: 0.95*

**C17** `content` `inherited` — `peimpexp.py RGSS301.dll --exports` reports **27
functions, 27 by name, 0 forwarded**, including `RGSSInitialize3`,
`RGSSSetupFonts`, `RGSSGetSymbol` and the **three UTF-16 string accessors**;
`--imports` reports **12 DLLs and 14 names**, including **`ws2_32.dll` imported
by ordinal `#116`** and **`advapi32!GetUserNameW`**; and the 27-against-66
difference is reported with the previous object's **43 regular-expression
names** named as the part that vanished. *Predicted: 0.90*

**C18** `content` `inherited` — `itsf.py header|list|internals` on
`RPGVXAce.chm` reports **version 3, header length 96, nine closures at residue
0**, **4 chunks tagged `PMGL PMGL PMGL PMGI`**, **356 listing entries**, **3
index entries**, **0 refusals**, a ResetTable of **40 + 226 × 8 = 1,848**, LZXC
compressed **6,610,974** and uncompressed **7,398,317 stated twice**, compile
clock **2012-03-12 17:20:34 UTC**, title `RPG MAKER VX Ace` and compiler
**`HHA Version 4.74.8702`** — **with no change to the tool**. *Predicted: 0.91*

**C19** `content` `inherited` — `chmx.py check` produces **7,398,317 bytes at
residue 0**, **339 of 339** section-1 entries lying inside the output and **172
of 172** `.html` entries whose first 400 bytes contain `<`; `chmx.py extract`
writes **340 files and 7,358,681 bytes**; and `lzx.py` decodes a stream
**nineteen times larger with 226 reset blocks instead of 26** without a
modification. *Predicted: 0.92*

**C20** `content` `inherited` — `chmclocks.py` over **five specimens** reports
`RPGVXAce.chm` header **0x0411**, code-4 **0x0409**, hdr-vs-c4 **0.062428 s**
and code10−code4 **61,207.891813 s = 17 h + 7.891813 s**, beside `RPGXP.chm`'s
**16 h + 3.953125 s**, `rpg2003.chm`'s **17.478706**, `rpg2000.chm`'s
**8.443916** and `SLPEI.chm`'s **8.157558**; and **the header-`u32` pairing
holds a fifth time**. *Predicted: 0.92*

**C21** `content` `inherited` — `pngcensus.py --by-dir` reports **1,456 parsed
of 1,456, 0 refused, 1,456 closing at residue 0**, **14,035 chunks walked and
14,035 of 14,035 CRC-32 verifying**, and **five IHDR shapes** of which
**310 files are interlaced** — depth 8 colour 2 × 37, colour 3 × 194, colour 4 ×
1, colour 6 non-interlaced × 914 and colour 6 interlaced × 310, summing to
1,456. *Predicted: 0.92*

**C22** `content` `inherited` — `oggcensus.py census` reports **363 parsed of
363**, **363 closing at residue 0**, **28,585 pages walked and 28,585 of 28,585
CRC-32 verifying**, **363 of 363 flagging end-of-stream**, channels
`{1: 284, 2: 79}`, rates `{22050: 260, 44100: 102, 32000: 1}` and a total
playing time of **5,522.628 s**; and the chapter states that this makes the
previous object's single flagless stream a defect of one file rather than of the
encoder. *Predicted: 0.92*

**C23** `content` `inherited` — `uuidscan.py` reports **3 version-1 UUIDs in 2
files** with **2 distinct node fields**, two of them in `RPGVXAce.chm` dated
**1997-03-15 12:41:51.615828** and one in `RPGVXAce.exe` dated **1996-07-08
20:31:25.984376**, node fields redacted by the program — against the previous
object's 33 in 9 files — **and there is not one Adobe XMP identifier in the
1,456 PNG**, which is checked rather than assumed. *Predicted: 0.90*

**C24** `content` `inherited` — `sift.py --group personal` reports **19 e-mail
shapes in 11 blobs** with its positive control firing and its negative control
quiet; `sift.py --group buildpath` reports **3 hits in 3 files**; and
`utf16sift.py` reports **17 hits that only a sixteen-bit pass finds**.
*Predicted: 0.92*

**C25** `content` `inherited` — **the absence of Kadokawa, which is the third of
the four claims the pre-briefing made once**: `namescan.py` reports `Kadokawa`
**0 of 2,026 in both encodings**, `Enterbrain` **24 at eight bits and 17 at
UTF-16 in 5 files**, `Degica` **4 in 4**, **`Yoji Ojima` 9 and UTF-16 only**,
**`Yukihiro Matsumoto` 1 and UTF-16 only**, **`Neil Hodgson` 3 and UTF-16
only**, `Tyler Warren` **8 in 1 file at eight bits**, and the editor's About
block reading **`Ruby Version 1.9.2`** and **`Scintilla Version 2.22`**.
*Predicted: 0.91*

**C26** `content` `inherited` — the walk over the 117 `.rvdata2` reports **117
files, 2,248,383 bytes, the walk landing on the last byte 117 of 117, 0
failures** and root objects **`{'RPG::Map': 117}`**; and the type-byte census
reports **`'i' 2585, 'F' 1323, '"' 996, 'o' 764, 'T' 729, 'I' 466, '[' 412,
'{' 117, 'u' 117`, totalling 7,509**, with **`I` at 466 against the previous
object's zero** identified as Ruby 1.9's encoding-tagged String. *Predicted: 0.91*

**C27** `content` `inherited` — the class census reports **11 distinct classes**
with `RPG::Map` **117 instances and 24 distinct ivars**, `RPG::BGM` **117 / 3**,
`RPG::BGS` **117 / 3**, `Table` **117 / 0**, and **`RPG::Event`,
`RPG::Event::Page`, `RPG::Event::Page::Condition`, `RPG::Event::Page::Graphic`,
`RPG::EventCommand`, `RPG::MoveCommand` and `RPG::MoveRoute` at 59 instances
each**; **68 distinct instance-variable names and 75 class/field slots**; and
`pc-rpgmakerxp-doc/docs/06` is re-read in the original to confirm that **six of
those seven were named there as documented and never instantiated**.
*Predicted: 0.89*

**C28** `content` `inherited` — `tilenames.py` reports **22 `.txt` and 22
`.png`** in `rtp\Graphics\Tilesets\`, **22 stems in both with none only-`.txt`
and none only-`.png`**, **2,544 total rows, 0 blank lines**, **fields per row
`{5: 2544}`** and **2,544 of 2,544 rows with exactly five fields**; and the first
row of `World_A2.txt` is `Grassland|草原|Prairie|Wiese|Prado`. *Predicted: 0.93*

**C29** `content` `inherited` — **the count of opaque text files, which is the
fourth claim the pre-briefing made once and which its own two files disagree
about**: `opaque.py` reports **68 files and 44,113,740 bytes** split
`.mp3` 23 / 25,354,236, `.txt` 22 / 202,479, none 6 / 55,482, `.bmp` 5 /
2,400,280, `.ttf` 4 / 15,795,408, `.mplus` 4 / 8,882, `.sazanami` 2 / 14,748,
`.pdf` 1 / 74,040 and `.zip` 1 / 208,185 — nine groups summing to 68 and to
44,113,740 at residue 0 — while `textprobe.py` reports **34 opaque files are
text**, `{'utf-8': 28, 'euc_jp': 6}`; **and 22 + 6 + 4 + 2 = 34 while the
extension table shows `.mplus` at 4 in one file and 6 in another**, so one of the
two published tables is wrong and the chapter says which. *Predicted: 0.84*

**C30** `content` `inherited` — **the claim that all twenty-six crossings are
Ogg**: `crossall.py --skip pc-rpgmakervxace-doc` reports **26 crossings of 1,935
distinct sha1**, all with `pc-rpgmakerxp-doc` and none with any of the other 105
repositories, at the three thresholds **26 / 26 / 6**; the twenty-six are named
one at a time and their formats counted **by magic and not by extension**, giving
**22 in `rtp/Audio/SE` and 4 in `rtp/Audio/BGS`**; and the five denominators —
**136** `-doc`, **67** `pc-*-doc`, **106** repositories swept, **473** list files,
**159,482** hash tokens — are re-derived, the first two with `ls` **before** the
sweep. *Predicted: 0.86*

**C31** `content` `inherited` — **P17 clause; the commands were run before this
document and their output is `notes/refusals-before.txt` and
`notes/refusalclass-before.txt`.** `refusals.py` points **85 readers**, and
`refusalclass.py` splits the refusals with **`argparse` at 23 for the sixth
time** over six populations and three objects, **`oserror` 16** and **`format`
12** — the twelve including `marshal48.py`, `rgssdb.py` and `rxscripts.py`
refusing on an extension; **and the refusal total is NOT the 52 the brief
publishes but depends on `PYTHONIOENCODING`**, being 52 with it set and 54
without, the two extra being `unityfs.py` and `unityarc.py` dying on a Japanese
file name. *Predicted: 0.88*

**C32** `content` `inherited` — the four counted carried defects fire again and
are reported with their ordinals: `namecensus.py` **`ZeroDivisionError`,
twenty-third**; `dircensus.py` **a complete formatted table over zero containers
with exit 0, twenty-fourth**; `protscan.py` **eleven pre-2010 optical markers at
a Steam download, 0 hits, control firing, nineteenth**; `kfaccount.py` **exit 0
printing its usage because no argument selects an action, seventh**.
*Predicted: 0.93*

**C33** `content` `inherited` — `calib3.py` re-derives the series by summing and
confirms **36 terms, sum −31.27, mean −0.8686, 24 negative and 1 zero, last ten
−43.43 for a mean of −4.3430, and a tail run of 5** — **eight claims checked one
at a time**, with any wrong one named. *Predicted: 0.94*

---

### Open, method

**C34** `method` `open` — every tool written this session has its name checked
against `tools/` before it is written; **every file-selecting tool selects by
magic and not by extension**; every reader gets `dirguard.py`'s guard; every
selftest is run **at least once with `PYTHONIOENCODING` unset**; **and P19 is
obeyed literally** — each new tool's docstring carries a section naming *the one
thing this tool would not notice*, and the check for that blind spot is written
**before** the tool is pointed at the object. The blind spots named in advance
are: for the magic table, **that a text codec accepting a binary header is not
an error the table can see, which is why the PDF was filed as Japanese**; for
the tileset reader, **that a five-field row count cannot tell a translated
string from a copied one**; for the map reader, **that a walk landing on the
last byte says nothing about whether the values were interpreted correctly**;
and for the name-encoding guard, **that a tool which prints nothing cannot
crash, so a silent tool is not evidence the guard works**. *Predicted: 0.90*

**C35** `method` `open` — every chapter opens with `*Measure: …*` naming the
commands that produce its figures; `docs/02` carries a command on every row;
`docs/01` states **what the object is, which denominator each figure uses, and
the coverage before and after**, tabulating **all eight denominators** with the
second — that the shop believes the tree weighs 342,514,066 bytes and it weighs
342,722,404 — named explicitly. *Predicted: 0.92*

**C36** `method` `open` — `pathcheck.py` over every tracked file reports **0
violations with its positive control firing and its negative control quiet**,
after being run **while the rule-0 log exists**, since that log is a record of
commands beginning `cd "<the project root>"` and caught three real violations
last session; and third parties' paths — Microsoft's `f:\dd\vctools\…`, Valve's
`winslave04` — are published as findings and named as such. *Predicted: 0.89*

**C37** `method` `open` — the repository is published on branch **`master`**
under `vs-sr-dev` with `git ls-files | grep -Eiv "^(README|docs/|notes/|tools/|
\.gitignore)"` **empty and a positive control that fires**, a description under
350 characters **read back from the remote and not from the command that set
it**, topics set, and **`rpgvxace-steam\`, `_pre\`, `_work\`, `prompt.txt`,
`.claude\` and `tools/__pycache__` absent from `git ls-files`**; and
`pc-gamelist-doc` is modified and pushed on **`main`**. *Predicted: 0.90*

**C38** `method` `open` — the repository is **under twenty documents**, and **no
chapter is a census of a resource family for its own sake**: the PNG, Ogg, MP3
and font figures appear as rows of `docs/02` and as evidence inside chapters
that make an argument, and the chapter count is justified in `docs/01` against
the previous ten sessions' 20, 17, 18, 19, 17, 16, 16, 16, 17 and 18.
*Predicted: 0.91*

---

### Open, content

*The five clauses P12 governs are named here in advance: **C43, C48, C52, C55
and C59**. Each asks for the strongest thing the object could conceivably
support and each is priced below 0.60. Every other open content clause is
priced at what this document actually expects.*

**C39** `content` `open` `lands` — **before any other work**, `coverage.py`
gains **four magics and an encoding probe** — MPEG audio with ID3, sfnt
(`00 01 00 00`, **distinguished from the Windows icon's `00 00 01 00` by a check
that must fail if they are swapped**), `BM`, `%PDF` and `PK\003\004`, plus UTF-8
and EUC-JP — **with binary signatures tested before text codecs**, and the tree
then reports **0 files and 0 bytes opaque at residue 0**, with **at least ten new
checks of which at least four assert a refusal or a misclassification**.
*Predicted: 0.90*

**C40** `content` `open` `lands` — **the misfiled PDF is fixed and the fix is
verified by a check that fails on the old ordering**: the 328,733-byte file is
reported as **`%PDF`** and not as Shift-JIS text, the check that proves it is
named, and the chapter states in three sentences that this is the **third**
appearance of `coverage.py`'s magic-table defect and its **first as a confident
wrong answer rather than an omission** — a different and worse failure than
silence. *Predicted: 0.88*

**C41** `content` `open` `constructs` — `marshal48.py`, `rgssdb.py` and
`rxscripts.py` are repaired to select files **by magic** rather than by a longer
list of extensions, the repair is the same shape in all three, and
`marshal48.py walk rpgvxace-steam/SampleMap` then reports **117 files walking to
the last byte**; **and the chapter states that this is `mzcensus.py`'s
eleven-appearance defect inside three tools that are one session old**, with the
`format` count of `refusalclass.py` re-run afterwards to show the three moving
out of it. *Predicted: 0.88*

**C42** `content` `open` `constructs` — the 117 maps are read rather than
walked: **every one of the 24 `RPG::Map` ivars is named**, the **117 `Table`
payloads are decoded to their dimensions and cell counts** with the byte
arithmetic closing at residue 0 on every file, and the map grids' **width ×
height × 3 layers** is checked against each `Table`'s own declared element count.
*Predicted: 0.88*

**C43** `content` `open` `constructs` — **the map grids join to the tileset
tables.** Each map names a tileset id; each tileset table holds five-language
names for its tiles; and **the tile ids the 117 maps actually use are resolved to
names through those 2,544 rows**, giving a count of distinct tiles used against
distinct tiles published, in a join whose residue is reported and whose
unmatched ids on both sides are named. **Nothing in this pipeline has joined two
of an object's own formats to each other before.** *Predicted: 0.45*

**C44** `content` `open` `constructs` — the 22 tileset tables are read in full:
**2,544 rows × 5 fields = 12,720 strings**, counted; the **five languages
identified by codepoint range and not by position**; the number of rows where
two or more language fields are **byte-identical** counted and explained; and the
**absence of Italian** stated beside the fact that the interface this
installation runs in is Italian, without inventing a reason for it.
*Predicted: 0.87*

**C45** `content` `open` `constructs` — the **59 events** are read: how many of
the 117 maps carry events and how many carry none, the distribution of events
per map, the **59 `RPG::EventCommand`** instances resolved to their command
codes, and the six classes `pc-rpgmakerxp-doc/docs/06` named as documented and
never instantiated shown **instantiated here, 59 times each**, with that
document's sentence quoted in the original. *Predicted: 0.86*

**C46** `content` `open` `lands` — `.bind` is reported for the **second object**
without being attributed: **562,176 bytes in both editors nine years apart**,
**9,549 bytes equal**, **first difference at 768**, **longest identical run
6,084 at offset 809**, both beginning `55 8b ec 5d c3` and both comparing
against `MZ` and `PE\0\0` within sixty-four bytes; **and `steam`, `valve` and
`SteamStub` are counted in this object's copy and reported as zero**, so that
the refusal to name it is a measurement and not a hedge. *Predicted: 0.89*

**C47** `content` `open` `constructs` — `rgssjoin.py` is run against the
extracted help file and the join is reported as **classes found in the data
against classes documented**, and **field names found against field names
documented**, with the previous object's **28 of 28 and 323 of 324** quoted as
the figure to beat and every unmatched name on both sides named — over **82
class pages against 68**. *Predicted: 0.86*

**C48** `content` `open` `constructs` — **the help file is asked the question
the previous one answered.** `pc-rpgmakerxp-doc/docs/08` quoted that product's
help declining to specify `.rgssad` and asking that it not be analysed. This
one's **172 HTML pages are searched for `.rgss3a`** and the result — whatever it
is, including nothing — is quoted in the original and set beside the previous
object's sentence, **with the count of occurrences and the pages they sit in**.
*Predicted: 0.55*

**C49** `content` `open` `constructs` — the two language DLLs are compared:
**2,945,024 against 2,917,888 bytes**, their section tables, their resource
directories and **the count of string-table entries in each**, with the
difference in bytes accounted for; and the finding that **the Italian one
declares `InternalName LangENU` and carries no `LegalCopyright`** is stated as a
property of a localisation shipped with its source's identity fields intact.
*Predicted: 0.85*

**C50** `content` `open` `nonnumeric` — **the rule about the owner's work is
written**, in the shape the four existing rules are written in: **a sentence, a
test somebody who disagrees can apply, and a reason.** The sentence is that
what the owner made is not the object and is measured only where it changes a
measurement of the object; the test is **whether removing the two files changes
a published figure**; and the chapter states that **`cd32.zip` was not opened**,
names the four `Game.ini` lines of `cd32.ini` as evidence about the *product*,
and spends exactly one sentence on the fact that the project's title is a
platform this collection documents elsewhere. *Predicted: 0.90*

**C51** `content` `open` `nonnumeric` — the personal-data chapter is **short**
and does not reopen the rule: the **19 addresses in 11 files** are reported,
**how many of the nineteen are duplicates of each other is counted** — which the
pre-briefing did not do — the count of **distinct** addresses is given, all
nineteen are shown to be third parties', `redact.py` is run with an `--expect`
that fires, and the chapter states whether the population changes the rule or
only the arithmetic, with a reason. *Predicted: 0.88*

**C52** `content` `open` `constructs` — **the seventeen-hour gap is decomposed
the way the sixteen-hour one was, and the two are compared as a pair.**
**17 h + 7.891813 s** against **16 h + 3.953125 s**; the compile remainder shown
to grow with container size across **all five** specimens with the sizes given;
the whole-hour term shown to be **present in 2 of 2 Japanese-header specimens
and 0 of 3 others**; a fixed zone bias excluded **by arithmetic** because the
two hour-counts differ; and **at least one new mechanism named with the
measurement that would distinguish it**, so that the next session inherits a
test and not a mystery. *Predicted: 0.45*

**C53** `content` `open` `constructs` — the **310 interlaced PNG** are
identified: which directories they are in, what they have in common, and whether
the interlace flag correlates with anything else the census measures — colour
type, dimensions, or the pack they arrived in — with the correlation stated as a
count and not as an impression. *Predicted: 0.85*

**C54** `content` `open` `constructs` — `jstore.py`'s claim is **written to
`notes/jstore-prediction.txt` before the command runs**, in at least six numbered
parts covering what it will claim, on which files, and why; the tool is then run
over the 117 `.rvdata2`; **the predictions are scored one at a time with the
wrong ones left standing and explained from the object**; and the running count
of empty closures is advanced from twenty-six with the new total given.
*Predicted: 0.86*

**C55** `content` `open` `constructs` — **the 23 MP3 and the 23 OGG of
`AdventurersJourney_SND` are shown to be, or not to be, the same twenty-three
pieces of music.** The stems are joined; the **durations are computed from both
formats** — Ogg from its last granule position, MP3 from its frame headers — and
compared pair by pair with a stated tolerance; and the answer is given as a count
of matching pairs out of 23 with the non-matching ones named. **This requires an
MP3 frame reader that does not exist in this box.** *Predicted: 0.50*

**C56** `content` `open` `constructs` — `depotsplit.py` gains a `--group` that
accepts a **path** rather than a top-level component, and the six depots are then
closed **by the tool** rather than by hand: **five exact directory groups, one
single file, and one remainder**, summing to 342,514,066 at residue 0, with
`dlc\Bonus` shown to fall inside the base depot **by the tool's own arithmetic**.
*Predicted: 0.86*

**C57** `content` `open` `lands` — `vendorhash.py` is run and
`notes/vendorhash.txt` is written, carrying `SciLexer.dll` at **2.22 / 545,280 /
linker 9.00** beside the previous object's **1.58 / 356,352 / linker 7.10**,
with both sha1 and both evidence offsets; **and the previous session's claim
that the `UNLHA32.DLL` vendor thread was "closed by the object" is reported as
reopened with a new subject**, quoted from `pc-rpgmakerxp-doc/docs/12` in the
original. *Predicted: 0.88*

**C58** `content` `open` `lands` — the three notes are written **under those
exact names** — `notes/crossall.txt`, `notes/sha1-all.txt`,
`notes/vendorhash.txt` — `crossnames.py` is run over the twenty-six crossings and
**classifies the rename**, giving how many of the 26 share a base name (none is
expected) and what the naming scheme changed from and to; and
`compratio.py --declared 321169744` is run with its difference against
342,514,066 reported. *Predicted: 0.89*

**C59** `content` `open` `constructs` — **the file-name encoding defect's true
scope is measured rather than asserted.** The pre-briefing names one tool.
**Every tool in the box that prints a file name is pointed at the tree with
`PYTHONIOENCODING` unset**, and the number that die of `UnicodeEncodeError` on
the Japanese file name is counted and published, beside the number that survive;
a **guard is written** so that a tool's output encoding is set for names as well
as for recovered text; and the guard is proved by a check **that fails without
it**. The pre-briefing's figure is one. *Predicted: 0.50*

**C60** `content` `open` `constructs` — `dirguard.py --survey` is re-run and
reported against **216 of 557**, the figure taken from
`notes/dirguard-survey-before.txt` and not from the brief; the new box's survey
is given as a count over its own denominator; and **every reader this session
writes is shown absent from the raised list**, which is the only claim the survey
can support about tools that did not exist when the 216 was measured.
*Predicted: 0.87*

**C61** `content` `open` `lands` — **the corrections chapter states its own
count before listing**, reports **all four of the claims the pre-briefing
declares unverified** with a verdict each — the depot mapping, the opaque text
count, the DLC sum and the all-Ogg crossings — reports **the refusal-count
disagreement of §C**, and splits the total between corrections found **by a
program** and corrections found **by a person**, which is P19's falsification
condition and must be reported whichever way it falls. *Predicted: 0.90*

**C62** `content` `open` `nonnumeric` — the leftovers chapter carries **at least
ten open questions with a reason each**, including all ten the brief names; and
the initialisms — `RGSS3`, `RVDATA2`, `RVPROJ2`, `RGSS3A`, `MP3`, `ID3`, `TTF`,
`SFNT`, `PDF`, `BMP`, `ZIP`, `EULA`, `DLC`, `VL`, `EUC`, `UTF` and any others —
are split into **demonstrated from the object, derived, attributed to a public
source, and not demonstrated**, with the four counts summing to the total.
*Predicted: 0.88*

**C63** `content` `open` `lands` — `pngpair.py` is pointed at the **84 repeated
hashes**, and the four groups the pre-briefing names are confirmed **by
counting**: 49 inside `dlc\Tyler Warren…`, 24 inside `Generator\`, 10 between
the two `VLGothic` trees and 1 in `Projects\`, summing to 84 with the 91 repeat
*instances* distinguished from the 84 repeated *hashes* and the difference
explained. *Predicted: 0.87*

**C64** `content` `open` `constructs` — the **`Year` cell is argued**, not
chosen: the six candidates — **2011** in five copyright fields, **2012-02-22**
RGSS3's link time, **2012-03-12** the help file's compile, **2012-03-14** the
bonus EULA in prose, **2014-03-05** the editor's link time and the build id
19572675 as a counter — are set out; the previous row's reasoning is quoted
(**it took 2005 because the copyright field and the help compile agreed, and
here they do not**); the `.bind` section is used as the reason a 2014 link time
is the wrong kind of date, as it was last time; and the cell that is written is
named with the argument that chose it. *Predicted: 0.86*

---

## What this document has already got wrong

Two things, before a chapter is written, and both are recorded here so the
corrections chapter cannot claim them as its own discoveries.

**The refusal count is not 52.** §C records it: the brief's figure depends on
`PYTHONIOENCODING`, and this session's harness does not set it. That is C31.

**And the opaque `.mplus` count does not agree with itself.** `_pre/formats.txt`
lists `.mplus` at **4 files / 8,882 bytes** inside a 68-file table whose nine
groups must sum to 68; `_pre/object.txt`'s by-extension table lists `.mplus` at
**6 files / 9,632 bytes**. Both cannot be right, and 23 + 22 + 6 + 5 + 4 + 4 + 2
+ 1 + 1 = 68 only with the 4. That is C29, and the chapter has to say which
table is wrong rather than quoting whichever one suits it.

*Every clause above is scored in the last chapter of this repository, whether it
was right or not. Every clause carries `method` or `content` and `inherited` or
`open`; every open content clause carries one of `lands`, `constructs` or
`nonnumeric`; and the two totals are never added together.*
