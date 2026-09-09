# 10 — whose bytes: nineteen occurrences are three addresses, and the fifth rule is about work that is not the object's

*Measure: `python tools/sift.py rpgvxace-steam --group personal`, in
`notes/sift-personal.txt`; `python tools/utf16sift.py rpgvxace-steam`, in
`notes/utf16sift.txt`; `python _work/addrcount.py` and `_work/addrparty.py`, in
`notes/addrcount.txt` and `notes/addrparty.txt`; `python tools/namescan.py
rpgvxace-steam --name …`, in `notes/namescan.txt`. No address appears in this
repository.*

---

## Nineteen is a count of occurrences, and the pre-briefing said so and did not do it

```
python tools/sift.py rpgvxace-steam --group personal
e-mail shape   19 hits in 11 blobs
positive control fired : YES (9 hits)   negative control quiet : YES

python tools/utf16sift.py rpgvxace-steam
hits that only a UTF-16 pass finds : 17
```

Nineteen, in eleven files, where the previous object had **zero at eight bits
and one at sixteen** and `pc-rpgmakerxp-doc/docs/11` needed a chapter to say
that `sift.py` could not see it. The pre-briefing observed that the honest
version of this figure counts how many of the nineteen are duplicates of each
other, and that it had not counted.

**Counted, it is three.**

```
python _work/addrcount.py

eight-bit e-mail-shaped hits : 19        files carrying at least one : 11
DISTINCT addresses           : 3         occurrences : 19   residue : 0
distinct domains             : 2

  address     times  files
  A05c5ad         8  VLGothic/{Changelog,LICENSE,LICENSE.en,README} x2 trees
  Ac2a902         8  the same eight files
  Ad8c1bb         3  the three DLC readmes
```

*(The labels are six hex digits of a hash of the address, so that two
occurrences can be seen to be one address without the address being written
down.)*

**Two of the three are one Japanese open-source font project's licence set,
which this object ships twice** — `VLGothic\` and `rtp\Fonts\VLGothic\` hold the
same ten files, and ten of the object's eighty-four repeated hashes are exactly
those ([09](09-the-programs.md)). Four files × two trees × two addresses = 16 of
the 19.

**The third is one address in three third parties' readmes.**

```
python _work/addrparty.py

  readme_TheAdventurer'sJourney.txt   addresses 1   names Degica True
  readme.txt (Royal Tiles)            addresses 1   names Degica True
  readme.txt (Tyler Warren)           addresses 1   names Degica True
  Readme.txt (Bonus)                  addresses 0   names Degica True

  distinct addresses across the four readmes : 1
  its domain contains 'degica'   : False
  its domain contains 'enterbrain' : False
  its domain is a .com           : True
```

**Three independently authored resource packs by three different people carry
the same contact address, and all four DLC readmes name Degica.** It is not any
of the three artists' address and it is not the publisher's own domain: it is
one storefront's support address, reproduced in three documents by whoever
packaged them. **So "three named third parties" have one point of contact
between them**, and that is a fact about how the packs were distributed rather
than about anybody personally.

---

## The rule is not reopened, and the arithmetic is what moved

Four objects settled this and the wording does not need touching:

| | |
|---|---|
| `pc-rpgmaker95-doc/docs/10` | publish what claims credit, redact what routes a message |
| `pc-rpgmaker2000-doc/docs/10` | where it cannot be established that an address has stopped routing, redact |
| `pc-rpgmaker2003-doc/docs/12` | a device identifier is neither credit nor routing, and is redacted anyway |
| `pc-rpgmakerxp-doc/docs/11` | an address a linker wrote into a version resource is the most deliberate publication and the least aimed at this buyer |

**Nineteen occurrences of three addresses change the arithmetic and not the
rule**, and the reason is that the population did not change in kind. All three
are third parties'; none is the publisher's; each is published by its owner
inside a document its owner wrote. `SciLexer.dll`'s `CompanyName` recurs
unchanged one build later and is redacted by `verres.py` by program, exactly as
before — the tool prints `Neil Hodgson [e-mail redacted: see docs on the
personal data]` without this session touching it.

**What the count does change is a sentence somebody might otherwise have
written.** "Nineteen e-mail addresses in this object" would have been wrong by a
factor of six, and the thing that made it wrong is a font shipped twice.

---

## A sweep's pattern is part of its result

Worth one paragraph because it nearly produced a wrong number here. A first
draft of `addrcount.py` used a looser e-mail pattern than `sift.py`'s — `{1,}`
instead of `{3,}` either side of the `@`, `{2,}` instead of `{2,4}` on the
top-level domain — and reported **50 hits in 36 files, 30 distinct addresses**.

**Thirty-one of the fifty were byte sequences inside compressed PNG and Ogg
payloads.** A run of bytes in a zlib stream that happens to look like an e-mail
address is not an address, and the difference between nineteen and fifty is
entirely the pattern. The script now copies the box's own regular expression
character for character and says in a comment why.

---

## The parties, and there are nine

```
python tools/namescan.py rpgvxace-steam --name …

  name                8-bit  files   UTF-16  files
  Kadokawa                0      0        0      0
  Enterbrain             24      5       17      5
  Degica                  4      4        0      0
  Yoji Ojima              0      0        9      5
  Yukihiro Matsumoto      0      0        1      1
  Neil Hodgson            0      0        3      2
  Tyler Warren            8      1        0      0
  Ruby Version            0      0        1      1
  Scintilla Version       0      0        1      1
  Lunarea                 0      0        0      0
```

**`Kadokawa` is 0 of 2,026 in both encodings, for the second object running.**
The two products before these were published by KADOKAWA GAMES and said so;
these two do not mention the name at all.

**Four parties are visible only to a sixteen-bit pass** — `Yoji Ojima`,
`Yukihiro Matsumoto`, `Neil Hodgson`, and the two version banners. That is the
blindness `pc-rpgmakerxp-doc/docs/11` made a chapter of, and `utf16sift.py` is
the instrument it produced. `RPGVXAce.exe`'s About block carries **`Ruby
Version 1.9.2`**, **`Copyright (C) 1993-2010 Yukihiro Matsumoto`** and
**`Scintilla Version 2.22`**, all in UTF-16.

**And `Lunarea`, who made the previous object's bonus pack, is not here.**

The nine: Enterbrain; Yoji Ojima; Yukihiro Matsumoto (Ruby); Neil Hodgson
(Scintilla); Degica; Tyler Warren; the Adventurer's Journey and Royal Tiles
authors; the VL Gothic / M+ / Sazanami font projects, with eight licence
documents between them; and Valve, whose two DLLs name two of Valve's build
machines in a `FileDescription`. **`winslave04` and `winslave05` are
published**, for the same reason Microsoft's `f:\dd\vctools\…` was published on
the previous object: an artefact from a third party's own infrastructure, put
there by that third party, in a signed binary they shipped.

---

## The fifth rule, and it is about work that is not the object's

**This is the first object in seventy-eight that contains work by the person
who owns the copy**, and the owner's instruction was explicit: *they may be
cited, without going into detail.*

Four rules exist for whose bytes these are. **None of them covers this**,
because all four are about a *publisher's* material reaching a buyer, and this
is a buyer's material sitting inside a publisher's tree. So the rule is written
here, in the shape the other four are written in — **a sentence, a test
somebody who disagrees can apply, and a reason.**

> **The rule.** What the owner of a copy made is not the object. It is measured
> exactly where it changes a measurement of the object — a residue, a wave, a
> file count — and it is not read.
>
> **The test.** Remove the file and ask whether a published figure moves. If a
> figure moves, the file is inside the perimeter as a *quantity* and its size,
> its name and its timestamp are reportable. If no figure moves, it is outside
> the perimeter and does not appear at all. **Nothing in the file's content is
> ever inside the perimeter, whatever the arithmetic says.**
>
> **The reason.** The object is a published product and every previous rule in
> this pipeline is about what a publisher chose to put in front of a buyer.
> The owner's own work was never published to anybody. Measuring it is
> unavoidable — a shop's total that does not close is a fact about the tree —
> but the thing that makes the measurement worth reporting is *the two
> independent instruments agreeing*, and neither of those instruments has to
> open the file.

**Applied here, it produces four sentences and no fifth.**

* `Projects\cd32.zip` is **208,185 bytes** and `Projects\cd32.ini` is **153**.
  Together they are the shop's **−208,338** residue and the whole of mtime wave
  2, five months after wave 1 ([03](03-the-shop.md)). **Two instruments that
  know nothing about each other name the same two files.**
* **`cd32.zip` was not opened.** That it is a ZIP is a magic byte and that is
  everything the coverage table needed; it is one of the 2,025 SPECIFIED files
  and contributes 0.0607 % of the tree.
* **`cd32.ini` is a `Game.ini`, and the awkwardness of that is the point.** A
  `Game.ini`'s **keys** are the vendor's format and its **values**, for the
  keys the format defines, are the vendor's defaults. So the file is compared
  against the format rather than transcribed, and what is published is the
  comparison:

  ```
  python _work/gameini.py                              (notes/gameini.txt)

  bytes   : 153      sections : ['[Game]']
  key=value lines    : 7      lines of neither : 0

  key        equals the vendor default
  RTP        True          Library   True          Scripts   True
  Title      n/a           the owner's, and cited

  keys present that are NOT in the four the format documents : 3
  ```

  **Three of the four documented keys hold the vendor's default value
  exactly**, and three further keys are present that the format's four do not
  include — Steam Cloud bookkeeping, whose *names* are structure and whose
  values are not printed here or anywhere. **The `Scripts` key is the one whose
  extension the vendor's own manual gets wrong** ([07](07-the-help-file.md)):
  the manual says `Data\Scripts.rvdata`, the format says `.rvdata2`, and the
  only `Game.ini` in this tree — which the vendor did not write — says
  `.rvdata2` too. **A buyer's configuration file is a second witness against a
  publisher's documentation**, and that is as good an argument as this chapter
  could have for the structural level being the right one.
* And there is exactly **one** `.ini` in `Projects\`. The editor ships a
  template project with a player, a splash bitmap and four workshop images, and
  **no `Game.ini` at all** — so the owner's file is the only specimen of that
  format in the object, and the help file is its only other witness.
* The project is titled **`CD32`**, which is a platform this same collection
  documents in a dozen other repositories. That is a fact about the collection
  and it gets this sentence and no more.

**And what the rule refuses is the thing that would have been easiest.** There
is a 208,185-byte ZIP here, this box has `zaccount.py`, and opening it would
have taken one command. The permission that was given was explicit and limited,
and a limited permission is not a smaller version of an unlimited one.
