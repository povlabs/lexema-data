# lexema-data

The source data [Lexema](https://github.com/povlabs/lexema) is built from.

## Where it comes from

- **[Wiktionary](https://it.wiktionary.org/)**, the Italian edition, written by its
  [contributors](https://it.wiktionary.org/wiki/Speciale:ListaUtenti). The raw page dumps come
  from [Wikimedia Downloads](https://dumps.wikimedia.org/itwiktionary/).
- **[Kaikki.org](https://kaikki.org/)**, which turns the Wiktionary dumps into structured JSON
  with [Wiktextract](https://github.com/tatuylonen/wiktextract). The Italian extract is at
  [kaikki.org/dictionary/rawdata.html](https://kaikki.org/dictionary/rawdata.html).

## What's here

`source/` holds the files the dictionary is seeded and updated from:

- `it-extract.jsonl.gz`: the Kaikki extract of Italian Wiktionary, release `it-0c432803` (July 2026)
- `itwiktionary-20260701-pages-articles.xml.bz2`: the Wiktionary dump that extract was built from
- `it-78385b62.jsonl.gz` and `itwiktionary-20260901-pages-articles.xml.bz2`: the September 2026 release

See [source/README.md](source/README.md) for checksums, sizes and dates. Newer releases are added
here and applied to the dictionary as diffs; the older files stay unchanged.

## Licence

Everything here is upstream data under
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), unmodified. Credit goes to
Wiktionary's contributors and to Kaikki.org. See [LICENSE](LICENSE).
