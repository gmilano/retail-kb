---
industry: retail
region: Global
updated: 2026-11-28
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

## Added 2026-11-22 (pass 3) — the retail media plane: agents that buy and sell advertising

Retail media — a retailer selling ads against its own first-party data — had
**zero mentions anywhere in this KB** before this pass ("retail media",
"advertising" and "clean room" all returned no hits across all eight files).
This section covers the agent-shaped part of it. The repository tables live in
`repos/foundations.md`; the market numbers, which vary by a factor of eight
depending on definition, live in `intel/market.md`.

### The agent layer here is two repos wide — measured, not estimated

| Agent | Repo | Licence (read at source) | refs | Last commit | What it actually does |
|---|---|---|---|---|---|
| Prebid Sales Agent | [prebid/salesagent](https://github.com/prebid/salesagent) | Apache-2.0 (10767B) | 2354 | 2026-11-23 (0d) | Server implementing the AdCP **sales-agent** role: exposes ad inventory to AI agents over **MCP and A2A**, integrates Google Ad Manager, multi-tenant isolation, 16 AdCP tools, admin UI, full campaign lifecycle from discovery to reporting |
| Setupad Sales Agent | [Setupad/salesagent](https://github.com/Setupad/salesagent) | Apache-2.0 (10767B) | 10 | 2026-10-19 (34d) | An independent second deployment of the same role — the evidence that the role has more than one implementer |

That is the entire inventory of real, licence-verified, agent-shaped retail
media code found on 2026-11-22. **Two rows, so two rows are written.** The
searches that produced nothing are listed below, because an informed gap is
information and a padded table is not.

**Read `prebid/salesagent`'s own status note before it goes in a client deck:**
*"Status: alpha. A pre-1.0 implementation of a pre-release protocol, under
active development. APIs still change between releases — `v2.0.0` introduced
breaking changes — so pin a version and expect to adapt on upgrade. It is one
of several AdCP sales-agent implementations, not a sole or canonical
reference."* The codebase is substantial and functional; the protocol under it
is not finished. It pins the `adcp` SDK exactly and enforces the pin with a CI
guard that fails on drift — copy that pattern for any pre-1.0 protocol work.

**Slug note:** `adcontextprotocol/salesagent` and `prebid/salesagent` return
identical HEAD SHAs (`dcd14d0f`) and identical ref counts (2354). By the rename
test, they are **one repository**; `prebid/salesagent` is canonical (it serves
the README, which states "maintained under Prebid.org"). Do not list both.

### The protocol under the agents, and an asymmetry worth naming

Cycle 8 mapped the agentic-*commerce* protocols (UCP, ACP, AP2, x402) and
concluded that **protocol neutrality is cheaper than betting on a winner**.
Agentic *advertising* has its own protocol layer, and the same conclusion holds
— but the two candidates are nothing like evenly matched.

| Protocol | Repo | Licence | refs | Last commit | State |
|---|---|---|---|---|---|
| **AdCP** (Ad Context Protocol) | [adcontextprotocol/adcp](https://github.com/adcontextprotocol/adcp) | Apache-2.0 (10767B) | **8610** | 2026-11-22 (0d) | Spec + SDKs, transported over **MCP and A2A**. Ships `CHARTER.md`, `IPR_POLICY.md`, `CONTRIBUTORS.md`, changesets, Dockerfile. Governance under AgenticAdvertising.org |
| **AAMP** | [IABTechLab/AAMP](https://github.com/IABTechLab/AAMP) | Apache-2.0 (11356B) | **5** | 2026-09-22 (61d) | ⚠️ The repository contains **exactly two files — `LICENSE` and `README.md` — and one commit** ("Revise section titles in README") |

Trade press in 2026 frames these as rival standards "dividing the advertising
industry", with the open question being whether they converge, coexist or
compete. On repository evidence the contest is not symmetric: one side has
8,610 refs, governance documents and commits landing during this pass; the
other has a README.

**State this precisely, because the imprecise version is wrong.** What is
measured is **GitHub presence, not the existence of a specification.** IAB Tech
Lab routinely publishes specs through its own site and working groups rather
than as repository code, so AAMP may well exist as a document that this
measurement cannot see. The decision-relevant conclusion is narrower and still
firm: **you cannot build against AAMP from GitHub today, and you can build
against AdCP today.** The AdCP FAQ states the two are **not wire-compatible**
and that implementing one does not require the other — so this is a real fork
in the road, not a layering choice.

**Falsifiable prediction, recorded so a later cycle can score it:** if AAMP is
a genuine competitor, `IABTechLab/AAMP` acquires implementation code beyond a
README before **2027-05-22**. If it is still two files then, AdCP is the only
buildable agentic-advertising protocol and should be treated as such rather
than hedged against.

### Agent-layer measurements that came back empty (2026-11-22)

| Query | Result |
|---|---|
| `gh api search/repositories q='adcp agentic advertising stars:>=5'` | **0** — a fifth measured false negative for `search/repositories` (adcp itself has 8610 refs) |
| `retail media stars:>=50` | **1**, and it is a 2020 generic ML regression repo with no licence |
| `retail media network stars:>=10` | **3**, all Windows-7/Minecraft DxDiag dumps — see below |
| `clean room advertising stars:>=50` | **0** literal |

### ⚠️ Cycle 8's Minecraft defect reproduced itself in this pass

Cycle 8's flagship finding was that `2No2Name/hopperOptimizations` — a
**Minecraft mod** about in-game hoppers — had been shipped in this very file as
retail *inventory* intelligence. Querying `retail media network stars:>=10`
today returns `dovnel/Win-7` (2015), `denman2328/Help` (2013) and
`Camus777/Minecraft` (2014): DxDiag system-information dumps in which
"Retail", "Media" and "Network" all appear as ordinary Windows vocabulary.

**Three of three hits are garbage, and all three look like plausible repos in
a results list.** The defence is not a better query; it is opening every row
before writing it. Nothing from those queries entered this KB.

---

## Added 2026-11-23 — the returns & recovery plane (agents for the reverse flow)

### The finding that governs this whole section

**The agent-shaped layer in retail's reverse flow is two repos wide, and
neither is a returns agent.** This is measured, not estimated, and the
measurement was nearly derailed by the ambiguity of the word itself:

- `returns agent` → **2464 repos, zero relevant.** The highest-starred hit
  (162★) is a Brainfuck web app that *"returns your user-agent to you"*. This
  is the single best specimen of false abundance in this knowledge base.
- `refund agent llm` → **191 repos**, and the whole top six is 141★ (a generic
  LangGraph demo), 6★, 9★, 7★, 0★, 0★.
- `customer support agent ecommerce` → **236 repos**, top result 12★ and
  unlicensed.

What exists, verified:

| Agent / repo | License | Stars | Last push | What it actually does |
|---|---|---|---|---|
| [budna-marketplace/recommerce](https://github.com/budna-marketplace/recommerce) | MIT | 16★/1f | 2026-11-09 | **Agent skills for comparing new and pre-owned items.** MIT, alive, and the only agent-shaped artifact found anywhere in the recommerce/resale layer. Small, but it is the real thing: it makes the new-vs-used trade-off an agent can reason about. |
| [Pragatheswar-72/support-agent](https://github.com/Pragatheswar-72/support-agent) | MIT | 6★/4f | 2026-07-01 | Multi-agent customer support: a LangGraph orchestrator routing to specialist agents. MIT. Useful as a *shape* for a post-purchase agent; 6★ means read it, don't depend on it. |

And one that is on-topic enough to name but cannot be used:

| Agent / repo | License | Stars | Last push | Why it is Tier 2 |
|---|---|---|---|---|
| [LikhithV02/Customer-Support-Agent](https://github.com/LikhithV02/Customer-Support-Agent) | **NONE** | 9★/2f | 2026-10-13 | Described as an agent that *"approves, denies or escalates refunds"* — precisely the decision this plane needs. **No licence ⇒ all rights reserved.** The closest thing to a refund-decision agent in open source is legally unusable. |

### The asymmetry worth naming

The reverse flow is the first plane in this KB where the **tool** layer is
strong and the **agent** layer is absent. Reverse routing has eight
permissive, actively committed solvers (see `repos/foundations.md` → Step 3,
incl. `google/or-tools` 14430★ and `PyVRP` MIT 734★), and anomaly detection has
`open-edge-platform/anomalib` at 6416★ Apache-2.0. What nobody has built is the
*agent that decides*: whether to authorise the return, what condition grade to
assign, and which disposition route is both cheapest and lawful.

That is the composable opportunity, and it is written up concretely as
Pattern 18 and Pattern 19 in `compose/patterns.md`.

### Agent-layer measurements that came back empty (2026-11-23)

- `returns agent` → 2464 repos, **0 relevant** (keyword collision).
- `refund agent llm` → 191 repos, nothing above 9★ on topic.
- `disposition engine` → **22 repos worldwide, 0 relevant.** No disposition agent.
- `takeback trade-in` → **0 repos.**
- `liquidation deadstock` → 1 repo, 0★.
- Warranty: `abdul-rafay-dev0/AssureX-Warranty-Claim-Engine` (MIT, **3★**, 2026-10-01) is the best permissive warranty-claim agent in existence. A 3★ repo is not a floor.

### ⚠️ Corrections and refinements to earlier cycles of this file

- **`anomalib` moved.** Earlier cycles of this KB discussed shelf vision as an
  AGPL-only corpus (2026-11-22, pass 2). That finding stands for *shelf*
  vision, but the escape hatch has now been located and it is permissive:
  **`open-edge-platform/anomalib`**, Apache-2.0, 6416★, pushed 2026-11-20. Note
  the owner: the old `openvinotoolkit/anomalib` slug still resolves over git
  but **422s** on the search API, which is the signature of a rename.
- **OptaPlanner's famous slug is a stub.** `apache/incubator-kie-optaplanner`
  (3512★) says in its own description that the project *"has moved"*. Where
  earlier cycles of this file reference OptaPlanner, the live targets are
  `apache/incubator-kie` (6344★) and `TimefoldAI/timefold-solver` (1879★,
  pushed 2026-11-23).

---

## Added 2026-11-23 (pass 5) — the price plane: agents that touch the number itself

**Plane opened this pass:** the price. Chosen by vocabulary probe against all
eight files *before* any web search, and the probe was unusually clean:
`elasticit`, `dynamic pric`, `competitor pric`, `price scrap`, `unit price`,
`drip pricing`, `shrinkflation`, `algorithmic collusion`, `personalized pricing`,
`clearance`, `revenue management`, `coupon`, `bundl` and `cross-sell` were all at
**literal zero** across the KB. The 19 hits for `markdown` were the *file format*;
`surveillance pricing` had exactly one mention.

> **This pass corrects two claims this KB has been carrying as settled fact.**
> See the correction notice in `repos/foundations.md` and trends #1 below.
> Both were produced by a single GitHub query each, and both are wrong as
> written. Rows here were verified on **2026-11-23**: existence via
> `git ls-remote`, stars + last push from one `search/repositories` call, and
> licence by reading the actual bytes wherever the API said `NOASSERTION` or
> `NONE`.

### Agent-facing and agent-shaped tooling on the price plane

| Agent / repo | Repo | License | Stars | Last push | Why it is here |
|---|---|---|---|---|---|
| OfferKit | [offerkit/offerkit](https://github.com/offerkit/offerkit) | **MIT** (`LICENSE` 1073 B read) | 58★ | 2026-11-20 | Agent-first, self-hostable promotion engine: coupons, gift cards, loyalty, referrals, stackable redemptions. Ships an **MCP server as a first-class surface** where every mutating endpoint declares a risk level (`safe` / `mutating` / `destructive`) so the LLM host can render the right confirmation. The only agent-native promotion engine found in open source. |
| Medusa Consumer Compliance | [zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance) | **MIT** (`LICENSE` 1064 B read) | 0★ | 2026-11-22 | Medusa v2 plugin implementing the **Omnibus 30-day lowest price**, unit prices, GPSR, the withdrawal function and the **personalised-pricing disclosure**. Records every price a customer could see per variant and pricing context, **never edits a recorded price**, keeps ≥400 days. The only code implementation of the price-compliance step found anywhere, at 0 stars and one day old. |
| changedetection.io | [dgtlmoon/changedetection.io](https://github.com/dgtlmoon/changedetection.io) | **Apache-2.0** (11382 B) | 35,967★ | 2026-11-22 | Website change detection with price-drop watchers and notification hooks. The practical substrate for competitor price observation, and by far the largest live repo on this plane. Surfaced under a `pricing mcp` query, not a retail one. |
| Crawlee | [apify/crawlee](https://github.com/apify/crawlee) | **Apache-2.0** | 26,521★ | 2026-11-23 | Browser-automation crawler for catalogue and price pages that defend themselves. Pairs with `apify/apify-mcp-server` (MIT, already in this file) to expose collection as agent tools. |
| Mercadona CLI | [ivorpad/mercadona-cli](https://github.com/ivorpad/mercadona-cli) | **NO LICENCE FILE** (root of `main` verified) | 338★ | 2026-10-06 | Self-described *"agent-friendly"* shopping CLI over a Spanish grocer: search products, read prices. The shape of a regional price agent — and **not usable**, because there is no grant. Listed as a shape, never as a dependency. |

### Measured: there is no retail pricing-agent boom, and the word "pricing" is contaminated

**[measured 2026-11-23]** `pricing agent created:>2026-06-01 stars:>=20` returns
**36 repos and not one retail pricing agent**: App Store PPP price updaters,
trading agents, an agent-authorization gateway, startup-advice skill packs.
`competitor monitoring stars:>=50` returns **2**, neither retail.
`price intelligence stars:>=20` returns **23**, whose two most on-topic hits are
Microsoft's dead Cortana solutions (below).

**New contamination family, and it has spread.** `pricing engine stars:>=200`
returns **6 repos** of which the top three are a Unity text-rendering engine
(`LightSideKittens/UniText`, 720★) and two **Claude/Codex marketing skill packs**
(`Yuzzyuk/marketing-os` 580★, `holy-templar/marketing-agi` 243★). Cycle 8 caught
this family polluting `ecommerce mcp`; it is now in the pricing vocabulary too.
Real, popular, and not retail pricing tooling. Excluded deliberately.

**Read the results, not the total — third confirmation, now with a ratio.**
`retail pricing` returns **4,472 repos and zero usable ones** in the top page
(student coursework from 2019–2023, a dead Magento toolkit, an API wrapper).
`markdown pricing` returns **263** of which exactly **one** is on-topic —
`topprismdata/fashion-lifecycle-pricing`, at 2★ with **no licence file**.

### Keyword collision *inside* a good repo — the new form of this trap

`pymc-labs/pymc-marketing` (Apache-2.0, 1314★, see `repos/foundations.md`) contains
`pymc_marketing/mmm/price_response.py`. Grepping the repo for *elasticity* finds it,
and it is **not retail pricing**: it models the price of a **delivered media unit**
(auction bid-up, rate-card tiers) inside the budget optimiser. The retail-relevant
module is `pymc_marketing/customer_choice/bayesian_blp.py`. Previous cycles of this
KB shipped a Minecraft hopper mod as inventory intelligence by matching on a
*repository name*; this is the same error one level down, matching on a *file name*
inside a repository that is genuinely excellent. **Read the module docstring.**

---

## Added 2026-11-23 (pass 6) — the fulfilment plane: agents that move the parcel

The five planes already in this file stop at the moment money changes hands. This pass covers
what happens next: promise a date, choose a node, pick it, hand it to a carrier, route the van,
prove it arrived. Everything below was measured on 2026-11-23 through `gh api search/repositories`,
with existence confirmed by `git ls-remote` and every licence read from the raw file, not the API field.

### The finding that governs this whole section

**The physics is solved and the commerce is empty.** Routing a vehicle — the hardest *mathematics*
on this plane — has at least ten maintained, mostly permissive implementations. Telling a shopper
when the parcel will arrive, and printing the carrier label that makes it move, have almost none.

| Step | Query run 2026-11-23 | Result |
|---|---|---|
| Promise a date (ATP) | `available to promise inventory` | 7 repos worldwide, **none above 1 star** |
| Print a carrier label | `shipping carrier label api stars:>=100` | **0** |
| Print a carrier label (shortened) | `shipping label carrier stars:>=30` | **0** |
| Track a parcel as the merchant | `tracking number carrier stars:>=50` | **0** |
| Prove delivery | `proof of delivery stars:>=30` | 2, both keyword collisions |
| Route the vehicle | `vehicle routing stars:>=200` | 16, the top six all alive |

### Tier 1 — permissive, alive, safe to build on

| Agent / repo | Repo | License | Stars | Last push | What it does |
|---|---|---|---|---|---|
| MCP Dev LATAM | https://github.com/codespar/mcp-dev-latam | MIT | 279 | 2026-11-13 | MCP servers wrapping real LATAM commerce APIs across 6 countries, including the carrier layer that measures as zero everywhere else |
| Beckn ONIX | https://github.com/beckn/beckn-onix | MIT | 101 | 2026-11-19 | Reference implementation of the Beckn network node — the stack ONDC's Open Delivery Protocol runs on |
| DPI Accelerator (Beckn ONIX) | https://github.com/GoogleCloudPlatform/dpi-accelerator-beckn-onix | Apache-2.0 | 11 | 2026-11-13 | Google Cloud's deployment accelerator for a Beckn network node |
| Shopify ActiveFulfillment | https://github.com/Shopify/active_fulfillment | MIT | 155 | 2024-09-24 | The only carrier-neutral, permissive fulfilment-service library found. **Dormant 2 years** — read it as a reference, not a dependency |
| nemlig MCP | https://github.com/kraenhansen/nemlig-mcp | MIT | 42 | 2026-10-15 | Unofficial MCP for a Danish grocery delivery service; small, but a real worked example of agent-to-delivery-slot interaction |

### Tier 2 — real and on-plane, but something blocks client work

| Agent / repo | Repo | License | Stars | Last push | The constraint |
|---|---|---|---|---|---|
| ATLAS (logistics MCP) | https://github.com/cargofy/ATLAS | **No licence file** | 20 | 2026-03-06 | The only logistics-specific MCP server found. Its README shows an Apache-2.0 badge linking to `LICENSE` — **that file returns 404 on every branch and every common filename.** Unusable until the owner adds one |
| shopper-mcp (Ozon) | https://github.com/eduard256/shopper-mcp | No licence | 94 | 2026-11-14 | Marketplace-side MCP for Ozon; no licence file |
| eCMR MCP (Skybridge) | https://github.com/cargoffer/ecmr-mcp-skybridge | No licence | 0 | 2026-05-25 | The *only* repo on GitHub matching "eCMR"; 0 stars, no licence. Recorded because its emptiness is the finding |

### ⚠️ A new form of the licence trap: the badge that points at nothing

Cycle 8 established *a short LICENSE file is a pointer, not a licence*. This pass found the next form:
**a README badge is not a licence either.** `cargofy/ATLAS` renders an Apache-2.0 shield linking to
`LICENSE`; the API reports no licence; `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING` and `NOTICE`
all 404 on the default branch. A reader who trusted the badge would have shipped an unlicensed
dependency into a client estate.

The same probe ran in the other direction and corrected a reflex: **`valhalla/valhalla` reports
`NOASSERTION`** — the flag that usually means trouble — **and is plain MIT.** Its `LICENSE.md` is a
43-byte pointer reading `For license information see [here](COPYING)`, and `COPYING` is a 1,135-byte
MIT text. The API flag was a false alarm. Read the file in *both* directions; do not downgrade a repo
on an API field any more than you would upgrade one on a badge.

### ⚠️ "Fulfillment" is ambiguous *in this industry* — the third such collision this KB has hit

`fulfillment agent stars:>=30` returns 5 repos and **4 of them are Dialogflow webhook libraries**,
where "fulfillment" means the code that satisfies a chatbot *intent* — nothing to do with shipping a
parcel. This is the same failure mode as pass 4's "returns" (refunds vs. `return` statements) and
cycle 8's Minecraft hopper. The industry word and the engineering word collide, and the search channel
cannot tell them apart.

**Vocabulary that actually retrieves this plane:** `vehicle routing`, `last mile`, `order router`,
`available to promise`, `shipping label`, `parcel tracking`, `eCMR`. **Vocabulary that does not:**
`fulfillment agent`, `supply chain agent`, `delivery mcp` — the last two now return AI-security
scanners and Claude skill packs far more often than retail tooling.

### Agent-layer measurements that came back empty (2026-11-23)

Written down because an informed gap is information and silence is not:

- `logistics mcp stars:>=20` → **4 repos worldwide**. One is on-plane and unlicensed (ATLAS), one is a
  3D warehouse digital-twin demo, one is the LATAM pack, one is an African API registry.
- `supply chain agent stars:>=100` → 11, of which the top results are a security scanner
  (`NVIDIA/SkillSpector`, 27,310★) and marketing skill packs. **No autonomous supply-chain agent.**
- `delivery route planning stars:>=100` → 1, and it is a dump of a W3C report. Zero real.
- There is **no agent anywhere that promises a delivery date.** The ATP step has no agent layer
  because it has no library layer either (see `repos/foundations.md`).

## Added 2026-11-26 (pass 7) — the merchandise planning, buying & trade-funds plane

The plane upstream of price (pass 5) and fulfilment (pass 6): assortment → space → size curve →
allocation → open-to-buy → purchase order → vendor-funded promotion → claim settlement. This is the
buying office, where a retail engagement usually starts.

**Read the star counts before the descriptions.** Every agent-shaped repo in this plane was verified on
2026-11-26 via a single batched `search/repositories` call (`repo:a/b repo:c/d …`, which returns stars,
forks, last push and SPDX together, so the fields cross-check). The result is the thinnest agent layer
measured in this KB so far.

| Agent | Repo | License | Stars | Last push | What it actually is |
|---|---|---|---|---|---|
| Responsive AI Clusters in Supply Chain | https://github.com/Appointat/Responsive-AI-Clusters-in-Supply-Chain | Apache-2.0 | 40 | 2024-03-28 | Multi-agent supply-chain coordination. The highest-starred agent in the plane **and abandoned for over two and a half years**. Read as a design reference only. |
| supplypilot-agent | https://github.com/lxingwei81-ux/supplypilot-agent | MIT | 2 | 2026-09-20 | Control-tower agent: demand forecast, multi-level BOM, inventory projection, ATP allocation, procurement approval tracking. README largely in Chinese. Its own README warns the business formulas must be checked against real company policy and audit requirements. |
| agentic-supply-planning | https://github.com/kavya2693/agentic-supply-planning | MIT | 0 | 2026-10-08 | LangGraph supervisor + four agents (demand, inventory, purchase orders, workflow). Large or urgent POs pause for planner approval; every agent step is written to an audit log. Synthetic lubricants data. **The approval-gate and audit-log shape is the reusable idea here**, not the domain content. |
| trade-promotions-for-claude-code | https://github.com/Enterprise-DNA-OS/trade-promotions-for-claude-code | MIT | 0 | 2026-10-18 | A trade-promotion system that is "just a database and Claude Code": commands to propose, agree and match claims to promotions. **The only MIT-licensed trade-promotion artifact that exists.** Treat as a schema sketch, not a dependency. |
| supply-chain-agent | https://github.com/mraisback/supply-chain-agent | **NONE** | 0 | 2026-08-31 | Multi-agent demand planning / inventory / network design / procurement. **No license file → all rights reserved. Not usable, at any scale, for any client.** Listed so nobody re-finds it and assumes otherwise. |
| Supply-Chain-Demand-Agent | https://github.com/shiva-shivanibokka/Supply-Chain-Demand-Agent | **NONE** | 0 | 2026-10-08 | Agentic RAG pipeline, 30-day part demand over synthetic data. **No license file → unusable.** |
| Supply-Chain-Agent | https://github.com/praditya7/Supply-Chain-Agent | **NONE** | 0 | 2026-09-28 | Capacitated facility-location + customer-allocation agent. Its own README says it is not meant for enterprise scale. **No license file → unusable.** |

That is the whole population: **seven repos, 42 stars between them, and the only one above 2 stars has
been dead since March 2024.** Three of the seven have no license file at all.

### The licence check that produced the "NONE" rows, and why it is trustworthy

A 404 on a raw license URL is **never on its own** proof that a license is missing — that was the lesson
from the media KB, where two repos looked unlicensed because their grants sat in `license.txt`
(lower-case) and `COPYING.md`. So each "NONE" above was established with a **control request**:

- probe seven license filenames (`LICENSE`, `LICENSE.md`, `LICENSE.txt`, `license.txt`, `LICENCE`,
  `COPYING`, `COPYING.md`) across both `main` and `master` → all 404, **and**
- fetch `README.md` on the same branch → **200**.

A README that resolves while every license name 404s is not a naming-convention failure and is not
throttling: the file genuinely is not there. All five no-license repos in this pass (three agents above,
two tools in `repos/foundations.md`) were confirmed this way.

### Explicitly not written here

`nickennethmichael/Procurement-AI-Agent` appeared in web search results as a procurement agent prototype,
but **did not resolve** in `search/repositories` when queried by slug. A search-result title is not an
existence proof, so it has no row. If a later pass resolves it, add it then.

## Added 2026-11-28 (pass 8) — the fresh & perishable food plane

**Plane opened this pass:** the perishable item — the food whose identity includes a *date*. Chosen by a
~75-term bounded vocabulary probe against the whole KB before any web search: `HACCP` 0, `FSMA` 0,
`critical tracking event` 0, `key data element` 0, `best before` 0, `use by` 0, `date code` 0, `lot code` 0,
`shelf life` 0, `spoilage` 0, `allergen` 0, `nutrition` 0, `catch weight` 0, `PLU` 0, `GDST` 0,
`cold chain` 1, `perishable` 1, `expiry` 1. Against `EPCIS` **30** and `DPP` **29** — meaning this KB
already knew the *wire format* for traceability and the *product-passport* layer, and had never once looked
at the food-specific layer that rides on them. Previous planes: product-data, store, retail media, returns,
price, fulfilment, merchandise planning.

**The agent layer here is real, permissive and alive — which makes it the exception in this KB.** Six
verified agent-surface repos below, five of them permissively licensed. Every other plane this KB has opened
produced an agent tier that was unlicensed, dead, or both.

| Agent / MCP server | Repo | Licence (file read, bytes) | Stars | Default-branch commit | What it actually does |
|---|---|---|---|---|---|
| OpenFoodFacts MCP (cyanheads) | [cyanheads/openfoodfacts-mcp-server](https://github.com/cyanheads/openfoodfacts-mcp-server) | Apache-2.0 — read, 11317 B | 2★ / 1f | 2026-11-24 | **Best-licensed and most recently active.** Barcode lookup, ingredient/nutrition filtered search, side-by-side comparison, and browsing the canonical tag vocabulary. STDIO or Streamable HTTP, so it drops into an agent runtime unchanged. |
| nutri-mcp | [charliezstong/nutri-mcp](https://github.com/charliezstong/nutri-mcp) | MIT — read, 1078 B | 5★ / 1f | 2026-01-12 (pushed 2026-10-29) | Widest data coverage: Open Food Facts **plus** USDA FoodData Central and Nutritionix behind one MCP surface. Open Food Facts needs no key; USDA is optional and improves micronutrients. |
| OpenFoodFacts MCP, offline | [noot-app/openfoodfacts-mcp-server](https://github.com/noot-app/openfoodfacts-mcp-server) | MIT — read, 1060 B | 2★ / 2f | 2026-06-11 (pushed 2026-07-01) | Queries a **local Parquet copy** of the product database through DuckDB. The only one that works with no network and no rate limit — the right choice for in-store or batch use. |
| Danish food-data MCP | [borgels/mcp-server-fooddata-dk](https://github.com/borgels/mcp-server-fooddata-dk) | **ISC** — read, 3768 B | 0★ / 0f | 2026-11-21 | Open Food Facts + the **DTU Frida** national composition database. A worked example of the regional pattern: one national dataset joined to the global one. GitHub reports `NOASSERTION`; the file is ISC and permissive. |
| OpenFoodFacts MCP (caleb-conner) | [caleb-conner/open-food-facts-mcp](https://github.com/caleb-conner/open-food-facts-mcp) | MIT — read, 1082 B | 1★ / 0f | 2025-08-06 | Barcode + filtered search, and the only one that interprets **Nutri-Score, NOVA and Eco-Score** rather than returning raw fields. Enforces Open Food Facts' published rate limits in code. ~15 months since a default-branch commit. |
| EUDR compliance agent | [nohosa001-pixel/eudr-compliance-agent](https://github.com/nohosa001-pixel/eudr-compliance-agent) | MIT — read, 1094 B | 0★ / 0f | 2026-11-25 | Agent wrapper over the EU Deforestation Regulation due-diligence workflow. **Permissively licensed and committed three days before this pass** — the deadline is 32 days away (see `intel/market.md`, EMEA). Read it as a starting point, not a compliance product. |

### ⚠️ The licence pattern this plane contributes: permissive wrapper, closed engine

[Vortx-AI/eudr-plugin](https://github.com/Vortx-AI/eudr-plugin) (0★, pushed 2026-11-26) has a real
Apache-2.0 LICENSE — **953 bytes, not the usual ~11,350**. The short form is not the finding. The finding is
what the file goes on to say, verbatim:

> This licence covers THIS REPOSITORY: the plugin manifest, the skills, and the MCP server declaration. It
> does not cover the eudr.dev service those files connect to, whose runtime is closed.

**This is a new licence shape for this KB, and it generalises to all twelve industries.** Previous rules
covered a badge that promises a licence that does not exist (pass 6) and an API flag that hides one that
does. This is a licence that is *entirely real and entirely honest* and still gives you nothing: it is
scoped to the thin wrapper, and the engine behind it is proprietary. **An MCP server is exactly the shape
that makes this invisible** — the manifest and the tool declarations are the open part, and the tools call
out. Before adopting any permissively-licensed MCP server, ask what runs *behind* the tool declaration. To
this repo's credit it says so in the licence file itself; most will not.

### The 'no licence file' rows, measured not assumed

Two agent-shaped repos in this plane are **unusable for want of a licence**, checked against ten filename
spellings (`LICENSE`, `LICENSE.md`, `LICENSE.txt`, `license.txt`, `LICENCE`, `LICENCE.txt`, `COPYING`,
`COPYING.txt`, `LICENSE-MIT`, `NOTICE`) on the default branch, reading **bytes** and not status codes:
`JagjeevanAK/OpenFoodFacts-MCP` (pushed 2026-02-03) and `AbhishekKhond005/Open-Food-Facts-MCP` (pushed
2026-10-23, self-described hackathon build). Neither gets a row.

### Explicitly not written here

- **`MrBridgeHQ/open-food-facts-mcp`** was described in search results with a full feature list — read-only
  server, TypeScript, English and French docs, "not affiliated with Open Food Facts". It **does not exist**:
  `git ls-remote` returns the auth-prompt 404 signature. A detailed search-result description is not an
  existence proof, and this is the second dead slug this KB has caught being described in confident prose
  (pass 6 caught `hotwax/poorti`).
- **No official Open Food Facts MCP server.** All six above are third-party. Open Food Facts itself ships
  API clients (`openfoodfacts-dart`, Apache-2.0; `openfoodfacts-python`, **no licence file** — see
  `repos/foundations.md`), not an agent surface. If a client engagement needs one that is answerable to the
  upstream project, it does not exist and would have to be contributed.
- **No agent for the cold chain, the markdown decision, or HACCP record-keeping.** Those are measured zeros,
  written up in `repos/foundations.md` rather than guessed at here.
