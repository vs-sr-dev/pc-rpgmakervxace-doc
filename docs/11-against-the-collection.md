# 11 — against the collection: twenty-six sound effects survive a generation, none of them under its own name

*Measure: `ls -1d ../*-doc/ | wc -l` and `ls -1d ../pc-*-doc/ | wc -l`, run
**before** the sweep; `python tools/crossall.py notes/sha1-all.txt --collection
.. --skip pc-rpgmakervxace-doc`, in `notes/crossall.txt`; `python
tools/crossnames.py notes/sha1-all.txt ../pc-rpgmakerxp-doc/notes/sha1-all.txt`,
in `notes/crossnames.txt`; `python tools/vendorhash.py rpgvxace-steam`, in
`notes/vendorhash.txt`.*

---

## The denominators, counted before the result

```
ls -1d ../*-doc/    | wc -l      136
ls -1d ../pc-*-doc/ | wc -l       67

crossall's own report:
  repositories swept       106
  list files swept         473
  hash tokens read     159,482
```

**All five re-derived, and the first two include this directory.** The 136 does
not move after this session, because publishing this repository does not create
a new one. All three of `crossall.py`'s own figures moved against the previous
run — 105 → 106, 468 → 473, 158,096 → 159,482 — because `pc-rpgmakerxp-doc` was
published between them and publishes five files under `notes\`.

`--skip pc-rpgmakervxace-doc` is required, and the sweep also excludes the
empty-file sha1, which occurs 57 times in 16 repositories and is a trap rather
than a crossing.

---

## Twenty-six of one thousand nine hundred and thirty-five

```
python tools/crossall.py notes/sha1-all.txt --collection .. --skip pc-rpgmakervxace-doc

   min bytes    my hashes    crossings         rate
           0         1935           26      1.3437 %
        4096         1866           26      1.3934 %
       65536          717            6      0.8368 %
```

**Every one of the twenty-six is with `pc-rpgmakerxp-doc` and none is with any
of the other 105 repositories.**

**And all twenty-six were checked by magic and not by extension**, because this
whole session is about a tool that trusted a file name:

```
grep "^   mine :" notes/crossall.txt | sed 's/.*mine : //' \
  | while read f; do head -c4 "rpgvxace-steam/$f" | od -c | head -1; done \
  | sort | uniq -c
     26 0000000   O   g   g   S
```

**Twenty-six of twenty-six begin `OggS`.** Twenty-two are in `rtp/Audio/SE` and
four in `rtp/Audio/BGS`; not one is a graphic, a font, a map or a piece of
music. That is the pre-briefing's fourth unverified claim and it holds.

The collection's six rates are now **1 of 12**, **10 of 962**, **0 of 477**,
**368 of 731**, **0 of 913** and **26 of 1,935**.

---

## None of them kept its name

```
python tools/crossnames.py notes/sha1-all.txt ../pc-rpgmakerxp-doc/notes/sha1-all.txt

   same base name in both objects : 0
   renamed                        : 26
      spaced            0     prefixed          0     retranslated     26
   the three classes sum to the renamed total : True  (0 + 0 + 26 = 26)

      005-System05    -> Equip1        006-System06    -> Shop
      007-System07    -> Save          008-System08    -> Load
      010-River01     -> River         011-System11    -> Collapse2
      012-System12    -> Collapse1     013-Fire01      -> Fire
      014-Move02      -> Fall          016-Drips01     -> Drips
      018-Darkness01  -> Darkness      018-Teleport01  -> Teleport
      022-Dive02      -> Dive          026-Door03      -> Open3
      027-Door04      -> Close3        033-Switch02    -> Switch2
      034-Switch03    -> Switch3       044-Chest01     -> Chest
      045-Push01      -> Push          046-Book01      -> Book1
      059-Applause01  -> Applause1     078-Small05     -> Crow
      084-Monster06   -> Monster3      085-Monster07   -> Monster4
      086-Action01    -> Skill1        087-Action02    -> Magic1
```

**Zero of twenty-six kept its base name, and the rename has a shape.** The
`NNN-Category##` scheme that four consecutive products used is gone, and what
replaced it is **what the sound is for**: `008-System08` is `Load`,
`044-Chest01` is `Chest`, `086-Action01` is `Skill1`. `crossnames.py`'s three
rules put all twenty-six in `retranslated`, and they are right to: none is the
old name with a space inserted or a prefix added.

**The two most informative are the ones where the category itself moved.**
`078-Small05` became **`Crow`** — a numbered slot in a size category became a
bird. `018-Darkness01` became `Darkness` and `018-Teleport01` became
`Teleport`: **two different sounds shared the number 018 in the old scheme**,
because the number indexed the category and not the library. A scheme that
needs `018-Darkness01` and `018-Teleport01` to coexist is a scheme that has
stopped being an index, and the successor abandoned it.

---

## Three measurements now exist, and they say the same thing three ways

`pc-rpgmakerxp-doc/docs/12` reported **0 of 913** and corrected its
predecessor's claim: *a published tree next door is necessary for a crossing
and is not sufficient.* It measured both sides and found that between the 2003
and the XP not one byte survived — new audio format, new graphics, new database
format, new toolchain.

```
  2003 -> XP        368 of 731   =  50.3420 %
  XP   -> VX Ace      0 of 913   =   0.0000 %      (measured from the XP's side)
  XP   -> VX Ace     26 of 1935  =   1.3437 %      (measured from this side)
```

*(The 0 of 913 and the 26 of 1,935 are the same event counted from opposite
ends: the previous session swept before this object existed, so its denominator
could not contain these files. The pair is not a contradiction and the two
figures are not comparable to each other — only to their own denominators.)*

**So the rate measures a re-use decision, and this time the decision was "keep a
handful".** The audio format did **not** change at this step — `.ogg` to
`.ogg`, where the previous step was `.wav` to `.ogg` — so bytes *could* have
survived wholesale, and 22 of 275 sound effects and 4 of 10 ambiences did.
**The other 253 did not.** This is not a library inherited; it is a library
rebuilt with a few files kept, and the renaming says the rebuild was
deliberate.

**Which sharpens the sentence rather than replacing it.** A published tree next
door is necessary and not sufficient; a shared format is also necessary and
also not sufficient; and what the rate actually measures is how much of a
predecessor a publisher chose to carry.

---

## What does not cross and might have

* **The fonts.** `VLGothic`'s two faces are 3,883,852 and 4,013,852 bytes here
  and no previous object shipped them at all.
* **Scintilla.** `SciLexer.dll` is in this object and in the previous one, at
  **2.22** and **1.58**, so the hashes cannot cross and **the vendor does**.

  ```
  python tools/vendorhash.py rpgvxace-steam        (notes/vendorhash.txt)

  250450334148…  6944256  RPGVXAce.exe   Microsoft     HTML Help runtime   -     @5286928
  95c9415d313d…   545280  SciLexer.dll   Neil Hodgson  Scintilla           2.22  @485160

  components : 2   carriers : 0
  ```

  **The version column is populated**, which is the repair
  `pc-rpgmaker2003-doc/docs/16` was scored a half for lacking, and this is the
  first object on which the list can be joined against a previous object's:
  one vendor, two builds, two hashes, two version strings, two linker versions,
  seven years apart. That is exactly the case the file was created for.
* **`.bind`**, 562,176 bytes in both editors, sharing its first 768 bytes and a
  6,084-byte run, and crossing in neither direction because the payloads differ
  ([09](09-the-programs.md)).

---

## And what a zero would not have meant

Twenty-six crossings means twenty-six shared *byte strings*. It does not mean
twenty-six shared *sounds*, and the converse matters more: **1,909 non-crossing
hashes do not mean 1,909 new pictures.** This object has 1,456 PNG against the
previous object's 548, and whether any of them is a re-encoding of something
published next door is not measured here and cannot be measured by a hash.
`pngpair.py` exists for that comparison and was pointed at this object's own
repeated hashes rather than across the boundary ([14](14-leftovers.md)).
