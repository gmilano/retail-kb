---
industry: retail
region: Global
updated: 2026-11-22
---

# 📈 Repos Trending — Retail & Consumer

> **Append-only.** Newest dated section on top; history preserved below. This file tracks **infrastructure,
> protocol and platform repos**. For agents and agent-facing tooling see `agents/trending.md` — until today
> the two files were byte-identical and this distinction did not exist.

## 2026-11-22 (pass 3)

**Plane added this pass: retail media infrastructure** — the auction, the
identity layer, the measurement layer and the clean room.

**Alive and committing within days of this pass (all Apache-2.0):**

| Repo | Licence (read at source) | refs | Last commit |
|---|---|---|---|
| [prebid/Prebid.js](https://github.com/prebid/Prebid.js) | Apache-2.0 (10760B, `master`) | 14749 | 2026-11-22 (0d) |
| [IABTechLab/uid2-operator](https://github.com/IABTechLab/uid2-operator) | Apache-2.0 (11348B) | 4067 | 2026-11-22 (0d) |
| [pymc-labs/pymc-marketing](https://github.com/pymc-labs/pymc-marketing) | Apache-2.0 (11356B) | 2338 | 2026-11-22 (0d) |
| [google/meridian](https://github.com/google/meridian) | Apache-2.0 (11357B) | 1725 | 2026-11-20 (2d) |
| [google/differential-privacy](https://github.com/google/differential-privacy) | Apache-2.0 (13499B) | 471 | 2026-11-20 (2d) |
| [apache/pinot](https://github.com/apache/pinot) | Apache-2.0 (11356B, `master`) | 17558 | 2026-11-21 (1d) |
| [apache/druid](https://github.com/apache/druid) | Apache-2.0 (19315B, `master`) | 17408 | 2026-11-21 (1d) |
| [prebid/prebid-server](https://github.com/prebid/prebid-server) | Apache-2.0 (10759B, `master`) | 4327 | 2026-11-19 (3d) |
| [prebid/prebid-server-java](https://github.com/prebid/prebid-server-java) | Apache-2.0 (10759B, `master`) | 3985 | 2026-11-18 (4d) |

**⚠️ Two licence facts that contradict public sources.**

- **UID2 is Apache-2.0, not BSD-2.** The Trade Desk's press release announcing
  the donation says BSD-2; `unifiedid.com` says Apache-2.0. Measured,
  `IABTechLab/uid2-operator/LICENSE` is the full Apache-2.0 text at **11348
  bytes**. A press release is not a licence.
- **OpenRTB ships no licence at all.**
  [InteractiveAdvertisingBureau/openrtb](https://github.com/InteractiveAdvertisingBureau/openrtb)
  (198 refs, 2026-04-14, 222d) — root tree confirmed: `.gitignore`,
  `OpenRTB v3.0 FINAL.md`, `README.md`, `ads.cert...BETA.md`, `extensions/`,
  `supplychainobject.md`. No licence under any of eight names on either branch.
  The substrate of all programmatic advertising is unlicensed. Implement from
  the spec; **do not vendor the repo** — same treatment as `bacen/pix-api`.

**Dormant — recorded so a later cycle does not resurrect them as live:**

| Repo | Licence | Last commit | Days |
|---|---|---|---|
| [qascade/dcr](https://github.com/qascade/dcr) | AGPL-3.0 (35215B) | 2023-06-13 | 1258 |
| [Snowflake-Labs/sfquickstart-data-clean-room](https://github.com/Snowflake-Labs/sfquickstart-data-clean-room) | Apache-2.0 (11356B) | 2024-03-11 | 986 |
| [Optable/match](https://github.com/Optable/match) | Apache-2.0 (10172B, `LICENCE.md`) | 2024-10-24 | 759 |
| [tiktok-privacy-innovation/PrivacyGo-DataCleanRoom](https://github.com/tiktok-privacy-innovation/PrivacyGo-DataCleanRoom) | Apache-2.0 (11356B) | 2024-10-31 | 752 |
| [tiktok-privacy-innovation/PrivacyGo](https://github.com/tiktok-privacy-innovation/PrivacyGo) | Apache-2.0 (11356B) | 2025-01-24 | 667 |
| [google/lightweight_mmm](https://github.com/google/lightweight_mmm) | Apache-2.0 (11357B) | 2025-06-17 | 523 | 
| [facebookexperimental/Robyn](https://github.com/facebookexperimental/Robyn) | MIT (1091B) | `main` 2025-06-27 | 513 |
| [google/private-join-and-compute](https://github.com/google/private-join-and-compute) | Apache-2.0 (11357B, `master`) | 2026-03-09 | 258 |
| [facebookincubator/GeoLift](https://github.com/facebookincubator/GeoLift) | MIT (1092B, `LICENSE.md`) | 2026-04-01 | 235 |

**The clean-room layer has no maintained option at all** — the three real
open-source clean rooms are the top three rows above, dormant 752–1258 days,
in a segment vendors size at $2.8B→$14.6B (Dataintelo, vendor figure). The
primitives are alive; the product layer is not. Assemble, do not fork —
`compose/patterns.md` Pattern 14.

**Dead slugs dropped this pass (`ls-remote` refs=0):**
`fvdrgserge/openadserver` (cited by a 2026 listicle as a "self-hosted
alternative to Google Ad Manager"), `IABTechLab/uid2-docs` (correct slug is
**`uid2docs`**, no hyphen), `InteractiveAdvertisingBureau/AAMP` (correct owner
is **`IABTechLab`**), `InteractiveAdvertisingBureau/aamp-spec`,
`adcontextprotocol/adcp-spec`, `AgenticAdvertising/adcp`,
`tiktok-privacy-innovation/privacy-go`.

**Method note — the licence probe produced a false negative.**
`Optable/match` was first recorded here as having no licence after probing
eight filenames on two branches. The file is **`LICENCE.md`** (British spelling
*with* `.md`). Add it to every probe. And: **a filename probe cannot prove
absence — `git ls-tree HEAD --name-only` on the bare clone can**, which is how
OpenRTB's missing licence was confirmed rather than guessed.

## 2026-11-22 (pass 2)

**Theme: fiscalisation is the best-equipped layer in retail open source, and its licence changes at every
border.** Earlier today this file added the product-data plane. This section adds the layer underneath the
till: the code that makes a sale lawful. It is the only retail capability where mature, maintained open
source exists for each jurisdiction *under a different licence in each one*. All rows measured 2026-11-22.

| Movement | Repo | License (read at source) | ★ / forks | Last push | Why it is trending |
|---|---|---|---|---|---|
| New — 🇧🇷 | [nfephp-org/sped-nfe](https://github.com/nfephp-org/sped-nfe) | **LGPL-3.0** (`LICENSE.md` 8851 B) | 1635★ / 1169 refs | 2026-11-13 | Largest fiscal library in retail open source. API reports `NOASSERTION`; the file says LESSER GPL, so dynamic linking keeps your till closed. **Keyword search never returned it** — found only via a `repo:` qualifier. |
| New — 🇧🇷 | [wmixvideo/nfe](https://github.com/wmixvideo/nfe) | **Apache-2.0** (10850 B, appendix stripped) | 770★ / 411f | 2026-11-16 | The permissive Brazilian option, and the JVM one. Highest-value row in this table for a Java retail stack. |
| New — 🇧🇷 | [TadaSoftware/PyNFe](https://github.com/TadaSoftware/PyNFe) | **LGPL-3.0** (7854 B) | 599★ / 237 refs | 2026-02-20 | Python NF-e. API says `NOASSERTION`; the file is a reformatted LGPL-3.0. Dormant 9 months. |
| New — 🇲🇽 | [phpcfdi/sat-ws-descarga-masiva](https://github.com/phpcfdi/sat-ws-descarga-masiva) · [SAT-CFDI/python-satcfdi](https://github.com/SAT-CFDI/python-satcfdi) · [eclipxe13/CfdiUtils](https://github.com/eclipxe13/CfdiUtils) | **MIT** × 3 (1106 / 1056 / 1111 B) | 198★ · 169★ · 146★ | 2026-09-20 · 2026-11-08 · 2026-11-15 | **Mexico is the only country in retail where the compulsory layer can be built with zero copyleft obligation.** `python-satcfdi`'s licence lives in a file called `license` with no extension, beside a `readme.rst`. |
| New — 🇲🇽 | [phpcfdi/resources-sat-catalogs](https://github.com/phpcfdi/resources-sat-catalogs) | **Unlicense** (2571 B, public domain) | 97★ / 424 refs | 2026-11-20 | SAT product/tax catalogues, public domain. The rarest licence in this KB. |
| New — 🇨🇱 | [LibreDTE/libredte-lib-core](https://github.com/LibreDTE/libredte-lib-core) | **AGPL-3.0** (`COPYING` 34520 B) | 228★ / 166f | 2026-11-19 | Chile's only maintained DTE core, and it is AGPL. `factura electronica DTE SII stars:>=20` → **0 results**, so there is no alternative to find. |
| New — 🇪🇺 | [phax/phase4](https://github.com/phax/phase4) | **Apache-2.0** (10173 B) | 246★ / 67f | 2026-11-18 | Peppol AS4 client/server, and the *maintained* access-point option. |
| **Licence alert — 🇪🇺** | [OxalisCommunity/oxalis](https://github.com/OxalisCommunity/oxalis) | **EUPL-1.1 or later** (declared in `COPYRIGHT`, 799 B; repo also ships `COPYING.LGPL`) | 150★ / 280 refs | 2026-04-16 | The reference Peppol Access Point, built by Norway's Difi. Two disagreeing licence artefacts, API says `NOASSERTION`, and **EUPL treats *communicating the work* as distribution** — hosting it as a service can trigger source provision like AGPL. Invisible to every SPDX field and SBOM scan of the source tree. Dormant since April. |
| New — 🇪🇺 | [josemmo/einvoicing](https://github.com/josemmo/einvoicing) · [num-num/ubl-invoice](https://github.com/num-num/ubl-invoice) · [phax/phive](https://github.com/phax/phive) | **MIT** · **MIT** · **Apache-2.0** | 180★ · 143★ · 79★ | 2026-11-07 · 2026-11-03 · 2026-11-19 | EN 16931 reading/writing, UBL/Peppol BIS generation, and document validation. All permissive, all pushed this month. |
| New — 🇮🇳 | [resilient-tech/india-compliance](https://github.com/resilient-tech/india-compliance) | **GPL-3.0** (`license.txt` 35149 B) | 286★ / 4725 refs | 2026-11-20 | GST e-invoicing and e-way bills **as an ERPNext app** — compliance shipped inside the ERP rather than beside it. |
| **Licence alert — LATAM** | [OCA/l10n-brazil](https://github.com/OCA/l10n-brazil) · [OCA/l10n-mexico](https://github.com/OCA/l10n-mexico) · [OCA/l10n-chile](https://github.com/OCA/l10n-chile) | **AGPL-3.0** × 3 (34523 B each) | 376★/339f · 20★/**56f** · 10★/**41f** | 2026-11-21 · 2026-11-09 · 2026-11-22 | **The inversion of cycle 8's headline.** Odoo core is LGPL so proprietary modules are allowed — but the modules that make the POS *lawful* in LATAM are AGPL. Note the fork:star ratios for Mexico and Chile — 2.8 and 4.1: nobody stars a tax localisation, they fork it to patch it. |
| New — till layer | [opensourcepos/opensourcepos](https://github.com/opensourcepos/opensourcepos) | **MIT** (2537 B incl. 26-name roster) | 4530★ / 1410 refs | 2026-11-22 | The only permissive **and** maintained standalone retail till. API says `NOASSERTION` purely because of the copyright roster above the grant. |
| New — till layer | [Blair2004/NexoPOS](https://github.com/Blair2004/NexoPOS) | **GPL-3.0** (35149 B) | 1310★ / 2125 refs | **2026-11-22 (same day)** | Most actively developed dedicated POS measured. |
| **Do not use** | [tngoman/Store-POS](https://github.com/tngoman/Store-POS) | **No licence file** (2 branches × 8 filenames probed) | 1058★ / 115 refs | 2026-10-25 | The single highest-starred result for `point of sale retail stars:>=300` — a query that returns exactly one repo — **and it carries no grant at all.** A keyword-ingest pass would have put it first. |

**Per-row audit:** 14 rows / 24 distinct repos, every one verified by `ls-remote` for existence and by
reading the licence file at source. Five GitHub API `NOASSERTION` fields resolved to real licences; one
repo (`Store-POS`) confirmed genuinely unlicensed; one new licence family entered this KB (**EUPL**) and
two new licence filenames (`COPYING.LGPL`, `COPYRIGHT`, plus lowercase `license` with no extension).

**Measured empty, and recorded as empty:** `planogram` → 502 repos whose **top result has 17 stars**;
`shelf monitoring retail stars:>=30` → **1** (unlicensed, self-described simulation);
`workforce scheduling stars:>=150` → **1**, dead since 2022-12-06; `retail loss prevention theft detection
stars:>=20` → **0**; `footfall people counting retail stars:>=50` → **0**;
`product detection retail shelf yolo stars:>=100` → **0**; `factura electronica DTE SII stars:>=20` → **0**.
---

## 2026-11-22

**Theme of the week: the product-data plane enters this KB.** Eight files, and not one of them previously
contained the strings `gs1`, `gtin`, `barcode`, `pim`, `epcis`, `traceability`, `digital product passport`
or `supply chain`. Measured by grep before any search was run — the largest vocabulary gap found in this
KB to date.

| Movement | Repo | License | ★ / forks | Last push | Why it is trending |
|---|---|---|---|---|---|
| New — identity | [gs1/GS1_DigitalLink_Resolver_CE](https://github.com/gs1/GS1_DigitalLink_Resolver_CE) | Apache-2.0 | 65★ / 45f | 2026-11-02 | GS1's reference resolver. Required infrastructure for both Sunrise 2027 and DPP. |
| New — identity | [zxing/zxing](https://github.com/zxing/zxing) | Apache-2.0 | 34217★ / 9428f | 2026-11-21 | The barcode-decoding floor, still being pushed daily at 34k stars. The 2D (DataMatrix/QR) support is what Sunrise 2027 needs. |
| New — events | [openepcis/epcis-repository-ce](https://github.com/openepcis/epcis-repository-ce) | Apache-2.0 | 17★ / 6f | 2026-10-22 | EPCIS 2.0 repository, Quarkus/Kafka/OpenSearch. Open-core — a commercial Business Edition exists above the CE. |
| New — events | [louisaxel-ambroise/epcis](https://github.com/louisaxel-ambroise/epcis) | Apache-2.0 (560 B pointer; API says `NOASSERTION`) | 36★ / 14f | 2026-11-22 | Committed on the day of this pass; the only live .NET EPCIS. |
| New — messages | [nerdocs/pydifact](https://github.com/nerdocs/pydifact) | MIT | 191★ / 54f | 2026-11-16 | EDIFACT in Python, actively maintained. EDI is still how retail trade documents actually move. |
| New — messages | [tastypackets/x12-parser](https://github.com/tastypackets/x12-parser) | MIT | 63★ / 12f | 2026-11-18 | Freshest X12 parser; TypeScript, streaming. |
| New — platform | [unopim/unopim](https://github.com/unopim/unopim) | MIT (verified by reading, 1078 B) | 11080★ / 193f | 2026-11-20 | The only permissive, maintained PIM. 57:1 star/fork ratio, so attention far exceeds deployment. |
| **Licence change caught** | [pimcore/pimcore](https://github.com/pimcore/pimcore) | ❌ **POCL** (bespoke vendor agreement, "Last Update: June 2025") | 3891★ / 1513f | 2026-11-22 | Universally still described as GPLv3 community edition. It is not GPL and has not been since June 2025. 24927-byte custom agreement. |
| New — DPP | [open-dpp/open-dpp](https://github.com/open-dpp/open-dpp) | AGPL-3.0 | 35★ / 19f | 2026-11-22 | Most active open DPP platform; pushed the day of this pass. |

*Per-row audit of the 2026-11-21 section below: re-checked, no dead slugs introduced. The protocol rows in
that section are revised upward in honesty — see `agents/trending.md` for the last-push measurements.*

## 2026-11-21

**Theme of the week: the agentic-commerce protocol layer is the fastest-moving thing in retail, and it is
entirely Apache-2.0.**

| Repo | License | Stars | Last push | Why it is trending |
|---|---|---|---|---|
| [Universal-Commerce-Protocol/ucp](https://github.com/Universal-Commerce-Protocol/ucp) | Apache-2.0 | 3,515 | **2026-11-21** | Google's UCP, announced at NRF Jan 2026, **pushed today**. Microsoft has adopted it in Merchant Center. The most active of the three competing standards. |
| [x402-foundation/x402](https://github.com/x402-foundation/x402) | Apache-2.0 | 6,820 | 2026-11-20 | HTTP-native per-request payments, now under foundation governance. ⚠️ `coinbase/x402` still resolves with an identical 11,324 B Apache LICENSE but a **different HEAD** — it is the pre-donation repo, *not* a redirect. Build against the foundation slug. |
| [google-agentic-commerce/AP2](https://github.com/google-agentic-commerce/AP2) | Apache-2.0 | 3,281 | 2026-06-17 | Agent Payments Protocol — the consent/mandate layer. Becoming the auditable artefact for agent purchases. |
| [agentic-commerce-protocol/agentic-commerce-protocol](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) | Apache-2.0 | 1,607 | 2026-07-18 | ACP, maintained by **OpenAI and Stripe** — what the ChatGPT commerce surface speaks. |
| [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | Apache-2.0 | 572 | 2026-11-11 | Brings x402 payments into the Agent-to-Agent protocol, so agents can bill each other. |
| [medusajs/medusa](https://github.com/medusajs/medusa) | MIT | 37,346 | **2026-11-21** | Pushed today. The most adoptable permissive commerce core; MIT confirmed by reading LICENSE (1,075 B) after the API reported `NOASSERTION`. |
| [gorse-io/gorse](https://github.com/gorse-io/gorse) | Apache-2.0 | 9,928 | 2026-11-20 | Recommender engine now shipping LLM rankers + multimodal embeddings. **Correction: 9,928★, not the ~12.5k earlier cycles recorded.** |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 | 35,652 | 2026-11-20 | The fully-Apache retrieval choice for product search, now that Meilisearch's EE parts are confirmed BUSL-1.1. |

**Licence corrections landed this week** (full detail in `agents/top.md` and `verticals/solutions.md`):
`meilisearch/meilisearch` is `MIT AND OpenLDAP AND BUSL-1.1`, not MIT; `odoo/odoo` is **LGPL-3.0**, not GPL;
`vendure-ecommerce/vendure` is GPL-3.0, not MIT; `nopSolutions/nopCommerce` is AGPL **plus mandatory
per-screen attribution**; `visa/trusted-agent-protocol` is **not open source**; and `apache/ofbiz` is
**archived since 2020** — use `apache/ofbiz-framework`.

**Dead on arrival:** `openmercato/open-mercato`, recommended as "MIT, self-hostable CRM/ERP" by a public
listicle, returns **refs=0**. It does not exist at that slug.

## History — 2026-07-02 (preserved verbatim; was byte-identical to agents/trending.md)

> ⚠️ **Audited 2026-11-21.** See the audit note in `agents/trending.md` for the per-row measurements. In
> short: 2 of the 10 slugs are dead (`indmdev/indmshopbot`, `Blakew316/shopconnect`), six of the remaining
> eight have 0–1 stars, and the only substantial repo is `gz-yami/mall4j` (5,329★, AGPL-3.0). Kept here
> because this file is append-only and the history is the point.

> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [indmshopbot](https://github.com/indmdev/indmshopbot) | MIT | InDMShopBot: The best Telegram Shopping Bot For Sellers, The Shop Bot is a Class | 29 |
| [mall4j](https://github.com/gz-yami/mall4j) | AGPL-3.0 | ⭐️⭐️⭐️ 电商商城 小程序电商商城系统 PC商城 H5商城 APP商城 Java商城 O2O商城 跨境商城 | 5.1k |
| [woocommerce](https://github.com/woocommerce/woocommerce) | ? | A customizable, open-source ecommerce platform built on WordPress. Build any com | 10.4k |
| [shopconnect](https://github.com/Blakew316/shopconnect) | AGPL-3.0 | Polygon ID–gated promotions & proof-of-purchase for e-commerce: browser-extensio | 0 |
| [multivendor-ecom](https://github.com/AneeshYadav2419/multivendor-ecom) | ? |  A full-stack marketplace where customers shop,  vendors manage their stores & a | 0 |
| [v2](https://github.com/Jaal-Yantra-Textiles/v2) | ? | Launch your design and artisanal garment marketplace with e-commerce, pre-produc | 17 |
| [shoplytics](https://github.com/MeaFew/shoplytics) | MIT | E-commerce User Behavior Analytics Platform \| 29M real user records \| SQL + Py | 0 |
| [New-Mughal-Paint](https://github.com/officialmrcoder/New-Mughal-Paint) | ? | A modern paint e-commerce platform built with Next.js, TailwindCSS, and Supabase | 0 |
| [retail-ai-store-level-intelligence](https://github.com/Svyatoslavpech/retail-ai-store-level-intelligence) | Apache-2.0 | Why the biggest AI opportunity in retail isn't at headquarters — it's on the sto | 0 |
| [shelfops](https://github.com/IFAKA/shelfops) | ? | Retail shelf audit demo comparing Cerebras Gemma 4 inference against local Gemma | 0 |

---
*Pipeline automático — se actualiza cada hora.*
