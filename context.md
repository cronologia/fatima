# context.md — cronologia/fatima

State of the repository, for the next agent or human. Read together with
`AGENTS.md` (working agreements + subject sourcing rules) and `KEYWORDS.md`
(name variants and search traps).

Last updated: **2026-08-05** (bootstrap commit).

---

## 1. What this repo is

A compiled static chronology of the **reported apparitions at Fátima, Portugal
(1916–2017)**, built from the `cronologia/core` template: one JSON file
(`data/chronology.json`) → `build.js` → `docs/{en,es,pt}/`, served by GitHub
Pages, zero runtime dependencies.

The editorial posture is the whole point of the project and is not negotiable:
**apparitions are reported events with Church judgments.** The data records who
reported what and when, and what the Church ruled and when, citing the ruling
document. The site's own voice never asserts — and never denies — the
supernatural claim. See `AGENTS.md` § "Data quality & sourcing rules" for the
five house rules this produces.

## 2. Current state

| Thing | State |
|---|---|
| `data/chronology.json` | 16 events, 5 facts, 6 figures, 3 organizations, 4 disambiguation items, 10 references |
| Date coverage | 1916 → 2017 |
| Unverified dates | **1** — the 1916 Angel apparitions (`dateVerified: false`) |
| `data/i18n/es.json` | 84/84 strings, hand-authored, `humanReviewed: false` |
| `data/i18n/pt.json` | 84/84 strings, hand-authored, `humanReviewed: false` |
| Optional viz (spine, map, swimlanes, lineage, charts) | **none declared** — the dataset carries no `threads`, `placesMap`, `numbersChart` etc., so none render |
| `data/archives.json` | **not created** — `scripts/archive-refs.js` has never been run (needs network) |
| `data/places.json` | **not vendored** — only needed if `placesMap` is ever declared |
| Gate | `validate-data.js` ✔ · `build.js` ✔ (3 locales) · `node --test` ✔ 144/144 |
| GitHub Pages | **not enabled yet** — owner action, see §6 |

### What the bootstrap changed vs. what it inherited

Inherited from the interrupted previous session: all 16 events, the facts,
figures, organizations, disambiguation items and the 10 references — the
research is theirs and was **not** redone.

Changed in this session, all of it sourcing/i18n hygiene rather than research:

- `references[].type` moved onto the compiler's **closed vocabulary**
  (`official`, `book`, `archive`, `news`, `encyclopedia`). Free-text types
  ("official site", "church document", "facsimile", "press feature") fell
  through `UI.refTypes` untranslated and rendered as English on the Spanish and
  Portuguese pages. Where the nuance mattered ("critical edition", "church
  document") it now lives in `publisherNote`, which *is* translated.
- Prose parentheticals moved out of `publisher` into `publisherNote` for
  `ilustracao-portuguesa-facsimile`, `ecclesia-90-anos`, `observador-fatima`.
  This was a **failing test** (`references: publisherNote carries the prose,
  publisher the citation`), and it is the same leftover-English defect.
- `publisherNote` **added** to the three references that carried none
  (`jp2-beatification-2000`, `francis-canonization-2017`,
  `wikipedia-our-lady-fatima`) — sourcing rule 3 wants every reference labeled
  for perspective.
- Organization prose moved out of the untranslated `founded` field into the
  translated `relation` field (`founded` is now a bare year on all three), and
  `Diocese of Leiria (today Leiria-Fátima)` → `Diocese de Leiria-Fátima`,
  `Lúcia dos Santos (Sister Lúcia)` → `Lúcia dos Santos (Irmã Lúcia)`. Same
  reason: `name`, `founded` and `dates` are never routed through the
  dictionaries, so English prose parked there ships to every locale.
- `data/i18n/{es,pt}.json` written from empty seed to complete (§3).
- `README.md`, `KEYWORDS.md`, this file; `AGENTS.md` de-templated.

**No event text, date, place or source assignment was altered.** The sourcing
posture of the inherited events was checked against the rules and found sound:
apparitions are reported (`the children reported…`), the 1930 letter is cited
by name, date and DCF doc number, the Miracle of the Sun is attributed to
Almeida/*O Século*, and the retrospective character of the memoirs is stated in
three separate places (the 1916 event, the 1917-07-13 event, the 1935 event)
plus a dedicated disambiguation item.

## 3. Translations

`data/i18n/es.json` and `pt.json` are **exact-key dictionaries**: the key is the
verbatim English source string, the value the translation. The key set was
computed by re-running **`build.js`'s own walk** (`TRANSLATABLE_KEYS` plus the
`SUBTREE_TRANSLATABLE` allowlist, under which the `references` subtree
translates **only** `publisherNote`) — **not** from
`scripts/translate.js --stats`, which is not the compiler.

- 84 strings per locale, 84/84 present. `_meta.coverage` states this.
- `_meta.generatedBy` records the truth: **hand-authored by an LLM**
  (Claude Opus 5) directly against the English source. No machine-translation
  backend was involved; `scripts/translate.js` was never run.
- `_meta.humanReviewed: false`. **No native speaker has read these strings.**
- Portuguese proper nouns stay Portuguese in every locale: Cova da Iria, Loca do
  Cabeço, Valinhos, Aljustrel, Lúcia dos Santos, Francisco and Jacinta Marto,
  *O Século*, *Ilustração Portuguesa*, *Documentação Crítica de Fátima*,
  *A Divina Providência*, *dignas de crédito*.
- The pt strings are written as **European Portuguese** (`regista`, `sítio`,
  `canónico`, `facto`, `perspetiva`, `invulgar`). A Brazilian reader will find
  them slightly foreign; this was a deliberate choice for a Portuguese subject.
  Worth a decision if the project later prefers a neutral register.
- Glossary markers keep the id and translate only the visible text:
  `[[cdf-ddf|Congregation for the Doctrine of the Faith]]` →
  `[[cdf-ddf|Congregación para la Doctrina de la Fe]]` /
  `[[cdf-ddf|Congregação para a Doutrina da Fé]]`. Verified in the rendered
  pages.

## 4. Verified vs. unverified

**Unverified (1):** `1916` — the three Angel apparitions.
`dateVerified: false`, and the site renders the `?` flag for it. Reason: the
Sanctuary's own narrative dates them **only by season** (spring / summer /
autumn 1916), and they are attested retrospectively in Lúcia's Second and
Fourth Memoirs (1937, 1941), not in any 1917 record. There is no primary source
that fixes a day. This flag should probably stay flagged forever rather than be
"resolved".

**Everything else carries `dateVerified: true`,** including `1935–1944`, which
is a range rather than a single day — the four completion dates and the 1944
manuscript date are all in the event `text` and are individually sourced.

**All dates rest on secondary or official-Church sources read *about* the
primary documents, not on the primary documents inspected page by page.** The
1930 pastoral letter's operative words are quoted from the DCF selection via
the Sanctuary's published description; nobody in this session opened the PDF at
doc. 133 and read it. That is the single biggest verification gap.

## 5. Open questions / known gaps

1. **The DCF PDF was never opened.** `fatima-dcf-selecao` is cited for the 1930
   letter's wording, the 1922 provision and Almeida's full text. Someone should
   download the free PDF, read doc. 133, and confirm the quoted phrases and the
   doc number. Until then, treat the quotation marks as provisional.
2. **Hemeroteca Digital (Lisbon) returns HTTP 403.** The *Ilustração
   Portuguesa* run is cited via a Wikimedia Commons facsimile instead. 403 is
   **inconclusive, not dead** (`net-access`); a session with different egress
   should retry and, if it resolves, cite the Hemeroteca directly.
3. **No Wayback snapshots yet.** `scripts/archive-refs.js` has never run;
   `data/archives.json` does not exist, so the references intro reports "0 with
   an Internet Archive fallback". Run it (or let `wayback.yml` run it) once the
   repo is on GitHub. `preserve-sources` applies.
4. **The reference list leans official.** Six of ten are Sanctuary or
   vatican.va. Observador is the only independent outlet and there is **no
   academic and no critical/skeptical source at all** — no historian of the
   Portuguese First Republic, nothing on the anticlerical politics of 1917,
   nothing from the meteorological/optical debunking literature, nothing on the
   Cold War "consecration of Russia" reception. Sourcing rule 3 ("sources span
   the spectrum by design") is **not yet satisfied**. This is the top research
   gap.
5. **The chronology stops at 2017 and starts at 1916.** Nothing on the
   1920s–30s growth of the pilgrimage, the 1942/1952/1984 consecrations, the
   1967/1982/1991/2000/2010 papal visits, the 1981–82 assassination attempt
   reading, Lúcia's 2005 death as an event (it is only in a fact), or her cause
   of beatification. Also nothing on the *Estado Novo*'s relationship to the
   shrine — politically contested terrain that a chronology of this subject
   eventually has to handle carefully.
6. **`meta.threads` is undeclared, deliberately.** A lane taxonomy over this
   subject ("the seers' accounts" / "the Church's judgments" / "the public
   phenomenon"?) is an interpretive act and needs its own ticket, with the
   omissions written down. Do not derive lanes from the text.
7. **The localized pages carry the template's "machine-translated"
   disclaimer** ("Traducción automática del inglés" / "Tradução automática do
   inglês") although these strings were hand-authored. The warning is still
   *directionally* true — unreviewed, non-authoritative — but the wording is
   inaccurate. It is `UI` chrome in `build.js`, shared with the template, so it
   was left alone rather than forked; the right fix is upstream in
   `cronologia/core` (a disclaimer keyed on `_meta.generatedBy`).
8. **`Congregation for the Doctrine of the Faith` renders in English on the
   Spanish and Portuguese pages** as an organization *name* (`name` is never
   translated, by design — it is a proper noun, and it matches the cited
   publisher on vatican.va). The body prose around it is localized via the
   glossary marker. Flagged in case the project later prefers localized
   institution names.
9. **No corpus sweep has been run.** `KEYWORDS.md` lists expected traps, not
   findings. No zero has been established for anything.

## 6. Owner action

**Enable GitHub Pages** for `cronologia/fatima`: Settings → Pages → Deploy from
branch → `main` / `/docs`. The site is already built and committed; nothing else
is needed. `.github/workflows/deploy.yml` handles rebuilds thereafter.
