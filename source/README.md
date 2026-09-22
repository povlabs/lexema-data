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
