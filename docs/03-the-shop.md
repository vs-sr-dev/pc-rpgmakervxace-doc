# 03 — the shop: two totals that fail to close, and each failure names something exactly

*Measure: `python tools/steamacf.py --path <steamapps>/appmanifest_220700.acf
--root rpgvxace-steam --check`, in `notes/steamacf.txt`; `python
tools/mtimes.py rpgvxace-steam --waves`, in `notes/mtimes-waves.txt`; `python
tools/depotsplit.py --root rpgvxace-steam --path … --rest 220701 --declare …`,
in `notes/depotsplit.txt`. The depot mapping is the pre-briefing's first
unverified claim and every figure below was produced by walking the tree.*

---

## Four objects closed at residue 0 because nobody had ever opened them

```
python tools/steamacf.py --path <steamapps>/appmanifest_220700.acf \
    --root rpgvxace-steam --check

SizeOnDisk declared      : 342514066
the tree, counted        : 342722404 over 2026 files
residue                  : -208338

installed depots:
   220701           62332617      220702          202842120
   220708           16523099      265461           57491682
   271961           15516018      291473            1386605
   sum           356092141
   residue against SizeOnDisk : -13578075
```

**Two failures to close, and the interesting thing about both is that they are
measurements.** `pc-rpgmaker2000-doc/docs/03` established what a closure at
residue 0 is worth — *a total that closes says the tree WEIGHS what Steam
thinks it weighs, and says nothing about any individual file*. What it did not
say, because no object had produced one, is what a **non-zero** residue is
worth. This object produces two, and each one is worth more than the closure
would have been.

---

## The first residue is the owner

**−208,338 is `Projects\cd32.zip` at 208,185 bytes plus `Projects\cd32.ini` at
153.** 208,185 + 153 = **208,338**, residue 0.

The tree is heavier than the shop believes by **exactly** the two files the
shop did not put there. `LastPlayed` is **1774010264** and not `"0"`, which is
the first time that has been true of anything in this collection: four RPG
Makers and a dozen games before them had been bought and never launched.

**What this chapter says about those two files, and what it does not, is
[10](10-whose-bytes.md)'s to settle.** Here they are a quantity: 208,338 bytes
that make an arithmetic fail, and the failure is how they were found.

---

## The second residue is the languages nobody installed

**−13,578,075 is depot 220708 minus one file.**

```
16,523,099    what depot 220708 declares
 2,945,024    RPGVXAceITA.dll, the only part of it on disk
-----------
13,578,075
```

`UserConfig` says `language "italian"`. **Depot 220708 is the language packs,
and Steam installs the one this machine asked for.** The manifest declares the
depot's full size because that is what the depot contains; the disk holds the
2,945,024 bytes of the interface this installation actually runs in.

**Two residues, two different kinds of thing.** The first is bytes the shop does
not know about. The second is bytes the shop knows about and did not deliver.
Neither is an error and neither would exist if the object had been left in its
wrapper.

---

## And with those two facts everything closes twice, by walking

The previous object's two depots were its two subtrees, and
`pc-rpgmakerxp-doc/docs/03` wrote that the shop's partition and the
filesystem's partition were the same partition. **On this object they are
not**, and `depotsplit.py` could not express the difference at all, because it
grouped by top-level directory name and here the mapping cuts **across** one
directory and **inside** another.

So the tool was given a `--group` that takes a **path** — a directory, or a
single file — with longest-match-wins, and a `--rest` for whatever is left
([12](12-the-tools.md)).

```
python tools/depotsplit.py --root rpgvxace-steam \
  --path "265461=dlc/AdventurersJourney_SND" \
  --path "271961=dlc/Tyler Warren RPG Battlers 1st 50" \
  --path "291473=dlc/RoyalTileset_GFX" \
  --path "220702=rtp" \
  --path "220708=RPGVXAceITA.dll" \
  --path "OWNER=Projects/cd32.zip" --path "OWNER=Projects/cd32.ini" \
  --rest 220701 --declare …

  label        files      counted     declared   residue  paths
  220701         864     62332617     62332617         0  <everything else>
  220702         780    202842120    202842120         0  rtp
  220708           1      2945024      2945024         0  RPGVXAceITA.dll
  265461          47     57491682     57491682         0  dlc/AdventurersJourney_SND
  271961         320     15516018     15516018         0  dlc/Tyler Warren RPG Battlers 1st 50
  291473          12      1386605      1386605         0  dlc/RoyalTileset_GFX
  OWNER            2       208338       208338         0  Projects/cd32.zip, cd32.ini
  SUM           2026    342722404

  every file claimed by exactly one group : True
  files no group claimed                  : 0
  the groups cover the tree, residue      : 0
  groups whose counted bytes differ from the declared figure : 0
```

**Seven groups, seven residues of zero, 2,026 files claimed exactly once, and
the tree covered.** Every figure in that table was produced by walking. No
group's total is the tree's total minus another group's, and the tool cannot be
made to produce one that way.

---

## `dlc\Bonus` is in a directory called `dlc\` and is not a DLC

The 864 files of `220701` include **`dlc\Bonus`**, and only arithmetic says so:

```
dlc                                          476 files     83751594 bytes
dlc/Bonus                                     97 files      9357289
dlc/AdventurersJourney_SND                    47 files     57491682   = depot 265461
dlc/Tyler Warren RPG Battlers 1st 50         320 files     15516018   = depot 271961
dlc/RoyalTileset_GFX                          12 files      1386605   = depot 291473

47 + 320 + 12 + 97 = 476, residue 0
57,491,682 + 15,516,018 + 1,386,605 = 74,394,305
83,751,594 - 74,394,305 = 9,357,289 = dlc\Bonus exactly
```

**`dlc\Bonus` is a preorder bonus, not a purchase**, which is why it travels in
the base depot with the editor. A directory name is a convenience for whoever
laid the tree out; the depot boundary is a commercial fact, and on this object
the two do not coincide. **That is the falsification of the sentence
`pc-rpgmakerxp-doc/docs/03` wrote**, and it took two objects to arrive: the
previous one had two depots that were two subtrees, and it read that as a
property of the shop rather than of that tree.

---

## The second witness, which knows nothing about the manifest

```
python tools/mtimes.py rpgvxace-steam --waves

wave 1   2025-10-16 13:59:10 .. 2025-10-16 13:59:55   2024 files   342514066 bytes   99.94%
wave 2   2026-03-20 13:37:42 .. 2026-03-20 13:37:42      2 files      208338 bytes    0.06%

--- wave 2 (2 files) ---
    2026-03-20 13:37:42       208185  Projects/cd32.zip
    2026-03-20 13:37:42          153  Projects/cd32.ini
```

**Wave 1's byte total is `SizeOnDisk` to the byte.** `mtimes.py` partitions by
timestamp gap and has never read a manifest; the manifest was written by Valve
and has never seen a timestamp. **They split the same 2,026 files the same
way, and neither was told about the other.**

`pc-rpgmaker2000-doc/docs/08` established that *a delivery mechanism that
verifies the bytes destroys the dates*, and three objects confirmed it. This is
the fourth confirmation and the first exception: **two dates in this tree are
real, and they are real because Steam did not write them.**

Two thousand and twenty-four files in **forty-five seconds**, and then two
files **five months later**.

---

## The ratio, and which denominator it uses

`BytesToDownload` is **321,169,744** and `BytesToStage` is **342,514,066**, a
ratio of **1.0665** — the lowest in the family, against 1.1183, 1.5194 and
1.3355, on a tree that is 87 % PNG and Ogg by weight. Two formats that are
already compressed do not compress again.

**And there are two ratios here, not one.** `compratio.py` prints

```
the shop declares BytesToDownload : 321169744
             against BytesToStage : 342722404
             a declared ratio of  : 1.0671
```

— and **342,722,404 is not what the shop declares.** It is the walked tree,
which includes the owner's two files. The shop's own `BytesToStage` is
342,514,066 and its own ratio is 1.0665. The tool has labelled its own walk as
the shop's declaration, which is a rule-3 failure inside an instrument
([13](13-corrections.md)): **every figure names its denominator, and this one
names somebody else's.** The difference is 208,338 bytes and it shows up in the
fourth decimal place — which is exactly how far a residue of one part in 1,644
propagates, and exactly why the label matters.
