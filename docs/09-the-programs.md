# 09 — the programs: a language DLL with no code in it, a section that names nobody in two products nine years apart, and 310 interlaced pictures that are one artist's export tool

*Measure: `python tools/pecensus.py rpgvxace-steam --by-magic`, in
`notes/pecensus.txt`; `python tools/verres.py dump rpgvxace-steam`, in
`notes/verres.txt`; `python tools/peimpexp.py rpgvxace-steam/RGSS301.dll
--exports|--imports`, in `notes/rgss-exports.txt` and `notes/rgss-imports.txt`;
`python _work/langdll.py`, in `notes/langdll.txt`; `python _work/bindcmp.py`
and `python _work/bindstrings.py`, in `notes/bindcmp.txt`; `python
_work/interlace.py` and `_work/interlace2.py`, in `notes/interlace.txt`;
`python _work/repeats.py` and `_work/recommended.py`, in `notes/repeats.txt`
and `notes/recommended.txt`.*

---

## Eight binaries, and two of the pre-briefing's three summary figures are wrong

```
python tools/pecensus.py rpgvxace-steam --by-magic

path                 fmt     bytes    linker  COFF (UTC)            CompanyName
Projects/Game.exe    PE32    140800     9.00  2011-10-06 04:40:34
RGSS301.dll          PE32   1085952     9.00  2012-02-22 00:14:13
RPGVXAce.exe         PE32   6944256     9.00  2014-03-05 06:17:58
RPGVXAceENU.dll      PE32   2917888     9.00  2014-03-06 01:34:27
RPGVXAceITA.dll      PE32   2945024     9.00  2014-03-06 01:32:17
SciLexer.dll         PE32    545280     9.00  2011-01-03 02:33:26   Neil Hodgson
steam_api.dll        PE32    106920    10.00  2013-11-21 23:27:55   Valve Corporation
steam_api64.dll      PE32+   121256    10.00  2013-11-21 23:26:50   Valve Corporation

binaries        : 8
by format       : PE32 7, PE32+ 1
Authenticode: 2 of 8 PE files carry a certificate table
    SIGNED  steam_api.dll     SIGNED  steam_api64.dll
```

**Not "PE32 8": PE32 7 and PE32+ 1.** `steam_api64.dll` is a 64-bit image, and
a tool that reads the optional-header magic says so. **Not "all eight at linker
9.00": six at 9.00 and the two Valve DLLs at 10.00** — Visual C++ 2008 for
Enterbrain and Scintilla, Visual C++ 2010 for Valve. **And two of the eight
carry an Authenticode certificate table**, which the pre-briefing does not
mention at all; the two that are signed are the two that are not Enterbrain's.

`sigcount.py --hex 4d5a5000` gives **0 of 2,026** — no Borland `MZP` stub
anywhere, at offset 0 or elsewhere. `mzcensus.py` gives **2 of 8**, its
twelfth appearance, missing the six DLLs and their 7,722,320 bytes because it
filters on the `.EXE` extension where a magic exists — **which is the defect
this session repaired in two readers and found in a third**
([12](12-the-tools.md)).

---

## Eight version resources of eight, and one of them declares itself English

```
python tools/verres.py dump rpgvxace-steam                    8 of 8

RGSS301.dll        FileDescription  RGSS3 Core
                   ProductName      Ruby Game Scripting System
                   LegalCopyright   Copyright (C) 2011 Enterbrain, Inc. / Yoji Ojima
RPGVXAce.exe       FileVersion      1, 0, 2, 2      ProductName  RPG Maker VX Ace
RPGVXAceENU.dll    FileVersion      1, 0, 3, 0s     InternalName LangENU
RPGVXAceITA.dll    FileVersion      1, 0, 2, 2      InternalName LangENU
                   LegalCopyright   (absent)
SciLexer.dll       FileVersion      2.22            Copyright 1998-2010 by Neil Hodgson
steam_api.dll      FileDescription  Steam Client API (…_win32@winslave04)
steam_api64.dll    FileDescription  Steam Client API (…_win64@winslave05)
Projects/Game.exe  FileDescription  RGSS3 Player
                   ProductName      Ruby Game Scripting System
```

**Eight, not six.** The pre-briefing says `Projects\Game.exe` carries none and
it carries one: `RGSS3 Player`, version `3, 0, 0, 1`, with the copyright field.

**Four findings.**

**One. `RGSS` is expanded by the linker, twice.** `RGSS301.dll` and
`Projects\Game.exe` both give `ProductName` as **`Ruby Game Scripting
System`**. The previous object's `RGSS104E.dll` carried **no version resource
at all**, and that expansion had to be recovered out of the help file's LZX
stream. Here two compilers wrote it into two binaries. `namescan.py` finds the
string in **four** files, all UTF-16 only.

**Two. Valve's DLLs name Valve's build machines.** `winslave04` and
`winslave05`, in a `FileDescription`, in a shipped and signed binary. That is
the same category as the previous object's `f:\dd\vctools\…`: a third party's
infrastructure, published by that third party, and therefore a finding to quote
rather than withhold ([10](10-whose-bytes.md)).

**Three. Scintilla is here again and it is a different Scintilla.**

```
pc-rpgmakerxp-doc     SciLexer.dll  356,352  linker 7.10  1.58  1998-2003
pc-rpgmakervxace-doc  SciLexer.dll  545,280  linker 9.00  2.22  1998-2010
```

`pc-rpgmakerxp-doc/docs/12` wrote that the four-object `UNLHA32.DLL` thread —
one third party's library at three versions, never crossing — had been "closed
by the object and not by a session". **It is not closed; it has a new
subject.** `notes/vendorhash.txt` carries both builds with both hashes and both
version strings, and the version column is the repair
`pc-rpgmaker2003-doc/docs/16` was scored a half for lacking. Two hashes that
cannot cross, one vendor that does.

**Four. The Italian DLL declares itself English, and the structure says why.**

---

## A language DLL with no code section

```
python _work/langdll.py

RPGVXAceITA.dll  2945024 bytes, 1 sections
  .rsrc     0x00001000    2944040 0x00000200    2944512

RPGVXAceENU.dll  2917888 bytes, 2 sections
  .rdata    0x00001000        123 0x00000200        512
  .rsrc     0x00002000    2916752 0x00000400    2916864

  ITA 2945024  -  ENU 2917888  =  27136 bytes
  .rdata       0 - 512   = -512
  .rsrc  2944512 - 2916864 = +27648
  SUM                       27136
  RESIDUE against the file-size difference : 0
```

**The Italian DLL is one section, and that section is `.rsrc`.** No `.text`, no
code, nothing but a resource tree. The English one has 123 bytes of `.rdata`
and otherwise the same. **These are not programs; they are resource
containers**, and the 27,136-byte difference between them decomposes into two
section deltas at residue 0.

**Which explains `InternalName LangENU` on the Italian build without needing a
story about carelessness.** Nobody recompiles a resource-only DLL to localise
it; somebody opens the English one, replaces the strings, and writes it back —
and `InternalName`, `FileVersion` and `LegalCopyright` live in the version
resource, which is one more resource in the tree. Two of the three were left
alone and one was deleted. **The Italian build's `FileVersion` is `1, 0, 2, 2`
against the English one's `1, 0, 3, 0s` — a version string ending in a
letter — so the two were edited from different starting points, and the one
this installation actually runs in is the older.**

18.5971 % of the two files' bytes are equal at the same offset, first
difference at byte 190, which is what two resource trees carrying different
strings look like.

---

## The interpreter's front door lost two thirds of itself

```
python tools/peimpexp.py rpgvxace-steam/RGSS301.dll --exports
EXPORTS : 27 functions, 27 by name, 0 forwarded

RGSSInitialize3   RGSSFinalize      RGSSGameMain      RGSSEval
RGSSGetBool       RGSSGetInt        RGSSGetDouble     RGSSGetTable
RGSSGetSymbol     RGSSGetStringACP  RGSSGetStringUTF8 RGSSGetStringUTF16
RGSSSetString     RGSSSetStringACP  RGSSSetStringUTF8 RGSSSetStringUTF16
RGSSErrorType     RGSSErrorMessage  RGSSGC
RGSSAudioInitialize   RGSSAudioFinalize
RGSSSetupRTP      RGSSAddRTPPath    RGSSClearRTPPath  RGSSGetRTPPath
RGSSGetPathWithRTP    RGSSSetupFonts
```

**Twenty-seven against the previous object's sixty-six**, and the difference is
not a shrinking API. That object's 66 were **23 `RGSS*` plus 43 names of Ruby's
regular-expression engine** — `regex_*`, `ruby_re_*`, `RegEncodingSJIS`. RGSS3
exports none of them: the interpreter is still inside, and the export table
stopped being its front door.

The four `RGSS*` names that are new tell the same story from the other side.
**`RGSSInitialize` became `RGSSInitialize3`**; `RGSSGetSymbol` and
**`RGSSSetupFonts`** appear; and the string accessors gained **UTF-16** forms
beside the UTF-8 and ACP ones — which is what a move from Ruby 1.8 to Ruby 1.9
looks like from outside a binary. It is the same generational change the 466
`I` type-bytes show from inside one ([05](05-the-maps.md)).

```
IMPORTS : 12 DLLs, 14 names
  kernel32 3 (GetProcAddress, GetModuleHandleA, LoadLibraryA)
  user32 1 (GetAsyncKeyState)      gdi32 1 (GetGlyphOutlineW)
  advapi32 1 (GetUserNameW)        shell32 1 (SHGetPathFromIDListW)
  winmm 1 (timeBeginPeriod)        comctl32 1 (PropertySheetW)
  ws2_32 1 (#116)                  msacm32 1 (acmStreamConvert)
  ole32 1 (CoUninitialize)         oleaut32 1 (VariantChangeTypeEx)
  kernel32 1 (RaiseException)
```

**The dynamic-loading pattern is unchanged**: twelve libraries, fourteen names,
`GetProcAddress` first. Everything else is resolved at run time.

**Winsock is imported by ordinal again and it is a different ordinal.** The
previous object imported `ws2_32.dll #55`; this one imports **`#116`**.
`pc-rpgmakerxp-doc/docs/16` left "which Winsock function" open because the
ordinal-to-name map is not in the object. **It is not in this one either, and
now there are two of them and they disagree** — which does not answer the
question but does say the import is not incidental.

**`GetUserNameW` is new and gets one sentence.** It is a capability of a
binary. The import table says the function is resolvable and says nothing
whatever about whether it is called, and this document is not going to pretend
otherwise.

---

## `.bind`, for the second object, and it still names nobody

```
python _work/bindcmp.py

RPGVXAce.exe .bind   562176 bytes  sha1 35174df7d7164edbe9…
RPGXP.exe    .bind   562176 bytes  sha1 633ec56a7954f1c48c…
identical            : False
bytes equal          : 9549 of 562176 (1.6986 %)
first differing byte : 768
   A[768..] 2aa5008b7580b9c00000008dbd80fcfffff3a58d8580fcff
   B[768..] ba6b008b7580b9c00000008dbd80fcfffff3a58d8580fcff
longest identical run: 6084 bytes at offset 809
```

**Exactly the same size, one product and nine years apart.** The first 768
bytes are byte-identical and so are bytes 809 to 6,892. Both begin
`55 8b ec 5d c3` — `push ebp; mov ebp,esp; pop ebp; ret`, a stub — and both
compare against `MZ` and `PE\0\0` within their first sixty-four bytes. **The
same loader with a few constants patched, in front of two different
high-entropy payloads.** The three bytes that differ at 768 are an immediate:
`2a a5 00` against `ba 6b 00`.

**And it is not attributed here either, for a reason that was re-measured
rather than carried over:**

```
python _work/bindstrings.py

  term         file 8-bit  file wide  bind 8-bit  bind wide
  steam                 9          3           0          0
  valve                 0          0           0          0
  SteamStub             0          0           0          0
  Themida / VMProtect / Armadillo / ASProtect / PECompact /
  UPX / obsidium / Denuvo                      0 everywhere
```

**Thirteen candidate names, two specimens, two encodings, and `.bind` names
none of them.** The interesting new number is the first one: **`steam` occurs
nine times in this editor and zero times in the previous one** — and **zero
times inside `.bind` in either.** So the surrounding executable talks about
Steam and the anonymous section does not, which makes the refusal to name it a
measurement instead of a hedge.

**What this session adds is not a name. It is that one unexplained section has
become a two-object pattern with a shared stub**, and that is what gets handed
on.

---

## The 84 repeated hashes, and 310 interlaced pictures that are one person

```
python _work/repeats.py

hashes appearing more than once : 84
files sharing a repeated hash   : 175
EXTRA copies                    : 91
  distinct + extra = files : 1935 + 91 = 2026   residue 0
  copies per repeated hash : {2: 80, 3: 2, 4: 1, 5: 1}

  group                         hashes   wasted bytes
  inside dlc/                       49        2072629
  inside Generator/                 24        1942770
  VLGothic shipped twice            10        7940282
  inside Projects/                   1         480056
  TOTAL                             84       12435737
```

**A repeated hash and an extra copy are different numbers and only the second
closes.** Eighty-four pictures appear more than once; ninety-one appearances
are beyond the first; 1,935 + 91 = 2,026.

**The pre-briefing says the 49 inside `dlc\` are Tyler Warren's `Recommended
Sizes`, which are his `280 Large` copied. They are not.**

```
python _work/recommended.py

  identical to 80 Tiny        24 of 50        identical to 200 Mid      6 of 50
  identical to 140 Small      13 of 50        identical to 280 Large    5 of 50
  identical to 50 Mini         1 of 50        matching NONE of the five 1
  RESIDUE : 0
```

**`Recommended Sizes` is a per-battler choice and not a copied directory.**
Twenty-four of the fifty monsters are recommended at 80 pixels tall, thirteen
at 140, six at 200, five at 280, one at 50 — and one, `King Slime.png`, matches
none of the five and is a sixth, unique file. 49 + 1 = 50, and the 49 are
exactly the 49 repeated hashes. **It is an artist's opinion about how big each
of his monsters should be drawn, encoded as file copies**, and the byte
arithmetic recovers it exactly.

### And the interlace flag is a fingerprint

No object in this collection has had an interlaced PNG. This one has 310 of
1,456 — **21.2912 %** — and `pngcensus.py` reports the flag as one row of an
IHDR table and says nothing about which files carry it.

```
python _work/interlace.py

  directory                                                   png  inter    share
  dlc/Tyler Warren RPG Battlers 1st 50/140 Small               50     49   98.00 %
  dlc/Tyler Warren RPG Battlers 1st 50/200 Mid                 50     49   98.00 %
  dlc/Tyler Warren RPG Battlers 1st 50/280 Large               50     49   98.00 %
  dlc/Tyler Warren RPG Battlers 1st 50/50 Mini                 50     49   98.00 %
  dlc/Tyler Warren RPG Battlers 1st 50/80 Tiny                 50     49   98.00 %
  dlc/Tyler Warren RPG Battlers 1st 50/Recommended Sizes       50     49   98.00 %
  …/Recommended Sizes/Example Alternate Colors                 17     16   94.12 %
  every other directory in the tree                          1139      0    0.00 %

  the interlaced files' colour types : {(8, 6): 310}
```

**All 310 are in one downloadable-content pack, and 1,139 files in twenty other
directories carry the flag zero times.** Not one of Enterbrain's 1,139 pictures
is interlaced and 310 of one third party's 317 are. **The flag is not a
property of the product; it is a setting in one artist's export tool.**

**And the seven exceptions are one battler.**

```
python _work/interlace2.py

  140 Small/Gold Slime.png                     144 x 140      32264
  200 Mid/Gold Slime.png                       206 x 200      59490
  280 Large/Gold Slime.png                     288 x 280     109257
  50 Mini/Gold Slime.png                        51 x 50        7720
  80 Tiny/Gold Slime.png                        82 x 80       13784
  Recommended Sizes/Gold Slime.png              82 x 80       13784
  …/Example Alternate Colors/Gold Slime.png     82 x 80       11025

  directories represented : 7   one per directory : True
  distinct base names     : 1   ['Gold Slime.png']
```

**One monster of fifty went through a different export path than the other
forty-nine, at every one of its seven sizes.** Six directories at 49 of 50 and
one at 16 of 17, and the odd file out is the same picture every time. That is
what "310 interlaced PNG and nobody knows why" turns into when somebody asks
where they are.
