# lexema-data

The source archive Lexema is built from.

`source/it-extract.jsonl.gz` is the Wiktextract dump of Italian Wiktionary,
release `it-0c432803`. See [source/README.md](source/README.md) for its
checksum, size and what it contains.

Lexema seeds its database in one pass over this archive. There is no converted
copy here: a converted tree of 541,247 files lived under `it/` until
2026-09-22 and was removed, because it held less than the archive does and was
seven times its size. It is still reachable in this repository's history if
anyone needs to read it.

This is upstream data under CC BY-SA 4.0, unmodified. It is not refreshed when
Wiktionary publishes a new dump.
