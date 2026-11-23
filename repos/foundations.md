---
industry: retail
region: Global
updated: 2026-11-23
---

# 🏗️ Foundational Repos — Retail & Consumer

> The layers you build a retail AI engagement **on top of**, rather than rebuild. All verified 2026-11-21
> (`git ls-remote` for existence, `search/repositories` for stars + last push, LICENSE read where the API
> was unclear). Ordered by layer, because the choice that matters in retail is which layer you sit at.

## Agentic-commerce protocols — the real differentiator this year

This layer did not exist in a usable form a year ago and is now the most important thing in the file.
Three competing standards plus two payment rails, **all Apache-2.0**:

| Spec / Repo | Repo | License | Stars | Last push | Role |
|---|---|---|---|---|---|
| UCP (Universal Commerce Protocol) | [Universal-Commerce-Protocol/ucp](https://github.com/Universal-Commerce-Protocol/ucp) | Apache-2.0 | 3,515 | 2026-11-21 | Google's standard, announced at NRF Jan 2026: lets agents discover products and complete orders. Microsoft has adopted it in Merchant Center. Pushed today — the most active of the three. |
| ACP (Agentic Commerce Protocol) | [agentic-commerce-protocol/agentic-commerce-protocol](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) | Apache-2.0 | 1,607 | 2026-07-18 | Maintained by **OpenAI and Stripe**. The checkout-side counterpart; this is what the ChatGPT commerce surface speaks. |
| AP2 (Agent Payments Protocol) | [google-agentic-commerce/AP2](https://github.com/google-agentic-commerce/AP2) | Apache-2.0 | 3,281 | 2026-06-17 | Consent and mandate layer for agent-initiated payments — the "did the human actually authorise this" problem. |
| x402 | [x402-foundation/x402](https://github.com/x402-foundation/x402) | Apache-2.0 | 6,820 | 2026-11-20 | HTTP-native per-request payments. Note the canonical home is now the **foundation** org; `coinbase/x402` still resolves (identical 11,324 B Apache LICENSE) but has a *different* HEAD, so it is the pre-donation repo, not a redirect. Build against the foundation slug. |
| A2A × x402 | [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | Apache-2.0 | 572 | 2026-11-11 | Bridges x402 into Google's Agent-to-Agent protocol, so agents can charge each other. |
| awesome-ucp | [Upsonic/awesome-ucp](https://github.com/Upsonic/awesome-ucp) | MIT | 131 | 2026-02-06 | Curated UCP ecosystem index — useful for tracking who has shipped adapters. |

**Read before choosing:** UCP and ACP are *not* interchangeable, and the two biggest commerce surfaces
speak different ones. `NVIDIA-AI-Blueprints/Retail-Agentic-Commerce` (Apache-2.0, in `agents/top.md`) is
the only reference implementation found that wires **both**, which makes it the cheapest way to stay
protocol-neutral instead of betting a client's roadmap on one standard.

## Recommendation & forecasting engines

| Repo | License | Stars | Last push | Base for AI? |
|---|---|---|---|---|
| [recommenders-team/recommenders](https://github.com/recommenders-team/recommenders) | MIT | 22,009 | 2026-11-05 | Yes — the reference recsys corpus, Linux Foundation governed |
| [gorse-io/gorse](https://github.com/gorse-io/gorse) | Apache-2.0 | 9,928 | 2026-11-20 | Yes — deployable engine with LLM rankers, not just a library |
| [NicolasHug/Surprise](https://github.com/NicolasHug/Surprise) | BSD-3-Clause | 6,829 | 2026-05-30 | Baseline only — explicit ratings, no implicit feedback |
| [Nixtla/statsforecast](https://github.com/Nixtla/statsforecast) | Apache-2.0 | 4,982 | 2026-11-19 | Yes — always build the statistical baseline first |
| [Nixtla/neuralforecast](https://github.com/Nixtla/neuralforecast) | Apache-2.0 | 4,318 | 2026-11-18 | Yes — neural demand models |
| [RUCAIBox/RecBole](https://github.com/RUCAIBox/RecBole) | MIT | 4,620 | 2025-02-24 | Vendor only — 94 algorithms but dormant ~21 months |
| [pytorch/torchrec](https://github.com/pytorch/torchrec) | BSD-3-Clause | live (refs=5,369) | — | Yes — large-scale sharded embeddings. `search/repositories` returns nothing for this live repo; LICENSE is 1,530 B BSD opening with a "All rights reserved" copyright line, which is normal BSD form, **not** a proprietary grant |
| [LarrySnyder/stockpyl](https://github.com/LarrySnyder/stockpyl) | MIT | 185 | 2026-06-10 | Yes — inventory optimisation (EOQ, newsvendor, multi-echelon) |
| [microsoft/RecAI](https://github.com/microsoft/RecAI) | MIT | 1,221 | 2026-01-27 | Vendor — LLM × recsys, dormant ~10 months |

## Retrieval & data layer

| Repo | License | Stars | Last push | Role |
|---|---|---|---|---|
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 | 35,652 | 2026-11-20 | Vector DB for product/semantic search. Fully Apache — the safe default over Meilisearch's BUSL-tainted EE |
| [apify/apify-mcp-server](https://github.com/apify/apify-mcp-server) | MIT | 17,199 | 2026-11-20 | Typed MCP access to external catalogue/pricing data |
| [Tracardi/tracardi](https://github.com/Tracardi/tracardi) | MIT | 657 | 2026-09-22 | Open CDP — profile unification, the input to any personalisation agent |
| [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | `MIT AND OpenLDAP AND BUSL-1.1` | 59,948 | 2026-11-20 | ⚠️ Mixed — see `agents/top.md`. EE parts are Business Source 1.1 |

## Regional payment rails

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [bacen/pix-api](https://github.com/bacen/pix-api) | **NO LICENSE FILE** | 3,010 | 2026-10-29 | Brazil's central bank Pix API spec — the rail that makes LATAM conversational checkout work. **Honesty requirement: there is no LICENSE file** (3 branches × 8 filenames all 404). It is an official public spec, but absent a grant, generate clients from it at build time and do not vendor the text into a client deliverable. |

## Measured gaps — searched for, genuinely not there

An informed gap is information; silence looks like coverage. These were searched this pass and came back
effectively empty:

- **Retail price optimisation: no credible open-source project exists.** `price optimization stars:>=100`
  returns 10 repos and **not one is retail** — they are energy market optimisers (`Akkudoktor-EOS/EOS`,
  `corneel27/day-ahead`), crypto MEV tooling and unrelated noise. Markdown/promo optimisation is the
  highest-value retail ML problem with the thinnest open-source floor.
- **Demand forecasting, retail-specific:** `retail demand forecasting stars:>=50` returns **2** repos, both
  student-grade (71★ unlicensed, 63★ MIT). The general-purpose Nixtla stack above is the only real option.
- **Product matching / entity resolution:** `product matching entity resolution stars:>=200` returns **0**.
  Catalogue deduplication across suppliers remains unsolved in the open.
- **Shrink / loss prevention:** no open tooling surfaced in either GitHub or web search. Vision-based shelf
  and theft analytics is entirely vendor territory.

---

## Added 2026-11-22 — the product-data plane, in three steps

The agentic-commerce layer above assumes a catalogue an agent can read. This section is that catalogue
layer, and it splits cleanly into three steps whose open-source health is **completely different**. All
rows verified 2026-11-22: existence by `git ls-remote`, stars/forks/last-push from one
`search/repositories` call, licence by reading the file.

### Step 1 — DECLARE what the product is (identity). Well equipped, permissive, alive.

| Repo | License | ★ / forks | Last push | Role |
|---|---|---|---|---|
| [gs1/GS1_DigitalLink_Resolver_CE](https://github.com/gs1/GS1_DigitalLink_Resolver_CE) | Apache-2.0 (read, 11357 B) | 65★ / 45f | 2026-11-02 | GS1's own resolver: GTIN → the authoritative set of URIs for that product. The piece Sunrise 2027 and DPP both need. |
| [gs1/GS1DigitalLinkToolkit.js](https://github.com/gs1/GS1DigitalLinkToolkit.js) | Apache-2.0 | 20★ / 6f | 2025-05-01 | Translates GS1 element strings ↔ Digital Link URIs; validates check digits and GCP length. |
| [gs1/GS1DL-resolver-testsuite](https://github.com/gs1/GS1DL-resolver-testsuite) | Apache-2.0 | 15★ / 8f | 2026-08-07 | Conformance suite for a resolver against the Digital Link spec — i.e. you can *prove* an implementation correct. |
| [zxing/zxing](https://github.com/zxing/zxing) | Apache-2.0 | 34217★ / 9428f | 2026-11-21 | The 1D/2D barcode decoding floor for the whole industry. DataMatrix and QR included. |
| [journeyapps/zxing-android-embedded](https://github.com/journeyapps/zxing-android-embedded) | Apache-2.0 | 5932★ / — | 2024-08-04 | Android scanning wrapper on ZXing. Widely used; dormant 2+ years. |
| [EventideSystems/brocade.io](https://github.com/EventideSystems/brocade.io) | AGPL-3.0 | 142★ / 9f | 2025-12-21 | Open GTIN/barcode product database. **The only repo above 100★ for `gtin barcode` — and it is AGPL,** so treat as a data service to call, not code to vendor. |

### Step 2 — MOVE it (events and trade messages). Also well equipped, mostly permissive.

| Repo | License | ★ / forks | Last push | Role |
|---|---|---|---|---|
| [openepcis/epcis-repository-ce](https://github.com/openepcis/epcis-repository-ce) | Apache-2.0 (read, 11357 B) | 17★ / 6f | 2026-10-22 | EPCIS 2.0 event repository (Quarkus + Kafka + OpenSearch). Open-core: a commercial Business Edition sits on top, so scope the CE boundary before promising features. |
| [openepcis/openepcis-epc-digitallink-translator](https://github.com/openepcis/openepcis-epc-digitallink-translator) | Apache-2.0 | 7★ / 4f | 2026-09-13 | EPC URN ↔ GS1 Digital Link, with GS1-rule validation. The join between step 1 and step 2. |
| [openepcis/epcis-testdata-generator](https://github.com/openepcis/epcis-testdata-generator) | Apache-2.0 | 8★ / 2f | 2026-10-28 | Generates valid EPCIS 2.0 / CBV 2.0 events — how you test a traceability integration without a client's real data. |
| [JaewookByun/epcis](https://github.com/JaewookByun/epcis) (Oliot) | Apache-2.0 | 51★ / 57f | 2026-01-15 | Academic-lineage EPCIS/CBV 2.0.0 implementation. Fork count (57) exceeds stars (51) — unusual, and the mark of a reference people actually modify. |
| [louisaxel-ambroise/epcis](https://github.com/louisaxel-ambroise/epcis) | Apache-2.0 — **declared in a 560 B pointer file**, API reports `NOASSERTION` | 36★ / 14f | 2026-11-22 | EPCIS 1.x + 2.0 on .NET 10. The only actively-pushed .NET option (committed the day of this pass). |
| [webofthings/epcis2.js](https://github.com/webofthings/epcis2.js) | Apache-2.0 | 37★ / 3f | 2025-09-26 | EPCIS 2.0 JavaScript SDK. |
| [ift-gftc/opentraceability](https://github.com/ift-gftc/opentraceability) | MIT | 8★ / 5f | 2026-09-24 | IFT/GFTC food-traceability libraries (C#). Partial protocol coverage by its own admission — read the caveat before promising conformance. |
| [indice-co/EDI.Net](https://github.com/indice-co/EDI.Net) | MIT (read, 1074 B) | 491★ / 172f | 2025-12-01 | EDIFACT + X12 + TRADACOMS serialiser/deserialiser. The best-licensed general EDI library found. |
| [kputnam/stupidedi](https://github.com/kputnam/stupidedi) | BSD-3-Clause | 293★ / 146f | 2026-09-16 | ASC X12 parse/generate in Ruby; high fork ratio, still maintained. |
| [nerdocs/pydifact](https://github.com/nerdocs/pydifact) | MIT (read, 1081 B) | 191★ / 54f | 2026-11-16 | EDIFACT in Python. Actively maintained. |
| [tastypackets/x12-parser](https://github.com/tastypackets/x12-parser) | MIT (read, 1071 B) | 63★ / 12f | 2026-11-18 | Streaming X12 parser in TypeScript. Smallest but freshest. |
| [php-edifact/edifact](https://github.com/php-edifact/edifact) | LGPL-3.0 | 289★ / 89f | 2025-10-30 | EDIFACT for PHP — relevant because the PIM/commerce layer in EMEA is overwhelmingly PHP. LGPL: dynamic linking is fine, modification is not free. |

### Step 3 — JUDGE whether the catalogue is *right*. No retail-specific floor at all.

The engines exist; **none of them knows anything about retail.** This is the whole finding.

| Repo | License | ★ / forks | Last push | Role |
|---|---|---|---|---|
| [unionai-oss/pandera](https://github.com/unionai-oss/pandera) | MIT | 4533★ / 527f | 2026-11-19 | Declarative dataframe validation. The most practical place to encode catalogue rules in Python. |
| [awslabs/deequ](https://github.com/awslabs/deequ) | Apache-2.0 | 3660★ / 584f | 2026-10-20 | Spark-scale data "unit tests" — the right fit for a multi-million-SKU catalogue. |
| [great-expectations/great_expectations](https://github.com/great-expectations/great_expectations) | Apache-2.0 | — (see note) | — | The best-known data-quality framework. **`search/repositories` returned HTTP 422 "cannot be searched" for this live repo** (`ls-remote` gives 11430 refs) — a fifth measurement of the search channel's false negatives, and the first where the failure was a 422 rather than an empty result. Stars left blank rather than guessed. |
| [sodadata/soda-core](https://github.com/sodadata/soda-core) | `NOASSERTION` — **not read this pass, treat as unverified** | 2463★ | 2026-11-22 | Data-contracts engine. Listed for completeness with its licence explicitly unresolved. |
| [dedupeio/dedupe](https://github.com/dedupeio/dedupe) | MIT | 4531★ / 578f | 2025-07-29 | Fuzzy matching / record dedup. The realistic basis for supplier-catalogue reconciliation. 16 months without a push. |
| [zinggAI/zingg](https://github.com/zinggAI/zingg) | AGPL-3.0 | 1275★ / 178f | 2026-11-03 | ML entity resolution / MDM. Alive, but AGPL — fine as a service behind an API, not for embedding in a client's product. |

### Measured gaps in this plane — searched for on 2026-11-22, genuinely not there

- **Product taxonomy classification: `product taxonomy classification stars:>=50` → 0. A literal zero.**
  Nothing open source maps a merchant's products onto a standard taxonomy, even though ACP's own feed
  schema has a `Category.taxonomy` field that is just a free-text string (see `intel/trends.md`).
- **`product description generation ai stars:>=30` → 0** and **`visual search product embedding stars:>=100`
  → 0.** The two most-demonstrated retail GenAI demos of the last two years have no open implementation
  above hobby scale.
- **Product attribute extraction is a 2019–2022 research graveyard.** `attribute extraction product
  stars:>=50` → **3**: `lonePatient/BERT-Attribute-Value-Extract` (62★, **no licence**, last push
  2020-02-18), `google-research-datasets/MAVE` (160★, `NOASSERTION`, 2022-12-16),
  `hackerxiaobai/OpenTag_2019` (84★, **no licence**, 2019-09-11). Not one is maintained and not one is
  usably licensed.
- **Product feeds — the false-abundance trap of this pass.** `product feed stars:>=100` returns **7 repos
  and not one is a retail product feed tool**: `feedbackjar` (product-team feedback), `RSSence` (RSS
  screensaver), `hacker-feeds-cli`, a Magento extension directory, a generic project list. The closest
  thing is `Czarto/ShopifyScripts` (MIT, 136★, dormant since 2024-05-24). Everything purpose-built for
  Google Merchant Center sits at 0–10 stars, often unlicensed, as single-platform plugins. **The layer the
  2026 trade press calls "the primary ranking layer of agentic commerce" has no open-source floor
  whatsoever.** Read the results, not the total: 99 repos matched `product feed merchant center`, and all
  of them were plugins.
- **No permissive MDM.** `master data management stars:>=100` → 4, of which only 2 are real software, and
  both are copyleft (`zingg` AGPL-3.0, `atrocore` GPL-3.0).

---

## Added 2026-11-22 (pass 2) — the store plane, in three steps

Same three-step method as the product-data plane earlier today, applied to the physical store:
**ring the sale → make it legal → see what is happening**. The gradient is sharper here than in any plane
this KB has measured, and it bends in an unexpected place: **the middle step is the best equipped**.

### Step 1 — RING IT (the register). Equipped, maintained, and copyleft.

| Repo | Licence (verified at source) | ★ / refs | Last push | Note |
|---|---|---|---|---|
| [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (43529 B, says LESSER) | 56025★ | 2026-11-22 | POS, stock, pricelists and fiscal localisations in one tree. API reports `NOASSERTION`. LGPL ⇒ proprietary modules are allowed — but see the AGPL inversion in step 2. |
| [frappe/erpnext](https://github.com/frappe/erpnext) | **GPL-3.0** (`license.txt` 34916 B, Markdown-formatted) | 41543★ / 52198 refs | 2026-11-22 | Full ERP with POS and warehouse. GPL-3.0, so a modified distribution must open. |
| [opensourcepos/opensourcepos](https://github.com/opensourcepos/opensourcepos) | **MIT** (LICENSE 2537 B) | 4530★ / 1410 refs | 2026-11-22 | The one genuinely permissive, genuinely maintained standalone retail till. API reports `NOASSERTION` only because the file carries a **26-name copyright roster** before the MIT grant. |
| [Blair2004/NexoPOS](https://github.com/Blair2004/NexoPOS) | **GPL-3.0** (LICENSE 35149 B) | 1310★ / 2125 refs | **2026-11-22 (same day)** | Laravel/Vue POS with inventory and registers. The most actively developed dedicated POS measured. |
| [Raktim94/nodedr-pos](https://github.com/Raktim94/nodedr-pos) | **AGPL-3.0** | 42★ | 2026-11-22 | Barcode checkout, returns, customer credit. AGPL ⇒ unusable as a hosted multi-tenant till without releasing source. |

**The warning row.** [tngoman/Store-POS](https://github.com/tngoman/Store-POS) — 1058★, 115 refs, pushed
2026-10-25 — is the **highest-starred result for `point of sale retail stars:>=300` (which returns exactly
one repo), and it has no licence file at all.** Probed on 2 branches × 8 filenames: nothing. No licence
means no grant: default copyright, not permission. The best-looking POS on GitHub cannot be used, and a
keyword-ingest pass would have put it at the top of the table.

### Step 2 — MAKE IT LEGAL (fiscalisation). The best-equipped layer in retail — and the only one whose licence changes by country.

This is the discovery of the pass. Every store transaction must be reported to a tax authority in a
country-specific format, and **mature open-source exists for each one — under a different licence in each
jurisdiction.** No other retail capability behaves this way.

| Country / network | Repo | Licence (read at source) | ★ / forks | Last push |
|---|---|---|---|---|
| 🇧🇷 Brazil NF-e | [wmixvideo/nfe](https://github.com/wmixvideo/nfe) | **Apache-2.0** (LICENSE 10850 B, appendix stripped) | 770★ / 411f | 2026-11-16 |
| 🇧🇷 Brazil NF-e | [nfephp-org/sped-nfe](https://github.com/nfephp-org/sped-nfe) | **LGPL-3.0** (`LICENSE.md` 8851 B) | 1635★ / 1169 refs | 2026-11-13 |
| 🇧🇷 Brazil NF-e | [TadaSoftware/PyNFe](https://github.com/TadaSoftware/PyNFe) | **LGPL-3.0** (LICENSE 7854 B) | 599★ / 237 refs | 2026-02-20 |
| 🇧🇷 Brazil NF-e | [nfewizard-org/nfewizard-io](https://github.com/nfewizard-org/nfewizard-io) | **GPL-3.0** (`LICENSE.txt` 34618 B) | 330★ | 2026-11-08 |
| 🇲🇽 Mexico CFDI | [phpcfdi/sat-ws-descarga-masiva](https://github.com/phpcfdi/sat-ws-descarga-masiva) | **MIT** (LICENSE 1106 B) | 198★ | 2026-09-20 |
| 🇲🇽 Mexico CFDI | [SAT-CFDI/python-satcfdi](https://github.com/SAT-CFDI/python-satcfdi) | **MIT** (`license`, 1056 B) | 169★ / 205 refs | 2026-11-08 |
| 🇲🇽 Mexico CFDI | [eclipxe13/CfdiUtils](https://github.com/eclipxe13/CfdiUtils) | **MIT** (LICENSE 1111 B) | 146★ | 2026-11-15 |
| 🇲🇽 Mexico CFDI | [phpcfdi/resources-sat-catalogs](https://github.com/phpcfdi/resources-sat-catalogs) | **Unlicense** (2571 B, public domain) | 97★ / 424 refs | 2026-11-20 |
| 🇨🇱 Chile DTE | [LibreDTE/libredte-lib-core](https://github.com/LibreDTE/libredte-lib-core) | **AGPL-3.0** (`COPYING` 34520 B) | 228★ / 166f | 2026-11-19 |
| 🇨🇱 Chile DTE | [LibreDTE/libredte-api-client-php](https://github.com/LibreDTE/libredte-api-client-php) | **LGPL-3.0** | 17★ | 2026-03-23 |
| 🇪🇺 Peppol AS4 | [phax/phase4](https://github.com/phax/phase4) | **Apache-2.0** (LICENSE 10173 B) | 246★ / 67f | 2026-11-18 |
| 🇪🇺 EN 16931 | [josemmo/einvoicing](https://github.com/josemmo/einvoicing) | **MIT** (LICENSE 1124 B) | 180★ / 43f | 2026-11-07 |
| 🇪🇺 Peppol AP | [OxalisCommunity/oxalis](https://github.com/OxalisCommunity/oxalis) | **EUPL-1.1 or later** — see below | 150★ / 280 refs | 2026-04-16 |
| 🇪🇺 UBL/Peppol | [num-num/ubl-invoice](https://github.com/num-num/ubl-invoice) | **MIT** (LICENSE 1070 B) | 143★ / 236 refs | 2026-11-03 |
| 🇪🇺 Validation | [phax/phive](https://github.com/phax/phive) | **Apache-2.0** (LICENSE 11325 B) | 79★ / 199 refs | 2026-11-19 |
| 🇪🇺 Peppol BIS spec | [OpenPeppol/peppol-bis-invoice-3](https://github.com/OpenPeppol/peppol-bis-invoice-3) | **No licence file** (spec repo) | 158★ / 349 refs | 2026-11-06 |
| 🇮🇳 India GST | [resilient-tech/india-compliance](https://github.com/resilient-tech/india-compliance) | **GPL-3.0** (`license.txt` 35149 B) | 286★ / 4725 refs | 2026-11-20 |

**The licence of being legal, by region:** Mexico **MIT/Unlicense** → Brazil **Apache-2.0 / LGPL-3.0** →
EU **Apache/MIT libraries over an EUPL access point** → India **GPL-3.0 inside ERPNext** → Chile
**AGPL-3.0 core**. A single multi-country rollout therefore crosses four licence families, and the
compliance obligation is not negotiable, so **the licence picks the architecture, not the other way round**.

### The sharpest licence finding of this pass: EUPL, and where it hides

`OxalisCommunity/oxalis` is the reference open-source **Peppol Access Point** — the component Globant would
run to connect a client to EU *and* Singapore e-invoicing. The GitHub API reports `NOASSERTION`. Probing 2
branches × 8 filenames found nothing; `README.md` returned 200, so the repo was reachable and the filenames
were wrong. A shallow clone resolved it in one call, and the repo ships **two disagreeing licence artefacts**:

- `COPYING.LGPL` — the full LGPL-3.0 text (7650 B), a filename no previous probe in this KB had tried.
- `COPYRIGHT` (799 B) — the **operative declaration**: *"Copyright 2010-2020 Norwegian Agency for Public
  Management and eGovernment (Difi) … Licensed under the EUPL, Version 1.1 or — as soon they will be
  approved by the European Commission — subsequent versions of the EUPL."*

**EUPL is the licence family that only appears in EU public-sector-origin infrastructure, and it is exactly
the family an EMEA compliance engagement walks into.** EUPL-1.2 §3 treats *communicating the work* as
distribution, so hosting a Peppol access point as a service can trigger source provision much as AGPL
would — and no SPDX field, badge or source-tree SBOM scan shows it, because the declaration lives in a file
called `COPYRIGHT`. **Add `COPYING.LGPL` and `COPYRIGHT` to the probe list.**

### Step 3 — SEE IT (shelf, queue, labour). No retail-specific floor at all.

| What was searched (2026-11-22) | Result |
|---|---|
| `planogram` | **502 repos — top result has 17★.** [Alijanloo/Retail-Shelf-Monitoring](https://github.com/Alijanloo/Retail-Shelf-Monitoring) MIT, 17★, 2 refs. Then [gamma-opt/ShelfSpaceAllocation.jl](https://github.com/gamma-opt/ShelfSpaceAllocation.jl) MIT 15★ (dead 2020-11-27) and [laitalaj/cvpce](https://github.com/laitalaj/cvpce) MIT 11★, 3 refs (dead 2021-06-24) — the only repo whose stated purpose *is* planogram-compliance evaluation. |
| `shelf monitoring retail stars:>=30` | **1 repo worldwide**: [mirzayasirabdullahbaig07/SmartStore-AI](https://github.com/mirzayasirabdullahbaig07/SmartStore-AI), 45★, **no licence**, and its own description calls it a *simulation*. |
| `product detection retail shelf yolo stars:>=100` | **0** |
| `SKU110K retail product detection dataset stars:>=50` | **0** |
| `self-checkout stars:>=10` | 28 results, and the top six are **keyword collisions on "self-hosted"** (payment gateways, a robotics framework, a W3C report dump). The only genuine entries: `Ashwinbicholiya/scanpay` MIT 40★ **dead since 2020-10-11** and `angsaikia/Walmart-Smart-Shopping-Cart` 38★ no licence, 2020. |
| `rfid inventory stars:>=30` | 3 results, **none retail**: a home asset-management app and a 3D-printer filament manager (`TigerTag`). Another false-friend pair. |
| `workforce scheduling stars:>=150` | **1 repo**: [Staffjoy/v2](https://github.com/Staffjoy/v2), MIT, 1686★, **dead since 2022-12-06**. The single best-starred workforce-management repo in open source has not moved in four years. |
| `employee shift scheduling stars:>=50` | 3 results, all GPL or unlicensed, best is 130★ and dead since 2019. |

**Conclusion for step 3, stated as a gap because it is one:** the shelf, the queue, the aisle and the roster
have **no maintained, retail-specific, permissively licensed open-source floor**. What exists is a generic
substrate — Timefold (Apache-2.0) for the roster, `supervision` (MIT) for the vision — plus a corpus of
student projects on AGPL weights. Together with cycle 8's finding that markdown/assortment optimisation has
no floor either, **store execution is now the second confirmed place to build proprietary Globant IP.**

### Method notes earned this pass (reusable across all twelve industries)

- **`search/repositories` with a `repo:owner/name` qualifier defeats the false-negative problem.** Earlier
  cycles concluded "existence is `ls-remote`, full stop" after keyword queries missed real repos. The
  qualifier resolved **7 of 7** slugs that keyword search had missed, *and* returns stars, forks, licence
  and `pushed_at` — which `gh api repos/<slug>` cannot, because it still 403s for non-attached repos. The
  false negatives are a keyword-ranking artefact, not an index gap. Use `repo:` for a known slug;
  `ls-remote` remains the authority on existence.
- **`NOASSERTION` is not "no licence" — it is "GitHub's classifier failed".** Four hit this pass and all
  four resolved by reading the file: `opensourcepos` = MIT behind a 26-name roster, `sped-nfe` = LGPL-3.0,
  `odoo` = LGPL-3.0, `oxalis` = EUPL-1.1 declared in `COPYRIGHT`.
- **An oversized MIT file is a long copyright roster, not a different licence.** MIT is ~1050–1130 B;
  `opensourcepos` at 2537 B is MIT plus 26 copyright lines. Useful byte fingerprints confirmed today:
  **34523 = AGPL-3.0**, **35149 = GPL-3.0 plain**, **34916 = GPL-3.0 Markdown**, **7650–8851 = LGPL-3.0**,
  **16725 = MPL-2.0**, **11325–11358 = Apache-2.0 full**, **10173–10850 = Apache-2.0 appendix-stripped**.
- **The control request must not assume `README.md` either.** `SAT-CFDI/python-satcfdi` 404s on
  `LICENSE`, `LICENSE.md`, `COPYING` **and `README.md`** on both branches, yet `ls-remote` gives 205 refs.
  The project is all-lowercase and reStructuredText: its files are `license` (no extension) and
  `readme.rst`. The media-pass rule "if README.md also 404s, your filenames are wrong" held — the fix is a
  shallow clone, and it cost one call.
- **In compliance code, forks beat stars as an adoption signal.** `OCA/l10n-mexico` has 20★ / **56 forks**
  and `OCA/l10n-chile` 10★ / **41 forks** (ratios 2.8 and 4.1). Nobody stars a tax localisation; they fork
  it to patch it for a client. A star-gated query would have discarded both as noise.

## Added 2026-11-22 (pass 3) — the retail media plane, in four steps

Retail media is the business of a retailer selling advertising against its own
first-party data. It is, by most counts, the fastest-growing profit pool in
retail — and before this pass the words **"retail media", "advertising" and
"clean room" appeared zero times in all eight files of this KB**. Nine cycles
had described retail as storefront, catalogue and store, and left out the part
that pays for them.

Everything below was measured on 2026-11-22: existence by `git ls-remote`
(ref count), liveness by a `--bare --depth 1 --filter=blob:none` clone reading
the last commit date, licence by reading the file at
`raw.githubusercontent.com`, with its byte size recorded. **Star counts are
deliberately absent** — `gh api repos/<slug>` is still 403 for non-attached
repos, so stars cannot be measured through the available channel, and this KB
has twice recorded fabricated star curves (Gorse, RecBole, NeuralForecast in
cycles 2/3/7; MDAgents in healthcare). An unmeasurable field is better left
out than guessed.

### Step 1 — SERVE IT (the auction). Mature, permissive, and committing today.

The header-bidding/auction substrate is the healthiest layer in this plane. All
Apache-2.0, all active within four days of this pass.

| Repo | Licence (read at source) | refs | Last commit | Role |
|---|---|---|---|---|
| [prebid/Prebid.js](https://github.com/prebid/Prebid.js) | Apache-2.0 (10760B, `master`) | 14749 | 2026-11-22 (0d) | Client-side header bidding; the de-facto browser auction layer |
| [prebid/prebid-server](https://github.com/prebid/prebid-server) | Apache-2.0 (10759B, `master`) | 4327 | 2026-11-19 (3d) | Go server-side auction; self-hostable alternative to hosted S2S |
| [prebid/prebid-server-java](https://github.com/prebid/prebid-server-java) | Apache-2.0 (10759B, `master`) | 3985 | 2026-11-18 (4d) | JVM implementation of the same spec; pick by platform team skills |
| [InteractiveAdvertisingBureau/openrtb](https://github.com/InteractiveAdvertisingBureau/openrtb) | ⚠️ **NO LICENCE FILE** (root tree verified) | 198 | 2026-04-14 (222d) | The OpenRTB 3.0 / AdCOM spec text itself — see warning below |
| [revive-adserver/revive-adserver](https://github.com/revive-adserver/revive-adserver) | ⚠️ **GPL-2.0** (15235B) | 858 | 2026-11-22 (0d) | The only mature open-source ad *server*; actively maintained, copyleft |

**⚠️ OpenRTB has no licence file.** The root tree of
`InteractiveAdvertisingBureau/openrtb` contains exactly: `.gitignore`,
`OpenRTB v3.0 FINAL.md`, `README.md`, `ads.cert: Signed Bid Requests 1.0
BETA.md`, `extensions/`, `supplychainobject.md`. No `LICENSE` under any of
eight candidate names, on either `main` or `master`. The substrate of all
programmatic advertising ships its specification with no grant attached.
Treat it exactly as cycle 8 treated `bacen/pix-api`: **implement from the
spec, do not vendor the repo** into a client deliverable.

**⚠️ revive-adserver is GPL-2.0, and that is the whole story of the ad-server
layer.** It is genuinely alive (committed the day of this pass). It is also
copyleft, which makes it a poor base for a white-label retail media product
sold to a retailer — the same shape as cycle 8's nopCommerce finding, for the
same commercial reason.

### Step 2 — SELL IT TO AN AGENT (agentic ad buying). New, Apache-2.0, alive.

This is the 2026 development, and it is the direct counterpart to the
agentic-*commerce* protocols cycle 8 mapped (UCP / ACP / AP2 / x402).

| Repo | Licence (read at source) | refs | Last commit | Role |
|---|---|---|---|---|
| [adcontextprotocol/adcp](https://github.com/adcontextprotocol/adcp) | Apache-2.0 (10767B) | 8610 | 2026-11-22 (0d) | **Ad Context Protocol** — spec + SDKs for agents buying media. Ships `CHARTER.md`, `IPR_POLICY.md`, `CONTRIBUTORS.md` |
| [prebid/salesagent](https://github.com/prebid/salesagent) | Apache-2.0 (10767B) | 2354 | 2026-11-23 (0d) | AdCP **sales-agent** server under Prebid.org: exposes inventory to agents over MCP + A2A, integrates Google Ad Manager |
| [Setupad/salesagent](https://github.com/Setupad/salesagent) | Apache-2.0 (10767B) | 10 | 2026-10-19 (34d) | A second, independent sales-agent deployment — evidence the role has more than one implementer |
| [IABTechLab/AAMP](https://github.com/IABTechLab/AAMP) | Apache-2.0 (11356B) | 5 | 2026-09-22 (61d) | IAB Tech Lab's rival protocol. ⚠️ **Repo contains two files: `LICENSE` and `README.md`, one commit.** See the asymmetry note |

`adcontextprotocol/salesagent` and `prebid/salesagent` return **identical HEAD
SHAs (`dcd14d0f`) and identical ref counts (2354)** — by the rename test this
KB has now used in three industries (matching HEAD = redirect, differing HEAD =
two repos), they are **one repository, not two**. The README is served from
`prebid/` and says "maintained under Prebid.org", so **`prebid/salesagent` is
the canonical slug.**

Read the project's own status note before proposing it: *"Status: alpha. A
pre-1.0 implementation of a pre-release protocol... It is one of several AdCP
sales-agent implementations, not a sole or canonical reference."* It pins the
`adcp` SDK version exactly in `pyproject.toml` and enforces the pin with a CI
guard (`tests/unit/test_adcp_spec_version.py`) that fails on drift — which is
the correct engineering posture toward a moving spec, and worth copying.

### Step 3 — IDENTIFY IT (identity and consent). Equipped and alive.

| Repo | Licence (read at source) | refs | Last commit | Role |
|---|---|---|---|---|
| [IABTechLab/uid2-operator](https://github.com/IABTechLab/uid2-operator) | **Apache-2.0** (11348B) | 4067 | 2026-11-22 (0d) | Unified ID 2.0 operator — the privacy-preserving identity service |
| [IABTechLab/uid2docs](https://github.com/IABTechLab/uid2docs) | Apache-2.0 (11356B) | 1543 | 2026-11-20 (2d) | UID2 integration documentation (note the slug: **no hyphen**) |
| [InteractiveAdvertisingBureau/iabtcf-es](https://github.com/InteractiveAdvertisingBureau/iabtcf-es) | Apache-2.0 (11360B, `master`) | 434 | 2026-09-01 (82d) | Reference TCF consent-string encoder/decoder — required for EU ad serving |
| [orestbida/cookieconsent](https://github.com/orestbida/cookieconsent) | MIT (1071B, `master`) | 275 | 2026-11-22 (0d) | Lightweight consent UI; MIT, so safe in a white-label storefront |

**⚠️ Licence correction — UID2.** Public sources conflict: The Trade Desk's
own press release announcing the contribution says the code would be released
under **BSD-2**, while `unifiedid.com` documentation states **Apache-2.0**.
Measured at source, `IABTechLab/uid2-operator/LICENSE` is the **full Apache-2.0
text at 11348 bytes**. Apache-2.0 is correct; the press release is wrong. This
is the fourth industry in which a vendor announcement has misstated the licence
of its own donated code. **A press release is not a licence.**

### Step 4 — PROVE IT (measurement, MMM, incrementality). Half of it is dead.

This layer is where the listicles and the repositories disagree most sharply.
Five libraries are routinely presented together as the open-source measurement
stack. Measured, **two are alive and three are not.**

| Repo | Licence (read at source) | refs | Last commit | Verdict |
|---|---|---|---|---|
| [google/meridian](https://github.com/google/meridian) | Apache-2.0 (11357B) | 1725 | 2026-11-20 (2d) | ✅ **Alive.** Bayesian MMM, geo-level priors, principled uncertainty. The default choice |
| [pymc-labs/pymc-marketing](https://github.com/pymc-labs/pymc-marketing) | Apache-2.0 (11356B) | 2338 | 2026-11-22 (0d) | ✅ **Alive.** Bayesian MMM **+ CLV + Bass diffusion** in one library; most customisable |
| [facebookincubator/GeoLift](https://github.com/facebookincubator/GeoLift) | MIT (1092B, `LICENSE.md`) | 211 | 2026-04-01 (235d) | ⚠️ Slowing. Geo-experiment lift testing; still the standard calibration tool |
| [facebookexperimental/Robyn](https://github.com/facebookexperimental/Robyn) | MIT (1091B) | 548 | `main` 2025-06-27 (513d) | ❌ **Dormant ~17 months.** See the branch trap below |
| [google/lightweight_mmm](https://github.com/google/lightweight_mmm) | Apache-2.0 (11357B) | 51 | 2025-06-17 (523d) | ❌ **Superseded by Meridian** — Google's own predecessor. Do not start here |

**⚠️ The Robyn branch trap — a transferable measurement error.**
`facebookexperimental/Robyn`'s **default branch is
`accuracy/allocator_v2_fixes`**, a feature branch, not `main`. Two consequences:

1. A plain `git clone` of Robyn checks out **non-release code from
   2024-11-21**. Anyone cloning it to build gets a feature branch.
2. Any automated ingest that measures "last commit" via the default branch
   reports **731 days** dormant. The honest figure, read from `main`
   explicitly, is **513 days** (2025-06-27). This pass made that error first
   and caught it only by re-measuring `main` by name.

**Method rule, applies to all twelve industries: the default branch is not
necessarily `main`. Resolve it, and measure `main`/`master` by name as well.**
Robyn is still presented by 2026 MMM commentary as one of two "open-source
giants" alongside Meridian. On the evidence it is a dormant library with a
confusing default branch, and Meridian or PyMC-Marketing should carry new work.

### Step 5 — MATCH IT PRIVATELY (the clean room). Not one maintained option.

The clean room is where a retailer and a brand compare audiences without
either handing over its customer list. It is the layer every retail media
network buys from a vendor, and vendors size it at **$2.8B (2025) → $14.6B
(2034), ~20.1% CAGR, with measurement-and-attribution the fastest-growing
application at 22.6%** (Dataintelo — a market-research vendor; directional).

**Every open-source data clean room found is dormant by more than two years:**

| Repo | Licence (read at source) | refs | Last commit | Note |
|---|---|---|---|---|
| [tiktok-privacy-innovation/PrivacyGo-DataCleanRoom](https://github.com/tiktok-privacy-innovation/PrivacyGo-DataCleanRoom) | Apache-2.0 (11356B) | 4 | 2024-10-31 (752d) | Closest thing to a purpose-built OSS clean room |
| [Snowflake-Labs/sfquickstart-data-clean-room](https://github.com/Snowflake-Labs/sfquickstart-data-clean-room) | Apache-2.0 (11356B) | 14 | 2024-03-11 (986d) | A **quickstart demo** bound to proprietary Snowflake, not a product |
| [qascade/dcr](https://github.com/qascade/dcr) | ⚠️ AGPL-3.0 (35215B) | 40 | 2023-06-13 (1258d) | Independent attempt; AGPL and abandoned |

The **primitives**, by contrast, are alive and permissive — which is why the
recipe in `compose/patterns.md` Pattern 14 assembles a clean room rather than
forking one:

| Repo | Licence (read at source) | refs | Last commit | Primitive |
|---|---|---|---|---|
| [google/differential-privacy](https://github.com/google/differential-privacy) | Apache-2.0 (13499B) | 471 | 2026-11-20 (2d) | ✅ DP aggregation/accounting across C++/Go/Java/Python |
| [OpenMined/PSI](https://github.com/OpenMined/PSI) | Apache-2.0 (11356B, `master`) | 235 | 2026-09-20 (63d) | ✅ Private set intersection (ECDH + Bloom/Golomb); C++/JS/Go/Python/Rust bindings |
| [google/private-join-and-compute](https://github.com/google/private-join-and-compute) | Apache-2.0 (11357B, `master`) | 31 | 2026-03-09 (258d) | ⚠️ Private join **and aggregate sum** — the exact clean-room primitive |
| [Optable/match](https://github.com/Optable/match) | Apache-2.0 (10172B, **`LICENCE.md`**) | 99 | 2024-10-24 (759d) | ❌ Dormant. Production-oriented Go PSI from an adtech vendor |
| [tiktok-privacy-innovation/PrivacyGo](https://github.com/tiktok-privacy-innovation/PrivacyGo) | Apache-2.0 (11356B) | 15 | 2025-01-24 (667d) | ❌ Dormant. **DPCA-PSI**: intersection statistics under differential privacy, built for ad measurement |

And the reporting layer underneath, both Apache-2.0 and committing this week:
[apache/pinot](https://github.com/apache/pinot) (11356B, `master`, 17558 refs,
2026-11-21, 1d) and [apache/druid](https://github.com/apache/druid) (19315B,
`master`, 17408 refs, 2026-11-21, 1d) — real-time OLAP, the standard way to
serve advertiser-facing campaign dashboards at ad-event volume.

### ⚠️ Method note earned this pass: the licence probe gave a false negative

This pass first recorded `Optable/match` as having **no licence file**, having
probed eight filenames (`LICENSE`, `LICENSE.md`, `LICENSE.txt`, `LICENCE`,
`LICENCE.txt`, `COPYING`, `LICENSE-APACHE`, `NOTICE`) on both `main` and
`master`. The file is **`LICENCE.md`** — British spelling *with* the `.md`
extension, a combination the probe list missed. It is Apache-2.0, 10172 bytes.

Two corrections follow, both reusable:

1. **Add `LICENCE.md` to every licence probe.** Cycle 8 already found
   Akeneo's `LICENCE.txt`; the `.md` variant is a separate miss.
2. **A filename probe cannot prove absence. A root-tree listing can.**
   `git ls-tree HEAD --name-only` on the bare clone is authoritative and
   costs nothing once cloned. That is how OpenRTB's missing licence was
   *confirmed* rather than merely suspected. **Use the tree to prove a
   negative; use raw reads to prove a positive.**

### Measured gaps in this plane — searched for on 2026-11-22, genuinely not there

| Query (`gh api search/repositories`) | Result | Reading |
|---|---|---|
| `retail media stars:>=50` | **1** | And it is `marcotav/supervised-machine-learning` (2020, no licence) — a generic regression tutorial. Not retail media |
| `retail media network stars:>=10` | **3** | **All three are Windows-7 / Minecraft DxDiag dumps** from 2013–2015. See the collision note |
| `clean room advertising stars:>=50` | **0** | Literal zero |
| `header bidding stars:>=50` | **2** | The whole header-bidding world is the Prebid org |
| `data clean room stars:>=20` | 18 hits, **3 real** | The rest are Android "Clean Architecture"/Room-DB apps, a news reader, a coin tracker |
| `marketing mix model stars:>=100` | **6** | Small, and 3 of the famous 5 are dormant (above) |
| `openrtb stars:>=100` | **10** | Thin for the substrate of all programmatic |
| `private set intersection stars:>=100` | **7** | Cryptography, not retail |
| `ad server stars:>=200` | **51** | The generic adtech layer *is* populated — the retail-shaped layer is not |
| `incrementality stars:>=20` | 952 | **Contaminated query, discarded** — the word is generic across ML and finance |

**⚠️ The keyword collision reproduced itself, live, in this pass.** Cycle 8's
flagship defect was `2No2Name/hopperOptimizations` — a **Minecraft mod** about
in-game hoppers — carried in `agents/top.md` as retail *inventory* intelligence.
Querying `retail media network stars:>=10` today returns `dovnel/Win-7`,
`denman2328/Help` and `Camus777/Minecraft`: DxDiag system-information dumps, in
which the words "Retail" (Windows edition), "Media" (Media Center) and
"Network" all appear. **Three of three hits are garbage.** A keyword search in
this sector returns confident, plausible-looking, wholly wrong rows, and the
only defence is opening each one. Nothing from either query was written into
this KB as data.

---

## Added 2026-11-23 — the returns & recovery plane (the reverse flow), in six steps

**Why this plane, and how it was chosen.** `retail-kb` already had four passes
(2026-11-21 base, then product-data, store and retail-media on 2026-11-22). Per
the method earned in cycle 8, this pass did not rewrite or re-verify them: it
ran a ~60-term vocabulary probe against all eight files *before* searching the
web, and the reverse flow came back almost empty. Measured, in the KB as it
stood this morning: `reverse logistics` 2 mentions, `recommerce` 1, `resale` 1,
`warranty` 1, and **`RMA` 0, `returns fraud` 0, `routing` 0, `BOPIS` 0,
`UFLPA` 0, `CSDDD` 0, `ESG` 0, `scope 3` 0**. The 47 hits for "returns" and 75
for "RMA" were **all false positives** — "returns" from prose like *"the query
returns 2 repos"*, "RMA" as a substring of *fo**rma**t*. Retail's largest
single margin leak had no vocabulary in this knowledge base.

Scale, for context: Shopify reports **~16% of all sales were returned in 2025,
~$850B** (cited from search results; see the source-quality note at the end of
this section).

### ⚠️ Read this first: the word "returns" is ambiguous *in this industry*, and it broke both channels

This is not a search-tooling annoyance, it is a property of the domain, and it
corrupted both the code search and the industry sources in the same pass:

- **Code search.** `returns management` → **3134 repos, zero retail-relevant in
  the top 8** (portfolio analytics, library book lending). `returns agent` →
  **2464 repos, zero relevant**; the 162★ hit is a Brainfuck web app that
  *"returns your user-agent to you"*. This is false abundance of the worst
  kind: a careless pass writes plausible rows from it.
- **Industry sources.** A KPMG APAC figure reads *"more than half of retailers
  report returns exceeding 10% from AI initiatives"*. That is **return on
  investment**, not merchandise returns. Quoting it in a returns deck would be
  a straightforward factual error.

**Rule:** in this plane, never search or quote the bare word "returns". Use
`RMA`, `reverse logistics`, `disposition`, `restocking`, `right of withdrawal`.

### Step 1 — PREVENT the return (fit and size prediction). Empty.

`size recommendation fashion` → **73 repos total**; top result 9★ and
unlicensed, every other result 0★. There is **no maintained, permissively
licensed size/fit prediction library**. `apparel` was absent from this KB
entirely before this pass.

The contrast inside this one step is the cleanest illustration of the
structural law this KB keeps recording. *Rendering* a garment onto a body is a
geometry problem and is well equipped (`virtual try on` → 5608 repos, real
star counts); *predicting whether it will fit this person* is a judgment
problem and is empty. The best-known permissive try-on repo is also **dead**:

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [bcmi/DCI-VTON-Virtual-Try-On](https://github.com/bcmi/DCI-VTON-Virtual-Try-On) | MIT | 508★/77f | 2023-12-06 | ACM MM 2023. Permissive and genuinely useful as a *renderer*. **Dormant ~2 years** — treat as a paper artifact, not a dependency. |
| [vcarlosrb/3d-body-measurements](https://github.com/vcarlosrb/3d-body-measurements) | MIT | 136★/35f | 2024-02-24 | Body measurement extraction. MIT and the highest-starred permissive option. **Stale since Feb 2024.** |

### Step 2 — AUTHORIZE the return (RMA and the right of withdrawal). One repo wide.

`rma returns` → 55 repos total. Exactly **one** is permissive, non-trivial and
alive:

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [mage-os/module-rma](https://github.com/mage-os/module-rma) | MIT | 23★/14f | 2026-11-17 | Return Merchandise Authorization for Mage-OS / Magento. **MIT, pushed six days before this pass.** The only credible standalone open-source RMA component found. Small — read it as a reference implementation, not a product. |

Everything else at this step is embedded in a commerce platform (Odoo, Spree,
Saleor, Medusa, Vendure — all already covered in `verticals/solutions.md`), or
is a sub-5★ WooCommerce plugin. One of those is worth naming only because of
what it reveals about demand:
`DevDiggers-Technologies/returns-for-woocommerce` (2★, unlicensed, pushed
2026-11-10) advertises *"the EU withdrawal button"* — a 2★ unlicensed plugin is
the visible open-source response to a pan-EU statutory right.

### Step 3 — MOVE it (reverse routing). Richly equipped, permissive, committing this week.

This is the one step of the reverse flow that is *better* equipped than most of
retail. Reverse routing is a vehicle-routing problem with pickups, and the VRP
corpus is mature, permissive and extremely alive. **None of these were in this
KB before today** (`or-tools`, `PyVRP`, `jsprit`, `vroom` were all absent):

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [google/or-tools](https://github.com/google/or-tools) | Apache-2.0 | 14430★/2558f | 2026-11-20 | Google OR-Tools. The CP-SAT/routing workhorse. Apache-2.0, the single safest optimisation dependency in this KB. |
| [Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend) | BSD-2-Clause | 8237★/3981f | 2026-11-22 | Routing engine on OSM data. Supplies the distance/duration matrices the solvers need. Pushed the day before this pass. |
| [valhalla/valhalla](https://github.com/valhalla/valhalla) | **MIT** (see licence note) | 6481★/1037f | 2026-11-21 | Routing engine with time-dependent costing. GitHub reports `NOASSERTION`; **it is MIT.** See the licence note below before trusting any SBOM on this one. |
| [VROOM-Project/vroom](https://github.com/VROOM-Project/vroom) | BSD-2-Clause | 1924★/452f | 2026-11-17 | Vehicle Routing Open-source Optimization Machine. Pairs directly with OSRM/Valhalla. The most practical "give me routes now" choice. |
| [graphhopper/jsprit](https://github.com/graphhopper/jsprit) | Apache-2.0 | 1842★/640f | 2026-11-19 | Java toolkit for rich VRPs — pickups *and* deliveries in one tour, which is exactly the reverse-logistics shape. |
| [TimefoldAI/timefold-solver](https://github.com/TimefoldAI/timefold-solver) | Apache-2.0 | 1879★/244f | 2026-11-23 | Already in this KB for rostering. Named again here because it solves VRP too. **Pushed the morning of this pass.** |
| [PyVRP/PyVRP](https://github.com/PyVRP/PyVRP) | MIT | 734★/165f | 2026-11-19 | State-of-the-art VRP solver, Python-first. MIT. Best fit for a data-science team. |
| [reinterpretcat/vrp](https://github.com/reinterpretcat/vrp) | Apache-2.0 | 512★/100f | 2026-10-28 | Rust VRP solver, pickup/delivery and multi-objective. Apache-2.0. |

**And the one retail-specific repo in the whole step is legally unusable:**

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [ANL-CEEESA/RELOG](https://github.com/ANL-CEEESA/RELOG) | **NONE** | 11★/2f | 2026-07-17 | "Reverse Logistics Optimization", from Argonne National Laboratory. The *only* domain-specific reverse-logistics optimiser that exists. **No licence file on `master`, `main` or `dev`** (8 filenames probed; `README.md` returns 200 on the same channel, so the branch and channel are right). No grant ⇒ default copyright, all rights reserved. **Do not vendor it.** Use the generic solvers above and model the reverse flow yourself. |

`reverse logistics` returns **364 repos** in total and, below RELOG, every
result is a sub-5★ unlicensed student project.

### Step 4 — GRADE it (condition assessment). Generic layer is excellent; retail-specific layer is zero.

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | Apache-2.0 | 6416★/1045f | 2026-11-20 | Anomaly/defect detection library. **Apache-2.0 and alive** — and therefore the single most important repo in this plane, because it is the only permissive escape from the AGPL shelf-vision corpus this KB documented on 2026-11-22. Was renamed (see note). |

Retail-specific grading does not exist. `grading condition used` → 96 repos,
**top five are all 0★** and are school-assignment graders or home inspection.
The two on-topic results are both 0★ hobby projects
(`hyeminLee-project/used_book_grading`, `MarceloNoguera/condition-grader`).
Nobody has published an open condition-grading model for returned retail goods.

### Step 5 — DECIDE its disposition (restock / reuse / repair / recycle / destroy). Zero. And this is now the legally binding step.

`disposition engine` → **22 repos worldwide, zero relevant** (game faction
systems, sales-lead routing, an AI coding-agent memory tool). This is the
starkest count recorded anywhere in this KB — starker than retail workforce
management (single repo), starker than the retail-media clean room.

It matters far more than its size suggests, because **since 19 July 2026 the EU
requires large companies to make exactly this decision and prove it** (ESPR
Article 25 — see `intel/market.md` → EMEA). The rule turns disposition from a
cost optimisation into an evidenced legal judgment, and there is no open-source
implementation of it anywhere.

The usable substrate is a general rules/decision engine, not anything retail:

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [apache/incubator-kie](https://github.com/apache/incubator-kie) | Apache-2.0 | 6344★/2609f | 2026-11-20 | Apache KIE — the live home of Drools (rules) and OptaPlanner. Apache-2.0, alive. The right substrate for a per-jurisdiction disposition policy. **Use this slug, not the famous one** — see the migration note. |

Dedicated DMN engines exist but are mostly dormant: `adamecr/Common.DMN.Engine`
(MIT, 97★, last push **2022-12-14**), `powerflows/powerflows-dmn` (Apache-2.0,
58★, **2024-10-17**). Permissive, but do not stake a compliance deadline on an
unmaintained rules engine.

### Step 6 — DETECT abuse (returns fraud) and RECOVER value (resale). Both effectively zero.

**Returns fraud is the clearest "money without code" result in this KB.** The
demand side is measured and large: an NRF / Happy Returns figure puts **~9% of
returns as fraudulent**, with **85% of merchants already using AI/ML against
returns fraud but only 45% believing those tools work on their own** (cited
from search results). The supply side:

- `returns fraud` → **155 repos**; the top six are **2, 6, 0, 0, 0, 4 stars**,
  and the 6★ entry is credit-card fraud, not returns. Nothing usable.
- The generic graph-fraud toolboxes that listicles recommend are **dead**:
  [safe-graph/DGFraud](https://github.com/safe-graph/DGFraud) (Apache-2.0,
  766★, last push **2022-04-20**) and `safe-graph/UGFraud` (Apache-2.0, 134★,
  **2022-04-18**). `awslabs/realtime-fraud-detection-with-gnn-on-dgl`
  (Apache-2.0, 225★) last moved **2024-03-31**.
- One genuinely live and permissive piece, and it is a *benchmark*, not a detector:

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| [SantanderAI/gen-fraud-graph](https://github.com/SantanderAI/gen-fraud-graph) | Apache-2.0 | 296★/81f | 2026-10-01 | Synthetic fraud-graph generator for benchmarking graph fraud models. Apache-2.0, alive. Valuable precisely because returns-fraud training data cannot be shared between retailers — generate, then benchmark. |

**Value recovery is emptier still.** `liquidation deadstock` → **1 repo
worldwide** (0★). `takeback trade-in` → **0 repos. Literally zero.**
`extended producer responsibility` → **24 repos worldwide, maximum 1★** — for a
legal regime now in force across the EU.

### Measured gaps in this plane — searched for on 2026-11-23, genuinely not there

Recorded so that silence is not mistaken for coverage:

- **Disposition decisioning:** `disposition engine` → 22 repos, 0 relevant. **No open-source implementation of the ESPR Article 25 decision exists.**
- **Trade-in / take-back:** `takeback trade-in` → **0 repos**.
- **Liquidation / deadstock:** `liquidation deadstock` → 1 repo, 0★.
- **EPR compliance:** `extended producer responsibility` → 24 repos, max 1★.
- **Returns fraud:** `returns fraud` → 155 repos, best real candidate ≤6★ and off-topic.
- **Size/fit prediction:** `size recommendation fashion` → 73 repos, best 9★ unlicensed.
- **Retail-specific condition grading:** `grading condition used` → 96 repos, top five 0★.
- **Retail-specific reverse-logistics optimiser:** exactly one exists (RELOG) and it has **no licence**.
- **Warranty claims:** `warranty claims` → 689 repos; best permissive is `abdul-rafay-dev0/AssureX-Warranty-Claim-Engine` (MIT, **3★**). Not a floor.
- **Right-to-repair tooling:** `right to repair` → 272 repos, and the top results are *automotive* (`jakka351/Opium-Den-OEM` 65★ unlicensed, VW component-protection docs). No consumer-goods repair-tooling corpus, despite the EU directive applying since 31 July 2026.

### ⚠️ Method notes earned this pass (reusable across all twelve industries)

**(1) The licence probe was still incomplete — add `LICENSE.TXT` with an
uppercase extension.** Cycle 8 added lowercase `license.txt` and `COPYING.md`.
That still missed
[Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend)
(8237★), whose licence lives in **`LICENSE.TXT`** — uppercase *extension*. The
probe must now cover case variants of the extension, not just the stem. The
current working set: `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `LICENSE.TXT`,
`license.txt`, `LICENCE`, `COPYING`, `COPYING.md`.

**(2) New licence-file category: the POINTER file.** `valhalla/valhalla`
(6481★) has a `LICENSE.md` of **44 bytes** whose entire content is
`For license information see [here](COPYING)`. GitHub's API therefore reports
**`NOASSERTION` / "Other"**, and the actual `COPYING` file is **plain MIT**.
This is a *false negative in the permissive direction*: an SBOM scan or licence
gate would flag a 6481★ MIT routing engine as unknown-licence and a careless
reviewer would drop it. Cycle 8 found the inverse (Chromaprint: MIT file,
LGPL compilation). **Rule: when SPDX says NOASSERTION, read the licence file
before concluding anything — in either direction.**

**(3) `git ls-remote` succeeding while `search/repositories` 422s means the
repo was RENAMED, not deleted.** `openvinotoolkit/anomalib` resolves fine via
`ls-remote` (14 refs) but `q=repo:openvinotoolkit/anomalib` returns HTTP 422.
The repo is now **`open-edge-platform/anomalib`** (6416★, Apache-2.0). The two
oracles disagreeing in *that specific direction* is a reliable rename
signature, and it is worth checking before writing a dead-link row.

**(4) The famous slug can be a migration stub.** `apache/incubator-kie-optaplanner`
(3512★) carries a description that begins *"OptaPlanner has moved to …"*. The
live project is `apache/incubator-kie` (6344★, pushed 2026-11-20) and the
independent successor is `TimefoldAI/timefold-solver`. Star count tracks
history, not liveness.

**(5) `gh api repos/<slug>` is unavailable in this session** (HTTP 403, outside
the session's repository scope). `gh api -X GET search/repositories -f
q='repo:<slug>'` is the only metadata channel, and it returns stars, forks,
`pushed_at`, `default_branch` and SPDX in one call. `git ls-remote` remains the
existence oracle.

### Source-quality notes for this section

**Every GitHub row above is verified**: existence by `git ls-remote`, metrics
and SPDX by the search API on 2026-11-23, and licence text by fetching the
actual file from `raw.githubusercontent.com` and checking its byte count.

**Non-GitHub URLs could not be fetch-verified in this session, and are not
cited as links below.** Both verification channels are blocked by this
session's network policy: `curl` returns `403 connect_rejected` from the egress
proxy and WebFetch returns `ENOTFOUND` for `eur-lex.europa.eu`,
`espratlas.com`, `modernretail.co`, `nrf.com`, `deloitte.com`, `emarketer.com`
and `planalto.gov.br`. Per the standing rule that a 404 is not a finding — and
that an unverified URL is not one either — the market and regulatory figures in
this pass are attributed **in prose to their named source** and flagged as
*search-result-derived, not fetch-verified*. The affected claims are the
Shopify ~16%/$850B return rate, the NRF/Happy Returns 9% and 85%/45% figures,
the KPMG and Coresight adoption numbers, and all statutory dates. **To promote
any of them to citable, these hosts must be added to the session's allowed
network domains.** The legal dates should in any case be checked against the
Official Journal text before they go into a client deliverable.

---

## Added 2026-11-23 (pass 5) — the price plane, and a correction to this file

### ⚠️ Correction notice: two claims this KB has carried are wrong as written

This file has stated since cycle 8, and `compose/patterns.md`, `intel/trends.md`,
`intel/market.md` and `verticals/solutions.md` all repeat it, that:

1. *"Retail price optimisation: no credible open-source project exists"* — on the
   evidence of **one** query, `price optimization stars:>=100`; and
2. *"`product matching entity resolution stars:>=200` returns 0 results"* — used
   to justify building product matching as proprietary IP.

Both were re-measured on 2026-11-23 against seven query families and direct
`repo:` lookups. **Claim 2 is false.** `entity resolution record linkage
stars:>=500` still returns **0**, yet all three leading libraries exist, are
permissive and are alive — `splink` 2594★ MIT, `dedupe` 4531★ MIT,
`zingg` 1275★ AGPL-3.0. That is a **measured search false negative**, the fifth
in this KB, and this time it did not merely hide a repo: it manufactured a
strategic recommendation.

**Claim 1 is wrong in its general form and right in a narrow one.** The
*elasticity/demand* layer is well equipped and permissive (below). What has no
licensed, maintained retail implementation is the **decision** step — the
markdown/promotion optimiser. Restate it that way, because the two have
different buy/build answers.

> **The sharper finding, and the headline of this pass:** every repository that
> is *specifically* a retail price optimiser **lacks a licence grant**. Three of
> three. Meanwhile every generic layer such an optimiser would be assembled from
> is permissive and actively maintained. The retail pricing gap is not *"no code
> exists"* — it is *"the code that exists cannot be granted."* That is a
> different problem with a different remedy.

### The six-step price gradient, measured 2026-11-23

```
OBSERVE → MATCH → MODEL → OPTIMISE → SET/EXECUTE → DEFEND
  ✅       ✅       ✅        ❌            ✅          ⚠️ one repo wide
generic  generic  generic   no licensed  permissive   0★, 1 day old
abundant permissive alive   retail impl  + agent-native  and EMEA-only
```

#### 1. OBSERVE — collect market prices. Abundant, generic, permissive.

| Repo | License | Stars | Last push | Role |
|---|---|---|---|---|
| [scrapy/scrapy](https://github.com/scrapy/scrapy) | BSD-3-Clause | 65,542★ | 2026-11-19 | The crawling framework. Nothing retail-specific about it, which is why no retail query finds it. |
| [dgtlmoon/changedetection.io](https://github.com/dgtlmoon/changedetection.io) | **Apache-2.0** (11382 B) | 35,967★ | 2026-11-22 | Change detection with price watchers and notification hooks. Deployable as-is for competitor monitoring. |
| [apify/crawlee](https://github.com/apify/crawlee) | **Apache-2.0** | 26,521★ | 2026-11-23 | Browser automation for pages that defend themselves. |
| [supermarkt/checkjebon](https://github.com/supermarkt/checkjebon) | **MIT** (1067 B) | 259★ | 2026-11-20 | Dutch supermarket price data and comparison. A *working regional price corpus*, not a framework — the only one of its kind found. **EMEA.** |
| [ByteSizedMarius/rewerse-engineering](https://github.com/ByteSizedMarius/rewerse-engineering) | **MIT** | 98★ | 2026-09-29 | Unofficial REWE (Germany) client in Go and Python: discounts, prices. **EMEA.** |

#### 2. MATCH — is it the same product? Well equipped, and this is the corrected claim.

| Repo | License | Stars | Last push | Role |
|---|---|---|---|---|
| [dedupeio/dedupe](https://github.com/dedupeio/dedupe) | **MIT** (1118 B) | 4,531★ | 2025-07-29 | Fuzzy matching and record deduplication. **Dormant ~16 months** — note before depending on it. |
| [moj-analytical-services/splink](https://github.com/moj-analytical-services/splink) | **MIT** (1076 B) | 2,594★ | 2026-11-11 | Probabilistic record linkage at scale, backed by the UK Ministry of Justice. **The live pick.** |
| [zinggAI/zingg](https://github.com/zinggAI/zingg) | **AGPL-3.0** (34523 B) | 1,275★ | 2026-11-03 | Entity resolution and MDM. AGPL — fine hosted for one client, a blocker inside a shipped product. |

#### 3. MODEL — elasticity and demand. The layer the KB said did not exist.

| Repo | License | Stars | Last push | Role |
|---|---|---|---|---|
| [py-why/dowhy](https://github.com/py-why/dowhy) | **MIT** | 8,410★ | 2026-11-17 | Causal graphs and identification — the step before any elasticity number is trustworthy. |
| [uber/causalml](https://github.com/uber/causalml) | **Apache-2.0** (`LICENSE` **561 B**, read) | 6,047★ | 2026-10-12 | Uplift modelling: who responds to a discount. API reported `NOASSERTION`. |
| [py-why/EconML](https://github.com/py-why/EconML) | **MIT** (2978 B, read) | 4,861★ | 2026-11-20 | Heterogeneous treatment effects — price response by segment. API reported `NOASSERTION`. |
| [pymc-labs/pymc-marketing](https://github.com/pymc-labs/pymc-marketing) | **Apache-2.0** (11357 B) | 1,314★ | 2026-11-22 | **The find of this pass.** `customer_choice/bayesian_blp.py` fits a Bayesian random-coefficients BLP model on *aggregate market-share panels*, documented for **"the common Nielsen / IRI / retailer-scanner data shape"**, returning **full posterior cross-price elasticities** with hierarchical pooling across markets. `MixedLogit` covers individual-level choice. Ships Spanish locale files. |
| [jeffgortmaker/pyblp](https://github.com/jeffgortmaker/pyblp) | **MIT** (`LICENSE.txt` 1077 B) | 297★ | 2026-11-13 | The mature classical BLP implementation: elasticities, diversion ratios, markups, HHI. Research-oriented but maintained. |
| [cvxgrp/elasticity-estimation](https://github.com/cvxgrp/elasticity-estimation) | **NO LICENCE FILE** (root of `main` verified) | 0★ | 2026-04-15 | Stanford/Boyd-group code for the April 2026 paper *Estimating Price Elasticity Matrices* — low-rank-plus-diagonal structure so large portfolios stay tractable. Algorithmically the best answer to retail's hardest pricing problem, and **unusable**: no grant. Read the paper, cite nothing, vendor nothing. |

Adjacent and permissive, for the promotion-spend side rather than the shelf price:
[google/meridian](https://github.com/google/meridian) (Apache-2.0, 1612★, 2026-11-21),
[facebookexperimental/Robyn](https://github.com/facebookexperimental/Robyn) (MIT, 1539★, 2026-11-10 —
already in this KB from pass 3, including the default-branch trap), and
[google/lightweight_mmm](https://github.com/google/lightweight_mmm) (Apache-2.0, 1055★,
**last push 2025-06-17, ~17 months dormant**; Meridian is its successor).

#### 4. OPTIMISE — decide the markdown. The empty step.

Solver substrate — all permissive, all alive, none retail:

| Repo | License | Stars | Last push | Role |
|---|---|---|---|---|
| [google/or-tools](https://github.com/google/or-tools) | **Apache-2.0** | 14,430★ | 2026-11-20 | CP-SAT and MIP. Already carried in this KB for reverse-logistics routing (pass 4). |
| [cvxpy/cvxpy](https://github.com/cvxpy/cvxpy) | **Apache-2.0** | 6,400★ | 2026-11-23 | Convex modelling — the natural expression of a markdown problem with margin and inventory constraints. |
| [Pyomo/pyomo](https://github.com/Pyomo/pyomo) | **BSD-3-Clause** (`LICENSE.md` 1735 B, Sandia/NTESS — read) | 2,563★ | 2026-11-21 | Algebraic modelling. API reported `NOASSERTION`. |
| [facebook/Ax](https://github.com/facebook/Ax) | **MIT** (`LICENSE` read at `main`) | *not measurable* | — | Adaptive experimentation — the honest way to run price tests. **`repo:facebook/Ax` returns HTTP 422 from `search/repositories`** while `ls-remote` gives 4642 refs; see the method note below. Stars deliberately left blank rather than guessed. |

Retail-specific attempts — **all dead, unlicensed, or both:**

| Repo | License | Stars | Last push | Verdict |
|---|---|---|---|---|
| [Azure/cortana-intelligence-price-optimization](https://github.com/Azure/cortana-intelligence-price-optimization) | **NO LICENCE FILE** (root of `master` verified) | 90★ | 2017-09-05 | Microsoft's retail price-optimisation solution. Nine years dead, no grant. |
| [Azure/cortana-intelligence-price-analytics](https://github.com/Azure/cortana-intelligence-price-analytics) | MIT (1183 B) | 38★ | 2023-06-27 | Double-ML price analytics. Properly licensed, dormant ~3.5 years. |
| [flix-tech/RevPy](https://github.com/flix-tech/RevPy) | MIT (1071 B) | 50★ | 2023-07-06 | Revenue-management heuristics (DAVN, DP-LP). **Airline**, not retail. Dormant ~3.4 years. |
| [topprismdata/fashion-lifecycle-pricing](https://github.com/topprismdata/fashion-lifecycle-pricing) | **NO LICENCE FILE** (root of `main` verified) | 2★ | 2026-08-28 | The only on-topic hit in 263 `markdown pricing` results. No grant. |

#### 5. SET / EXECUTE — apply the price. Adequate and permissive.

[offerkit/offerkit](https://github.com/offerkit/offerkit) (MIT, 58★, 2026-11-20) for
promotions, plus the promotion and price-list modules already inside the permissive
platform layer this KB verified in cycle 8 —
[medusajs/medusa](https://github.com/medusajs/medusa) (MIT, `LICENSE` read 1075 B;
API still reports `NOASSERTION`), [saleor/saleor](https://github.com/saleor/saleor)
(BSD-3-Clause, 23,593★), [odoo/odoo](https://github.com/odoo/odoo) (**LGPL-3.0**, so
proprietary pricing modules are permitted — cycle 8's most commercially useful
licence fact).

**The hardware end is empty.** Trade press this year reports tier-one and big-box
retailers scaling **electronic shelf labels** — the physical execution surface of
every dynamic price. **[measured]** `electronic shelf label stars:>=5` returns
**16 repos, all hobbyist ESP32/e-paper projects**: `rbaron/elink` (116★, **no
licence**, dead 2022-08-04), `tuanpmt/esp_epaper` (MIT, 21★, 2026-11-21 — a display
driver, not an ESL system), `Northstrix/Electronic-Shelf-Label-Management-System`
(MIT, 9★, dead 2024-06-07). There is **no open-source ESL management system** at
retail scale. Ties directly to the store plane (pass 2).

#### 6. DEFEND — prove the price was lawful. One repo wide.

[zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance)
(MIT, 0★, 2026-11-22) is the only implementation found, and it covers **EMEA only**
(EU + Polish duties). Algorithmic-collusion auditing exists solely as academic
replication code: [matteocourthoud/Algorithmic-Collusion-Replication](https://github.com/matteocourthoud/Algorithmic-Collusion-Replication)
(MIT, 22★, dead 2023-06-20), [luciasauer/algorithmic_pricing_llms](https://github.com/luciasauer/algorithmic_pricing_llms)
(MIT, 8★, 2025-07-09), [becmn/algorithmic-collusion](https://github.com/becmn/algorithmic-collusion)
(MIT, 0★, 2026-10-30 — Q-learning vs LLM agents in a repeated Bertrand duopoly).
Useful as evidence that the risk is studied; **not** an audit tool.

**Sixth/seventh confirmation of the structural law, and the cleanest instance yet:
the mandated step is the empty one.** Regulation attaches to *judgment about the
price*; open source equips *collection, measurement and execution of the price*.

### Not retail pricing, despite the vocabulary — exclusion note

`revenue management stars:>=50` surfaces [getlago/lago](https://github.com/getlago/lago)
(**AGPL-3.0**, 10,910★) and [meteroid-oss/meteroid](https://github.com/meteroid-oss/meteroid)
(**AGPL-3.0**, 1,369★). Both are excellent **SaaS metering and subscription billing**
platforms. Neither prices merchandise. They are the single largest and most
confusing false-positive family on this plane, and both are AGPL, so a careless
pick is a licence problem on top of a fit problem.

### Method notes added 2026-11-23 (pass 5)

1. **`search/repositories` HTTP 422 does *not* imply a rename.** Pass 4 recorded
   *"ls-remote OK + 422 = repo was RENAMED"*. `facebook/Ax` falsifies the rule as
   stated: `ls-remote` gives **4642 refs**, the default branch is `main`, and
   `raw.githubusercontent` serves an MIT `LICENSE` — yet `repo:facebook/Ax` and
   `repo:facebook/ax` both return 422. **Restated: 422 means search cannot see the
   repo. Rename is one cause; an index gap on a live repo is another.**
   `ls-remote` plus a raw licence read settles which.
2. **A short licence file is not automatically a pointer.** Cycle 8's rule
   (*"a short LICENSE is a pointer, not a licence — read it"*) came from
   Meilisearch's 468 B multi-licence redirect. `uber/causalml`'s `LICENSE` is
   **561 B** and is a *valid* Apache-2.0 grant by reference to the canonical URL.
   So: **short ≠ invalid; short = read it.** Both halves of the rule matter.
3. **The byte-size licence fingerprint table held.** `zingg`'s `LICENSE` is
   **34523 B**, matching this KB's own cycle-8 entry for AGPL-3.0 exactly.
4. **Licence probes must cover `LICENSE.md`.** `Pyomo` declares BSD-3-Clause there
   and nowhere else; pass 4 added `LICENSE.TXT` for the same reason.
5. **Three of three** retail-price-specific repos had **no licence file at root**,
   detected only by direct `raw.githubusercontent` reads across nine filename
   variants. The GitHub API field said `NONE` or `NOASSERTION` without
   distinguishing *"no grant"* from *"unrecognised grant"* — a distinction that
   decides whether a client can use the code.

**Informed gap — provenance of every statutory date and market figure below.**
Non-GitHub hosts remain unreachable from this session (`eur-lex.europa.eu`,
`gov.br`, `accc.gov.au` and law-firm hosts all return **000 / connection refused**
through the proxy, re-tested 2026-11-23). Every legal date and market number in
this pass is **search-result-derived and not fetch-verified**, and is marked as
such where it appears. Read the official text before any of it reaches a client.

---

## Added 2026-11-23 (pass 6) — the fulfilment plane (order → doorstep), in seven steps

Measured 2026-11-23. Stars and push dates from `gh api search/repositories`; existence from
`git ls-remote`; every licence below read from the raw file on the repo's **actual default branch**.

### The shape of this plane in one sentence

Steps 4 and 5 — routing the vehicle and resolving the address — are the best-equipped, most
permissive layers this KB has measured in any industry. Steps 1, 6 and 7 — promising a date,
printing a carrier label, proving delivery — are effectively empty. **The open-source floor covers
the part a mathematician recognises and stops at the part a retailer is actually judged on.**

### Step 1 — PROMISE it (available-to-promise, delivery date). Empty.

`available to promise inventory` returns **7 repositories worldwide**, and the highest star count
among them is **1**. Not one is a usable library. The full list of what exists, so nobody re-runs this:

| Repo | Stars | License | Last push | Note |
|---|---|---|---|---|
| https://github.com/netsphere-labs/bonsaiERP3 | 0 | AGPL-3.0 | 2026-11-02 | Ruby ERP that names ATP in its description; a general ERP, not an ATP engine |
| https://github.com/Mohith26/stockfind | 0 | No licence | 2026-09-08 | B2B multi-warehouse availability API, single author |
| https://github.com/pankaj-gyaanora-ai/gyaanora-inventory-visibility | 0 | No licence | 2026-09-17 | Multi-source inventory reconciliation, single author |
| https://github.com/SumiX21-beep/OMS-System | 1 | No licence | 2026-07-01 | Sourcing logic (which node ships) as a student-scale project |

This is the sixth confirmation of the structural law this KB keeps re-deriving: **the step the
business is judged on is the step with no open-source floor.** A retailer's delivery promise is the
single most visible number on the product page, and there is nothing to fork.

### Step 2 — ORCHESTRATE it (order management, order routing). Equipped, and almost entirely non-permissive.

| Repo | Stars | License | Last push | Note |
|---|---|---|---|---|
| https://github.com/fleetbase/fleetbase | 4,799 | AGPL-3.0 | 2026-11-20 | Modular logistics operating system; the largest on-plane platform |
| https://github.com/openshiporg/openship | 1,680 | AGPL-3.0 | 2026-11-17 | Order router: sales channels → fulfilment partners and 3PLs |
| https://github.com/berndruecker/flowing-retail | 1,331 | Apache-2.0 | 2024-08-01 | **A sample, not a product** — order fulfilment decomposed into sagas/microservices. Dormant since 2024, still the clearest reference architecture for the step |
| https://github.com/apache/ofbiz-framework | 1,151 | Apache-2.0 | 2026-11-22 | ERP with order management in-tree; permissive and genuinely alive |
| https://github.com/openoms-org/openoms | 33 | **Elastic License 2.0** | 2026-09-02 | See the correction below |
| https://github.com/hotwax/fulfillment | 9 | Apache-2.0 | 2026-11-17 | Store-fulfilment app (pick/pack/ship in-store); tiny but permissive and current |

**⚠️ Two source errors caught at this step.**

1. **`openoms-org/openoms` is not MIT.** A libraries.io mirror lists it as MIT. Its `LICENSE` file is
   3,899 bytes and reads `Elastic License 2.0`. ELv2 is **source-available, not open source** — it
   forbids providing the software to third parties as a managed service. For a studio whose output is
   often exactly that, this is a hard blocker, and the public claim points the wrong way.
2. **`hotwax/poorti` does not exist.** A search result and an ecosyste.ms listing both cite
   `github.com/hotwax/poorti` as an Apache-2.0 store-fulfilment suite. `git ls-remote` on it fails
   authentication (the 404 signature). The live HotWax slug is `hotwax/fulfillment`. Another dead slug
   arriving with a plausible licence and a plausible description attached.

### Step 3 — PICK it (warehouse / inventory of record). Equipped; licences are mixed but workable.

| Repo | Stars | License | Last push | Note |
|---|---|---|---|---|
| https://github.com/inventree/InvenTree | 7,890 | MIT | 2026-11-23 | Inventory management, MIT, committing today. The permissive anchor of this step |
| https://github.com/openboxes/openboxes | 936 | **EPL-1.0** | 2026-11-22 | WMS with stock movement and lot tracking. Eclipse Public License — weak copyleft, file-level; compatible with commercial work but not GPL-compatible in the usual direction |

### Step 4 — ROUTE it (the vehicle routing problem). Richly equipped and overwhelmingly permissive.

| Repo | Stars | License | Last push | Note |
|---|---|---|---|---|
| https://github.com/google/or-tools | 14,430 | Apache-2.0 | 2026-11-20 | The general solver; its routing library is the industry default |
| https://github.com/VROOM-Project/vroom | 1,924 | BSD-2-Clause | 2026-11-17 | Purpose-built VRP engine, pairs directly with OSRM/Valhalla |
| https://github.com/TimefoldAI/timefold-solver | 1,879 | Apache-2.0 | 2026-11-23 | Constraint solver for routing **and** rostering; committing today |
| https://github.com/graphhopper/jsprit | 1,842 | Apache-2.0 | 2026-11-19 | Java VRP toolkit with rich constraints |
| https://github.com/PyVRP/PyVRP | 734 | MIT | 2026-11-19 | Modern, well-documented Python VRP solver |
| https://github.com/reinterpretcat/vrp | 512 | Apache-2.0 | 2026-10-28 | Rust VRP solver |

### Step 5 — PLACE it on a map (routing engine + geocoding). Equipped; this is where the copyleft is.

| Repo | Stars | License | Last push | Note |
|---|---|---|---|---|
| https://github.com/Project-OSRM/osrm-backend | 8,237 | BSD-2-Clause | 2026-11-22 | Routing engine; permissive |
| https://github.com/graphhopper/graphhopper | 6,828 | Apache-2.0 | 2026-11-20 | Routing engine; permissive |
| https://github.com/valhalla/valhalla | 6,481 | **MIT** (see note) | 2026-11-21 | Routing engine with time-dependent costing. API reports `NOASSERTION`; the real licence is MIT in `COPYING` |
| https://github.com/openvenues/libpostal | 4,925 | MIT | 2026-05-13 | Statistical international address parser. **The single most useful repo on this plane for LATAM** |
| https://github.com/osm-search/Nominatim | 4,575 | GPL-3.0 | 2026-11-21 | Geocoder; copyleft |
| https://github.com/pelias/pelias | 3,608 | MIT | 2026-07-24 | Modular geocoder; permissive |
| https://github.com/komoot/photon | 3,205 | Apache-2.0 | 2026-11-20 | Geocoder; permissive |
| https://github.com/GIScience/openrouteservice | 1,996 | GPL-3.0 | 2026-11-23 | Routing API with many profiles; copyleft |

**The licence pattern is clean and worth memorising:** on this plane the *engines* are permissive
(BSD-2 / Apache / MIT) and the *geocoders* split — Pelias MIT and Photon Apache-2.0 against Nominatim
GPL-3.0 and openrouteservice GPL-3.0. There is always a permissive option at every step of 4 and 5,
so **no routing engagement needs to accept copyleft.** That is not true of any other step on this plane.

### Step 6 — HAND IT OFF (carrier labels, manifests). Near-empty, and what exists is per-carrier and copyleft.

`shipping carrier label api stars:>=100` → **0**. `shipping label carrier stars:>=30` → **0**.
Shortening to `shipping label stars:>=50` → 5 repos, and reading them (not the total) is the finding:

| Repo | Stars | License | Last push | Why it does not fill the gap |
|---|---|---|---|---|
| https://github.com/Automattic/woocommerce-services | 112 | GPL-2.0 | 2026-11-20 | Alive, but a WooCommerce plugin bound to hosted services |
| https://github.com/poundifdef/ClassicUPS | 58 | NOASSERTION | 2024-04-03 | One carrier (UPS), dormant 2 years |
| https://github.com/postnl/postnl-magento2 | 58 | No licence file | 2026-09-16 | One carrier, one storefront, no licence |
| https://github.com/typingbeaver/snake-label | 53 | GPL-3.0 | 2026-02-10 | Converts German DHL/Hermes labels for a label printer |

**There is no carrier-neutral, permissive, maintained shipping-label library in the world** — with one
regional exception, which is the LATAM finding below and the most commercially interesting result of
this pass.

### Step 7 — PROVE it (tracking the merchant can read, proof of delivery, eCMR). Effectively zero.

- `tracking number carrier stars:>=50` → **0**.
- `parcel tracking stars:>=100` → **2**, and both are *consumer* apps under GPL-3.0:
  https://github.com/itsvic-dev/deliveries (258★, 2026-09-19) and
  https://github.com/proninyaroslav/libretrack (371★, 2026-06-30). The tracking that exists is built
  for the person waiting for the parcel, not the retailer answering "where is it".
- `proof of delivery stars:>=30` → 2, both keyword collisions ("content delivery", a terms-of-use dump).
- `ecmr electronic consignment note` → **1 repo, 0 stars, no licence**
  (https://github.com/cargoffer/ecmr-mcp-skybridge, 2026-05-25). Against an EU regulation with a
  2027 date on it (see `intel/market.md` → EMEA), that is the whole open-source response.

Adjacent and genuinely useful, though not parcel-level:
https://github.com/traccar/traccar (8,176★, Apache-2.0, 2026-11-22) — GPS fleet tracking with 200+
device protocols. If you need to prove a *vehicle* was at an address, this is the permissive floor.
It will not tell you which parcel came off the van.

### ⚠️ The LATAM exception — the empty step is filled, in one MIT repo

https://github.com/codespar/mcp-dev-latam (279★, MIT, pushed 2026-11-13) wraps regional carriers as
MCP servers. Verified by cloning the repo and reading the tool definitions, not the README:

| Package in-tree | Country | Tools it actually exposes |
|---|---|---|
| `packages/ecommerce/melhor-envio` | Brazil | `calculate_shipping`, `create_shipment`, **`generate_label`**, `get_tracking_history`, `list_agencies`, `cancel_shipment` |
| `packages/ecommerce/correios` | Brazil | `calculate_shipping`, **`buy_label_range`**, `create_prepost`, **`create_reverse`**, `find_cep` |
| `packages/ecommerce/superfrete` | Brazil | multi-carrier freight |
| `packages/mexico/skydropx` | Mexico | multi-carrier shipping |
| `packages/argentina/andreani` | Argentina | carrier integration |
| `packages/colombia/coordinadora` | Colombia | carrier integration |

So steps 6 and 7 — measured as **zero worldwide** — are covered for six LATAM countries by one
MIT-licensed, actively maintained repo, already shaped as agent tools. `create_reverse` on Correios
also fills part of the returns plane's empty "authorize the return" step from pass 4.

**Method note earned here:** `ls packages/logistics/` returned nothing and I nearly recorded the
README as overstated. The packages are real; they live under `packages/ecommerce/` and under country
folders. **Do not conclude from one path guess — grep the tree.** A directory that is missing where
you expected it is evidence about your expectation, not about the repo.

### Measured gaps in this plane — searched for on 2026-11-23, genuinely not there

- **No open-source delivery-promise / ATP engine** (7 repos, max 1 star).
- **No carrier-neutral label library** outside LATAM (0 repos ≥30★).
- **No merchant-side parcel-tracking library** (0 repos ≥50★).
- **No proof-of-delivery library** (0 real repos ≥30★).
- **No eCMR implementation of any size** (1 repo, 0★, unlicensed).
- **No autonomous supply-chain agent** (`supply chain agent stars:>=100` → 11, all off-plane).
