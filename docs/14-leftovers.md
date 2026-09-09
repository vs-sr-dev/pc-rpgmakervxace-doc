# 14 — leftovers: thirteen questions with a reason each, and thirty-three initialisms of which nine the object expands itself

*Measure: every question below names what would answer it and why this session
did not. The initialism table splits four ways and the four counts sum to the
total, which is the discipline `pc-rpgmakerxp-doc/docs/16` set and which is the
only thing that stops an expansion list from becoming a list of guesses.*

---

## The thirteen questions

**1. What `.bind` is.** Second object, 562,176 bytes both times, the same first
768 bytes and the same 6,084-byte run at offset 809, two different high-entropy
payloads. **Thirteen candidate vendor and packer names occur zero times in
either specimen, in both encodings** — while `steam` occurs nine times in the
surrounding executable and zero times in the section
([09](09-the-programs.md)). *What would answer it:* a third specimen of the
same size from a product outside this family, or the same section in a build
whose provenance is documented. Not in this object.

**2. What varies by exactly one hour between two Japanese-locale help
compiles.** Sixteen hours on one, seventeen on the other, both landing within
eight seconds of a whole hour. A fixed zone bias is dead by arithmetic. *What
would answer it:* **a sixth ITSF specimen with a `0x0411` header compiled
between late March and late October whose whole-hour term is sixteen** — or one
compiled in winter whose term is seventeen. The measurement is named in
[08](08-the-clocks.md) and it is one command once the specimen exists.

**3. What `ws2_32.dll #116` is.** Second object, second ordinal — the previous
one imported `#55`. The ordinal-to-name map is not in either object and Winsock
does not ship one. *What would answer it:* a Microsoft import library, which is
outside the perimeter. **Two disagreeing ordinals is more than the previous
session had and is still not an answer.**

**4. Whether the 96 `dlc\Bonus\Portraits` join the Generator.** 96 files,
9,354,791 bytes, in a preorder pack; 508 files in `Generator\`, which is a
character-part vocabulary. *What would answer it:* a geometry and palette
comparison of the kind `pngpair.py` makes, pointed across the two directories
rather than at this object's own repeated hashes. **Not run, and it is the
single most likely thing to be worth running next.**

**5. What the 117 maps are pictures *of*.** The grids are read, the tile ids
are resolved to bands, the events are read and are empty. **Nobody has rendered
one**, and rule 4 forbids running the object. *What would answer it:* composing
the four layers against the tileset images, which is drawing and not decoding
and would need an argument for why it is documentation.

**6. What the `@note` field of each map contains.** One of the 24 ivars, an
`RString` on 103 maps and an encoding-tagged one on 14. Read as a type and not
as a value.

**7. Whether the 23 MP3 and 23 OGG are the same *music*.** They are the same
**length**: 23 of 23 agree, the MP3 longer every time by 2.03 to 2.97
frame-times, which is what encoder padding does and what a Vorbis granule count
does not ([02](02-the-technical-sheet.md)). **A frame walk decodes no audio**,
so this is as far as duration goes. *What would answer it:* decoding both, which
is a different tool and a different claim.

**8. What the two language DLLs actually say.** 2.9 MB of resource tree each,
compared here by section, size and resource-directory arithmetic — **residue 0
on a 27,136-byte difference** — and not by string. **The Italian DLL has one
section and no code**, which is the structural finding
([09](09-the-programs.md)). What is in the string tables is a translation and
reading it is reading a translation.

**9. Whether `Projects\Game.exe` is what a new project would receive.** 140,800
bytes, `FileDescription` **`RGSS3 Player`**, COFF 2011-10-06 — five months
before RGSS3's own link time. *What would answer it:* creating a project, which
is running the object.

**10. Whether 2011 is itself a release date.** The copyright field says 2011
and every artefact of the localisation says 2012 ([08](08-the-clocks.md)). A
product made in one year and released in another is the obvious reading and it
is **not in the bytes**, so the cell takes 2012 and the 2011 is reported beside
it rather than explained.

**11. What the 3,651 published-and-unused tile ids are.** The derived bands
cover 6,784 ids and the 117 maps use 3,133. A sample map does not use every
tile in its tileset, so the number is expected — but **which** pages are unused
is a fact about what these demonstration maps demonstrate, and it is not
measured.

**12. Whether any of the 1,909 non-crossing hashes is a re-encoding of
something published next door.** Zero shared bytes is not zero shared pictures,
this object has 1,456 PNG against the previous object's 548, and a hash cannot
answer it ([11](11-against-the-collection.md)). **Inside this object the same
question has an answer**: `pngcensus.py` reports **1,376 distinct IDAT streams
over 1,456 files** and **153 files sharing one** — and 175 files share a
repeated whole-file hash, of which 20 are the VL Gothic documents and 2 are
bitmaps. **175 − 20 − 2 = 153, residue 0**, so inside this tree every shared
pixel stream is also a shared file and no picture is shipped twice in different
wrapping. Across the boundary, nobody has asked.

**13. Who the three resource packs' authors are, beyond one readme line
each.** `Tyler Warren` occurs 8 times in 1 file; the Adventurer's Journey and
Royal Tiles readmes name their authors once apiece; **and all three carry the
same contact address, which is none of theirs** ([10](10-whose-bytes.md)).
*What would answer it:* anything outside the object, which is outside the
perimeter. What the object supports is that three packs by three people were
assembled and distributed by one party, and it supports that with an
arithmetic rather than a claim.

*Three questions the pre-briefing left open are not on this list because they
were answered: what the 310 interlaced PNG are ([09](09-the-programs.md)),
whether this help file declines to specify `.rgss3a` ([07](07-the-help-file.md)),
and what the 22 tileset tables say ([06](06-the-tile-vocabulary.md)).*

---

## Thirty-three initialisms

**Nine are demonstrated from the object itself**, which is more than any
previous session in this family managed, and the reason is that this object
ships its own manual and its own installer script.

### Demonstrated from the object — 9

| | expansion | where |
|---|---|---|
| **RGSS** | **Ruby Game Scripting System** | `ProductName` in `RGSS301.dll` and `Projects\Game.exe`, written by the linker; and in the help file three times |
| **BGM** | **background music** | `/rpgvxace/1140_intro_supporttool.html`, in one sentence with the next three |
| **BGS** | **background sounds** | the same sentence |
| **ME** | **music effects** | the same sentence |
| **SE** | **sound effects** | the same sentence |
| **EULA** | **END USER LICENSE AGREEMENT** | `dlc\Bonus\Readme.txt`, first line, in capitals |
| **RVDATA2** | `.rvdata2` → **`RPGVXAce Data`** | `VXAce_install.vdf`, the registered description |
| **RVPROJ2** | `.rvproj2` → **`RPGVXAce Project`** | the same file |
| **RGSS3A** | `.rgss3a` → **`RPGVXAce.Archive`** | the same file — the format the help file then declines to specify |

*One sentence of the vendor's own manual expands four of the nine. It was found
by grepping the LZX stream this collection learned to decode one object ago,
which is the second time that decoder has paid for itself in a chapter that is
not about it.*

### Derived here — 5

| | derivation |
|---|---|
| **RV** in `.rvdata2` / `.rvproj2` | the previous product's were `.rxdata` / `.rxproj` for **RPG maker XP**; this product is **VX Ace**; the letter tracks the product line. The `2` is VX Ace against VX, which this session did not document |
| **ENU / ITA** | the two language DLLs' names and `InternalName LangENU`, against `UserConfig language "italian"` |
| **IHDR / IDAT / PLTE** | PNG chunk type codes, read from the 14,035 chunks walked |
| **PMGL / PMGI** | the ITSF directory chunk tags, read from the four chunks |
| **A1..A5, B, C** | the tileset page kinds, derived from 22 file names and confirmed by their row counts closing at 2,544 ([06](06-the-tile-vocabulary.md)) |

### Attributed to a public source — 13

`PE` Portable Executable, `COFF` Common Object File Format, `DLL` Dynamic Link
Library, `LCID` Locale Identifier (Microsoft); `PNG` Portable Network Graphics,
`CRC` Cyclic Redundancy Check (W3C / ISO 15948); `MP3` MPEG-1/2 Audio Layer III
(ISO/IEC 11172-3); `TTF` TrueType Font (Apple, Microsoft); `PDF` Portable
Document Format (ISO 32000); `BMP` bitmap (Microsoft); `EUC` Extended Unix
Code; `UTF` Unicode Transformation Format (Unicode, RFC 3629); `UUID`
Universally Unique Identifier (RFC 4122).

**These are attributions and not measurements.** Every one is checkable against
a document nobody in this collection wrote, and none of them is in the object.

### Not demonstrated — 6

| | why not |
|---|---|
| **ID3** | not an acronym in its own specification; the usual gloss is a backronym |
| **ZIP** | not an acronym; a name |
| **LZX** | not an acronym; a name |
| **SFNT** | disputed even among the font formats' own documents |
| **ITSF** | the usual gloss is *Info-Tech Storage Format* and **no vendor document says so**, which is the whole reason this container sits in the DECODED bucket rather than SPECIFIED |
| **HHA** | the compiler string is `HHA Version 4.74.8702` on all five specimens and nothing expands it |
| **RTP** | **and this one is a finding.** The help file has a whole section on it, calls it `RGSS-RTP`, describes `RTP=` in `Game.ini` as *"the trademark name of the RGSS-RTP the game is using"* — **and never expands the three letters.** A vendor's own manual devoting a section to a thing without saying what it stands for is worth recording, and it is why this entry is here rather than in the attributed column |

**9 demonstrated + 5 derived + 13 attributed + 6 not demonstrated = 33**, and
the four counts sum to the total.

*This heading said thirty-two until the four groups were added up. It is
recorded because it is the same failure the rest of this repository is about —
a number carried in a header while the rows underneath moved — and because a
list of expansions whose own arithmetic does not close has no business
correcting anybody else's.*
