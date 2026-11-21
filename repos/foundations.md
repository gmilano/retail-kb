---
industry: retail
region: Global
updated: 2026-11-21
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
