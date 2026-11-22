---
industry: retail
region: Global
updated: 2026-11-22
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
