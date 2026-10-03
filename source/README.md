# Source archive

`it-extract.jsonl.gz` is the Wiktextract dump every file in `it/` was derived
from. It is kept because the content files are derived data: if the converter
turns out to have been wrong, this is the only thing that can produce them
again.

| | |
|---|---|
| Release | `it-0c432803` |
| SHA-256 | `0c432803c672aceccd48787eb64807c5366fdbd6796715c9a99e31c0024d5dcf` |
| Size | 38.0 MB |
| Lines read | 560,357 Italian records, 541,247 distinct words |

The release id is the first eight characters of that SHA-256, so the name of
the release and the identity of this file are the same fact. `manifest.json`
at the repository root records both, and a conversion checks what it read
against them.

This is upstream data under CC BY-SA 4.0, unmodified. It is not updated when
Wiktionary publishes a new dump: Italian vocabulary does not change, and a
re-conversion happens when Lexema's own converter needs fixing, not when
upstream moves.

## Raw page dump

`itwiktionary-20260701-pages-articles.xml.bz2` is the Italian Wiktionary dump
the archive above was most likely built from: Wiktextract wrote the archive on
2026-07-16, and this is the last dump before that date. Every one of the
archive's Italian records has a page of its exact title in it.

It is not newer data replacing the archive. It is the raw page source the
archive was converted from, kept so Lexema's seed can read the definitions the
conversion dropped ([#28](https://github.com/hueypov/lexema/issues/28)). The
archive is never changed by it. It was downloaded once from Wikimedia and is
not replaced by later dumps.

| | |
|---|---|
| Dump date | 2026-07-01 (`dumpstatus.json`: `done`, updated 2026-07-03 03:46:04) |
| Source | `https://dumps.wikimedia.org/itwiktionary/20260701/itwiktionary-20260701-pages-articles.xml.bz2` |
| Downloaded | 2026-09-23 |
| SHA-1 | `2bdd444236f7dcd26fee3652dbd641c31d0d9651`, as Wikimedia's `dumpstatus.json` lists it |
| SHA-256 | `0e4232980291ec93de2a9885d89517c857a01c77c328557e129feca1779da38d` |
| Size | 70,997,844 bytes |
| Pages | 758,429 in the main namespace |

This is upstream data under CC BY-SA 4.0,
unmodified.

## Feed release it-78385b62 (September 2026)

Since hueypov/lexema ADR 0025, newer kaikki releases are applied to the dictionary as diffs through the CI dictionary deploy, which reads its files from this folder (`src/deploy/dataFiles.ts`). These two files are the first such feed release:

| File | Checksum | Size |
|---|---|---|
| `it-78385b62.jsonl.gz` | SHA-256 `78385b6229d1…` (full value in `ARCHIVE_FACTS`) | 43,612,281 bytes |
| `itwiktionary-20260901-pages-articles.xml.bz2` | SHA-1 `c72d2411b1de…` (full value in `KNOWN_DUMPS`) | 71,291,038 bytes |

The archive was retrieved from kaikki.org on 2026-09-28. The dump was downloaded from dumps.wikimedia.org. Both are upstream data under CC BY-SA 4.0, unmodified. The July files above stay unchanged.
