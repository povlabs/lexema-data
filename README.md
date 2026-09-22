# Lexema content data

This repository is the editable content source for Lexema releases. The
converter reads a completed Lexema SQLite release and writes one JSON file per
Italian word; the application seeds from these files and not from the upstream
archive.

The source text is Italian Wiktionary data distributed by [Kaikki](https://kaikki.org/dictionary/Italian/), under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
Lexema restructures that source and may add an Italian explanation, an English
explanation, and an Italian example. Those Lexema-written fields are separate
from source-derived fields and are never overwritten by conversion. They are
also published under CC BY-SA 4.0; see [LICENSE](LICENSE).

## Layout and identity

Files are laid out as
`it/<first>/<first-two>/<first-three>/<first-four>/<word>.json`. The four
components are the first one, two, three, and four Unicode code points after
lowercasing with Italian locale rules; a code point that is not a Unicode letter
is `_`, and missing code points are `_`. Letters whose Unicode case-folding could
alias another code point on a case-insensitive filesystem are percent-encoded in
the directory components. Thus every word is placeable: `casa` is under
`it/c/ca/cas/casa/`, `a` under `it/a/a_/a__/a___/`, and `1x` under
`it/_/_x/_x_/_x__/`. The filename is UTF-8 percent-encoded (including uppercase ASCII letters)
before adding `.json`, so words containing `/` remain safe and case variants do
not collide on a case-insensitive filesystem. This is the only filename
encoding; the JSON retains the verbatim source word.

The root `manifest.json` contains the release id, archive SHA-256, and archive
size. The fixed four-level layout keeps each word's path stable for the life of
the repository. Adaptive bucket splitting was deliberately rejected: when a new
word tips a bucket over a cap, every existing path in that bucket moves and a
re-conversion diff becomes unreadable. Each word file names that release id and
has an `entries` object. Entries are keyed as `<escaped-pos>:<escaped-pos_title>`:
`%`, `:` and `#` become `%25`, `%3A` and `%23`, so a literal title `X#2` cannot
collide with a generated `#2` suffix. If the same word has more than one source
record with the same pair, records are sorted by source-line hash and suffixed
`#2`, `#3`, and so on. For example, `sale` has `noun:Sostantivo`,
`noun:Sostantivo, forma flessa`, and `verb:Voce verbale`; `bello`'s two
`noun:Sostantivo` records are `noun:Sostantivo` and `noun:Sostantivo#2`.
Consequently every active key resolves to exactly one source record, while the
source's own title remains visible. A duplicate generated key fails conversion
rather than overwriting an entry.

When a new release drops a record, conversion removes its key from `entries`.
When it drops a whole word, conversion deletes that word file unless it has
Lexema-written fields. Such a file remains with `status: "orphaned"`, its
editorial values under `orphanedEntries`, and its prior release under
`orphanedFromReleaseId`; it is visibly not current content. Dropped entries in
a still-current word are likewise removed and their editorial values retained
under `orphanedEntries`.

Entries contain only the served source facts: the word, part of speech and
source title, tags and raw tags, senses (glosses, labels and form-of targets),
forms and their tags, grammar claims, and provenance for every value. Each
provenance object includes the source line number and JSON pointer; the entry
carries its source line SHA-256, and the file carries the release id and archive
SHA-256. Editorial fields belong in the entry's `lexema` object:
`italianExplanation`, `englishExplanation`, and `italianExample`. Conversion
preserves editorial values, but may normalize JSON whitespace and key order.
