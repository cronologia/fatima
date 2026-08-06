# context.md — cronologia/fatima

State of the repository, for the next agent or human. Read together with
`AGENTS.md` (working agreements + subject sourcing rules) and `KEYWORDS.md`
(name variants and search traps).

Last updated: **2026-08-05** (widened scope — before/after/reported miracles, core#71).

---

## 1. What this repo is

A compiled static chronology of the **reported apparitions at Fátima, Portugal
(1917)** together with **what came before and after them (1881–2017)**, built
from the `cronologia/core` template: one JSON file
(`data/chronology.json`) → `build.js` → `docs/{en,es,pt}/`, served by GitHub
Pages, zero runtime dependencies.

The editorial posture is the whole point of the project and is not negotiable:
**apparitions are reported events with Church judgments.** The data records who
reported what and when, and what the Church ruled and when, citing the ruling
document. The site's own voice never asserts — and never denies — the
supernatural claim. See `AGENTS.md` § "Data quality & sourcing rules" for the
five house rules this produces.

**Reported miracles follow the same posture, and it is worth stating separately
(core#71).** A miracle is a claim, not an event. Only two things attached to one
are datable and may enter `events[]`: (1) **the account** — that a cure was
*reported*, by whom, and when first attested; and (2) **the recognition act** —
a dated decision of the Church with a document behind it. So no `label` in this
dataset says "N was cured": the 1930 event says the commission's report
*enumerates* seventeen reported cures, and the 1999 and 2017 events are the two
*decrees* in the seers' cause. Aggregate claims are attributed to whoever makes
them (Formigão's report, not the site). Reported cures earn **no rung on the
approval ladder** — the ladder is about judgments on the *apparitions*, and it
was not touched by this wave.

## 2. Current state

| Thing | State |
|---|---|
| `data/chronology.json` | 33 events, 6 facts, 6 figures, 4 organizations, 4 disambiguation items, 31 references, an `approvalLadder` and a `consecrations` section |
| Date coverage | 1881 → 2017 |
| Unverified dates | **1** — the 1916 Angel apparitions (`dateVerified: false`) |
| `data/i18n/es.json` | 193/193 strings, hand-authored, `humanReviewed: false` |
| `data/i18n/pt.json` | 193/193 strings, hand-authored, `humanReviewed: false` |
| Optional viz (spine, map, swimlanes, lineage, charts) | **none declared** — the dataset carries no `threads`, `placesMap`, `numbersChart` etc., so none render |
| `data/archives.json` | **not created** — `scripts/archive-refs.js` has never been run (needs network) |
| `data/places.json` | **not vendored** — only needed if `placesMap` is ever declared |
| Gate | `validate-data.js` ✔ · `build.js` ✔ (3 locales) · `node --test` ✔ 183/183 |
| GitHub Pages | live at https://cronologia.github.io/fatima/ |
| Recorded date disagreements | **4** — `dateNote` on the 1918 restoration, the 1922 bulletin, the 1953 dedication and the 2017 decree |

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

### What the scope-widening wave changed (core#71)

The chronology was a tight band around 1916–1917 plus the Church's judgments. It
now carries the conditions that made the reports legible and the institutional
history that followed. **17 events added** (16 → 33), all sourced; **12
references added** (12 → 24); one fact added (`Reported cures`) and one
organization (`Congregation for the Causes of Saints`).

*Before (5):* the suppression of the Diocese of Leiria (30 September 1881 — an
act of the liberal **monarchy**, not of the Republic, which the sources make
plain and which readers routinely conflate); the proclamation of the Republic
(5 October 1910); the Law of Separation (20 April 1911); the restoration of the
diocese by *Quo vehementius* (17 January 1918); and the appointment of the
first resident bishop (15 May 1920). Those last two are what the approval
ladder's first rung already leaned on to explain the vacancy, and the
chronology now carries them.

*After (12):* the Capelinha (1919), the bomb attack on it (1922), *Voz da
Fátima* (1922), the commission's report (1930), Pius XII's consecration (1942),
the coronation of the image (1946), the Rosary basilica (1953), Paul VI's
pilgrimage (1967), the decree on the first reported cure (1999), Sister Lúcia's
death (2005), the Trinity basilica (2007) and the decree on the second reported
cure (2017).

**Every later papal act is named for what it is** — a consecration, a
coronation by a legate, a visit, a decree in a *cause about two persons*. None
is worded as a verdict on authenticity, because the ladder's Rome rung is
`not-found` and nothing added here may contradict it. The ladder itself was not
edited: no new Church act on the *apparitions* turned up.

**The retrospective-attestation caveat survives untouched** — the 1916 event,
the 1917-07-13 event, the 1935–1944 memoirs event and the dedicated
disambiguation item all still carry it, and the 1916 date is still
`dateVerified: false`.

**The DCF PDF was opened this time** (see §5.1, now closed). The free PDF at
`fatima.pt/files/upload/fontes/F001_DCF_selecao.pdf` was downloaded and read:
doc. 133 sits at pp. 549–550 and the operative words quoted in this dataset —
*"1º declarar como dignas de crédito as visões das crianças na Cova da Iria …
nos dias 13 de maio a outubro de 1917; 2º permitir oficialmente o culto de
Nossa Senhora de Fátima"* — are verbatim. The same read produced the 13 April
1930 commission report (doc. 120), its chapter *As curas extraordinárias* with
the seventeen cases, and the minute of approval (doc. 121).

### The `consecrations` section (repo-local, not a template feature)

Nine papal acts from 1942 to 2022, rendered below the chronology as a summary
table plus one card per act. It exists because the owner asked for it on the
premise that Fátima was approved because several popes each did part of a
consecration. **The premise does not survive the dates and the section is built
to show that rather than to argue it:** the approval is the diocesan pastoral of
13 October 1930, and every act in the section postdates it — the first by twelve
years.

Three closed enums drive the table, validated in `consecrationActs()` (unknown
value → build failure, exactly like the ladder's `status`):

| Enum | Values | Why it exists |
|---|---|---|
| `kind` | `consecration` · `entrustment` · `exhortation` | Signum Magnum asks the FAITHFUL to renew their own consecration and is routinely counted as a papal one; the 2013 act calls itself an *affidamento* and never says "consecrate" |
| `russia` | `named` · `unnamed` · `described` | The first of the two reported conditions. Only 1952 and 2022 are `named` |
| `bishops` | `united` · `alone` · `unknown` | The second. Only 1984 and 2022 are `united` |

**The renderer computes no verdict, and a test enforces that.** There is no
"satisfied" column, no tick, no cross, no total — the two columns report facts
about texts, and whether the conditions were met is a live dispute the page
attributes rather than settles (Sister Lúcia's letter of 8 November 1989, the
CDF's 2000 conclusion that further discussion is baseless, and the writers who
continue to disagree are all recorded). `test/build-helpers.test.js` fails if a
pass/fail glyph or the word "satisfied" ever reaches the markup.

`quote` is deliberately OUTSIDE `SUBTREE_TRANSLATABLE.consecrations`: the
excerpts are verbatim Latin, Italian and English from the acts themselves,
carried with a `lang` attribute, and a translated sentence inside quotation
marks attributed to Pius XII would be a fabrication. Translations belong in the
surrounding `text`, flagged as such.

Findings worth keeping, all from reading the acts rather than the literature:

- **1942** names neither Fátima nor Russia. The nearest is "ai popoli separati
  per l'errore o per la discordia".
- **1952** (*Sacro vergente anno*, AAS 44, pp. 505–511, read from the gazette
  PDF) names Russia and never mentions Fátima.
- **1964** is widely reported as Paul VI renewing the consecration. It is not:
  nn. 40 and 48 read *affidiamo* and *raccomandiamo*, the consecration recalled
  is Pius XII's, and the literature reporting the renewal also tends to date
  that act to 1952 when the world consecration was 1942.
- **2022** is the only act whose own text meets both conditions. The Holy See
  did not present it as supplying anything missing from 1984, and neither does
  this page.

## 3. Translations

`data/i18n/es.json` and `pt.json` are **exact-key dictionaries**: the key is the
verbatim English source string, the value the translation. The key set was
computed by re-running **`build.js`'s own walk** (`TRANSLATABLE_KEYS` plus the
`SUBTREE_TRANSLATABLE` allowlist, under which the `references` subtree
translates **only** `publisherNote`) — **not** from
`scripts/translate.js --stats`, which is not the compiler.

- 150 strings per locale, 150/150 present. `_meta.coverage` states this.
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

1. **~~The DCF PDF was never opened.~~ CLOSED.** The PDF was downloaded and
   read in the core#71 wave: doc. 133 is at pp. 549–550 and the quoted operative
   words check out verbatim, as do the 3 May 1922 provision, the 13 April 1930
   commission report (doc. 120) and its approval minute (doc. 121). What was
   **not** done is a page-by-page read of the whole 640-page volume; the events
   citing it name the document and page they rest on.
2. **Hemeroteca Digital (Lisbon) returns HTTP 403.** The *Ilustração
   Portuguesa* run is cited via a Wikimedia Commons facsimile instead. 403 is
   **inconclusive, not dead** (`net-access`); a session with different egress
   should retry and, if it resolves, cite the Hemeroteca directly.
3. **No Wayback snapshots yet.** `scripts/archive-refs.js` has never run;
   `data/archives.json` does not exist, so the references intro reports "0 with
   an Internet Archive fallback". Run it (or let `wayback.yml` run it) once the
   repo is on GitHub. `preserve-sources` applies.
4. **The reference list still leans official, and got more so.** 21 of 24 are
   Sanctuary, diocesan or vatican.va/causesanti.va. Two additions widen it a
   little: `parlamento-separacao-1911` is a **civil** state source rather than
   an ecclesiastical one, and `leiria-fatima-bula-1918` is by a working
   historian (Saul António Gomes) reading the bull, though published by the
   diocese. Observador remains the only independent outlet and there is still
   **no academic press and no critical/skeptical source at all** — no historian
   of the Portuguese First Republic writing outside a diocesan series, nothing
   from the meteorological/optical debunking literature, nothing on the Cold War
   "consecration of Russia" reception. Sourcing rule 3 is **still not
   satisfied**, and this remains the top research gap.
5. **Coverage is now 1881–2017, but there are named holes.** Deliberately left
   out for want of a reachable, dated source in this session: the
   1982/1991/2010 papal visits (only Paul VI's 1967 homily and the two later
   Roman decrees were verified against vatican.va / causesanti.va); the 1984
   Act of Entrustment; the 1981 assassination attempt and the bullet in the
   crown, which is a *reading* of a Fátima connection and needs its own
   sourcing; the 1931 national consecration of Portugal; the 1954 pilgrimage
   institutions; and the *Estado Novo*'s relationship to the shrine, which is
   contested terrain no source here supports handling carefully. Also **no
   individual reported cure is named as an event**: the seventeen 1924–1929
   cases are recorded as an enumeration in the commission's report because
   `Voz da Fátima` itself is not reachable online from this session, so no
   per-case citation could be given.
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
8. **`Congregation for the Doctrine of the Faith` and `Congregation for the
   Causes of Saints` render in English on the Spanish and Portuguese pages** as
   organization *names* (`name` is never translated, by design — they are proper
   nouns, and they match the cited publishers on vatican.va and causesanti.va). The body prose around it is localized via the
   glossary marker. Flagged in case the project later prefers localized
   institution names.
9. **No corpus sweep has been run.** `KEYWORDS.md` lists expected traps, not
   findings. No zero has been established for anything.
10. **`dateNote` is stored but never rendered.** Four events carry one (the 1918
   restoration, the 1922 bulletin, the 1953 dedication, the 2017 decree) and
   `build.js` has no branch for the field, so the disagreement lives in the data
   and not on the page. Every one of those four also states the disagreement in
   its `text`, which *is* rendered and translated, so nothing is hidden from a
   reader — but the field itself is dead weight until the template renders it.
   Same situation as `lourdes`, which is where the convention comes from.
11. **The Portuguese UI string for `not-found` reads `Não há registro de que
   este passo tenha ocorrido`.** `registro` is Brazilian; European Portuguese is
   `registo`, and the rest of this repo's pt is European. It is `UI` chrome in
   `build.js`, shared with the template, so it was left alone rather than
   forked — the fix belongs upstream in `cronologia/core`.

## 6. Owner action

GitHub Pages is enabled and the site is live at
<https://cronologia.github.io/fatima/>; `.github/workflows/deploy.yml` handles
rebuilds. Nothing is pending on the owner.
