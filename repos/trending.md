---
industry: retail
region: Global
updated: 2026-11-22
---

# 📈 Repos Trending — Retail & Consumer

> **Append-only.** Newest dated section on top; history preserved below. This file tracks **infrastructure,
> protocol and platform repos**. For agents and agent-facing tooling see `agents/trending.md` — until today
> the two files were byte-identical and this distinction did not exist.

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
