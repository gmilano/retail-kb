---
industry: retail
region: Global
updated: 2026-11-23
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

## Added 2026-11-22 (pass 3) — the retail media plane

### 19. Retail's largest profit pool had no vocabulary in this knowledge base

Before this pass, **"retail media", "advertising" and "clean room" returned
zero hits across all eight files.** Nine cycles described retail as storefront,
catalogue and store — the cost side — and omitted the part that increasingly
pays for them. Vendor estimates for 2026 range from **~$25.5B to $200.4B**
depending on definition (see `intel/market.md`); either way it was missing
entirely.

This is the third consecutive pass to find a whole plane absent (pass 1: product
data; pass 2: the physical store). **The lesson is now a method, not an
accident: grep ~25-50 candidate domain terms against all eight files *before*
searching the web.** It cost one call and located this gap immediately. Terms
still returning zero after this pass, as candidates for the next one:
`last mile`, `route optim`, `cold chain`, `perishable`, `food waste`,
`recommerce`, `resale`, `circular`, `BNPL`, `accessib`/`WCAG`/`EAA`,
`virtual try-on`, `CLV`/`lifetime value`, `contact cent`, `warranty`,
`feature store`.

### 20. The money and the open-source floor are completely decoupled here

`retail media stars:>=50` returns **one** repo — a 2020 generic ML regression
tutorial. `retail media network stars:>=10` returns **three**, all Windows
DxDiag dumps. `clean room advertising stars:>=50` returns **zero**. Meanwhile
`ad server stars:>=200` returns **51**.

The generic adtech substrate is populated; **the retail-shaped layer does not
exist.** There is no Odoo of retail media. A retail media capability must be
*assembled* from permissive adtech and privacy primitives — which is both the
risk and the opportunity, and puts retail media on this KB's short list of
capabilities with no open-source floor, next to markdown/assortment
optimisation and shelf vision.

### 21. Agentic *advertising* arrived, and its standards contest is wildly asymmetric

Cycle 8 mapped agentic *commerce* (UCP, ACP, AP2, x402 — all Apache-2.0) and
concluded protocol neutrality beats picking a winner. Advertising now has the
same layer:

- **AdCP** (`adcontextprotocol/adcp`): Apache-2.0, **8610 refs**, commits on the
  day of this pass, governance documents (`CHARTER.md`, `IPR_POLICY.md`),
  transported over **MCP and A2A**, docs at v3.2.x after an Oct-2025 launch at
  v2.0.0. Working implementations exist (`prebid/salesagent`, Apache-2.0, alpha).
- **AAMP** (`IABTechLab/AAMP`): Apache-2.0, **5 refs**, **two files — `LICENSE`
  and `README.md` — one commit**, last touched 61 days before this pass.

Trade press frames these as rival standards dividing the industry. Stated
precisely: this measures **GitHub presence, not the existence of a
specification** — IAB Tech Lab publishes specs off-GitHub, so AAMP may exist as
a document. The decision-relevant version: **AdCP is buildable today and AAMP
is not**, and the AdCP FAQ states the two are **not wire-compatible**, so this
is a fork in the road rather than a layering choice. Prediction to score:
AAMP gains implementation code before **2027-05-22**, or it is not a
competitor.

### 22. The clean room is the one layer every retailer buys and nobody maintains

The four-step gradient in this plane (`repos/foundations.md`) ends in a hole:

| Step | State |
|---|---|
| SERVE IT (auction) | ✅ Prebid stack, Apache-2.0, commits within 0–4 days |
| SELL IT TO AN AGENT | ✅ AdCP + salesagent, Apache-2.0, alive, alpha |
| IDENTIFY IT (identity/consent) | ✅ UID2 operator + TCF, Apache-2.0, alive |
| PROVE IT (measurement) | ⚠️ **2 of 5** famous libraries alive |
| MATCH IT PRIVATELY (clean room) | ❌ **Zero maintained options** |

Every open-source data clean room found is dormant **752–1258 days**
(`PrivacyGo-DataCleanRoom` 752d, Snowflake quickstart 986d — and a demo, not a
product — `qascade/dcr` 1258d and AGPL-3.0). The **primitives** are alive and
permissive: `google/differential-privacy` (2d), `OpenMined/PSI` (63d),
`google/private-join-and-compute` (258d).

So the layer with the strongest vendor growth story — clean rooms at
$2.8B→$14.6B, measurement & attribution fastest at 22.6% CAGR (Dataintelo,
vendor) — has **no maintained open-source alternative at all.** Assemble from
primitives, don't fork a corpse: `compose/patterns.md` Pattern 14.

### 23. Two of five famous measurement libraries are alive; the listicles say five

Measured 2026-11-22: **`google/meridian` (2d) and `pymc-labs/pymc-marketing`
(0d) are alive.** `facebookincubator/GeoLift` is slowing (235d).
**`google/lightweight_mmm` (523d) is superseded by Google's own Meridian.**
**`facebookexperimental/Robyn` is dormant ~513 days** while 2026 commentary
still presents it as one of two "open-source giants" beside Meridian.

Start new measurement work on Meridian (Bayesian, geo priors) or
PyMC-Marketing (MMM + CLV + Bass diffusion in one library). Calibrate with
GeoLift while it lasts. Do not start on Robyn or lightweight_mmm.

### 24. Default branch ≠ `main`, and it corrupts both builds and liveness data

Two of this pass's repos have a default branch that is neither `main` nor
`master`:

- **`facebookexperimental/Robyn` → `accuracy/allocator_v2_fixes`** (a feature
  branch, last touched 2024-11-21). Default-branch tooling reports **731 days**
  dormant; `main` is **513 days**. A plain `git clone` yields non-release code.
- **`matomo-org/matomo` → `6.x-dev`** (development branch, alive 0d).

Both consequences matter: a client build gets the wrong code, and this KB's own
dormancy numbers get the wrong branch. **Resolve the default branch, then
measure `main`/`master` by name as well.** This pass made the Robyn error
first and caught it only by re-measuring.

### 25. The licence of a product is not the licence of its repository

Cycle 8 established that a short licence file is a pointer, not a licence
(Meilisearch: 468 bytes declaring `MIT AND OpenLDAP AND BUSL-1.1`). This pass
extends it twice:

- **Snowplow is three licences in one product.** `snowplow/snowplow` declares
  **Apache-2.0** (11359B), but **`stream-collector` and `enrich` — the two
  services you actually deploy — are under the proprietary Snowplow Limited Use
  License Agreement v1.1 (6637B)**, and the browser tracker is BSD-3. A team
  reading "Snowplow is Apache-2.0" mislicenses the core of a first-party data
  pipeline.
- **An empty licence file is not a licence.** `snowplow/snowplow` ships a
  **0-byte `LICENSE.md`** beside its real `LICENSE`. Tooling preferring the
  `.md` variant, or merely testing for a filename, reads an empty grant.

**Audit per deployed artefact, not per project.**

### 26. Two public licence claims were wrong, in opposite directions

- **UID2 is Apache-2.0.** The Trade Desk's own press release says the donated
  code would be **BSD-2**; `unifiedid.com` says Apache-2.0. Measured,
  `IABTechLab/uid2-operator/LICENSE` is the full **Apache-2.0** text, 11348
  bytes. **A press release is not a licence** — the fourth industry in which a
  vendor announcement misstated the licence of its own donated code.
- **OpenRTB has no licence at all.**
  `InteractiveAdvertisingBureau/openrtb` (222d) ships only spec markdown — root
  tree verified, no licence under eight candidate names on either branch. The
  substrate of all programmatic advertising is unlicensed. Implement from the
  spec; do not vendor the repo (the `bacen/pix-api` treatment from cycle 8).

### 27. The EMEA date cycle 8 recorded was real but its scope was too broad

Cycle 8 recorded a "transitional deadline of 2026-12-02 for systems already on
market". Refined from this pass's sources, **2026-12-02 binds providers of
systems that generate synthetic content and were placed on the market before
2026-08-02, and covers Article 50(2) in full — machine-readable marking and
detectability.** It does **not** bind deployers, systems that do not generate
synthetic content, or paragraphs 1, 3 and 4, which have applied since
**2026-08-02**. A further date, **2027-02-02**, requires providers to implement
a watermark-detection interoperability solution.

This matters for retail media because **AI-generated ad creative is synthetic
content.** It also matters as a method note: **this KB's own prior entries need
re-scoping, not just extending** — a date carried forward at the wrong scope is
a wrong fact with a correct number in it.

### 28. The keyword collision is a structural property of this sector, not bad luck

Cycle 8's flagship defect was a **Minecraft mod** (`2No2Name/hopperOptimizations`,
about in-game hoppers) shipped in `agents/top.md` as retail *inventory*
intelligence. This pass queried `retail media network stars:>=10` and got
`dovnel/Win-7`, `denman2328/Help` and `Camus777/Minecraft` — **DxDiag
system-information dumps from 2013–2015**, in which "Retail", "Media" and
"Network" all occur as ordinary Windows vocabulary. **Three of three hits,
every one plausible-looking in a results list.**

Retail's vocabulary is made of common English words, so keyword retrieval in
this industry has a structurally high false-positive rate. **The only defence
is opening every row before writing it.** Also recorded: `data clean room
stars:>=20` returns 18 hits of which **3 are real** (the rest are Android
"Clean Architecture"/Room-database apps, a news reader, a coin tracker), and
`incrementality stars:>=20` returns 952 and was **discarded as contaminated**.

### Source-quality notes for this section

- **Every repo claim** here was measured on 2026-11-22: `ls-remote` for
  existence and refs, bare `--depth 1 --filter=blob:none` clone for last commit
  date, `raw.githubusercontent.com` read for licence text with byte size
  recorded, `ls-tree` to prove absence. **Star counts are deliberately omitted**
  — `gh api repos/<slug>` is 403 for non-attached repos, so stars are not
  measurable through the available channel, and this KB has twice shipped
  fabricated star curves. An unmeasurable field is better left blank.
- **Every market figure** is vendor or trade research (WARC, EMARKETER, Grand
  View, Persistence, Mordor, Research and Markets, Dataintelo, Deloitte,
  McKinsey, Coresight, Bain, Criteo, Retail Economics) with differing scopes
  and undisclosed methods. Attributed inline, treated as directional.
- **LATAM's headline figures are co-produced with the market leader** (EMARKETER
  with Mercado Ads, which holds >50% share). Cited with the conflict named.
- **Regulation was searched per region and mostly not found.** EMEA has dated,
  statutory obligations. North America, APAC and LATAM returned **no citable
  retail-media-specific regulation**, and that is recorded as a gap in each
  regional section rather than smoothed over.

---

## Added 2026-11-23 — the returns & recovery plane

### 29. Retail's largest margin leak had no vocabulary in this knowledge base

Fifth plane, fifth time this has happened, and this was the biggest hole yet.
Before this pass `RMA`, `returns fraud`, `routing`, `BOPIS`, `takeback`,
`UFLPA`, `CSDDD`, `ESG` and `scope 3` were all at **zero mentions** across all
eight files, while `reverse logistics` had 2, `recommerce` 1, `resale` 1 and
`warranty` 1. Retail returns run at roughly **16% of sales (~$850B in 2025,
per Shopify)**.

The method that found it is now proven five times and costs about one tool
call: when the target KB already has same-day passes, **do not rewrite and do
not re-verify — grep ~25–60 candidate terms against the existing files before
touching the web.** The gap announces itself.

### 30. ⚠️ "Returns" is genuinely ambiguous *in this industry*, and it corrupted both channels in one pass

This is the most operationally important trend entry of the pass, because it
is a trap that produces confident, plausible, wholly wrong deliverables.

**It broke code search.** `returns management` → **3134 repos, zero
retail-relevant in the top 8** (portfolio analytics, library book lending).
`returns agent` → **2464 repos, zero relevant**, its 162★ top hit a Brainfuck
web app that *"returns your user-agent to you"*. And inside the KB's own
prose, a naive grep for "returns" scored **47 hits that were all false
positives** — phrases like *"the query returns 2 repos"* — while `RMA` scored
75 hits that were all the substring in *fo**rma**t*.

**It broke the industry sources too.** A KPMG APAC figure reads *"more than
half of retailers report returns exceeding 10% from AI initiatives"*. That is
**return on investment**. In a returns-reduction deck it is a factual error.

Cycle 8's trend #28 recorded that keyword collision is a structural property
of this sector. This extends it: **in the reverse-flow plane the collision is
semantic, not merely lexical, and it contaminates prose and prose-derived
statistics as readily as it contaminates repo search.** Search and quote
`RMA`, `reverse logistics`, `disposition`, `restocking`, `right of
withdrawal` — never the bare word.

### 31. The structural law, sixth confirmation — and the sharpest form it has taken: the mandated step is the empty one

Every plane in this KB has shown the same gradient: *format and geometry
problems are well equipped, judgment problems are not.* The reverse flow shows
it across six steps, and then adds a twist no previous plane had.

| Step | Nature of the problem | Open-source state |
|---|---|---|
| 1. PREVENT (fit prediction) | Judgment about one body | **Empty** — 73 repos, best 9★ unlicensed |
| 2. AUTHORISE (RMA) | Policy formatting | **One repo** — `mage-os/module-rma`, MIT, alive |
| 3. MOVE (reverse routing) | **Pure geometry** | **Abundant** — 8 permissive solvers, `or-tools` 14430★, all pushed this week |
| 4. GRADE (condition) | Perception, generic | Generic: **excellent** (`anomalib` 6416★ Apache-2.0). Retail-specific: **zero** |
| 5. DECIDE (disposition) | **Judgment + legal liability** | **Zero** — 22 repos, 0 relevant |
| 6. RECOVER / DETECT | Judgment + money | **~Zero** — `takeback trade-in` returns **0 repos** |

Step 3 is a solved problem with a 14430★ Apache-2.0 dependency pushed three
days before this pass. Step 5 — the adjacent step, in the same warehouse, on
the same unit — has **22 repositories worldwide and none of them are about
retail**.

**The twist: the empty step is the one the law now targets.** Since **19 July
2026**, ESPR Article 25 requires EU large companies to decide and evidence the
disposition of unsold apparel and footwear. The media pass found a three-step
gradient from *declare* (equipped) to *liquidate* (zero). This pass finds the
same shape with the legal obligation landing **precisely on the zero**. The
generalisable claim, now testable in the remaining industries:

> Open source equips the step that can be specified, and abandons the step that
> must be *judged and defended*. Regulation attaches to exactly the latter.
> Therefore: **the arrival of a mandate is a reliable predictor of an
> open-source vacuum, not of an open-source response.**

Corroborating counts from this pass alone: `extended producer responsibility`
→ **24 repos worldwide, max 1★**, for a regime in force across the EU; and
`right to repair` → 272 repos whose top results are *automotive*, 16 months
after a consumer-goods repair directive began applying.

### 32. The obligation is *typed*, and that is what makes it a build rather than a report

ESPR Article 25 does not merely forbid destruction. Sources are explicit that
**recycling an unsold garment counts as destruction while preparing it for
reuse does not**, and that derogations under **Delegated Regulation (EU)
2026/296** must be justified. So the disposition decision has a legal type
system: `reuse`/`repair` lawful, `recycle`/`destroy` restricted and
evidenced.

A cost optimiser cannot express that; a rules engine can. This is why the
right substrate is **Apache KIE / Drools** (Apache-2.0, 6344★, alive) rather
than a scoring model — and why the EMEA engagement is a compliance build while
the identical North American one is an optimisation build.

### 33. The one quantified "AI reduced returns" result in the world is European, and it came from the *equipped* step

Across every search in this pass, exactly one retailer-reported figure
connected AI to a measured fall in returns: **Zalando, attributing ~a fifth of
recent revenue growth to AI-driven personalisation and reporting a 7%
reduction in its return rate.** Note where that win was earned — at
**recommendation**, a step this KB already documented as well equipped — not
at the empty fit-prediction layer. Prevention pays, but it pays through the
tools that already exist.

Against it, the gap that funds the work: Retail Economics reports **95% of
European retailers using or testing AI in marketing and e-commerce and only
5% achieving scalable ROI**.

### 34. Returns fraud is the clearest "money without code" result in this KB

Demand: ~**9% of returns are fraudulent**, **85% of merchants already deploy
AI/ML against it**, and only **45% believe those tools work on their own**
(NRF / Happy Returns). Supply: `returns fraud` → **155 repos whose top six are
2, 6, 0, 0, 0 and 4 stars**, with the 6★ entry being credit-card fraud. The
graph-fraud toolboxes that listicles still recommend — `DGFraud` (766★),
`UGFraud` (134★) — have been **dead since April 2022**.

Only one live permissive piece exists and it is a **benchmark generator**,
not a detector: `SantanderAI/gen-fraud-graph` (Apache-2.0, 296★, 2026-10-01).
That is the correct shape, because returns-fraud data cannot legally or
commercially be pooled across retailers — so you generate, then benchmark.

An adjacent and newer surface: eMarketer, citing Chargeback911, reports
payment providers' tools are inadequate against AI-enabled chargeback fraud
**where autonomous agents are involved** — joining this plane directly to the
agentic-commerce plane of 2026-11-21.

### 35. ⚠️ Three new licence-verification failures, all of which would have produced wrong rows

Cycle 8 established that a raw-channel 404 is never by itself proof that a
licence is missing. This pass found three further failure modes:

1. **`LICENSE.TXT` — an uppercase *extension*.** Cycle 8's fix added lowercase
   `license.txt`. That still missed **`Project-OSRM/osrm-backend` (8237★)**,
   whose licence is in `LICENSE.TXT`. The probe must vary the case of the
   extension as well as the stem.
2. **The pointer licence file — a new category.** `valhalla/valhalla` (6481★)
   has a **44-byte** `LICENSE.md` whose entire content is
   `For license information see [here](COPYING)`. GitHub's API therefore
   reports **`NOASSERTION` / "Other"**, while `COPYING` is **plain MIT**. This
   is a false negative in the *permissive* direction — a licence gate or SBOM
   scan would reject a 6481★ MIT routing engine as unknown-licence. Cycle 8
   found the inverse with Chromaprint. **Rule: `NOASSERTION` means "read the
   file", never "no licence", and never "bad licence".**
3. **Rename vs deletion is distinguishable.** `git ls-remote` succeeding while
   `search/repositories q=repo:<slug>` returns **HTTP 422** is the signature of
   a **renamed** repository. `openvinotoolkit/anomalib` is now
   `open-edge-platform/anomalib` (6416★, Apache-2.0). Previous cycles treated
   `refs=0` as non-existence; this adds the complementary test.

And one liveness trap: **`apache/incubator-kie-optaplanner` (3512★) says in
its own description that the project "has moved."** The live repo is
`apache/incubator-kie` (6344★). Stars accumulate against history, not against
maintenance.

### 36. The licence shape inverts again — platforms copyleft, components permissive

In the store plane the platforms were permissive and the fiscal libraries
copyleft. Here it is reversed: the platforms carrying returns functionality are
**copyleft** (Odoo LGPL-3.0 with its verified `Repairs` app, ERPNext GPL-3.0
with its `Warranty Claim` doctype) while every component needed to build the
missing disposition layer is **Apache-2.0, BSD-2 or MIT** (`incubator-kie`,
`anomalib`, `or-tools`, `vroom`, `osrm`, `PyVRP`).

The practical reading: **configure the copyleft platform, own the permissive
decision layer.** The one standalone RMA component that can be re-licensed
into a client's closed product is `mage-os/module-rma`, MIT, 23★.

### Source-quality notes for this section

Every GitHub claim above is verified on 2026-11-23 — existence by
`git ls-remote`, metrics and SPDX by `search/repositories`, licence by
fetching the file and checking its byte count.

**Every non-GitHub figure in this section is search-result-derived and could
not be fetch-verified**, because both verification channels are blocked by
this session's network policy: `curl` returns `403 connect_rejected` from the
egress proxy and WebFetch returns `ENOTFOUND` for `eur-lex.europa.eu`,
`espratlas.com`, `modernretail.co`, `nrf.com`, `deloitte.com`, `emarketer.com`
and `planalto.gov.br`. This affects the Shopify return-rate figures, the
NRF/Happy Returns 9%/85%/45% figures, the Coresight, KPMG, Retail Economics
and Deloitte adoption numbers, the Zalando result, and **all statutory dates
including ESPR Article 25 and Directive (EU) 2024/1799**. They are attributed
in prose to their named sources and must be checked against the Official
Journal and the companies' own filings before entering a client deliverable.
**To make them citable, those hosts need to be added to the session's allowed
network domains.**

One dated figure is flagged in place rather than dropped: the **59%** "keep
it" adoption number is a goTRG survey of 21 retailers from the **2023**
holiday season — the most specific available, but three years old.
