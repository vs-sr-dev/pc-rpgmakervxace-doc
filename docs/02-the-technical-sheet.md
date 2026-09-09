# 02 — the technical sheet: every figure in this repository, with the command that reproduces it

*Measure: this page is the index of commands. Every row names the command that
produces its figure and the file under `notes/` that holds that command's
output. Nothing on this page is argued; the arguments are in the chapters it
points to.*

---

## The tree

| figure | value | command |
|---|---:|---|
| files | 2,026 | `python tools/treecensus.py rpgvxace-steam` |
| bytes | 342,722,404 | as above, and re-derived by `find rpgvxace-steam -type f -printf '%s\n' \| awk '{s+=$1;n++} END {print n,s}'` |
| directories | 45 | `python tools/treecensus.py rpgvxace-steam` |
| empty directories | 0 | `python _work/copyverify.py` |
| distinct sha1 | 1,935 | `python tools/hashall.py rpgvxace-steam` |
| repeated hashes | 84 | `python _work/repeats.py` |
| extra copies | 91 | as above; 1,935 + 91 = 2,026, residue 0 |
| files sharing a repeated hash | 175 | as above |
| unreadable | 0 | `python tools/hashall.py rpgvxace-steam` |
| copy verified on four axes | 2,026 / 2,026 / 2,026 / 45 | `python _work/copyverify.py` |

## The shop

| figure | value | command |
|---|---:|---|
| `SizeOnDisk` | 342,514,066 | `python tools/steamacf.py --path <steamapps>/appmanifest_220700.acf --root rpgvxace-steam --check` |
| residue against the walked tree | **−208,338** | as above |
| six depots, summed | 356,092,141 | as above |
| residue against `SizeOnDisk` | **−13,578,075** | as above |
| build id | 19572675 | `python tools/steamacf.py --path <…>.acf` |
| `LastUpdated` | 1760616017 | as above |
| `LastPlayed` | **1774010264** | as above |
| `BytesToDownload` | 321,169,744 | as above |
| interface language | `italian` | as above |
| the seven groups, walked, residue 0 | see [03](03-the-shop.md) | `python tools/depotsplit.py --root rpgvxace-steam --path … --rest 220701 --declare …` |
| declared / downloaded ratio | 1.0665 | `python _work/pcts.py` |

## The clocks

| figure | value | command |
|---|---:|---|
| mtime waves | 2 | `python tools/mtimes.py rpgvxace-steam --waves` |
| wave 1 | 2,024 files, 342,514,066 bytes | as above |
| wave 2 | 2 files, 208,338 bytes | as above |
| COFF stamps failing a falsity test | 0 of 8 | `python tools/stampcheck.py rpgvxace-steam` |
| distinct COFF days | 6 | `python tools/pecensus.py rpgvxace-steam --by-magic` |
| the `.chm`'s compile clock | 2012-03-12 17:20:34 UTC | `python tools/itsf.py header rpgvxace-steam/RPGVXAce.chm` |
| the five-specimen clock table | see [08](08-the-clocks.md) | `python tools/chmclocks.py rpgvxace-steam/RPGVXAce.chm …` |
| version-1 UUIDs | 3 in 2 files | `python tools/uuidscan.py rpgvxace-steam` |

## The programs

| figure | value | command |
|---|---:|---|
| binaries | 8 | `python tools/pecensus.py rpgvxace-steam --by-magic` |
| by format | **PE32 7, PE32+ 1** | as above |
| linker versions | **9.00 × 6, 10.00 × 2** | as above |
| Authenticode certificate tables | **2 of 8** | as above |
| version resources | **8 of 8** | `python tools/verres.py dump rpgvxace-steam` |
| `Copyright (C) 2011 Enterbrain, Inc. / Yoji Ojima` | **4 fields** | as above |
| `mzcensus.py`, twelfth appearance | 2 of 8 | `python tools/mzcensus.py rpgvxace-steam` |
| `MZP` stubs | 0 of 2,026 | `python tools/sigcount.py rpgvxace-steam --hex 4d5a5000` |
| `RGSS301.dll` exports | 27, 27 by name, 0 forwarded | `python tools/peimpexp.py rpgvxace-steam/RGSS301.dll --exports` |
| its imports | 12 DLLs, 14 names, `ws2_32 #116` | `python tools/peimpexp.py rpgvxace-steam/RGSS301.dll --imports` |
| `.bind` | 562,176 bytes in both editors | `python _work/bindcmp.py` |
| bytes equal between the two `.bind` | 9,549 of 562,176 | as above |
| first difference / longest identical run | 768 / 6,084 at 809 | as above |
| packer or vendor names inside `.bind` | **0 of 13, both specimens** | `python _work/bindstrings.py` |
| language DLL sections | ITA **1**, ENU 2 | `python _work/langdll.py` |
| their size difference, accounted | 27,136, residue 0 | as above |
| protection markers | 0 of 11, control firing 8 of 8 | `python tools/protscan.py rpgvxace-steam` |

## The data format

| figure | value | command |
|---|---:|---|
| `.rvdata2` files / bytes | 117 / 2,248,383 | `python tools/coverage.py tree --root rpgvxace-steam` |
| walks landing on the last byte | 117 of 117 | `python tools/marshal48.py walk rpgvxace-steam/SampleMap` |
| root objects | `{'RPG::Map': 117}` | as above |
| distinct classes | 11 | `python tools/rgssdb.py summary rpgvxace-steam/SampleMap` |
| `RPG::Map` ivars | **24, on 117 of 117** | `python tools/rvmap.py fields rpgvxace-steam/SampleMap` |
| distinct ivar names / class-field slots | 68 / 75 | `python tools/rgssjoin.py join --data … --docs …` |
| `Table` payloads closing at residue 0 | 117 of 117 | `python tools/rvmap.py grid rpgvxace-steam/SampleMap` |
| tables whose x,y equal `@width`,`@height` | 117 of 117 | as above |
| declared shape | 3-D, z = **4** | as above |
| cells | 1,085,288 | as above |
| distinct non-zero tile ids | 3,133 | as above |
| tile-id range | 1 .. 8,156 | as above |
| empty cells | 756,658 (69.7196 %) | `python _work/pcts.py` |
| events | **59, in 11 of 117 maps** | `python tools/rvmap.py events rpgvxace-steam/SampleMap` |
| commands per event page | `{1: 59}`, code `{0: 59}` | as above |
| entropy of `.RVDATA2` | 2.0714, 0 blocks above 7.5 | `python tools/entropy.py rpgvxace-steam --tree --by-ext` |

## The tile vocabulary

| figure | value | command |
|---|---:|---|
| tables / images | 22 / 22, stem residue 0 | `python tools/tiletable.py census rpgvxace-steam/rtp/Graphics/Tilesets` |
| rows / fields per row | 2,544 / `{5: 2544}` | as above |
| strings | 12,720 | as above |
| blank lines / empty fields | 0 / 0 | as above |
| encodings | `{'utf-8': 22}` | as above |
| columns containing Japanese | **[2], all 2,544 rows** | `python tools/tiletable.py langs rpgvxace-steam/rtp/Graphics/Tilesets` |
| rows with five distinct strings | 2,400 of 2,544 | `python tools/tiletable.py dupes rpgvxace-steam/rtp/Graphics/Tilesets` |
| rows where all five agree | **0** | as above |
| the id layout, derived from row counts | residue **0** over 3,133 ids | `python tools/rvmap.py join rpgvxace-steam/SampleMap --tilesets rpgvxace-steam/rtp/Graphics/Tilesets` |

## The help file

| figure | value | command |
|---|---:|---|
| ITSF closures | 9, residue 0 | `python tools/itsf.py header rpgvxace-steam/RPGVXAce.chm` |
| chunks / listing entries / index entries | 4 / 356 / 3 | as above |
| reset blocks | 226 | as above |
| LZX output | 7,398,317, residue 0 | `python tools/chmx.py check rpgvxace-steam/RPGVXAce.chm` |
| section-1 entries inside the output | 339 of 339 | as above |
| `.html` entries beginning `<` | 172 of 172 | as above |
| extracted | 340 files, 7,358,681 bytes | `python tools/chmx.py extract rpgvxace-steam/RPGVXAce.chm --out _work/chmx` |
| classes documented | 82 | `python tools/rgssjoin.py join --data rpgvxace-steam/SampleMap --docs _work/chmx/rgss` |
| classes in the data, documented | **11 of 11** | as above |
| in the data and NOT documented | **0** | as above |
| field slots matched on the class's own page | 69 of 75 | as above |
| **field slots matched once inheritance is followed** | **75 of 75** | as above |

## The resources, as rows and not as a chapter

| figure | value | command |
|---|---:|---|
| PNG parsed / closing at residue 0 | 1,456 / 1,456 | `python tools/pngcensus.py rpgvxace-steam --by-dir` |
| PNG chunk CRC-32 verified | 14,035 of 14,035 | as above |
| IHDR shapes | 5 | as above |
| **interlaced PNG** | **310, all in one DLC pack** | `python _work/interlace.py` |
| Ogg parsed / closing at residue 0 | 363 / 363 | `python tools/oggcensus.py census rpgvxace-steam` |
| Ogg page CRC-32 verified | 28,585 of 28,585 | as above |
| Ogg streams flagging end-of-stream | **363 of 363** | as above |
| Ogg playing time | 5,522.628 s | as above |
| MP3 walks landing on the last byte | **23 of 23** | `python tools/mp3frames.py census rpgvxace-steam/dlc/AdventurersJourney_SND/MP3` |
| MP3 frames walked | 60,648 | as above |
| MP3 playing time | 1,584.274 s | as above |
| **MP3 longer than its Ogg twin** | **23 of 23, by 2.03–2.97 frame-times** | `python tools/mp3frames.py pair <MP3> <OGG> --tolerance 0.0784` |
| MIDI / JPEG | **none; both censuses refuse cleanly** | `python tools/smfcensus.py …`, `python tools/jpegcensus.py …` |

## The parties and the personal data

| figure | value | command |
|---|---:|---|
| `Kadokawa` | **0 of 2,026, both encodings** | `python tools/namescan.py rpgvxace-steam --name Kadokawa` |
| `Enterbrain` | 24 eight-bit + 17 UTF-16, 5 files | as above, `--name Enterbrain` |
| `Yoji Ojima` | 9, **UTF-16 only**, 5 files | as above |
| `Yukihiro Matsumoto` | 1, UTF-16 only | as above |
| `Neil Hodgson` | 3, UTF-16 only, 2 files | as above |
| `Lunarea` | **0** | as above |
| e-mail shapes, eight-bit | **19 hits in 11 files** | `python tools/sift.py rpgvxace-steam --group personal` |
| **distinct addresses among the 19** | **3** | `python _work/addrcount.py` |
| hits only a UTF-16 pass finds | 17 | `python tools/utf16sift.py rpgvxace-steam` |
| drive-letter build paths | 3 in 3 files | `python tools/sift.py rpgvxace-steam --group buildpath` |

## Against the collection

| figure | value | command |
|---|---:|---|
| `-doc` directories | 136 | `ls -1d ../*-doc/ \| wc -l` |
| `pc-*-doc` directories | 67 | `ls -1d ../pc-*-doc/ \| wc -l` |
| repositories swept / list files / tokens | 106 / 473 / 159,482 | `python tools/crossall.py notes/sha1-all.txt --collection .. --skip pc-rpgmakervxace-doc` |
| crossings | **26 of 1,935 = 1.3437 %** | as above |
| all with one repository | `pc-rpgmakerxp-doc` | as above |
| the 26, by magic | **26 of 26 `OggS`** | as above, then `head -c4` on each |
| crossings with the same base name | **0** | `python tools/crossnames.py notes/sha1-all.txt ../pc-rpgmakerxp-doc/notes/sha1-all.txt` |
| third-party components listed | 2 | `python tools/vendorhash.py rpgvxace-steam` |

## The equipment

| figure | value | command |
|---|---:|---|
| Python files, on arrival | 558, 0 differing | `python tools/toolsdiff.py ../pc-rpgmakerxp-doc/tools --expect-differing 0` |
| Python files, at publication | 562, **11 differing, 4 new** | `python tools/toolsdiff.py ../pc-rpgmakerxp-doc/tools` |
| forbidden control bytes | 0 of 562 | `python tools/toolscan.py` |
| selftest checks / failures | **221 / 0** over nine tools | `notes/selftests.txt` |
| readers pointed / refusing | 85 / **50** | `python tools/refusals.py rpgvxace-steam` |
| `argparse` share, **sixth time** | 23 | `python tools/refusalclass.py notes/refusals.txt` |
| tools crashing on an empty directory | **216 of 561**, unchanged | `python tools/dirguard.py --survey --tools tools` |
| **tools dying on a non-Latin-1 file name** | **7 of the 9 that print one** | `python tools/nameguard.py --survey --tools tools` |
| rule-7 violations in tracked files | 0, control firing | `python tools/pathcheck.py --needle <a directory this work lives under>` |
| rule-0 refusals | see [12](12-the-tools.md) | `python tools/rule0hook.py --report` |
| published percentages recomputed | 29, **1 wrong** | `python _work/pcts.py` |
