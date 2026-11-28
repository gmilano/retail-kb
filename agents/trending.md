---
industry: retail
region: Global
updated: 2026-11-28
---

# 📈 Agents Trending — Retail & Consumer

> **Append-only.** Newest dated section on top; history preserved below. This file tracks **agents and
> agent-facing tooling**. For infrastructure and platform repos see `repos/trending.md` — until today the
> two files were byte-identical, so the agents/repos distinction never actually existed in this KB.

## 2026-11-28 (pass 8) — the fresh & perishable food plane

**This week's signal is an inversion of the last seven passes: the agent tier in this plane is the healthy
part.** Six verified agent surfaces, five permissively licensed (Apache-2.0, ISC, 3× MIT), two with
commits in the last five days. Compare pass 7's buying plane — seven repos, 42 stars, three unusable for
want of a licence. The difference is not maturity, it is **that a public dataset exists to wrap**: Open
Food Facts (1,220★, AGPL-3.0, pushed 2026-11-28, the day of this pass) has produced at least eight
third-party MCP servers, while the buying office has no public dataset and produced none.

**Freshest this week:** `cyanheads/openfoodfacts-mcp-server` (Apache-2.0, 2★, **2026-11-24**),
`borgels/mcp-server-fooddata-dk` (ISC, 0★, **2026-11-21**), `nohosa001-pixel/eudr-compliance-agent`
(MIT, 0★, **2026-11-25**), `Vortx-AI/eudr-plugin` (Apache-2.0 scoped, 0★, **2026-11-26**).

**Two of those four are EUDR agents committed in the last three days**, against an EU deadline of
**30 December 2026 — 32 days from this measurement**. That is the clearest instance this KB has recorded of
*a date producing code*: see `intel/trends.md` for the full version of the claim and the falsifiable
prediction attached to it.

**New licence shape, and it is an MCP-specific trap:** `Vortx-AI/eudr-plugin` carries a genuine Apache-2.0
file of **953 bytes** (the full text is ~11,350) whose closing paragraph states that it covers the manifest,
skills and MCP declaration only — *"the eudr.dev service those files connect to, whose runtime is closed"*.
A permissively-licensed MCP server can be an open wrapper on a closed engine, and the manifest is exactly
where that is invisible. Recorded in `agents/top.md` as a rule for all twelve industries.

**Measured empty this week, and these are the useful zeros:** no agent for the **cold chain**, none for the
**markdown decision**, none for **HACCP record-keeping**, and **no official Open Food Facts MCP server** —
all eight are third-party. `MrBridgeHQ/open-food-facts-mcp` was described in search results feature by
feature and **does not exist** (`ls-remote` 404 signature) — the second confidently-described dead slug this
KB has caught, after pass 6's `hotwax/poorti`.

## 2026-11-26 (pass 7) — the merchandise planning, buying & trade-funds plane

**The headline is a zero.** Every agent-shaped repo in the buying/planning plane, verified today:
`Appointat/Responsive-AI-Clusters-in-Supply-Chain` (Apache-2.0, 40★, **dead since 2024-03-28**),
`lxingwei81-ux/supplypilot-agent` (MIT, 2★, 2026-09-20), `kavya2693/agentic-supply-planning` (MIT, 0★,
2026-10-08), `Enterprise-DNA-OS/trade-promotions-for-claude-code` (MIT, 0★, 2026-10-18),
`mraisback/supply-chain-agent` (**no license**, 0★), `shiva-shivanibokka/Supply-Chain-Demand-Agent`
(**no license**, 0★), `praditya7/Supply-Chain-Agent` (**no license**, 0★).

**Seven repos, 42 stars, three unusable for want of a license file.** [measured 2026-11-26]

What moved this week is not the agents — it is the **curated lists**. Three appeared or were refreshed in
the last six weeks (`Awesome-Retail-Assortment-Planning` MIT 6★ pushed 2026-11-16,
`Awesome-Retail-Merchandising-Cloud` MIT 0★ 2026-10-11, `Awesome-Consumer-Goods-CRM` MIT 0★ 2026-10-12),
plus `kishorkukreja/awesome-supply-chain` (MIT, 102★, 2026-10-06), which ships **agent skills** for Claude
Code and Codex including a planogram-optimization skill. Somebody is actively mapping this plane and
almost nobody is watching. Lists are appearing faster than implementations — read that as demand without
supply, which is the buy signal, not the warning.

**Contrast worth keeping:** on the agentic-commerce side `google-agentic-commerce/AP2` alone holds 3,286★
under Apache-2.0. The sell side of retail has three well-starred Apache-2.0 protocols; the buy side has
42 stars in total. Attention is going to the checkout, not the buying office.

**One agent pattern is worth stealing even at 0★:** `agentic-supply-planning` gates large or urgent
purchase orders on explicit planner approval and writes every agent step to an audit log. That shape —
agent proposes, human approves above a threshold, every step auditable — is what makes a planning agent
deployable in a buying office. Take the shape, leave the lubricants data.

## 2026-11-23 (pass 6) — the fulfilment plane

**Plane opened this pass:** everything after the money moves — promise, pick, label, route, prove.
Chosen because the five planes already in this KB (product data, store, retail media, returns, price)
all stop at checkout, and the reverse flow was mapped in pass 4 while the *forward* flow never was.

**New agent rows (all verified by `git ls-remote` + raw-file licence read, 2026-11-23):**

| Agent / repo | License | Stars | Last push | Why it is here |
|---|---|---|---|---|
| https://github.com/codespar/mcp-dev-latam | MIT | 279 | 2026-11-13 | Carrier labels, shipping quotes and tracking as MCP tools for 6 LATAM countries — the step that measures as **zero worldwide** |
| https://github.com/beckn/beckn-onix | MIT | 101 | 2026-11-19 | Reference node for the Beckn network behind ONDC's Open Delivery Protocol |
| https://github.com/GoogleCloudPlatform/dpi-accelerator-beckn-onix | Apache-2.0 | 11 | 2026-11-13 | Google Cloud deployment path for the above |
| https://github.com/Shopify/active_fulfillment | MIT | 155 | 2024-09-24 | Carrier-neutral fulfilment-service library; **dormant 2 years**, reference only |
| https://github.com/kraenhansen/nemlig-mcp | MIT | 42 | 2026-10-15 | Small worked example of an agent booking a grocery delivery slot (Denmark) |
| https://github.com/cargofy/ATLAS | **none — badge lies** | 20 | 2026-03-06 | Only logistics-specific MCP server found; Apache badge, no licence file on any branch |

**What moved on the protocol layer since cycle 8 (re-measured, not assumed):**

| Repo | Cycle 8 | 2026-11-23 | Delta |
|---|---|---|---|
| Universal-Commerce-Protocol/ucp | 3,515 | 3,517 | +2 |
| agentic-commerce-protocol | 1,607 | 1,609 | +2 |
| google-agentic-commerce/AP2 | 3,281 | 3,283 | +2 |
| anthropics/commerce-agents | 3,497 | 3,502 | +5 |
| NVIDIA-AI-Blueprints/Retail-Agentic-Commerce | 89 | 89 | 0 |
| Shopify/ucp-cli | 84 | 84 | 0 |

Two days, near-zero movement. Recorded because cycle 8 caught *fabricated* growth curves in this KB;
a flat, boring, re-measured delta is the evidence that this pass did not invent one.

**⚠️ The headline agent finding is a defect, not a repo:** the two agentic-commerce protocols type a
delivery timestamp pair that **means different things**. ACP types `earliest_delivery_time` /
`latest_delivery_time` (when the shopper *receives* it). UCP types `earliest_fulfillment_time` /
`latest_fulfillment_time` (when the merchant *hands it off*). Any adapter that maps one onto the other
silently drops the entire transit time from the promise. Details and file paths in `intel/trends.md`.

**Collision caught this pass:** `fulfillment agent` is a Dialogflow term. Four of the five repos it
returns are chatbot webhook libraries. Third industry-word collision in this KB after "hoppers" and
"returns".

## 2026-11-23 (pass 5) — the price plane

**Plane opened this pass:** the price itself. Chosen by a 46-term vocabulary probe
against all eight KB files **before** any web search: `elasticit`, `dynamic pric`,
`competitor pric`, `price scrap`, `unit price`, `drip pricing`, `shrinkflation`,
`algorithmic collusion`, `personalized pricing`, `clearance`, `revenue
management`, `coupon`, `bundl` and `cross-sell` were all at **literal zero**. The
19 hits for `markdown` were the file format.

**New and alive in the agent layer — two repos, and the smaller one matters more:**

| Agent / repo | License | Stars | Last push | Why it is here |
|---|---|---|---|---|
| [offerkit/offerkit](https://github.com/offerkit/offerkit) | MIT (1073 B read) | 58★/173 refs | 2026-11-20 | Agent-**first** promotion engine, not agent-adapted: the MCP server is a first-class surface and **every mutating endpoint declares a risk level** (`safe`/`mutating`/`destructive`) so the LLM host renders the right confirmation. The design pattern is worth more than the code. |
| [zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance) | MIT (1064 B read) | **0★**/21 refs | 2026-11-22 | One day old. The **only** code implementation of a pricing *duty* found in any region: Omnibus 30-day reference price, unit prices, personalised-pricing disclosure. Append-only price history that never edits a recorded price. |

**This pass corrected two of this KB's own claims**, both produced by a single
GitHub query each and then quoted as fact by four later sections:
`entity resolution record linkage stars:>=500` **still returns 0** while `splink`
(MIT 2594★), `dedupe` (MIT 4531★) and `zingg` (AGPL 1275★) all exist — the fifth
measured search false negative here; and retail elasticity **does** have a
permissive floor in `pymc-marketing`'s `customer_choice/bayesian_blp.py`
(Apache-2.0, 1314★), documented for *"Nielsen / IRI / retailer-scanner"* panels.

**No pricing-agent boom — measured.** `pricing agent created:>2026-06-01
stars:>=20` returns **36 repos and zero retail pricing agents** (App Store PPP
updaters, trading agents, an agent-authorization gateway, startup skill packs).
`competitor monitoring stars:>=50` → **2**, neither retail.
`price intelligence stars:>=20` → **23**, whose two most on-topic hits are
Microsoft's dead Cortana solutions (2017 and 2023).

**The week's sharpest trap — collision *inside* a correct dependency.**
`pymc-marketing` contains `mmm/price_response.py`, which a grep for *elasticity*
finds and which prices a **delivered media unit** (auction bid-up, rate-card
tiers), not a retail product. Cycle 8 shipped a Minecraft hopper mod as inventory
intelligence by matching a *repository* name; this is the same error one level
down, matching a *file* name inside an excellent repo. Read the docstring.

**Contamination, third family in the pricing vocabulary.** `pricing engine
stars:>=200` returns a Unity text engine (`LightSideKittens/UniText`, 720★) and
two Claude/Codex **marketing skill packs** (`Yuzzyuk/marketing-os` 580★,
`holy-templar/marketing-agi` 243★). Cycle 8 caught this family in `ecommerce mcp`;
it has spread. Excluded deliberately.

**Dormancy / licence check on what gets recommended:**
`ivorpad/mercadona-cli` (338★, self-described *"agent-friendly"* grocery CLI) has
**no licence file** on `main`; `flix-tech/RevPy` (MIT, 50★) dead **2023-07-06**
and airline-oriented; `Azure/cortana-intelligence-price-analytics` (MIT, 38★) dead
**2023-06-27**; `Azure/cortana-intelligence-price-optimization` (90★) dead
**2017-09-05** and **no licence file**.

---

## 2026-11-23 — the returns & recovery plane

**Plane opened this pass:** retail's reverse flow (prevent → authorise → move →
grade → decide → recover/detect). Chosen by vocabulary probe, not by web
search: `RMA`, `returns fraud`, `routing`, `BOPIS` and `takeback` were all at
**zero mentions** across all eight KB files this morning.

**What is new and alive in the agent layer — all two of it:**

| Agent / repo | License | Stars | Last push | Why it is here |
|---|---|---|---|---|
| [budna-marketplace/recommerce](https://github.com/budna-marketplace/recommerce) | MIT | 16★/1f | 2026-11-09 | Agent skills for comparing new vs pre-owned items. The only agent-shaped recommerce artifact in open source. |
| [Pragatheswar-72/support-agent](https://github.com/Pragatheswar-72/support-agent) | MIT | 6★/4f | 2026-07-01 | LangGraph orchestrator routing to specialist support agents. A shape to copy, not a dependency. |

**The week's sharpest measurement — the keyword collision that nearly produced
fake rows.** `returns agent` returns **2464 repos and zero relevant ones**; its
top hit at 162★ is a Brainfuck web app that *"returns your user-agent to you"*.
`returns management` returns **3134 repos**, all portfolio analytics and library
lending. In this industry the word "returns" is genuinely ambiguous — it also
corrupted a KPMG APAC statistic, where *"returns exceeding 10% from AI
initiatives"* means **return on investment**, not merchandise. Search
`RMA` / `reverse logistics` / `disposition` instead.

**Dormancy check on what the listicles recommend:** `safe-graph/DGFraud`
(Apache-2.0, 766★) last pushed **2022-04-20**; `safe-graph/UGFraud`
(Apache-2.0, 134★) **2022-04-18**; `bcmi/DCI-VTON-Virtual-Try-On` (MIT, 508★)
**2023-12-06**. All three are still presented as current options for returns
fraud and try-on. They are not.

**Measured empty (2026-11-23):** `disposition engine` → 22 repos, 0 relevant ·
`takeback trade-in` → **0 repos** · `liquidation deadstock` → 1 repo, 0★ ·
`refund agent llm` → nothing on topic above 9★. The agent that *decides* a
return's fate does not exist in open source.

## 2026-11-22 (pass 3)

**Plane added this pass: retail media — agents that buy and sell advertising.**
"Retail media", "advertising" and "clean room" had **zero hits across all eight
files** before today.

**New this week — agentic advertising became buildable.**

- **[prebid/salesagent](https://github.com/prebid/salesagent)** — Apache-2.0
  (10767B), 2354 refs, last commit **2026-11-23 (0d — landed during this
  pass)**. Implements the **AdCP sales-agent role**: exposes ad inventory to AI
  agents over **MCP and A2A**, 16 AdCP tools, Google Ad Manager integration,
  multi-tenant isolation. Self-declared **alpha**; `v2.0.0` introduced breaking
  changes. Pins the `adcp` SDK exactly with a CI guard that fails on drift.
- **[adcontextprotocol/adcp](https://github.com/adcontextprotocol/adcp)** —
  Apache-2.0 (10767B), **8610 refs**, last commit **2026-11-22 (0d)**. The
  protocol itself: discovery, media buying, creative, audience activation,
  reporting, carried over MCP + A2A. Ships `CHARTER.md` and `IPR_POLICY.md`.
  Launched by an adtech coalition in Oct 2025 at v2.0.0; docs now at v3.2.x.
- **[Setupad/salesagent](https://github.com/Setupad/salesagent)** — Apache-2.0
  (10767B), 10 refs, 2026-10-19 (34d). A second independent implementation of
  the sales-agent role.

**The rival standard is a README.**
[IABTechLab/AAMP](https://github.com/IABTechLab/AAMP) — Apache-2.0 (11356B),
**5 refs**, 2026-09-22 (61d) — contains **exactly two files, `LICENSE` and
`README.md`, and one commit.** Trade press describes AdCP and AAMP as rivals
splitting the industry; the repositories are 8610 refs against 5. This measures
GitHub presence, not whether a spec document exists elsewhere — but you cannot
build against AAMP from GitHub today. The AdCP FAQ states the two are **not
wire-compatible**. Prediction to score later: if AAMP is real competition it
gains implementation code before **2027-05-22**.

**Dormancy correction — Robyn is not alive, and its branch hides it.**
[facebookexperimental/Robyn](https://github.com/facebookexperimental/Robyn)'s
**default branch is `accuracy/allocator_v2_fixes`**, a feature branch last
touched 2024-11-21. Its `main` is **2025-06-27 — 513 days dormant.** 2026 MMM
commentary still lists it as one of two "open-source giants" beside Meridian.
A plain `git clone` gets the stale feature branch; default-branch tooling
reports a wrong 731 days. **Measure `main` by name.**

**Slug hygiene:** `adcontextprotocol/salesagent` = `prebid/salesagent` —
identical HEAD `dcd14d0f`, identical 2354 refs, therefore one repo under a
redirect, not two. Canonical: `prebid/salesagent`.

**Keyword collision, reproduced live:** `retail media network stars:>=10`
returns three repos and **all three are Windows-7/Minecraft DxDiag dumps**
(`dovnel/Win-7`, `denman2328/Help`, `Camus777/Minecraft`). Same failure mode as
cycle 8's Minecraft hopper mod shipped as retail inventory intelligence.
Nothing from that query was written as data.

## 2026-11-22 (pass 2)

**Theme: there is no store-operations agent — the agent surface over the store is an MCP server bolted to
the ERP.** Earlier today this file tracked the agent layer above the *catalogue*. The measurement that
matters now is that the agent layer above the *store* does not exist as agents at all; it exists as
wrappers around Odoo and ERPNext, because that is where the till, the stock ledger and the country tax
localisation already live. All rows measured 2026-11-22.

| Movement | Repo | License | ★ / forks | Last push | Why it is trending |
|---|---|---|---|---|---|
| New to this KB | [ivnvxd/mcp-server-odoo](https://github.com/ivnvxd/mcp-server-odoo) | **MPL-2.0** (LICENSE 16725 B) | 419★ / 190f | **2026-11-22 (same day)** | The strongest store-plane agent surface in open source. Exposes Odoo models over MCP, which means POS sessions, stock moves, pricelists and `l10n_*` fiscal modules. MPL-2.0 is file-level copyleft — new files stay proprietary. |
| New to this KB | [marcfargas/odoo-toolbox](https://github.com/marcfargas/odoo-toolbox) | **LGPL-3.0** (7652 B) | 44★ / 116 refs | 2026-10-26 | TypeScript SDK + CLI + MCP server + skill modules, CI-tested against live Odoo. The TS-stack counterpart to the row above. |
| New to this KB | [hachecito/odoo-mcp-improved](https://github.com/hachecito/odoo-mcp-improved) | MIT (1072 B) | 49★ / 6f | 2026-11-18 | Sales- and stock-specific MCP tools rather than generic model access. |
| New to this KB | [nasroykh/foxmayn_frappe_cli](https://github.com/nasroykh/foxmayn_frappe_cli) | MIT | 16★ | 2026-11-11 | Frappe/ERPNext CLI, MCP server and desktop app. Small, permissive, current. |
| **Maintenance alert** | [rakeshgangwar/erpnext-mcp-server](https://github.com/rakeshgangwar/erpnext-mcp-server) | MIT (1071 B) | 131★ / 12 refs | **2026-04-25 (211 days)** | The best-known ERPNext MCP server has not moved in seven months. Usable, not maintained — and ERPNext is where the India GST localisation lives. |
| **Licence alert** | [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | **AGPL-3.0** (34523 B) | 63669★ / 12024f | 2026-11-22 | Not new, but newly relevant: every shelf-vision repo surfaced by search is built on it, so **the entire visible open-source shelf-vision corpus is AGPL-derived.** The network clause reaches a hosted store-analytics service. |
| **The permissive alternative** | [roboflow/supervision](https://github.com/roboflow/supervision) | **MIT** (LICENSE.md 1065 B) | 51699★ / 4964f | 2026-11-20 | Detector-agnostic tracking, polygon zones, line counters. The reason a licensable store-vision build is possible at all — see `compose/patterns.md` Pattern 12. |
| **Tool, not agent** | [TimefoldAI/timefold-solver](https://github.com/TimefoldAI/timefold-solver) | **Apache-2.0** (11358 B) | 1879★ / 244f | 2026-11-20 | Listed here because the correct use is *as an agent's tool*: solver for feasibility, agent for negotiation. Maintained successor to OptaPlanner (3512★), whose own description now redirects elsewhere. |

**Per-row audit of claims made about the agent layer this week:** 8 of 8 rows verified by `ls-remote` for
existence and by reading the licence file at source. Four repos whose GitHub API licence field reads
`NOASSERTION` were resolved to real licences by reading the file — none of them was actually unlicensed.

**Measured empty, and recorded as empty:** `retail execution store audit mobile stars:>=5` → **0 results
worldwide**. The store-task-execution category that Yoobic, Zipline and Flip sell into has no open-source
entry point at any star threshold. `order management fulfillment stars:>=100` → **0**.
---

## 2026-11-22

**Theme of the week: the catalogue, not the checkout.** Last week's section tracked protocol
implementations. This week the measurement that matters is that the agent layer *above* the catalogue is
one repo wide.

| Movement | Repo | License | ★ / forks | Last push | Why it is trending |
|---|---|---|---|---|---|
| New to this KB | [NVIDIA-AI-Blueprints/Retail-Catalog-Enrichment](https://github.com/NVIDIA-AI-Blueprints/Retail-Catalog-Enrichment) | Apache-2.0 | 47★ / 26f | 2026-11-18 | Pushed four days before this pass. NVIDIA now ships **both** halves of agentic retail: the commerce agent (`Retail-Agentic-Commerce`, 89★, pushed 2026-11-20) and the catalogue enrichment that feeds it. The only `catalog enrichment ai stars:>=20` result worldwide. |
| New to this KB | [gs1/GS1_DigitalLink_Resolver_CE](https://github.com/gs1/GS1_DigitalLink_Resolver_CE) | Apache-2.0 | 65★ / 45f | 2026-11-02 | The standards body itself maintains a permissive resolver — the inverse of what this KB's media pass found, where the standards bodies' code was unlicensed or closed. Directly usable as an agent tool. |
| **Maintenance alert** | [agentic-commerce-protocol](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) | Apache-2.0 | 1610★ | **2026-07-18 (127 days)** | ACP's default branch has not moved in over four months, and its product-feed RFC is still marked `Status: Proposal / Version: unreleased`. Stars kept rising; the repo did not. |
| **Maintenance alert** | [google-agentic-commerce/AP2](https://github.com/google-agentic-commerce/AP2) | Apache-2.0 | 3283★ | **2026-06-17 (158 days)** | The payment-mandate standard is the *most* dormant of the three. |
| Still alive | [Universal-Commerce-Protocol/ucp](https://github.com/Universal-Commerce-Protocol/ucp) | Apache-2.0 | 3516★ | 2026-11-21 | The only one of the three standards under active maintenance. |
| Active, unverified licence | [sodadata/soda-core](https://github.com/sodadata/soda-core) | `NOASSERTION` (not read) | 2463★ | 2026-11-22 | Logged because data contracts are the obvious vehicle for catalogue rules — and logged *with* its licence marked unresolved rather than guessed. |

*Per-row audit of the 2026-11-21 section below: all rows re-checked, none found dead. ACP and AP2 are
re-listed above because their **last-push dates** were not recorded yesterday and change the reading.*

## 2026-11-21

**Theme of the week: the official vendor agents arrived, and they are permissively licensed.**

| Agent / tool | Repo | License | Stars | Last push | Why it is trending |
|---|---|---|---|---|---|
| Shopify UCP CLI | [Shopify/ucp-cli](https://github.com/Shopify/ucp-cli) | MIT | 84 | 2026-11-09 | **New.** Shopify's own shopping skill for AI agents, and it is MIT. First-party commerce-platform agent code under a permissive licence is a genuine first. |
| NVIDIA Retail Agentic Commerce | [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce) | Apache-2.0 | 89 | 2026-11-20 | **New slug.** Reference implementation of **both** ACP and UCP — the only one found that covers both. Supersedes the `NVIDIA-RetailBlueprint` slug earlier cycles cited, which does not resolve. |
| Commerce Agents | [anthropics/commerce-agents](https://github.com/anthropics/commerce-agents) | Apache-2.0 | 3,497 | 2026-11-16 | Shopping **and merchant-side** agent blueprint with retail/telecom/entertainment examples. Now the best-documented starting point in the sector. |
| eBay MCP | [YosefHayim/ebay-mcp](https://github.com/YosefHayim/ebay-mcp) | MIT | 201 | 2026-11-20 | Live marketplace pricing and listings as agent tools — the comparables feed for a pricing agent. |
| Wocart | [bighadj22/Wocart](https://github.com/bighadj22/Wocart) | Apache-2.0 | 426 | 2026-11-16 | Permissive AI cart layer over the GPL WooCommerce estate — the clean way into the WordPress SMB install base. |
| CommerceAgentBench | [Accio-org/CommerceAgentBench](https://github.com/Accio-org/CommerceAgentBench) | Apache-2.0 | 1,310 | 2026-08-29 | Not new this week, but newly relevant: stateful replicas of real stores, so agent claims can be proven before a client trusts them. |

**Measured context — there is still no retail agent boom.** `retail agent created:>2026-06-01 stars:>=50`
returns **2** repos worldwide; `retail AI agent stars:>=100` returns **2**. What grew is the *protocol and
access* layer, not the agent population. Fourth industry in this rotation to measure the same thing.

**Negative result worth recording:** the `ecommerce mcp` / `commerce mcp` queries are now dominated by
Claude-Code **marketing and SEO skill packs** (`AgriciDaniel/claude-seo` 31,209★, `nexscope-ai/eCommerce-Skills`
1,474★, `CosmoBlk/email-marketing-bible`, `kangise/ecommerce-ai-skills`, `thatrebeccarae/claude-marketing`).
These are real and popular but they are content-marketing tooling, not retail agents. The media KB shipped
eight such repos as its headline agents before catching it — they are excluded here deliberately.

## History — 2026-07-02 (preserved verbatim; rows unverified at the time of writing)

> ⚠️ **Audited 2026-11-21.** This section was byte-identical to `repos/trending.md`, and most rows were
> 0-star noise rather than trending agents. Measured now: **`indmdev/indmshopbot` (listed first, "the best
> Telegram Shopping Bot") is a DEAD SLUG — refs=0**, as is **`Blakew316/shopconnect`**.
> `gz-yami/mall4j` is real (5,329★, AGPL-3.0, pushed 2026-11-16) and was correctly licensed here.
> `Jaal-Yantra-Textiles/v2` is 20★ and unlicensed; `AneeshYadav2419/multivendor-ecom` 1★ unlicensed;
> `MeaFew/shoplytics` 0★ (real slug is `MeaFew/Shoplytics`); `officialmrcoder/New-Mughal-Paint` 0★;
> `Svyatoslavpech/retail-ai-store-level-intelligence` 0★; `IFAKA/shelfops` 0★ and unlicensed. The
> `woocommerce` row's "?" licence is **GPL-2.0**. No row in this section was a retail *agent*.

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
