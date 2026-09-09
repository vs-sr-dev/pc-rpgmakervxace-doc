# 04 — the magic table: a classifier that answered confidently and wrongly, and the ordering rule that is the actual repair

*Measure: `python tools/coverage.py selftest` — **69 checks, 0 failures**, run
with `PYTHONIOENCODING` unset, in `notes/selftests.txt`; `python
tools/coverage.py tree --root rpgvxace-steam` before and after, in
`notes/coverage-tree-before.txt` and `notes/coverage-tree.txt`; `python
tools/coverage.py ambiguity --root rpgvxace-steam`, in
`notes/coverage-ambiguity.txt`.*

---

## The third appearance, and the first that was not a silence

`pc-rpgmaker2003-doc/docs/10` recorded this table missing a magic and closing
at residue 0 anyway, over 67,623 bytes. `pc-rpgmakerxp-doc/docs/04` recorded it
again, over 10,966,146 bytes — 162 times the first — and repaired it with three
magics.

**This is the third appearance and it is a different failure.** Forty-four
million bytes were opaque, which is the same shape as before. But one file was
not opaque:

```
  bucket      files        bytes      share  format
  specified       1       328733    0.0959 %  plain text, Shift-JIS (JIS X 0208; Microsoft cp932)
```

That is `dlc\Tyler Warren RPG Battlers 1st 50\…<nine kana>.pdf`. **It is a
PDF.** The cp932 probe read 512 bytes of a PDF header, found no illegal
multi-byte sequence in what is mostly ASCII punctuation, and filed it as a
Japanese text document — **in the SPECIFIED bucket, with a format name, closing
at residue 0 while doing it.**

**A classifier that omits is a classifier you can audit.** Its opaque bucket is
a list of things to go and look at, and every previous session found the gap by
reading that list. **A classifier that answers wrongly puts the file in the
bucket nobody re-reads**, and it took a session that already knew a PDF was
there to notice.

---

## The repair is not "add `%PDF`"

Adding the signature fixes this file. **The ordering is what fixes the class.**

A single-byte text codec cannot fail on arbitrary bytes. A multi-byte one fails
only on illegal sequences, and there are byte strings that are not text in any
language which nevertheless contain no illegal cp932 sequence — a PDF header
being one of them. So a text probe placed above a binary signature does not
merely *miss* the binary file. **It claims it.**

The rule is now stated in the source, enforced by a function, and asserted:

> **Every binary signature is tested before every text codec.**

```python
def _ordering_ok(magics=None):
    seen_text = False
    for probe, _buck, _name in (magics if magics is not None else MAGICS):
        if probe in TEXT_PROBES:
            seen_text = True
        elif seen_text:
            return False
    return True
```

```
THE ORDERING RULE: every binary signature is tested before every text codec   ok
and the rule is falsifiable -- a binary probe moved below a text codec is REFUSED   ok
```

**The second check is the one that matters.** A rule that cannot fail is
decoration; that check builds a two-element table with a text probe above a
binary one and requires `_ordering_ok` to say no. A future edit that appends a
magic to the end of `MAGICS` — the natural place to append — is shadowed by
three text probes, and the selftest fails loudly instead of the table quietly
claiming a file.

---

## What was added

Five binary signatures and two text codecs.

| probe | signature | why it is not two bytes |
|---|---|---|
| MPEG-1/2 Audio | `ID3` + syncsafe size, **or** an eleven-bit frame sync | eleven set bits occur once per 2,048 random bytes, so the **four reserved field values** are rejected: version `01`, layer `00`, bitrate index `1111` and `0000`, sampling index `11` |
| sfnt / TrueType | `00 01 00 00`, `OTTO`, `true`, `ttcf` | **one byte from the Windows icon's `00 00 01 00`**, which was already in the table |
| Windows BMP | `BM` + a reserved u32 of zero + a declared size ≥ 14 | `BM` alone claims any text file beginning `BMW` |
| PDF | `%PDF-` | five bytes, and the one that was missing |
| ZIP | `PK\003\004`, `PK\005\006`, `PK\007\010` | `PKZIP is a program` is not an archive |
| UTF-8 | strict decode, printable, **requires a high byte** | pure ASCII must reach the ASCII probe, not this one |
| EUC-JP | the same shape as the cp932 probe | the six font documents nobody could read |

**The sfnt hazard has two checks, one in each direction:**

```
THE ONE-BYTE HAZARD: 00 01 00 00 is a font                        ok
THE ONE-BYTE HAZARD: 00 00 01 00 is an icon and is NOT called a font   ok
```

**And the misfiling has two of its own**, one asserting the fix and one
asserting that the old order would still have taken it — because a repair whose
failure mode is no longer reachable is a repair you cannot test:

```
THE MISFILING: a PDF header is a PDF and not Shift-JIS text                   ok
and the cp932 probe WOULD have taken it, which is why the order matters       ok
```

**Twenty-four checks were added, of which six assert a refusal or a
non-confusion rather than an acceptance**, because the defect this repairs was
never a probe saying no.

---

## The result

```
  specified  2025 files    336088585 bytes    98.0644 % of 342722404
  decoded       1 files      6633819 bytes     1.9356 %
  derived       0 files            0 bytes     0.0000 %
  opaque        0 files            0 bytes     0.0000 %
  SUM        2026 files    342722404 bytes   100.0000 %   RESIDUE 0
```

**Zero files and zero bytes opaque**, and the Shift-JIS row is gone entirely:
this object contains **no Shift-JIS text at all**. The row that existed before
was one PDF.

---

## The order among the three text codecs is a decision, and its cost is published

The ordering rule settles binary against text. It does not settle text against
text, and nothing can:

**EUC-JP's lead bytes 0xA1..0xFE are cp932's single-byte half-width katakana**,
so a EUC-JP document decodes under cp932 into nonsense without one illegal
sequence. No probe of this shape can tell them apart. The table's order —
UTF-8, then EUC-JP, then cp932 — is therefore a **decision**, and a decision
whose cost is not measured is a decision nobody can check.

So it is measured:

```
python tools/coverage.py ambiguity --root rpgvxace-steam

files accepted by at least one multi-byte text codec : 35
files accepted by MORE THAN ONE                      : 1

  utf-8                      28
  euc_jp                      6
  euc_jp+cp932                1

    dlc/Tyler Warren RPG Battlers 1st 50/…<nine kana>.pdf   euc_jp+cp932
```

**The one ambiguous file is the PDF**, and it is not filed under either of
them, because `%PDF-` is tested first. **Twenty-eight plus six is thirty-four,
which is exactly the count of text files the pre-briefing's independent probe
found**, and the thirty-fifth is the file the ordering rule exists for.

*A probe that answers "this could be two things" about exactly one file, and
that file is the one a signature already claimed, is the cleanest report this
mode could have produced.*

---

## And the tool written to measure the defect died of a different one

`coverage.py ambiguity` prints file names. Its first run, on a tree whose only
ambiguous file has a Japanese name, ended in `UnicodeEncodeError` — the same
defect the pre-briefing attributed to one tool and this session measured at
seven ([12](12-the-tools.md)).

**A tool written to catch a classifier lying about a Japanese PDF could not
print the Japanese PDF's name.** It now calls `nameguard.guard()`, like
`hashall.py` and `mtimes.py` and two others, and the fix is one line in each.
