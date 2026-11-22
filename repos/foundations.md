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
