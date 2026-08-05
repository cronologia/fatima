# KEYWORDS.md — search terms, name variants and known traps

A **finding aid** for anyone searching sources, archives or corpora for this
project. Listing a term here is *not* asserting it, and it is not a claim that
the term appears anywhere. Read this before running a sweep (`sourcing-rules`,
"Absence is a claim").

**No corpus sweep has been run for this repo yet.** Nothing below is recorded as
a verified zero. The "traps" are failure modes to design a search *against*,
not findings. Before reporting that anything is absent, verify the zero, pair it
with a positive control from the same corpus by the same method, and write down
what established that the corpus is entire.

---

## 1. The apparition / the devotion

| Lang | Forms |
|---|---|
| **pt** | Nossa Senhora de Fátima · Nossa Senhora do Rosário de Fátima · Virgem de Fátima · as aparições de Fátima · o milagre do sol · a Senhora do Rosário · a Senhora mais brilhante que o sol |
| **es** | Nuestra Señora de Fátima · Virgen de Fátima · Nuestra Señora del Rosario de Fátima · las apariciones de Fátima · el milagro del sol |
| **en** | Our Lady of Fátima / Fatima · Our Lady of the Rosary of Fátima · the Fátima apparitions · the Miracle of the Sun |
| **fr** | Notre-Dame de Fátima · les apparitions de Fátima · le miracle du soleil |
| **it** | Madonna di Fátima · le apparizioni di Fátima · il miracolo del sole |
| **la** | *Beatae Mariae Virginis de Fatima* (liturgical memorial, 13 May) — **(to verify against the Roman Missal / Martyrologium)** |

## 2. The seers

- **Lúcia** — Lúcia dos Santos · Lúcia de Jesus dos Santos · Irmã Lúcia (pt) ·
  Sor Lucía (es) · Sister Lucia / Sr. Lucy (en) · Sœur Lucie (fr).
  Religious names in the Dorothean and then Carmelite communities differ from
  her baptismal name and are a common citation mismatch — **(to verify against
  the Sanctuary's `cronologia dos videntes` before using any of them)**.
- **Francisco** — Francisco Marto · Francisco de Jesus Marto · São Francisco
  Marto (after 2017).
- **Jacinta** — Jacinta Marto · Jacinta de Jesus Marto · Santa Jacinta Marto
  (after 2017). Spelling **Jacinta**, not *Jacintha*.
- Collectively: *os três pastorinhos* (pt) · *los tres pastorcillos* (es) ·
  *the three shepherd children / the three seers* (en) · *les trois bergers* /
  *les trois pastoureaux* (fr). Portuguese sources also say *os videntes*.

## 3. Other people

- **José Alves Correia da Silva** — Bishop of Leiria 1920–1957; the man who
  signed the 1930 approval. Appears as *D. José Alves Correia da Silva*,
  *D. José* and, in shorthand, *o Bispo de Fátima*. Searching only "Correia da
  Silva" is a very common Portuguese surname pair and will over-match.
- **Manuel Nunes Formigão** — the canon who interrogated the children from
  September 1917. He published under the pen name **"Visconde de Montelo"**;
  contemporary printings of the interrogations may carry only that name —
  **(to verify against the DCF before citing the pseudonym)**.
- **Avelino de Almeida** — the *O Século* correspondent. Search his headline as
  well as his name: *"Coisas espantosas!"*, *"Como o sol bailou ao meio-dia em
  Fátima"*.
- **Judah Ruah** — the *Ilustração Portuguesa* photographer (spelling varies:
  *Judah Bento Ruah*).
- **Angelo Sodano** (announced the Secret's publication, 13 May 2000) ·
  **Joseph Ratzinger** (the 2000 theological commentary).

## 4. Places

- **Cova da Iria** — the apparition site. Also written *Cova de Iria*.
- **Aljustrel** — the seers' hamlet **in the parish of Fátima**. ⚠️ There is
  also an **Aljustrel in the Alentejo** (a district municipality, mining town);
  an unqualified "Aljustrel" search returns mostly that one.
- **Loca do Cabeço** — the 1916 Angel site (also *Cabeço*).
- **Valinhos** — the 19 August 1917 site.
- **Vila Nova de Ourém** — the county whose administrator detained the children
  on 13 August 1917. Often shortened to **Ourém**; the administrator is usually
  named in sources as *Artur de Oliveira Santos* — **(to verify)**.
- **Leiria** — the diocese; restored 1918, renamed **Leiria-Fátima** in 1984.
- **Pontevedra** and **Tuy** — where Lúcia wrote the memoirs. *Tuy* (Spanish) =
  *Tui* (Galician); both spellings occur.
- **Coimbra** (pt) / **Coímbra** (es) — where Lúcia died in 2005.

## 5. Documents and set phrases

- **"A Divina Providência"** — the pastoral letter of **13 October 1930**; the
  key diocesan approval document. Many sources cite only "the 1930 approval"
  and never name the letter, so search the date *and* the title. Watch for the
  transposed date *30 October 1930*.
- ***dignas de crédito*** — the operative phrase ("worthy of belief"). Search
  the Portuguese, not only the English gloss.
- **Documentação Crítica de Fátima** (**DCF**) — the Sanctuary's multi-volume
  critical edition; the one-volume selection covers **1917–1930**. The 1930
  letter is **doc. 133** in that selection.
- **"The Message of Fatima"** (CDF, 26 June 2000) — *A Mensagem de Fátima* (pt),
  *El mensaje de Fátima* (es).
- **The Secret** — *o Segredo* / *o Terceiro Segredo* (pt), *el Secreto* /
  *el Tercer Secreto* (es), *le troisième secret* (fr). Note the memoirs speak
  of **one** Secret **in three parts**; "the three secrets" is a later popular
  reformulation and a bad search key.
- **Memórias da Irmã Lúcia** — the four memoirs (1935, 1937, 1941 ×2), plus the
  manuscript of **3 January 1944**.
- **1917 interrogations** — *interrogatórios* (parish and Formigão).

## 6. Traps to design searches against

1. **The accent.** `Fátima` ≠ `Fatima`. Portuguese and Spanish sources accent
   it; English ones often do not; vatican.va uses **Fatima** unaccented in its
   English titles (the CDF document is *"The Message of Fatima"*). Search both,
   and never match an accented string with a wildcard and call the result a
   zero.
2. **`Fátima` is one of the most common given names in the Portuguese- and
   Spanish-speaking world**, and — as the daughter of Muhammad — a central name
   in Islam. Other repos in this organization cover Islamic subjects. A bare
   `Fátima` sweep over any shared corpus is dominated by false positives;
   qualify with `Cova da Iria`, `1917`, `aparições`, `Leiria` or `pastorinhos`.
3. **`Fátima` is also a place name** (the Portuguese town, plus streets,
   parishes, schools and hospitals worldwide named after the devotion).
4. **"Miracle of the Sun" is a claim, not an event label.** Sources that report
   it, sources that assert it and sources that debunk it all use the same
   phrase. Match on the phrase, then read *who* is speaking before recording
   anything.
5. **"Approved by the Church" is ambiguous.** The 1930 act is **diocesan**.
   Sources saying "the Vatican approved Fátima" are almost always compressing
   the diocesan approval plus later papal acts; there is no separate papal
   approval decree. Do not let a loose secondary source create a phantom event.
6. **Retrospective attestation.** Any 1917 detail traced only to the memoirs
   (1935–1941) or the 1944 manuscript is *not* a 1917 source. Check the date of
   the **text**, not the date of the **event**, before treating a claim as
   contemporary.
7. **Hard-wrapped and hyphenated PDFs.** The DCF selection is a scanned/typeset
   PDF; a phrase search can break across a line ("Cova da\nIria") or a
   hyphenated word. Search on short distinctive tokens as well as phrases.
8. **Bot filters, not dead links.** The Lisbon *Hemeroteca Digital* returned
   HTTP 403 from this project's sessions. `403`/`429`/timeouts are
   **INCONCLUSIVE**, never "dead" — see `net-access` and the link-health rules
   in `AGENTS.md`.
