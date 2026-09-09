# 13 — corrections: twenty, of which thirteen were found by a program and seven by reading its output

*Measure: every correction below names the command that produced the right
figure and the file under `notes/` that holds it. The count is stated before
the list and the split at the end is P19's falsification condition, reported
whichever way it falls.*

**Twenty corrections. Thirteen by a program, seven by a person reading one.**
The pre-briefing declared four of its own statements unverified and warned that
it had measured much and verified little; **all four were checked and all four
hold**, and six further errors turned up in statements it did not flag.

---

## A — against the pre-briefing

**1. The refusal count is not 52, and it is not a fact about the object.**
`_pre/tools.txt` publishes *52 refusals of 85 readers*, `exception` 1. Run in a
shell with `PYTHONIOENCODING` unset it reports **54**, `exception` **3**. The
two extra are `unityfs.py` and `unityarc.py` dying of `UnicodeEncodeError` on a
Japanese file name. **A figure attributed to the object was a figure about an
environment variable**, and it was the first row of P17's register to be
checked. After the repair in [12](12-the-tools.md) the two runs are identical
and the count is **50**.
*`python tools/refusalclass.py notes/refusals.txt` — `notes/refusalclass-before.txt`, `notes/refusalclass.txt`*

**2. The eight binaries are not all PE32.** `_pre/executable.txt`: *binaries
examined : 8, by format : PE32 8*. `pecensus.py --by-magic` reports **PE32 7
and PE32+ 1**; `steam_api64.dll` is a 64-bit image and its optional-header
magic says so.
*`python tools/pecensus.py rpgvxace-steam --by-magic` — `notes/pecensus.txt`*

**3. They are not all at linker 9.00.** The same file tabulates `9.00` on all
eight rows. **Six are 9.00 and the two Valve DLLs are 10.00** — Visual C++ 2008
for Enterbrain and Scintilla, 2010 for Valve.
*same command, same file*

**4. There are eight version resources, not six.** `_pre/executable.txt`:
*verres.py dump rpgvxace-steam — 6 of 8*, and `_pre/tools.txt` adds
*`Projects\Game.exe` and one other carry none*. **`verres.py` reports 8 of 8**,
and `Projects\Game.exe` carries `FileDescription` **`RGSS3 Player`**,
`ProductName` **`Ruby Game Scripting System`**, `FileVersion` `3, 0, 0, 1` and
the copyright field.
*`python tools/verres.py dump rpgvxace-steam` — `notes/verres.txt`*

**5. The 2011 copyright field appears four times, not five.** Both `prompt.txt`
and `_pre/object.txt` say *five resources say `Copyright (C) 2011 Enterbrain,
Inc. / Yoji Ojima`*. **Four do**: `RGSS301.dll`, `RPGVXAce.exe`,
`RPGVXAceENU.dll` and `Projects\Game.exe`. **`RPGVXAceITA.dll` carries no
`LegalCopyright` at all** — which the pre-briefing itself reports two pages
earlier, in the same file. This one matters beyond bookkeeping, because the
`Year` argument in [08](08-the-clocks.md) counts those fields.
*`grep -c "Copyright (C) 2011 Enterbrain" notes/verres.txt` → 4*

**6. `dlc\` is 24.4372 % of the tree, not 24.4373 %.**
83,751,594 × 100 ÷ 342,722,404 = 24.43724…, which rounds down. **Twenty-nine
published four-decimal percentages were recomputed in exact decimal and this is
the only one wrong** — against five of twenty-five on the previous object.
*`python _work/pcts.py` — `notes/percentages.txt`*

**7. The ITSF compile remainder does not grow with the container.**
`_pre/clocks.txt`: *il resto … cresce col file: 3,95 s su 347 KB, 7,89 s su 6,6
MB*. Within that pair it does. **Across all five specimens it does not order by
size at all**: 347 KB → 3.95 s, 2.5 MB → 8.16, 5.5 MB → 8.44, 6.3 MB →
**17.48**, 6.6 MB → 7.89. The largest container has the second-smallest
remainder. What survives is that all five lie between 3.95 and 17.48 seconds,
which is a plausible band for a help compile and is not a trend.
*`python tools/chmclocks.py <five containers>` — `notes/chmclocks.txt`*

**8. `Recommended Sizes` is not `280 Large` copied.** `_pre/object.txt` and
`_pre/provenance.txt` both say so. Matched by sha1 against all five size
directories, its fifty files are **24 from `80 Tiny`, 13 from `140 Small`, 6
from `200 Mid`, 5 from `280 Large`, 1 from `50 Mini`, and one — `King
Slime.png` — matching none of the five.** 49 + 1 = 50, and the 49 are exactly
the 49 repeated hashes inside `dlc\`. **It is an artist's per-monster
recommendation, not a duplicated folder.**
*`python _work/recommended.py` — `notes/recommended.txt`*

**9. Four readers select by the wrong extension, not three — and one of the
three is misattributed.** The pre-briefing names `marshal48.py`, `rgssdb.py`
and `rxscripts.py`. **`rgssjoin.py` does it too**, and was found by running it.
**And `rxscripts.py` is not an instance**: it wants a single `Scripts.rxdata`,
refuses a directory by design, and **this tree contains no scripts file of any
name**, so no extension filter could have saved it.
*`python tools/rgssjoin.py join --data … --docs …`; `find rpgvxace-steam -iname "*script*"` → nothing*

**10. Two binaries are Authenticode-signed and the pre-briefing does not
mention it.** `pecensus.py` reports *2 of 8 PE files carry a certificate
table*, and the two are `steam_api.dll` and `steam_api64.dll` — the two that
are not Enterbrain's. An omission rather than an error, recorded because the
same file lists six other properties of the same eight binaries.
*`python tools/pecensus.py rpgvxace-steam --by-magic` — `notes/pecensus.txt`*

**11. `RGSS` is expanded in four files, not one.** `_pre/executable.txt` frames
`RGSS301.dll`'s `ProductName` as the place the expansion appears. `namescan.py`
finds `Ruby Game Scripting System` in **four files, all UTF-16 only**:
`RGSS301.dll`, `Projects\Game.exe`, `RPGVXAceENU.dll` and `RPGVXAceITA.dll`.
**Two of them carry it as `ProductName`**, where the previous object had it in
none.
*`python tools/namescan.py rpgvxace-steam --name "Ruby Game Scripting System"` — `notes/namescan.txt`*

**12. Fifty-nine events are in eleven maps, and every one of them is empty.**
Not an error — the pre-briefing's *59 eventi* is right — but it is reported
there as a class census, and a class census cannot see that 106 of the 117 maps
carry none, that every event has one page, and that every page's command list
holds one command whose code is the default-constructed terminator. **The
sharper statement changes what the object is**, and it is [05](05-the-maps.md).
*`python tools/rvmap.py events rpgvxace-steam/SampleMap` — `notes/rvmap-events.txt`*

### The four claims the pre-briefing flagged as unverified

| | claim | verdict |
|---|---|---|
| **the six-depot mapping** | five exact directory groups, one single file, one remainder | **holds**, walked, seven residues of 0 ([03](03-the-shop.md)) |
| **the count of opaque text files** | 34, and two of its tables appear to disagree | **holds** — see B.1 below; the disagreement was this session's error |
| **the DLC sum against the three depots** | 83,751,594 − 74,394,305 = 9,357,289 = `dlc\Bonus` | **holds**, to the byte |
| **all 26 crossings are Ogg** | 22 SE + 4 BGS | **holds**, and checked **by magic**: 26 of 26 begin `OggS` |

---

## B — against this session's own documents and tools

**1. `docs/00`'s clause C29 asserted that two of the pre-briefing's tables
could not both be right, and they can.** The clause reasoned that
`_pre/formats.txt`'s opaque table (`.mplus` 4 files / 8,882 bytes) contradicts
`_pre/object.txt`'s extension table (`.mplus` 6 files / 9,632 bytes). **The two
count different populations**: one counts `.mplus` inside the OPAQUE bucket and
the other counts it over the whole tree.

```
python _work/asciicheck.py                              (in notes/percentages.txt's neighbourhood)
  VLGothic/LICENSE_E.mplus     375 bytes  ASCII head   high bytes in file: 0
  VLGothic/LICENSE_J.mplus     329 bytes  high bytes in head
  9632 - 8882 = 750    the two LICENSE_E.mplus together = 750
```

**The two `LICENSE_E.mplus` are pure ASCII and were classified `plain text,
ASCII` — never opaque.** 6 − 2 = 4, and 9,632 − 8,882 = 750 = 2 × 375, residue
0. **The pre-briefing was right and the predictions document was wrong**, which
is the correction P15 exists to force and it is recorded as one.

**2. `mp3frames.py` read the Vorbis sample rate at the wrong offset, and every
duration in its first pairing table was 256 times too small.** The Vorbis
identification header puts `audio_channels` at +11 and `audio_sample_rate` at
+12; reading at +11 picks up the channels byte plus three bytes of the rate.
The table printed **0 of 23 agreeing** with every delta equal to the MP3
duration itself. **A uniform factor of 256 across 23 independent files is a bug
and not a finding**, and three checks now assert the offset against a
hand-built header.
*`python tools/mp3frames.py selftest` — `notes/selftests.txt`*

**3. A check in `mp3frames.py`'s selftest asserted the wrong bitrate.** It
required an MPEG-2 Layer III frame at index 9 to be 64 kbit/s; it is 80, and
the tool's derived frame length of 261 bytes was right. **The check failed on
its first run and the tool was correct** — which is the only useful thing a
check can do the first time it is run.

**4. `nameguard.py`'s docstring claimed the source file was pure ASCII and it
was not.** The file held the Japanese bait name as a literal, so the tool
written to protect other tools from a non-ASCII name was itself a file
containing one. **Its own first check caught it** and the constant is now built
from codepoints.

**5. This session read `protscan.py`'s positive control as a result.** The
first glance at *total hits across every marker : 8* read eight protection
markers where the table says **0 of 11 markers and a four-zero-bytes positive
control firing on 8 of 8 binaries**. Nothing was published; it is recorded
because it is the same shape as A.10 in reverse — **a control column and a
result column in one total** — and the tool prints them apart for exactly this
reason.

---

## C — against neighbouring repositories and inherited tools

**1. `compratio.py` labels its own walk as the shop's declaration.** It prints
*the shop declares BytesToDownload : 321169744, against BytesToStage :
342722404* — and the manifest's `BytesToStage` is **342,514,066**. The 342.7 M
is `compratio.py`'s own walk of the tree, which includes the owner's two files.
**Rule 3 says every figure names its denominator; this one names somebody
else's.** The two ratios are 1.0665 and 1.0671, and the difference is 208,338
bytes in the fourth decimal place.
*`python tools/compratio.py rpgvxace-steam --declared 321169744` — `notes/compratio.txt`*

**2. `pc-rpgmakerxp-doc/docs/12` wrote that the `UNLHA32.DLL` vendor thread was
"closed by the object and not by a session".** It is not closed. **It has a new
subject**: `SciLexer.dll` at 2.22 / 545,280 / linker 9.00 here against 1.58 /
356,352 / linker 7.10 there — one vendor, two builds, hashes that cannot cross,
seven years apart. `notes/vendorhash.txt` carries both rows with the version
column that `pc-rpgmaker2003-doc/docs/16` was scored a half for lacking.

**3. `pathcheck.py` was the only rule-7 violation in this repository, and it
was its own output.** Run over 625 tracked files it reported **three
violations**, all of them in `notes/pathcheck.txt`: two because the report
echoes its needles verbatim on a line beginning `needles :`, and one because
the positive control plants a path built from the first needle. **The program
written to enforce rule 7 published this machine's directory names in the file
that proves it did not** — which is the joke `pc-rpgmakerxp-doc/docs/14` had to
report about the rule-0 hook's log, one object later and in the checker itself.

The needles are now masked on the way out — they are still what the scan uses
and no longer what the report says — and **the check is now a fixed point**:
running it again over its own committed output gives 0 violations, which it
did not before.
*`python tools/pathcheck.py --needle <a directory this work lives under>` — `notes/pathcheck.txt`*

**4. `pc-rpgmakerxp-doc/docs/03` wrote that a shop's depot boundary is a
directory boundary.** On that object it was, twice. **On this one it is neither
of the two things it could be**: `dlc\Bonus` sits inside a directory called
`dlc\` and belongs to the *base* depot, and depot 220708 is **one file** inside
a directory whose other files belong elsewhere. `depotsplit.py` could not
express either and now can ([03](03-the-shop.md)).

---

## The split, which is P19's falsification condition

> **P19.** *Falsification: if the next session's corrections chapter still
> splits better than three-to-one in favour of programs, the checks were
> already sufficient and naming the blind spot in advance bought nothing.*

| found by | count | which |
|---|---:|---|
| **a program** | **13** | A.1 (running `refusals.py`), A.2, A.3 (`pecensus.py`), A.4, A.5 (`verres.py`), A.6 (`pcts.py`), A.8 (`recommended.py`), A.9 (`rgssjoin.py` refusing), A.11 (`namescan.py`), B.1 (`asciicheck.py`), B.3, B.4 (two selftests failing), **C.3 (`pathcheck.py` firing on its own output)** |
| **a person reading output** | **7** | A.7 (sorting the clock table by size), A.10 (reading a census row nobody had quoted), A.12 (opening the events instead of counting the classes), B.2 (noticing that every delta equalled the MP3 duration), B.5 (misreading a control), C.1 (reading a label), C.4 (reading a residue that would not close) |

**Thirteen to seven is 1.86 to one, and P19's condition is "better than three
to one".** It is not met, so **P19's falsification does not fire**: naming each
new tool's blind spot in advance and writing the check before pointing the tool
at the object bought something measurable.

**And the honest reading is narrower than that number.** Last session's split
was fourteen by a program to five by a person, which is 2.8 to one and also
under three. **The ratio moved the right way and it was already under the
threshold**, so one session cannot separate "P19 worked" from "the threshold
was set loosely". What P19 can claim specifically is **B.3 and B.4**: two
errors in this session's own new code, caught by checks written before the
tools were run, on their first execution — and **A.9**, a fourth defective
reader nobody had listed, found because the session ran the tool instead of
believing the list.

*What the person-column has in common is worth one line, because it is the same
line every session: **six of the seven are somebody reading a table that had
already been printed.** No check finds a claim that is false because it was
sorted by the wrong column.*
