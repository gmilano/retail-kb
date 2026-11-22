---
industry: retail
region: Global
updated: 2026-11-22
---

# 🎯 AI Agents & Commerce Intelligence — Retail & Consumer

> Open source agents and engines for retail. Focus: MIT / Apache 2.0 / BSD — what Globant can build on.
> **Every row below was verified on 2026-11-21**: existence via `git ls-remote`, stars + last-push from
> the same GitHub `search/repositories` call (so the two always cross-check), and license by reading the
> actual LICENSE file wherever the API returned `NOASSERTION`. Star counts are point-in-time and are
> **not** carried forward from earlier cycles — see the corrections section for why that matters here.

## Tier 1 — Permissive, actively maintained (safe to build on)

| Agent / Engine | Repo | License | Stars | Last push | What it does |
|---|---|---|---|---|---|
| Commerce Agents | [anthropics/commerce-agents](https://github.com/anthropics/commerce-agents) | Apache-2.0 | 3,497 | 2026-11-16 | Reference blueprint for shopping **and merchant-side** agents, with worked retail, commerce, telecom and entertainment examples. The best-documented starting point for a retail agent engagement. |
| Recommenders | [recommenders-team/recommenders](https://github.com/recommenders-team/recommenders) | MIT | 22,009 | 2026-11-05 | Linux Foundation best-practice recsys: ~30 algorithms with evaluation and deployment notebooks. The reference implementation, not a toy. |
| WrenAI | [Canner/WrenAI](https://github.com/Canner/WrenAI) | Apache-2.0 | 18,354 | 2026-11-20 | GenBI text-to-SQL agent over warehouses. License read and confirmed genuine Apache-2.0 (2,214 B) despite the API reporting `NOASSERTION`. |
| Apify MCP Server | [apify/apify-mcp-server](https://github.com/apify/apify-mcp-server) | MIT | 17,199 | 2026-11-20 | Typed MCP access to competitor catalogues, pricing and product pages. The practical answer to retail's real bottleneck (see trends #3). |
| Gorse | [gorse-io/gorse](https://github.com/gorse-io/gorse) | Apache-2.0 | 9,928 | 2026-11-20 | Recommender engine with classical **and LLM rankers** plus multimodal content via embeddings. Deployable as a service, not a library. |
| StatsForecast | [Nixtla/statsforecast](https://github.com/Nixtla/statsforecast) | Apache-2.0 | 4,982 | 2026-11-19 | Fast statistical forecasting at scale. For demand planning, start here before reaching for deep learning. |
| NeuralForecast | [Nixtla/neuralforecast](https://github.com/Nixtla/neuralforecast) | Apache-2.0 | 4,318 | 2026-11-18 | Neural demand forecasting (NBEATS, NHITS, TFT). Pairs with StatsForecast as the baseline-vs-model comparison. |
| x402 | [x402-foundation/x402](https://github.com/x402-foundation/x402) | Apache-2.0 | 6,820 | 2026-11-20 | HTTP-native payments protocol — revives HTTP 402 so an agent can pay per request. Now under a foundation, not a single vendor. |
| CommerceAgentBench | [Accio-org/CommerceAgentBench](https://github.com/Accio-org/CommerceAgentBench) | Apache-2.0 | 1,310 | 2026-08-29 | Benchmarks long-horizon agents against stateful, reproducible replicas of real online stores. Use it to prove an agent works before a client does. |
| RecAI | [microsoft/RecAI](https://github.com/microsoft/RecAI) | MIT | 1,221 | 2026-01-27 | Microsoft's LLM-plus-recsys toolkit (explainable recs, conversational recs). Useful, but **no push in ~10 months** — vendor it. |
| Tracardi | [Tracardi/tracardi](https://github.com/Tracardi/tracardi) | MIT | 657 | 2026-09-22 | Open customer data platform (CDP) — profile unification and real-time segmentation. MIT confirmed by reading `LICENSE.md` (2,018 B). |
| daydreams | [daydreamsai/daydreams](https://github.com/daydreamsai/daydreams) | MIT | 628 | 2026-10-09 | Agent framework aimed at autonomous on-chain/commerce execution. |
| Wocart | [bighadj22/Wocart](https://github.com/bighadj22/Wocart) | Apache-2.0 | 426 | 2026-11-16 | AI shopping-cart layer over WooCommerce — the permissive bridge into the GPL WordPress estate. |
| eBay MCP | [YosefHayim/ebay-mcp](https://github.com/YosefHayim/ebay-mcp) | MIT | 201 | 2026-11-20 | MCP server over the eBay APIs: live marketplace pricing and listings as agent tools. |
| NVIDIA Retail Agentic Commerce | [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce) | Apache-2.0 | 89 | 2026-11-20 | Reference implementation of **both** ACP and UCP. Small but the only blueprint that wires the two competing protocols together. |
| Shopify UCP CLI | [Shopify/ucp-cli](https://github.com/Shopify/ucp-cli) | MIT | 84 | 2026-11-09 | Shopify's own agent shopping skill built on UCP. MIT confirmed by reading LICENSE (1,061 B). Official vendor code under a permissive license — rare and worth using. |

## Tier 2 — Real and useful, but license or staleness constrains client work

| Agent / Engine | Repo | License | Stars | Last push | Constraint |
|---|---|---|---|---|---|
| Meilisearch | [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | **`MIT AND OpenLDAP AND BUSL-1.1`** | 59,948 | 2026-11-20 | ⚠️ **Not plain MIT.** The LICENSE (468 B) states the Enterprise Edition parts are **Business Source License 1.1** and declares that exact SPDX expression. Three earlier cycles of this file recorded it as flat "MIT". The MIT core is fine; anything EE-marked is not. Verify per-feature before building search on it. |
| Surprise | [NicolasHug/Surprise](https://github.com/NicolasHug/Surprise) | BSD-3-Clause | 6,829 | 2026-05-30 | Clean permissive recsys library, but scikit-era — explicit rating prediction only, no implicit-feedback or sequence models. Fine as a baseline. |
| RecBole | [RUCAIBox/RecBole](https://github.com/RUCAIBox/RecBole) | MIT | 4,620 | **2025-02-24** | 94 algorithms and genuinely MIT, but **dormant ~21 months**. See corrections: earlier cycles recorded a *rising* star count on a repo that had already stopped moving. |
| Trusted Agent Protocol | [visa/trusted-agent-protocol](https://github.com/visa/trusted-agent-protocol) | **Visa Developer Center Terms of Use — NOT open source** | 223 | 2025-10-28 | ⚠️ Looks adoptable (it sits under Visa's GitHub org), but `LICENSE.md` is a 398-byte pointer binding you to Visa's developer terms and product terms. **No OSS grant.** Read it as a spec; do not vendor the code. |

## Corrections to earlier cycles of this file

**The live file this replaced was the raw 2026-07-02 pipeline output, and its headline rows were not retail agents.**

- **`2No2Name/hopperOptimizations` was listed as a retail inventory agent. It is a Minecraft mod** —
  "hoppers" are an in-game item. MIT, 62★, dormant since 2022-02-27. A pure keyword collision that three
  cycles of ingest carried as retail intelligence.
- `guymorita/recommendationRaccoon` (MIT, 816★) is real but **last pushed 2020-09-11** — six years dormant.
- `criteo-research/reco-gym` (Apache-2.0, 483★) real, **dormant since 2021-07-09**.
- `LarrySnyder/stockpyl` (MIT, 185★, pushed 2026-06-10) is real, active and genuinely relevant — the one
  row of the ten that held up. The old file recorded it at 164★.

**Star counts in `rotation.json` carried fabricated growth curves.** Measured this pass against what
cycles 2, 3 and 7 recorded:

| Repo | Recorded (cycle 2 → 3 → 7) | Measured 2026-11-21 | Verdict |
|---|---|---|---|
| gorse-io/gorse | ~10.5k → 11.2k → 12.5k | **9,928** | Inflated ~26%; the curve was invented |
| RUCAIBox/RecBole | ~5.5k → 5.8k → 7.2k | **4,620**, last push 2025-02-24 | Inflated ~56% **and rising while the repo was dead** |
| Nixtla/neuralforecast | ~9k → 9.8k → 10.5k | **4,318** | Inflated ~2.4x |
| Nixtla/statsforecast | ~4.5k → 5.1k → 5.2k | **4,982** | Roughly right |
| Canner/WrenAI | ~14k → 16k → 17k | **18,354** | *Under*stated |
| meilisearch/meilisearch | ~54k → 57k → 57k | **59,948** | Understated — and the license was wrong |

A metric that rises while `last_push` does not move is the signature of an invented number, and one
`search/repositories` call returns stars and `pushed_at` together, so the cross-check is free. The bias
here is sloppiness, not a consistent direction — two of six were understated.

**Slugs that do not resolve.** Earlier cycles recorded `NVIDIA-RetailBlueprint` and
`NVIDIA-ShoppingAssistant` with star counts; neither slug resolves. The real asset is
`NVIDIA-AI-Blueprints/Retail-Agentic-Commerce` (89★, listed above). Separately, the listicle-recommended
"Open Mercato, MIT" (`openmercato/open-mercato`) returns **refs=0** — it does not exist at that slug.

*Verification method: `git ls-remote` for existence (the only reliable oracle — `search/repositories`
returns false negatives and 422s on live repos, and `curl -sI github.com` is blind through this proxy);
stars and `pushed_at` from one `search/repositories` call; licenses read from raw.githubusercontent.com
whenever the API said `NOASSERTION` or returned nothing.*

---

## Added 2026-11-22 — the product-data plane (agents that make a catalogue machine-readable)

Yesterday's pass established that the **access** layer is populated: UCP, ACP, AP2, x402 and the NVIDIA
blueprint let an agent reach a storefront and complete a purchase. This pass asked the question underneath
it: once the agent arrives, **can it tell what the product is?** The answer is where the open-source floor
stops.

### The agent-shaped layer is one repo wide — measured, not estimated

| Agent / service | Repo | License | ★ / forks | Last push | What it does |
|---|---|---|---|---|---|
| NVIDIA Retail Catalog Enrichment | [NVIDIA-AI-Blueprints/Retail-Catalog-Enrichment](https://github.com/NVIDIA-AI-Blueprints/Retail-Catalog-Enrichment) | Apache-2.0 (read, 11347 B) | 47★ / 26f | 2026-11-18 | GenAI pipeline that turns bare product images into structured catalogue copy and attributes. **The only result worldwide for `catalog enrichment ai stars:>=20`.** |
| Shopify MCP server | [GeLi2001/shopify-mcp](https://github.com/GeLi2001/shopify-mcp) | MIT | 238★ / 121f | 2026-04-05 | Typed access to Shopify Admin API (products, variants, inventory) for MCP hosts. Most-starred third-party commerce MCP server; 7 months since last push. |
| SAP Commerce (Hybris) MCP | [Emenowicz/hybris-mcp](https://github.com/Emenowicz/hybris-mcp) | MIT | 17★ / 6f | 2026-09-24 | FlexibleSearch, ImpEx, Groovy and cron access to SAP Commerce Cloud — the enterprise catalogue most Globant retail clients actually run. |
| GS1 Digital Link Resolver CE | [gs1/GS1_DigitalLink_Resolver_CE](https://github.com/gs1/GS1_DigitalLink_Resolver_CE) | Apache-2.0 (read, 11357 B) | 65★ / 45f | 2026-11-02 | Resolves a GTIN/Digital Link URI to the set of URIs for that product (spec sheet, DPP, recall, recipe). **The standards body's own reference implementation, permissively licensed and alive.** Usable directly as an agent tool: one identifier in, authoritative links out. |

**That is the whole list.** The queries that returned nothing are listed in `repos/foundations.md` under the
2026-11-22 gap section. `product description generation ai stars:>=30` → **0**.
`visual search product embedding stars:>=100` → **0**. `product taxonomy classification stars:>=50` → **0**.

### Corrections and refinements to earlier cycles of this file

- **Refinement to the 2026-11-21 "product matching / entity resolution = 0" gap.** That measurement was
  right for the *retail-specific* query and wrong as a general conclusion. Generic entity resolution is well
  equipped: [dedupeio/dedupe](https://github.com/dedupeio/dedupe) (MIT, 4531★ / 578f, last push
  2025-07-29) and [zinggAI/zingg](https://github.com/zinggAI/zingg) (AGPL-3.0, 1275★ / 178f, 2026-11-03).
  The accurate statement is: **the engines exist, the retail rule packs do not.** That is a better
  commercial position than a bare gap, and it changes the recipe — compose, do not build from zero.
- **Protocol maintenance re-measured, and it changes yesterday's picture.** Yesterday's rows carried stars
  but not last-push for the three standards. Measured today: ACP (`agentic-commerce-protocol`) 1610★,
  **last push 2026-07-18 — 127 days**; AP2 (`google-agentic-commerce/AP2`) 3283★, **last push 2026-06-17 —
  158 days**; UCP (`Universal-Commerce-Protocol/ucp`) 3516★, **last push 2026-11-21 — yesterday**. Of the
  three Apache-2.0 standards, **only Google's UCP is under active maintenance.** Protocol-neutrality via
  the NVIDIA blueprint remains the right engineering call, but do not describe ACP or AP2 to a client as
  fast-moving: they are, on the evidence of their own default branches, parked.

---

## Added 2026-11-22 (pass 2) — the store plane: agents for the register, the receipt and the shelf

The earlier section on this date added the *product-data* plane. This section adds the plane that was
missing underneath it: **the physical store**. Grep of all eight files before any search was run returned
**zero** occurrences of `planogram`, `self-checkout`, `rfid`, `computer vision`, `workforce`, `scheduling`,
`labor`, `store operations`, `task management`, `point of sale`, `kiosk`, `reverse logistics`,
`loss prevention` (1 passing mention), `fraud`, `chargeback`, `loyalty`, `customer service`, `e-invoic`,
`invoice`, `cfdi`, `nf-e` and `peppol`. Retail's own majority channel had no vocabulary in this KB at all.

### The finding that governs this whole section

**There is no store-operations agent.** The agent surface over the store is an **MCP server bolted to the
incumbent ERP/POS** — because that is where the till, the stock ledger *and* the country tax localisation
already live. Every row below was verified on 2026-11-22 by `git ls-remote` (existence) and by reading the
licence file over the raw channel (licence), with stars and last-push read the same day.

| Agent / tool | Repo | Licence (verified at source) | ★ / forks | Last push | What it actually does |
|---|---|---|---|---|---|
| Odoo MCP server | [ivnvxd/mcp-server-odoo](https://github.com/ivnvxd/mcp-server-odoo) | **MPL-2.0** (LICENSE 16725 B) | 419★ / 190f | **2026-11-22 (same day)** | The strongest store-plane agent surface found. Exposes Odoo models over MCP — which in Odoo means POS sessions, stock moves, pricelists and the `l10n_*` fiscal modules. MPL-2.0 is file-level copyleft: your own new files stay proprietary. |
| ERPNext MCP server | [rakeshgangwar/erpnext-mcp-server](https://github.com/rakeshgangwar/erpnext-mcp-server) | MIT (LICENSE 1071 B) | 131★ / 12f | 2026-04-25 | Connects an assistant to an ERPNext instance via the Frappe REST API. ERPNext carries the POS, warehouse and India GST modules. Dormant 211 days — usable, not maintained. |
| Odoo MCP (extended tools) | [hachecito/odoo-mcp-improved](https://github.com/hachecito/odoo-mcp-improved) | MIT (LICENSE 1072 B) | 49★ / 6f | 2026-11-18 | Adds sales/stock-specific tools on top of the generic Odoo MCP pattern. Small but alive. |
| Odoo SDK + MCP + skills | [marcfargas/odoo-toolbox](https://github.com/marcfargas/odoo-toolbox) | **LGPL-3.0** (LICENSE 7652 B) | 44★ / 116 refs | 2026-10-26 | TypeScript SDK, CLI and MCP server, CI-tested against live Odoo. LGPL-3.0: link dynamically and your application stays closed. |
| Frappe/ERPNext CLI + MCP | [nasroykh/foxmayn_frappe_cli](https://github.com/nasroykh/foxmayn_frappe_cli) | MIT | 16★ | 2026-11-11 | CLI, MCP server and desktop app for Frappe/ERPNext. Smallest of the set; listed because it is permissive and current. |
| Scheduling/rostering solver | [TimefoldAI/timefold-solver](https://github.com/TimefoldAI/timefold-solver) | **Apache-2.0** (LICENSE.txt 11358 B) | 1879★ / 244f | 2026-11-20 | Not an agent, but the only *maintained* engine for the shift-rostering problem retail actually has. The successor to OptaPlanner (`apache/incubator-kie-optaplanner`, 3512★, its own description now redirects elsewhere). Give an agent this as a tool rather than asking an LLM to build a roster. |
| Shelf-vision primitives | [roboflow/supervision](https://github.com/roboflow/supervision) | **MIT** (LICENSE.md 1065 B) | 51699★ / 4964f | 2026-11-20 | The permissive way to build shelf/queue vision: detector-agnostic tracking, zone counting, annotation. Pair with a non-AGPL detector — see the licence warning below. |

**Seven rows, and that is all there were.** No padding: the measured searches that returned nothing are
written down under "measured gaps" in `repos/foundations.md` rather than filled with plausible repos.

### The licence trap in this plane — read this before writing any shelf-vision proposal

[ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) — 63669★, 12024 forks, pushed
2026-11-22, the default YOLO everyone reaches for — is **AGPL-3.0**. Its `LICENSE` is 34523 bytes and its
first line reads `GNU AFFERO GENERAL PUBLIC LICENSE`. Byte-for-byte the same file as
`OCA/l10n-brazil`'s. Every student shelf-monitoring repo surfaced by search is built on it, which means
**the entire visible open-source shelf-vision corpus is AGPL-derived**, and AGPL's network clause reaches a
hosted store-analytics service. The permissive route is `roboflow/supervision` (MIT) over an
Apache/MIT-licensed detector, with the Ultralytics weights and package left out of the build.

### Agent-layer measurements that came back empty (2026-11-22)

- `retail execution store audit mobile stars:>=5` → **0 results worldwide.** Store-task execution — the
  category Yoobic, Zipline and Flip sell into — has no open-source entry point at any star threshold.
- `order management fulfillment stars:>=100` → **0.** No open-source OMS above 100 stars.
- `footfall people counting retail stars:>=50` → **0.**
- `retail loss prevention theft detection stars:>=20` → **0.** Confirms cycle 8's finding with a tighter
  query; shrink has no open-source floor in either channel.
