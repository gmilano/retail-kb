---
industry: retail
region: Global
updated: 2026-11-22
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

## 9. The product-data plane is where the open-source floor stops — a three-step gradient

Added 2026-11-22. Retail's catalogue problem splits into three steps, and their open-source health is
nothing alike. The gradient tracks exactly one variable: **is the step a format problem or a judgement
problem?**

1. **DECLARE what the product is** — a format problem. **Well equipped and permissively licensed, by the
   standards body itself:** `gs1/GS1_DigitalLink_Resolver_CE` (Apache-2.0, 65★, pushed 2026-11-02),
   `gs1/GS1DigitalLinkToolkit.js`, a conformance test suite, and `zxing/zxing` (Apache-2.0, 34217★, pushed
   2026-11-21) underneath it all.
2. **MOVE it** — also a format problem. **Also well equipped:** EPCIS 2.0 has four live implementations
   across Java, .NET and JavaScript, all Apache-2.0 or MIT; EDI has `EDI.Net` (MIT, 491★), `stupidedi`
   (BSD-3, 293★), `pydifact` (MIT, 191★, pushed 2026-11-16).
3. **JUDGE whether the catalogue is right** — pure judgement. **`product taxonomy classification
   stars:>=50` → 0. `product description generation ai stars:>=30` → 0. `visual search product embedding
   stars:>=100` → 0.** `product feed stars:>=100` returns 7 repos of which **zero are retail product-feed
   tools**. Attribute extraction is three unmaintained 2019–2022 research repos, two of them unlicensed.

**[measured]** This is the sixth industry in this KB where the same law holds: *the open-source floor
reaches exactly as far as the problem is a format, and stops where it becomes a judgement.* Retail's
version is unusually sharp because step 3 is the step the 2026 trade press calls the primary ranking layer
of agentic commerce — the commercially decisive step is the one with nothing under it.

## 10. ACP's product-feed surface is newer, thinner and less binding than the vendor coverage says

Added 2026-11-22, **measured against the spec repo itself, not commentary.** Vendor write-ups describe
"ACP publishing a versioned 67-field spec" for product feeds. Read from
`agentic-commerce-protocol/agentic-commerce-protocol` at spec version `2026-04-17`:

- The feed schema is **20 named objects carrying 62 properties in total** — close to the quoted figure, but
  not it. Anyone citing "67 fields" has not opened the file.
- **The feed surface did not exist before April 2026.** Versions `2025-09-29`, `2025-12-12` and
  `2026-01-16` contain only `agentic_checkout` and `delegate_payment`; `2026-01-30` adds discount and
  extension; `schema.feed.json` first appears in `2026-04-17`. And `rfcs/rfc.product_feeds.md` is still
  marked **`Status: Proposal`, `Version: unreleased`**.
- **A GTIN is not required.** `Variant.required` is `["id", "title"]` — nothing else. The `Barcode` object
  requires `type` and `value` *if you supply one*, but the `barcodes` array itself is optional.
- **Taxonomy is punted entirely.** `Category` is `{value, taxonomy}` where `taxonomy` is an unconstrained
  string. The protocol does not say which taxonomy, and (see trend #9) nothing open source will classify
  into one for you.

**The distinction to sell:** protocol conformance and agent *visibility* are different problems. ACP's
floor is `id` + `title`. Google Merchant Center's trust layers reportedly exclude products with missing
GTINs, and Google's own published benchmark is a **~20% click increase** for retailers who add correct
GTINs (one vendor inflates this to 40% — use 20%). **Being ACP-compliant does not make a catalogue
sellable.** The surfaces, not the protocols, set the real bar.

## 11. Two of the three agentic-commerce "standards" are dormant

**[measured 2026-11-22]** Last-push on the default branch: **UCP 2026-11-21** (alive), **ACP 2026-07-18
(127 days)**, **AP2 2026-06-17 (158 days)**. Star counts over the same period kept climbing — ACP 1607 →
1610, AP2 3281 → 3283 — which is precisely why stars are the wrong instrument. Protocol-neutrality through
`NVIDIA-AI-Blueprints/Retail-Agentic-Commerce` (Apache-2.0, 89★, pushed 2026-11-20) remains the right
engineering call, because the surfaces still speak different protocols. But the narrative of "three
fast-moving competing standards" is not supported by the repositories.

## 12. Identity is the one piece of work that every 2027 retail deadline requires

Added 2026-11-22. Sunrise 2027 (POS able to read 2D codes), the EU Digital Product Passport, EUDR
due-diligence, and agent-readable catalogues are four unrelated programmes with **one shared
prerequisite**: a resolvable product identifier with trustworthy attributes behind it. GS1 Hong Kong's CEO
put the commercial version of this plainly in a November 2026 KPMG China / GS1 HK study — AI systems favour
products backed by data the system can interpret and trust.

That makes identity work unusually easy to fund: it is the only line item that a compliance budget, a
logistics budget and a growth budget can all legitimately pay for. It is also the step where permissive
open source is strongest (trend #9, step 1), so the build is cheap and the margin sits in step 3.

## Low-confidence items — flagged, not promoted

- The **$3–5T by 2030** agentic-commerce figure is McKinsey via second-hand citation; we did not reach the
  primary report.
- **India's ~33% consumer adoption / ~80% business exploration** is a single quoted expert estimate.
- All **LATAM WhatsApp figures** conflict between vendor sources (see `intel/market.md` warning).
- US regulatory claims could not be verified at all.
- The widely repeated "**95% of GenAI pilots deliver no profit impact**" (MIT, 2025) is cited here only
  because two independent retail sources lean on it; we did not verify the study's scope.
- **GS1 Sunrise 2027's date is not firm and the initiative is not law.** Sources split between
  31 Dec 2027 and Jan 2027, almost all of them vendor QR-code blogs. GS1's own "2D in Retail" guidance
  reportedly sets **no sunset date for linear barcodes** and ends dual marking only once ~90% of POS
  systems can read 2D — a capability threshold, not a deadline. Claims that Walmart, Target, Tesco and
  Carrefour have committed trace only to vendor blogs and were **not** verified.
- **The EU DPP Registry "went live with a test environment on 2026-07-20"** appears only in secondary
  commentary; not confirmed against a Commission source this pass.
- **APAC track-and-trace market sizes** (China ~$670M, Japan ~$400M, India ~$380M for 2026) come from a
  single market-research vendor. Directional only.
- **LATAM AI regulation status** (Brazil PL 2338 with ANPD as enforcement authority; Mexico LFPDPPP plus
  INAI guidance on automated decisions) is sourced to a consultancy marketing blog and was not verified
  against the Brazilian Congress or INAI.

---

## Added 2026-11-22 (pass 2) — the store plane

### 13. Retail's majority channel had no vocabulary in this knowledge base

Measured by grep across all eight files **before** any search was run: zero occurrences of `planogram`,
`self-checkout`, `rfid`, `computer vision`, `workforce`, `scheduling`, `store operations`, `point of sale`,
`reverse logistics`, `fraud`, `loyalty`, `customer service`, `e-invoic`, `cfdi`, `nf-e` or `peppol`. Eight
cycles of this KB described retail entirely as e-commerce and agentic commerce. **Most retail revenue is
rung up in a store**, and this is the trend note that records the omission as well as closing it.

### 14. The open-source gradient in the store inverts the usual shape: the *middle* is best equipped

Every plane this KB has measured — healthcare's identifiers, media's rights reservation, retail's product
data — degrades monotonically: declaring is easy, moving is harder, judging is empty. **The store plane does
not.** Ringing the sale is adequately served but copyleft (NexoPOS GPL-3.0, ERPNext GPL-3.0, Odoo LGPL-3.0,
with `opensourcepos` MIT as the one permissive maintained till). **Making the sale lawful is the
best-equipped layer in retail open source.** Seeing what is actually happening on the shelf, in the queue
and on the roster is empty. The compulsory middle is where the code is, because **a tax authority is a
specification that cannot be ignored, deferred or A/B tested** — which is precisely what a standards body
is not.

### 15. Compliance is the one retail capability whose licence is a function of geography

Mexico CFDI is MIT and Unlicense. Brazil NF-e is Apache-2.0 and LGPL-3.0. Chile DTE is AGPL-3.0 with no
alternative. The EU is Apache/MIT libraries over an **EUPL-1.1** access point. India is GPL-3.0 inside
ERPNext. The United States has no mandate at all. **A single multi-country retail rollout therefore crosses
four licence families, and because the obligation is not optional, the licence chooses the architecture.**
No other layer in this KB behaves this way: a recommender or a search index has the same licence everywhere.

### 16. The entire visible shelf-vision corpus is AGPL-derived, and nobody says so

`ultralytics/ultralytics` — 63669★, 12024 forks, pushed the day of this pass — is **AGPL-3.0**, and it is
what every shelf-monitoring repo surfaced by search is built on. `planogram` returns 502 repos whose top
result has **17 stars**; `shelf monitoring retail stars:>=30` returns **one** repo, unlicensed, describing
itself as a simulation. So the picture is not "open source is behind on shelf vision" but something sharper:
**the demos are abundant, uniformly tiny, and uniformly copyleft at the weights layer.** The permissive
route exists (`roboflow/supervision`, MIT, 51699★) but requires deliberately not using the default detector.

### 17. Workforce management is the starkest single-repo result this KB has recorded

`workforce scheduling stars:>=150` → **one repo worldwide**: `Staffjoy/v2`, MIT, 1686★, **last pushed
2022-12-06.** Four years dead, and still the best-starred workforce-management project in open
source. Retail's single largest controllable cost line has one abandoned repo above 150 stars. Compare
media's "music royalty accounting" (14 results, top six summing to 0 stars): the shape is the same — the
work that costs the most money attracts the least open code.

### 18. Peppol is no longer a European competence

Singapore's GST InvoiceNow mandate requires connection to the **Peppol** network through an
IMDA-accredited Access Point. The same architecture, and the same EUPL-licensed reference implementation,
serves EU and APAC compliance. A capability built for a French mandate is sellable in Singapore — the only
cross-region capability transfer this KB has been able to demonstrate from primary mechanics rather than
analogy.

### Source-quality notes for this section

- France's 1 September 2026 go-live is well sourced but **enforcement is contested**: one source says DGFiP
  will not automatically sanction good-faith efforts, another says no grace period exists in law.
- **Belgium (1 January 2026) and Poland KSeF (1 February 2026) are single-sourced** from a vendor timeline.
- The claim that **Germany's 2027 rules include "e-Kasa" fiscalisation for B2C retail is recorded as not
  verified and probably conflated** — *e-Kasa* is Slovakia's system; Germany uses KassenSichV/TSE.
- **Frontline AI adoption figures conflict by a factor of two**: a BCG 2026 survey cited by a vendor reports
  74% of frontline workers using AI daily or several times weekly; a UKG survey reports 33% for retail,
  hospitality and food service. Different measures, not a settled number.
- Vendor-reported store outcomes (e.g. Hugo Boss: 25% of administrative time saved, 3% incremental revenue)
  come from the vendor that sold the system. Directional only.
- APAC deployment counts (CloudPick 1,200+ locations; a 15,000-store FamilyMart/7-Eleven commitment) trace
  to a single market-research page. **Unverified.**
- North America remains the weakest-sourced region, a second cycle running; the reported FTC order barring a
  retailer from facial recognition for five years **does not name the retailer** in the source.
