---
industry: retail
region: Global
updated: 2026-11-21
---

# 📡 Trends — Retail & Consumer

> What actually changed, with the evidence attached. Measurements marked **[measured]** come from GitHub
> search this pass and are reproducible; the rest are sourced claims with their source quality noted.

## 1. The protocol war is the story of the year, and all three standards are Apache-2.0

A year ago there was no standard way for an agent to complete a purchase. Now there are three, and they
are **all permissively licensed**: Google's **UCP** (3,515★, pushed today), OpenAI+Stripe's **ACP**
(1,607★), and Google's **AP2** for payment consent (3,281★), plus **x402** (6,820★) for HTTP-native
per-request payment. **[measured]**

The practical consequence: the integration work is unblocked by licensing but **blocked by fragmentation**.
The two biggest demand surfaces speak different protocols. Protocol-neutrality via
`NVIDIA-AI-Blueprints/Retail-Agentic-Commerce` (the only Apache-2.0 implementation of both) is a cheaper
bet than picking a winner.

## 2. Consumer adoption has decisively outrun merchant readiness

This is the sector's defining asymmetry, and it holds in every region:

- US: **74% of consumers have used an AI shopping agent** (CI&T), but only **~1.5% of US e-commerce** flows
  through agent platforms.
- EMEA: **95% of retailers using or testing AI, 5% achieving scalable ROI** (Retail Economics) — a 90-point
  execution gap.
- LATAM: a scan of **75 e-commerce sites** found agents **can browse but cannot buy**.

Demand is not the constraint. Merchant-side plumbing is.

## 3. The scarcity is typed access to commerce data, not agents — fourth industry running

**[measured]** This pass reproduces the finding that has now held across legal, financial, healthcare and
retail:

| Query | Results |
|---|---|
| `retail agent created:>2026-06-01 stars:>=50` | **2** worldwide |
| `retail AI agent stars:>=100` | **2** |
| `agentic commerce stars:>=50` | **46** |
| `ecommerce mcp stars:>=30` | **34** |
| `commerce mcp stars:>=30` | **30** |
| `product catalog mcp stars:>=5` | **9** |

There is no boom in new retail-vertical agents. There *is* a well-populated access layer. Build at the
typed-access layer — wrap catalogue, inventory, orders and pricing as MCP tools — and the agent becomes the
easy part.

**Retail differs from healthcare in one important way, though:** `agentic commerce` at 46 is a genuinely
larger permissive cohort than healthcare's equivalent, because retail has real *protocol* momentum behind
it rather than only individual connectors.

## 4. Permissive at the platform layer — the opposite of media

Retail's commerce platforms are genuinely permissive: Medusa (MIT), Saleor (BSD-3), Spree (BSD-3), Bagisto
(MIT), Shopware (MIT), Sylius (MIT). You rarely need to accept copyleft to ship a storefront.

The copyleft concentrates in **ERP/CRM** instead — and the single most commercially relevant fact in the
whole KB is that **Odoo is LGPLv3, not GPL**, so proprietary modules are permitted. That is widely
misreported.

## 5. "Open source" claims in this sector are failing license audit at a high rate

**[measured]** Of the platform/engine licences read this pass, these were materially misreported by public
sources or by earlier cycles of this KB:

- **Meilisearch** — carried as "MIT" by three cycles; actually `MIT AND OpenLDAP AND BUSL-1.1`.
- **nopCommerce** — AGPL **plus a mandatory "powered by nopCommerce" link on every UI screen**.
- **Vendure** — GPLv3 by default, routinely listed as MIT.
- **Twenty** — AGPL + per-file commercial EE + MIT SDKs; public sources said BSL-1.1 *or* GPLv3, both wrong.
- **PrestaShop** — two licences in one repo (OSL-3.0 core, AFL-3.0 modules).
- **visa/trusted-agent-protocol** — sits under Visa's GitHub org with a `LICENSE.md` that is a **pointer to
  Visa's proprietary developer terms**. Not open source at all.
- **Apache OFBiz** — the slug everyone links (`apache/ofbiz`) is **archived since 2020**.

Reading the licence file costs one HTTP request. Not reading it has twice put network-copyleft and
non-commercial terms into this KB as recommendations.

## 6. Agent-initiated payments became real infrastructure, not a demo

All three major US card networks now support agentic commerce; **Amex** shipped an ACE developer kit with
**purchase protection for registered agent purchases**; **Alipay launched AI Pay** in China to accept
payments from autonomous agents. AP2 exists specifically to carry the human's *mandate* for a purchase.

Implication for delivery: the consent/authorisation record is now the auditable artefact. An agent that
logs a per-decision mandate trail produces compliance evidence by construction — the same pattern that
made healthcare's Brazilian AI-governance requirement a sales filter rather than a blocker.

## 7. Regulation has become a regional design constraint with real dates

| Region | Instrument | Status |
|---|---|---|
| EMEA | EU AI Act **Art. 50** transparency | **In force since 2026-08-02**; transitional deadline **2026-12-02** |
| EMEA | Digital Omnibus on AI | High-risk deadlines **postponed to Dec 2027 / Aug 2028** |
| APAC | Singapore IMDA agentic AI governance framework | Published **Jan 2026**; covers delegation chains + multi-agent coordination |
| APAC | South Korea AI Basic Act | Effective **Jan 2026** |
| APAC | China | Registration + labelling mandatory; penalties to **¥50M** |
| LATAM | Brazil CADE / WhatsApp | Rival AI chatbots reportedly permitted from **2026-03-06** — *unverified* |
| North America | FTC / proposed "AI AGENT Act" | **Unverified** — secondary sources only; check primary sources |

## 8. Where the open-source floor is missing (and therefore where the margin is)

**[measured]** `price optimization stars:>=100` returns **zero retail** repos — the hits are energy market
optimisers and crypto MEV tooling. `retail demand forecasting stars:>=50` returns **2**, both student
projects. `product matching entity resolution stars:>=200` returns **0**. Shrink/loss-prevention surfaced
nothing in either channel.

Assortment, markdown and promotion optimisation is simultaneously the highest-value retail ML problem and
the one with no open-source starting point. That is the natural home for proprietary IP on top of a
permissive platform.

## Low-confidence items — flagged, not promoted

- The **$3–5T by 2030** agentic-commerce figure is McKinsey via second-hand citation; we did not reach the
  primary report.
- **India's ~33% consumer adoption / ~80% business exploration** is a single quoted expert estimate.
- All **LATAM WhatsApp figures** conflict between vendor sources (see `intel/market.md` warning).
- US regulatory claims could not be verified at all.
- The widely repeated "**95% of GenAI pilots deliver no profit impact**" (MIT, 2025) is cited here only
  because two independent retail sources lean on it; we did not verify the study's scope.
