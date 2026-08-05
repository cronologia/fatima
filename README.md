# Nossa Senhora de Fátima — Cronologia

An open, source-referenced chronology of the **reported apparitions at Fátima,
Portugal (1916–2017)**: what the three seers reported and when, what the
contemporary press recorded, what the Church ruled and in which document, and
the later beatifications, canonizations and the 2000 publication of the
"Third Secret".

Part of the [Cronologia](https://github.com/cronologia) project family.

- **Site** (once GitHub Pages is enabled): <https://cronologia.github.io/fatima/>
- **Source of truth:** [`data/chronology.json`](data/chronology.json)
- **Published in:** English (authoritative), Spanish, Portuguese

## What this site does — and what it deliberately does not do

The apparitions at Fátima are **reported** events with **Church judgments**.
This chronology records two separable things and keeps them separate:

- **who reported what, and when** — the children's accounts, the crowd
  estimates, the contemporary press reports;
- **what the Church ruled, and when, citing the ruling document** — above all
  the pastoral letter *"A Divina Providência"* of **13 October 1930**, in which
  Bishop José Alves Correia da Silva of Leiria declared the visions *dignas de
  crédito* ("worthy of belief") and officially permitted the cult.

The site **never asserts the supernatural claim as fact in its own voice**, and
never denies it either. The "Miracle of the Sun" of 13 October 1917 is
attributed to the contemporary press — Avelino de Almeida in *O Século*,
15 October 1917, and the crowd photographs in *Ilustração Portuguesa*,
29 October 1917 — not stated as an occurrence.

Much of the now-familiar 1917 narrative (the 1916 Angel apparitions, the vision
of hell, the three-part "Secret") is attested **only retrospectively**, through
Lúcia's memoirs of 1935–1941 and her manuscript of 3 January 1944. That gap is
recorded on the face of the data, in the events themselves and in the
Disambiguation section. It is a sourcing caveat, not a verdict.

Dates not yet verified against a primary source carry a visible `?` flag.

## How it is built

A zero-dependency Node script compiles one JSON file into a static site.

```
node scripts/validate-data.js   # schema + sources + glossary-link check
node build.js                   # data/chronology.json -> docs/{en,es,pt}/
node --test                     # helpers, data invariants, i18n completeness
```

`docs/` is generated output committed to the repo and served by GitHub Pages.
**Never hand-edit it**: change `data/chronology.json`, rebuild, and commit data
and `docs/` together.

## Translations

`data/i18n/es.json` and `data/i18n/pt.json` are exact-key dictionaries mapping
each English source string to its translation. In this repo they were
**hand-authored by an LLM against the English source**, not produced by a
machine-translation backend, and **no native speaker has reviewed them yet**
(`_meta.humanReviewed: false`). Portuguese proper nouns — Cova da Iria, Loca do
Cabeço, Lúcia dos Santos, Francisco and Jacinta Marto, *O Século*, *Ilustração
Portuguesa*, *Documentação Crítica de Fátima* — stay in Portuguese in every
locale.

`test/i18n-completeness.test.js` mirrors the compiler's own walk and fails if
any translatable string is missing from a locale, or if a dictionary key has
gone stale.

## Contributing

Corrections against primary sources are very welcome — open an issue or a pull
request. Read [`AGENTS.md`](AGENTS.md) (working agreements and the
subject-specific sourcing rules), [`context.md`](context.md) (current state and
open questions) and [`KEYWORDS.md`](KEYWORDS.md) (name variants and search
traps) first.

## Licence

Data and prose: open data, corrections welcome. Cited sources remain the
property of their publishers; the `Ilustração Portuguesa` facsimile is a
public-domain scan hosted on Wikimedia Commons.
