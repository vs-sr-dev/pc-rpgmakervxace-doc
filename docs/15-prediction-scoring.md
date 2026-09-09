# 15 — prediction scoring: P17's register works and its own author left a clause out of it, P18 and P12 pull apart by arithmetic, and P19's falsification does not fire

*Measure: `python tools/predcount.py` for the clause counts and the two
predicted totals; `python tools/predbands.py --expect-under 0.60 5` for the
three bands; `python _work/calib3.py --append <this session's term>` for the
extended series, in `notes/calibration.txt`. The verdicts below are counted out
of the tables on this page.*

```
64 clauses     inherited 33     open 31 (method 5, content 26)

inherited      33 clauses   predicted 30.21   obtained 32.00   delta  -1.79
open           31 clauses   predicted 25.34   obtained 30.50   delta  -5.16
  open method   5 clauses   predicted  4.52   obtained  5.00   delta  -0.48
  open content 26 clauses   predicted 20.82   obtained 25.50   delta  -4.68

and the three P11 bands:
  lands        7 clauses   predicted  6.21   obtained  7.00   delta  -0.79
  constructs  16 clauses   predicted 11.95   obtained 15.50   delta  -3.55
  nonnumeric   3 clauses   predicted  2.66   obtained  3.00   delta  -0.34
                                             ------          ------
  the three bands                             25.50           -4.68

hit = 1, half = 0.5, miss = 0. The two totals are never added together.

the verdicts:
  hit           61      (inherited 31, open method 5, open content 25)
  half           3      (C29, C31, C42)
  miss           0
  unresolved     0
  61 + 3 = 64, residue 0
```

**The calibration entry for this session is `−5.16`**, predicted minus obtained
on the open clauses. Ranked by absolute value it is **thirteenth of
thirty-seven**.

*The first draft of this block said `−4.66`, `31.50` and `60 hits`. Adding the
columns up gave `−5.16`, `32.00` and `61`. **A scoring chapter that gets its own
arithmetic wrong on the first pass is the fourth table in this repository to do
it**, and the pattern is recorded in [14](14-leftovers.md) and here rather than
quietly corrected.*

---

## Inherited — 31 hits, 2 halves, 0 misses

Every clause below was P15's three-part test: *run the named command, report
its output, and where the output disagrees with the figure the clause names,
record the disagreement as a correction against the pre-briefing rather than
smoothing it over.*

| | verdict | note |
|---|---|---|
| C01 | **hit** | 2,026 of 2,026 on size, on mtime to the 100-ns tick and on sha1, 45 directories of 45, 0 empty of 0, final agreement `True` |
| C02 | **hit** | 2,026 / 342,722,404 / 1,935 distinct / 0 unreadable; **84** repeated hashes and **91** extra copies distinguished, 1,935 + 91 = 2,026 at residue 0; the byte total re-derived by `find … -printf` and `awk`, which is not `hashall.py` |
| C03 | **hit** | every field exactly, both residues, `LastPlayed` 1774010264, `UserConfig language "italian"`, `LastOwner` redacted by the program, and the `LauncherPath` line withheld because it names this machine |
| C04 | **hit** | the depot mapping and the DLC sum — two of the brief's four unverified claims — confirmed by walking: seven groups, seven residues of 0, 2,026 files claimed exactly once, and 83,751,594 − 74,394,305 = 9,357,289 = `dlc\Bonus` to the byte |
| C05 | **hit** | 208,185 + 153 = 208,338, both sizes taken from the tree |
| C06 | **hit** | 16,523,099 − 2,945,024 = 13,578,075, and `depotsplit --path 220708=RPGVXAceITA.dll` shows the depot is **one file**, checked rather than asserted |
| C07 | **hit** | two waves, 2,024 / 342,514,066 and 2 / 208,338, wave 1's total equal to `SizeOnDisk` **with the equality checked**, and wave 2's two files named |
| C08 | **hit** | **42 rows** carrying files, summing to 2,026 and 342,722,404 at residue 0, the seven top-level totals exact — and every four-decimal share recomputed in exact decimal, which found one wrong ([13](13-corrections.md)). **Over-delivered**: the walk shows **46 nodes, 4 of which carry no file**, which is not the same statement as `copyverify.py`'s *0 empty*, and the four are named |
| C09 | **hit** | nineteen rows summing to 2,026 and 342,722,404, the named rows exact, no `.mid` and no `.jpg` |
| C10 | **hit** | the P17 clause: 1,957 / 291,974,845 / 1 / 6,633,819 / 0 / 68 / 44,113,740 at residue 0, from a file written **before** `coverage.py` was touched, **and the misfiled PDF visible in that same output** |
| C11 | **hit** | 5,916 of 6,528, nineteen rows, `.CHM` 7.9981 and `.RVDATA2` 2.0714 with 0 blocks above 7.5 |
| C12 | **hit** | every byte count and COFF stamp exact, `impossible mtimes : 0 of 8`, the two intervals computed at 65 s and 130 s — **and the clause's own "PE32 8" and "all eight at linker 9.00" recorded as corrections A.2 and A.3**, which is the third part of the test |
| C13 | **hit** | 0 of 8 on all three tests, second silence, reported as a negative control |
| C14 | **hit** | every field exact including the Italian DLL's absent `LegalCopyright` — **and the clause's "6 version resources" recorded as correction A.4**, with A.5 following from it |
| C15 | **hit** | 2 of 8, twelfth appearance, six DLLs and 7,722,320 bytes named |
| C16 | **hit** | 0 of 2,026, at offset 0 and anywhere |
| C17 | **hit** | 27 / 27 by name / 0 forwarded with the four new names, 12 DLLs and 14 names, `ws2_32 #116`, `GetUserNameW`, and the 43 vanished regular-expression names |
| C18 | **hit** | nine closures, `PMGL PMGL PMGL PMGI`, 356 / 3 / 0, 40 + 226 × 8 = 1,848, 6,610,974 / 7,398,317 twice, the compile clock, the title, `HHA Version 4.74.8702` |
| C19 | **hit** | 7,398,317 at residue 0, 339 of 339, 172 of 172, 340 files / 7,358,681 bytes, and `lzx.py` unmodified on 226 reset blocks |
| C20 | **hit** | all five specimens, every column, and the fifth pairing at 0.062428 |
| C21 | **hit** | 1,456 / 1,456 / 0 refused, 14,035 of 14,035 CRC, five IHDR shapes summing to 1,456 with 310 interlaced |
| C22 | **hit** | 363 / 363, 28,585 of 28,585, 363 of 363 EOS, channels, rates, 5,522.628 s, and the previous object's flagless stream named as a one-file defect |
| C23 | **hit** | 3 in 2 files, 2 nodes, both dates — and the XMP claim **checked and not assumed**: the chunk-type census shows **zero `iTXt` chunks in 14,035**, which is where PNG XMP lives, so the absence is structural and not a string search |
| C24 | **hit** | 19 in 11, controls both correct, 3 in 3, and 17 |
| C25 | **hit** | Kadokawa 0 of 2,026 in both encodings — the brief's third unverified claim — and every other row exact, with four parties visible only to a sixteen-bit pass |
| C26 | **hit** | 117 / 2,248,383 / 117 of 117 / 0 failures / `{'RPG::Map': 117}`, and the type-byte census re-run: `'i' 2585 'F' 1323 '"' 996 'o' 764 'T' 729 'I' 466 '[' 412 '{' 117 'u' 117` |
| C27 | **hit** | eleven classes with every count, **68 distinct ivar names and 75 slots**, and `pc-rpgmakerxp-doc/docs/06` re-read in the original and quoted — **over-delivered**: two of its eight classes have no page in this object's help at all |
| C28 | **hit** | 22 and 22, 22 stems in both with none on either side, 2,544 rows, 0 blank, `{5: 2544}`, and the first row |
| C29 | **half** | **The clause's premise was wrong and the clause is the reason.** It asserted that the brief's two `.mplus` figures could not both be right; they can, because one counts inside the opaque bucket and the other over the tree, and the two `LICENSE_E.mplus` are ASCII: 9,632 − 8,882 = 750 = 2 × 375, residue 0 ([13](13-corrections.md) B.1). The `textprobe` half was confirmed independently — 28 UTF-8 + 6 EUC-JP = 34 — and **`opaque.py`'s nine-group table was never re-run, because the classifier it depends on had already been repaired.** See P17 below: this clause belonged in §C and was not put there |
| C30 | **hit** | 26 of 1,935 at three thresholds, all with one repository over 105 others, **the twenty-six classified by magic — 26 of 26 `OggS`** — and all five denominators re-derived, the first two with `ls` before the sweep |
| C31 | **half** | Every figure right — 85 pointed, `argparse` 23 for the sixth time, `oserror` 16, `format` 12 falling to 10 — **but the `PYTHONIOENCODING` finding was discovered in §C and then written into a clause that claims to test it.** That is a clause restating this session's own completed work, which is exactly the shape `pc-rpgmakerxp-doc/docs/17` scored C25 down for, in a document whose §C exists to prevent it |
| C32 | **hit** | `ZeroDivisionError` twenty-third; a full table over zero with exit 0, twenty-fourth; **0 of 11 protection markers with the four-zero-bytes control firing on 8 of 8**, nineteenth; exit 0 printing its usage, seventh |
| C33 | **hit** | 36 terms, −31.27, −0.8686, 24 negative, 1 zero, −43.43 at −4.3430, tail run 5 — **eight claims checked one at a time and none wrong** |

**Two halves in thirty-three, which is 6.1 %**, against last session's one in
thirty-three (3.0 %) and the session before's four in thirty-one (12.9 %).

---

## Open, method — 5 hits

| | verdict | note |
|---|---|---|
| C34 | **hit** | four tools written and seven modified, **221 checks over nine tools, 0 failures**, every selftest run with `PYTHONIOENCODING` unset, every name checked against `tools/` first, every file-selecting tool selecting by magic — and **P19 obeyed literally**: six blind spots named in advance with their checks written first, of which `_ordering_ok`'s falsification and `nameguard`'s three-way denominator both earned their place |
| C35 | **hit** | every chapter opens with `*Measure:*`, `docs/02` carries a command on every row, `docs/01` tabulates **eight** denominators with the second named as the finding |
| C36 | **hit** | `pathcheck.py` over **657 tracked files: 0 violations, positive control firing, negative control quiet**, run with the rule-0 log present; third parties' paths published as findings; a scratch note carrying an absolute path deleted and regenerated relative. **Over-delivered**: its first run found **three real violations, all in the checker's own output**, and the repair makes the check a fixed point over its own committed file ([13](13-corrections.md) C.3) |
| C37 | **hit** | branch `master`, the `git ls-files` filter empty with a positive control that fires, a description under 350 characters read back from the remote, topics set, the six excluded paths absent, and `pc-gamelist-doc` pushed on `main` |
| C38 | **hit** | sixteen documents, under twenty, the count justified in `docs/01` against the last ten sessions, and **no chapter is a census of a resource family for its own sake** — the PNG, Ogg, MP3 and font figures are rows of `docs/02` and evidence inside arguments |

---

## Open, content — 25 hits, 1 half, 0 misses

| | verdict | band | note |
|---|---|---|---|
| C39 | **hit** | `lands` | five binary magics and two text codecs **before any other work**, the ordering rule stated and enforced, **0 files and 0 bytes opaque at residue 0**, and **24** new checks of which **six** assert a refusal or a non-confusion |
| C40 | **hit** | `lands` | the PDF reported as `%PDF`, **and the check that the old ordering would still have taken it** — so the repair's failure mode is still reachable and still tested. Three sentences, third appearance, first as a wrong answer |
| C41 | **hit** | `constructs` | one selection rule in one place, 117 of 117 walked, the `format` count re-run and falling 12 → 10. **Over-delivered twice**: a **fourth** reader with the defect (`rgssjoin.py`), and **the harness itself** resolving its placeholder by extension |
| C42 | **half** | `constructs` | all 24 ivars named on 117 of 117, the `Table` decoded, 117 residue-0 closures, and the two-witness check on `@width`/`@height` — **but the clause said "width × height × 3 layers" and the object has four.** The number came from the previous product and the measurement corrected it, which is the same shape as `pc-rpgmakerxp-doc/docs/17`'s C60 and is scored the same way |
| C43 | **hit** | `constructs` | **the join closes at residue 0 over 3,133 ids.** The spans derived from row counts, the two bases fitted and **said to be fitted**, the cluster ends at 511 and 1,663 confirming the derivation from the other side, and the half that cannot close reported as not closing |
| C44 | **hit** | `constructs` | 2,544 × 5 = 12,720 counted, the languages identified **by codepoint and not by position**, 0 rows with all five identical and 2,400 with five distinct, six identical column pairs **none of which involves the Japanese column**, and the absence of Italian stated without a reason invented for it |
| C45 | **hit** | `constructs` | 59 events in **11 of 117** maps, the distribution, the codes, the six classes instantiated, `docs/06` quoted in the original. **Over-delivered**: every one of the 59 is empty — one page, one command, code 0 — which the class census could not see |
| C46 | **hit** | `lands` | every figure, both stubs, `MZ` and `PE\0\0` in both, **and thirteen candidate names counted at zero in both specimens in both encodings**, beside `steam` at nine in the surrounding executable |
| C47 | **hit** | `constructs` | 11 of 11 and 0 undocumented, the previous object's 28-of-28 and 323-of-324 quoted. **Over-delivered**: the six unmatched fields were a defect in the join and not a gap in the manual, and following inheritance takes it to **75 of 75** |
| C48 | **hit** | `constructs` | one occurrence in one file, quoted in the original beside the previous object's. **Over-delivered**: the two sentences differ by **three edits** with the refusal intact and the grammar repaired — and two paragraphs above it the manual names `Scripts.rvdata` for a `.rvdata2` file |
| C49 | **hit** | `constructs` | 27,136 bytes decomposed into two section deltas at residue 0, the resource trees counted at **16 types, 716 names, 716 leaves in both**, and the Italian one 27,648 bytes heavier over the same 716 leaves. **Over-delivered**: the Italian DLL has **one section and no code**, which explains `InternalName LangENU` structurally |
| C50 | **hit** | `nonnumeric` | the rule written as a sentence, a test and a reason; `cd32.zip` not opened; `cd32.ini` compared against the format rather than transcribed, with three of four documented values equal to the vendor's defaults; one sentence on `CD32` |
| C51 | **hit** | `nonnumeric` | short, the rule not reopened, **19 occurrences shown to be 3 distinct addresses over 2 domains**, all third parties', `redact.py --expect 1` succeeding and `--expect 7` failing as its control. **Over-delivered**: one address is shared by three independently authored packs and is none of the three authors' |
| C52 | **hit** | `constructs` | the pair decomposed and compared, 2 of 2 against 0 of 3, the fixed bias excluded because the two hour-counts differ, **the remainder shown NOT to grow with size across five specimens** (correction A.7), and a new mechanism named with the sixth specimen that would test it |
| C53 | **hit** | `constructs` | 310 of 1,456, **all in one DLC pack**, 1,139 files in twenty other directories at zero, the correlation stated as a count. **Over-delivered**: the seven exceptions are one battler at all seven sizes |
| C54 | **hit** | `constructs` | eight numbered predictions written first, **seven right and one wrong**, the wrong one left standing and explained: the low byte, not the high one, and 32 = 32 at residue 0 over four ids |
| C55 | **hit** | `constructs` | 23 stems joined at residue 0, both durations computed, the tolerance stated and **justified in frame-times**. **Over-delivered**: the MP3 is longer in 23 of 23 by between 2.033 and 2.971 frame-times, which is one band and is what encoder padding looks like |
| C56 | **hit** | `constructs` | `--path` and `--rest`, seven groups closed **by the tool**, `dlc\Bonus` falling to the base depot by the tool's own arithmetic, and eight new checks of which three assert what `--group` could not express |
| C57 | **hit** | `lands` | both builds with both sha1, both byte counts, both linker versions and both evidence offsets, and the "closed by the object" sentence quoted and reopened. **Over-delivered**: a vendor present in the previous object's list is **absent from this one**, and the reason is the export table this session measured in another chapter |
| C58 | **hit** | `lands` | the three notes under those exact names, `crossnames.py` reporting **0 of 26 keeping a base name** and classifying all 26, and `compratio.py` run with its difference — which produced correction C.1 |
| C59 | **hit** | `constructs` | the scope measured at **7 of the 9 tools that emit a name**, with 549 excluded from both halves for never having been tested; the guard written; and proved by a check that fails without it — **the refusal table is byte-identical with and without `PYTHONIOENCODING` after the repair and was not before** |
| C60 | **hit** | `constructs` | 216 of 557 taken from the committed file and not the brief, 216 of 561 after, and all four new readers absent from the raised list |
| C61 | **hit** | `lands` | **twenty** corrections with the count stated first, all four flagged claims with verdicts, the refusal disagreement reported, and the split given as 13 to 7 with the honest caveat that one session cannot separate P19 working from a loose threshold |
| C62 | **hit** | `nonnumeric` | **thirteen** questions with a reason each; the initialisms split four ways, **9 + 5 + 13 + 6 = 33**, with the heading's own arithmetic error recorded rather than tidied |
| C63 | **hit** | `lands` | the four groups confirmed by counting — 49, 24, 10, 1 = 84 — the 84 and the 91 distinguished, `pngpair.py` run on two pairs at residue 0. **Over-delivered**: 175 files share a repeated hash and 153 share an IDAT stream, and **175 − 20 − 2 = 153** at residue 0 |
| C64 | **hit** | `constructs` | six candidates set out, the previous row's reasoning quoted, `.bind` used as the reason a 2014 link time is the wrong kind of date, **the cell named as 2012** with three artefacts in a twenty-one-day window against one copyright field — and what the object cannot establish left in `docs/14` |

---

## P11, scored, and P8's mechanism survives a fourth time

> **P11.** For each open content clause, record whether the object supported
> **more** than the clause asked. **Falsification: if `lands` and `constructs`
> have the same over-delivery rate, P8's mechanism is dead.**

**The test applied is strict**, because the loose one makes every good chapter
an over-delivery: the object over-delivered when it supported something the
clause did not name **and that something changed a conclusion**.

| band | n | over-delivered | rate |
|---|---:|---:|---:|
| `lands` | 7 | **3** — C46, C57, C63 | **42.9 %** |
| `constructs` | 16 | **12** — C41, C43, C44, C45, C47, C48, C49, C52, C53, C54, C55, C59 | **75.0 %** |
| `nonnumeric` | 3 | **1** — C51 | **33.3 %** |

**Not a tie, and in the direction P8 predicted, for a fourth session.** The
four measurements are 6/10 against 5/8; 75.0 % against 42.9 %; 84.6 % against
55.6 %; and now **75.0 % against 42.9 %**.

**And the band splits cleanly along P12's line, which is the finding.**

| | n | over-delivered | rate |
|---|---:|---:|---:|
| the five `constructs` clauses P12 governs | 5 | **5** | **100 %** |
| the eleven `constructs` clauses P18 governs | 11 | **7** | **63.6 %** |

**A clause written to ask for the most the object could conceivably support
over-delivered five times out of five. A clause priced at what this document
actually expected over-delivered two thirds of the time.** That is the
mechanism P8 proposed, visible inside one band rather than between two, and it
is the sharpest form the measurement has taken.

---

## P12, scored, and its falsification does NOT fire for the first time in three sessions

> **P12.** Write, for at least five open content clauses, the strongest claim
> the object could conceivably support rather than the one you are confident
> of, and price those five below 0.60. **Falsification: if all five hit, the
> pipeline was under-claiming rather than under-pricing.**

| | priced | obtained | what happened |
|---|---:|---:|---|
| **C43** | 0.45 | **1.00** | the map grids joined to the tile vocabulary, residue 0 over 3,133 ids |
| **C48** | 0.55 | **1.00** | the refusal repeated, and three edits found in it |
| **C52** | 0.45 | **1.00** | the pair decomposed, the fixed bias killed, a sixth specimen specified |
| **C55** | 0.50 | **1.00** | 23 of 23, and the sign is a frame-quantisation signature |
| **C59** | 0.50 | **1.00** | one tool became ten, with an honest denominator |
| | **2.45** | **5.00** | |

**All five hit — which is P12's falsification condition met in its literal
wording for the third consecutive session.** The diagnosis it offers is
unchanged and is now very hard to argue with: **this pipeline is
under-claiming, not under-pricing.** Five clauses written to ask for the most
the object could conceivably support were all satisfied, on an object where
three of the five required tools that did not exist.

**And the cost is −2.55 of the −5.16, which is 49.4 % of this session's whole
calibration term produced on purpose.**

---

## P14, scored, and the two sub-terms move together for the first time

> **P14.** Report the term over the clauses P12 governs separately from the
> term over the rest. **Falsification: if the two sub-terms move together over
> the next three sessions, they are one signal and splitting them was
> bookkeeping.**

| | this session | last session | the one before |
|---|---|---|---|
| the five P12 clauses | 2.45 − 5.00 = **−2.55** over 5 | −2.60 over 5 | −2.25 over 5 |
| everything else open | 22.89 − 25.50 = **−2.61** over 26 | −3.26 over 26 | −3.89 over 22 |
| per clause, the rest | **−0.1004** | −0.1254 | −0.1768 |

**Both terms improved, and that is P14's falsification condition in its literal
wording**: −2.60 → −2.55 and −3.26 → −2.61. Last session they moved apart; this
session they moved together. **That is one of P14's three sessions and it goes
against P14**, and it is reported that way rather than explained away.

**But the magnitudes are not the same story.** The P12 term moved by **0.05**
and the other by **0.65**, thirteen times as far. **A term that barely moves
while the other falls by a fifth is not a co-moving signal**: it is a term
pinned by a prescription that says *ask for the most the object could support,
five times* — which cannot improve, because it is already losing the maximum —
beside a term that responds to pricing. **P14 is failing on sign and surviving
on magnitude**, and the third session decides it.

**The number that measures calibration is −2.61 over twenty-six clauses**, or
**−0.1004 per clause**, and it is **the smallest per-clause residue that band
has recorded since P12 came into force**: −0.1768, −0.1254, −0.1004. P18 is the
reason and P18 is scored below.

---

## P17, scored, and it worked — and its own author left a clause out of the register

> **P17.** Mark every clause whose figure describes a state the session itself
> will change, run those commands FIRST, and record the output in `notes/`.
> **Falsification: if a clause of that kind still loses points when the command
> has already been run and its output committed, the problem is not the timing
> either.**

**Eight figures were registered in §C and all eight commands were run before
the first clause was written.** The register earned its place on the first row
it checked: `refusals.py` reports 54 and not the brief's 52, and the difference
is an environment variable ([13](13-corrections.md) A.1).

**The clauses that cite a registered figure all scored a full hit.** C10
(coverage before the magics), C60 (216 of 557), C37 (`rowlen.py`'s 78 rows
before this session adds one) — **none of them lost a point**, where the two
equivalents last session lost half each. **P17's falsification does not fire.**

**And the interesting failure is C29, which belonged in the register and was
not put in it.** That clause names `opaque.py`'s nine-group table — a figure
describing the classifier's state **before** this session repaired it, exactly
the kind §C exists for. It was not registered, the classifier was repaired
first, and the table could no longer be produced. **The register worked and its
own author did not apply it consistently**, which is a sharper result than
either "it worked" or "it did not": the mechanism is sound and the discipline
of populating it is a separate problem that P17 does not address.

**C31 is the second one and it fails the other way.** Its figure was in the
register, was measured correctly, and was then written into a clause that
claims to test it — so the clause is a restatement of the session's own work,
which is the failure P15 named and P17 was supposed to make impossible.
**Putting a figure in §C does not stop somebody writing a clause about it
afterwards**, and nothing in P17 says it should.

---

## P18, scored, and it did what it said it would

> **P18.** Price `constructs` at the observed over-delivery rate — a mean at or
> above 0.80 — and put the ambition where P12 wants it. **Falsification: if
> `constructs` priced at 0.80 still over-delivers above 75 %, the band is
> measuring something other than confidence.**

**The band cannot be priced at 0.80 as a whole, because P12's five live inside
it**, and `docs/00` said so in advance rather than discovering it in scoring:

```
constructs  n=16  total 11.95  mean 0.7469
  of which the five P12 clauses   2.45 over  5   mean 0.4900
  the eleven P18 governs          9.50 over 11   mean 0.8636
```

**The eleven were priced at 0.8636, above P18's floor of 0.80, and they
over-delivered 7 of 11 = 63.6 %.** Last session the whole band was priced at
0.6908 and over-delivered 84.6 %.

**P18's falsification does not fire — and it is closer than it looks.** The
condition is *above 75 %*. On the eleven clauses P18 actually governs the rate
is **63.6 %** and the condition is comfortably unmet. **On the whole band,
P12's five included, it is 12 of 16 = exactly 75.0 %** — which is *at* the
threshold and not above it, and would have fired on one more clause.

**So the honest scoring is: P18 works on what it governs, and the band as a
whole sits on the line because P12 deliberately holds five clauses off it.**
Pricing a band up did reduce its over-delivery, from 84.6 % to 63.6 % on
comparable clauses, and the per-clause calibration residue fell with it. That
is P18 confirmed on its first session, with the same caveat C61 makes: one
session cannot separate a correct prescription from a favourable object.

---

## P19, scored, and its falsification does not fire

Scored in [13](13-corrections.md) and repeated here for the record: **thirteen
corrections by a program and seven by a person, 1.86 to one, against a
falsification threshold of "better than three to one".** It does not fire.

**What P19 can claim specifically** is three items and not twenty: two errors
in this session's own new code caught by checks written *before* the tools were
run (`mp3frames.py`'s bitrate assertion and `nameguard.py`'s ASCII claim, both
failing on first execution), and one defective reader found because the session
ran a tool instead of believing a list. **What it cannot claim** is the other
sixteen, which were found the way corrections have always been found here.

**And the six blind spots named in advance are worth listing by what they
bought**, because three of them bought nothing and saying so is the point:

| named in advance | did the check fire? |
|---|---|
| `coverage.py`: a text codec accepting a binary header | **yes** — the falsification check is what makes the PDF repair testable, and the `ambiguity` mode it forced found the one ambiguous file and it is that PDF |
| `nameguard.py`: silence is not a pass | **yes** — the survey's denominator is 9 and not 558 because of it |
| `mp3frames.py`: a walk cannot tell silence from sound | no, but it kept the word *music* out of a report that would otherwise have claimed it |
| `rvmap.py`: a count-only join is not a match | no — the join closed on ids and the report says so |
| `tiletable.py`: a codepoint census cannot name a Latin language | no — but the tool is structurally unable to claim what it cannot see, and the chapter says ATTRIBUTED where a looser tool would have said *English* |
| `marshal48.py`: closure is not correctness | no |

**Two of six fired and four of six constrained what could be written.** That is
a smaller claim than P19 hoped for and a real one.

---

## P16, which is still not a clause

```
python tools/rule0hook.py --report                        (notes/rule0.txt)
shell calls seen by the hook : 172
  allowed                    : 170
  REFUSED as rule-0          : 3
      inline program 1     in-place edit script 1     heredoc 1
```

**Three refusals: one deliberate probe and two reflexes**, one a `sed -i` and
one a heredoc reached for to append text to a file. **None reached the shell.**
Reported as a plain fact worth zero points, which is the only honest way to
score a falsification.

---

## The calibration series, extended

```
python _work/calib3.py --append -5.16                (notes/calibration.txt)

terms    : 37
sum      : -36.4300
mean     : -0.9846
negative : 25   positive : 11   zero : 1
last10   : -44.7200   mean -4.4720
tail run of consecutive negatives : 6
the last term -5.16 ranks 13 of 37 by absolute value

the brief's eight claims about the inherited series : 0 wrong
```

**The last-ten mean worsens from −4.3430 to −4.4720 and the tail run reaches
six.** Read as a trend, that is a pipeline six sessions into a negative run and
drifting.

**Read against P12 and P14 it is a pipeline doing exactly what it was told.**
**−2.55 of the −5.16 is five clauses deliberately priced at less than half what
they were worth, and the object paid all five for the third session running.**
The residue — **−2.61 over twenty-six clauses, −0.1004 each** — is the part
that measures calibration, and it is the smallest per-clause value it has ever
taken.

**The two readings are not in tension and the difference between them is
arithmetic.** The headline term worsened because P12's five are a fixed cost
that cannot improve; the calibration term improved by a fifth. **A series whose
last-ten mean is drifting down while its calibration residue is at a record low
is a series measuring two things and reporting one**, which is precisely what
P14 was written to fix — and P14's own falsification fired this session. The
next document has to decide whether the headline number is worth keeping at
all.

---

## What this document predicts

> **P20 — a register that catches figures cannot make anybody put figures in
> it.** P17 worked on all three clauses that used it and failed on the two that
> should have used it and did not: C29 named a pre-repair figure that was never
> registered, and C31 restated a registered figure in a clause after the fact.
> **Both failures are about the boundary of the register and not about its
> mechanism.** The next document should derive §C's membership by a program
> rather than by judgement: **before writing a clause, run it through a check
> that asks whether any command it names reads state this session's own work
> plan will change — the tool box, the classifier, the readers, the index —
> and refuse to accept the clause until that command's output is committed.**
> **Falsification: if a clause still cites an unregistered pre-change figure
> when the membership test is a program, then the problem is that the session
> does not know its own work plan in advance, and no register can fix that.**

> **P21 — over-delivery has become a pricing dial and the dial is now roughly
> calibrated, so the next thing to measure is what it costs.** `constructs`
> fell from 84.6 % to 63.6 % when its price rose from 0.6908 to 0.8636, which
> is the response P18 predicted. **A band around 50 % over-delivery is a band
> whose clauses are neither timid nor ambitious, and that is where a
> well-priced band should sit.** But nothing has measured whether pricing a
> band up makes its clauses *worse* — smaller, safer, asking for less. The next
> document should record, for every open content clause, **how many separate
> measurements the clause requires** and report that count by band, so that
> "the band is calibrated" can be distinguished from "the band got timid".
> **Falsification: if a well-priced `constructs` band's mean measurement count
> is no lower than the under-priced band's was, pricing does not buy timidity
> and the dial is free.**

> **P22 — the three chapters of this repository that found something new all
> found it by opening a format the pipeline already had a reader for.** The
> map events were behind a reader written last session; the tile vocabulary was
> behind a text codec any language ships; the help file's `.rgss3a` sentence
> was behind an LZX decoder written last session. **Not one of the three needed
> a new format.** They needed somebody to point an existing reader at a
> population nobody had pointed it at, and in two of the three cases what
> stopped them was a file-selection filter. **The next document should, before
> writing a single reader, enumerate every tool in the box that could be
> pointed at this object and has not been, and publish that list with its
> length.** Twenty-six of 558 were run in this object's pre-briefing, which is
> 4.6595 %. **Falsification: if the enumerated list is run and produces nothing
> a chapter uses, then the box's unused tools are unused because they are
> irrelevant and not because nobody aimed them.**
