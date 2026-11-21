---
industry: retail
region: Global
updated: 2026-11-21
---

# 🧩 Composition Patterns — Retail & Consumer

> Concrete recipes: named repos, named licences, and how to wire them. Every repo referenced here is
> verified in `agents/top.md`, `repos/foundations.md` or `verticals/solutions.md` as of 2026-11-21.
>
> *This file previously contained a single "Receta 1: [Por definir]" stub with every field set to an
> em-dash.*

## Pattern 1 — Agent-reachable storefront (the flagship)

**Problem it solves:** the measured asymmetry in `intel/trends.md` #2 — consumers are using shopping
agents, but the merchant cannot be transacted with. In LATAM this was measured across 75 sites: agents can
browse, but cannot buy.

```
[Medusa (MIT) | Saleor (BSD-3)]          ← permissive commerce core
          ↓ expose domain as typed tools
[MCP server: catalogue / inventory / cart / order]
          ↓ speak both standards
[NVIDIA Retail-Agentic-Commerce (Apache-2.0)]  → UCP + ACP endpoints
          ↓ payment + consent
[AP2 (Apache-2.0) mandate record] + [x402 (Apache-2.0) if per-request billing]
          ↓
[Reachable from ChatGPT (ACP) and Google/Microsoft surfaces (UCP)]
```

**Wiring notes.** Do not implement UCP or ACP from the spec by hand — start from the NVIDIA blueprint,
which is the only Apache-2.0 implementation of both, then replace its catalogue adapter with your
Medusa/Saleor adapter. Keep the MCP tool layer separate from the protocol layer: the protocols will churn,
your domain tools will not. Put a human approval gate on anything that changes price or moves money, and
persist the AP2 mandate alongside the order — that record is the audit artefact.

**Effort:** the protocol layer is days, not months. The real work is the domain tool layer.

## Pattern 2 — Merchandising & demand planning agent

**Stack:** `Nixtla/statsforecast` (Apache-2.0) → `Nixtla/neuralforecast` (Apache-2.0) →
`LarrySnyder/stockpyl` (MIT) → `Canner/WrenAI` (Apache-2.0) as the analyst-facing surface.

```
[ERP: Odoo (LGPL-3.0) or ERPNext (GPL-3.0)]  ← sales + stock history
          ↓
[StatsForecast baseline]  ──compare──  [NeuralForecast models]
          ↓ forecast
[stockpyl: reorder points, safety stock, multi-echelon]
          ↓
[WrenAI GenBI agent]  ← planner asks in natural language, gets SQL-grounded answers
```

**Wiring notes.** Always ship the StatsForecast baseline first and keep it in production alongside the
neural model — in demand planning the statistical baseline frequently wins, and having both is what makes
the comparison honest to a client. **Odoo's LGPL-3.0 is the key enabler here**: your forecasting module can
stay proprietary. Under ERPNext's GPL-3.0 it cannot, so if the client wants to own the IP, choose Odoo.

## Pattern 3 — Personalisation / recommendation service

**Stack:** `Tracardi` (MIT) → `gorse-io/gorse` (Apache-2.0) → `qdrant` (Apache-2.0), with
`recommenders-team/recommenders` (MIT) for offline evaluation.

```
[Tracardi CDP (MIT)]  ← unify web/app/WhatsApp identity into one profile
          ↓ events
[Gorse (Apache-2.0)]  ← classical + LLM rankers, multimodal embeddings
          ↓ candidates          ↘
[Qdrant (Apache-2.0)]  ← semantic/visual similarity over product catalogue
          ↓
[Ranked slate → storefront + agent tool]
```

**Wiring notes.** Use `recommenders-team/recommenders` **offline** to benchmark Gorse against established
baselines before claiming a lift; it is the reference corpus and it keeps the engagement defensible.
**Choose Qdrant over Meilisearch** for this layer: Meilisearch's Enterprise Edition parts are BUSL-1.1,
whereas Qdrant is wholly Apache-2.0. Use `Surprise` (BSD-3) only as a sanity baseline — it has no
implicit-feedback support.

## Pattern 4 — LATAM conversational checkout (the regional play)

**Problem it solves:** the highest-evidence regional gap in this KB — WhatsApp reach of 82–91% with
e-commerce at 17.7% of retail sales in Mexico, and agents unable to complete purchases.

```
[WhatsApp Business channel]
          ↓ intent
[Shopping agent — start from anthropics/commerce-agents (Apache-2.0)]
          ↓ typed tools
[MCP over Medusa (MIT) or PrestaShop modules (AFL-3.0)]
          ↓ checkout
[Pix — client generated from bacen/pix-api at build time]
          ↓ consent
[AP2 mandate record (Apache-2.0)]
```

**Wiring notes and honesty requirements.** `bacen/pix-api` has **no LICENSE file** (verified across 3
branches × 8 filenames): generate the client from the spec during the build, never vendor the spec text
into a client deliverable, and say so up front. For PrestaShop (common in LATAM) write **modules** under
AFL-3.0 rather than patching the OSL-3.0 core. Confirm the CADE/WhatsApp third-party-chatbot opening
against primary sources before making it load-bearing in a proposal.

## Pattern 5 — EMEA AI Act Article 50 compliance layer

**Problem it solves:** a dated, immediate obligation — Article 50 in force since 2026-08-02, transitional
deadline **2026-12-02** for systems already on the market.

```
[Existing storefront + chatbot + generative product imagery]
          ↓ inventory every AI touchpoint
[Disclosure registry: which system, which surface, what output]
          ↓
[Runtime labelling: chatbot "you are talking to an AI"; synthetic imagery marked]
          ↓
[Per-decision event log → evidence pack]
```

**Wiring notes.** This is deliberately not an AI problem — it is an inventory-and-labelling problem, which
is why it scopes fast and sells now. Build the per-decision event log as the same component Pattern 1 uses
for AP2 mandates; one audit spine serves both the payment-consent and the AI-transparency obligation. Carry
the honest caveat from `intel/market.md`: Article 50 labelling is the near-term certainty, high-risk
classification was postponed to 2027–2028, and some analyses hold that direct obligations fall on the
system's *provider* rather than a pure retailer.

## Pattern 6 — Competitive pricing intelligence (with the gap stated)

**Stack:** `apify/apify-mcp-server` (MIT) + `YosefHayim/ebay-mcp` (MIT) → your own optimiser.

```
[Apify MCP (MIT)]  ← competitor catalogue + price pages as typed tools
[eBay MCP (MIT)]   ← live marketplace comparables
          ↓
[Normalisation + product matching]   ⚠️ NO OPEN-SOURCE OPTION — see below
          ↓
[Markdown / promo optimiser]         ⚠️ NO OPEN-SOURCE OPTION — build as IP
          ↓
[Merchandising agent proposes, human approves]
```

**Wiring notes.** Be explicit with the client that two boxes in this diagram have **no open-source
floor**: `product matching entity resolution stars:>=200` returns 0 results, and `price optimization
stars:>=100` returns no retail repos at all. That is not a failure of the search — it is why this pattern
is the best place to build proprietary Globant IP. Also respect robots/ToS on collection; Apify handles the
mechanics but not the client's legal exposure.

## Anti-patterns — learned the hard way in this KB

- **Do not trust a star count carried in a rotation note.** Three cycles recorded Gorse at 12.5k (really
  9,928) and RecBole rising to 7.2k (really 4,620, and dormant since 2025-02-24). Re-measure; stars and
  `pushed_at` arrive in the same API call.
- **Do not infer a licence from a listicle or from a GitHub org's reputation.** Meilisearch is not MIT,
  Vendure is not MIT, and `visa/trusted-agent-protocol` is not open source despite living under Visa's org.
- **Do not fork nopCommerce for white-label retail.** Its licence demands a visible "powered by
  nopCommerce" link on *every* UI screen.
- **Do not link `apache/ofbiz`** — archived since 2020. Use `apache/ofbiz-framework`.
- **Do not let keyword ingest write the agents table.** This KB shipped a **Minecraft hopper mod** as a
  retail inventory agent, and the "ecommerce mcp" queries are heavily polluted with Claude-Code
  marketing/SEO skill packs that are not retail tooling at all.
- **Do not build on a retail agent because it exists.** Only 2 retail agents worldwide were created in the
  last ~6 months with ≥50 stars. Build at the typed-access layer instead.
