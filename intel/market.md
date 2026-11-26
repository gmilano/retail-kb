---
industry: retail
region: Global
updated: 2026-11-26
---

# 🗺️ Market Map — Retail & Consumer

> Key players, market structure and opportunities **placed by region**. Figures are sourced from trade
> press, consultancies and market-research firms; where sources disagree the range is given rather than a
> single invented number. Treat percentages from vendor blogs as directional.
>
> *This file previously held a placeholder player row plus "To research" in three of four regions.*

## Market size — treat as a range, not a number

| Measure | Figure | Source quality |
|---|---|---|
| Agentic commerce redirected retail spend by 2030 | **$3–5 trillion** globally | McKinsey, cited second-hand — the most-quoted figure in the sector |
| US retail spend via AI platforms, 2026 | **~$20.9B** (~1.5% of US e-commerce) | Trade press; scope differs from the next row |
| "America AI in retail" market, 2026 | **~$6.43B** | Mordor Intelligence — different scope, not comparable to the above |
| APAC AI-in-retail market | **$3.37B (2025) → ~$4.62B (2026)** | Fortune Business Insights |
| Retail execs expecting AI-driven personalisation within a year | **67%** | Deloitte 2026 outlook, cited second-hand |

⚠️ **Do not stack these.** The two US figures measure different things (spend flowing *through* agents vs.
spend *on* AI software) and earlier cycles of this KB blended such numbers into single growth claims.

### Added 2026-11-22 (pass 3) — retail media: the numbers differ by 8x, and that is a definition problem

Retail media is the fastest-growing profit pool in retail and the published
figures for it are irreconcilable until you notice that **two different things
are both called "retail media".**

| Source | 2026 figure | Trajectory | What is being counted |
|---|---|---|---|
| WARC | **$200.4B** | $223.4B in 2027 (+11.5%; **+9.8% excluding Amazon**) | **Ad spend** — money flowing through retail media |
| Grand View Research | $34.2B | $68.8B by 2033 (10.5% CAGR) | **Networks** — the platform/technology market |
| Persistence Market Research | $32.6B | $109.4B by 2033 (18.9% CAGR) | Networks (most aggressive) |
| Research and Markets | $26.23B | from $23.96B in 2025, 9.5% CAGR → ~$37.8B by 2030 | Networks |
| Mordor Intelligence | ~$25.5B | 6.35% CAGR through 2031 | Networks (most conservative) |
| Dataintelo | $2.8B (2025) | $14.6B by 2034, 20.1% CAGR; **measurement & attribution fastest at 22.6%** | **Data clean rooms** only |

**The spread between $25.5B and $200.4B is roughly 8x, and it is not a
disagreement about growth.** WARC counts advertiser spend; the others count the
networks and technology that carry it. Both are defensible; quoting one as the
other is not.

**Rule for this KB: never state a retail media number without saying which of
the two it is.** Cycle 8 was criticised in its own notes for carrying
`$215.31B LATAM` and `WhatsApp $18.2B` as settled fact with no source. The
figures above are all vendor or trade research with differing scopes and
undisclosed methods — directional, and attributed.

**The one firm, non-vendor-shaped conclusion:** even the most conservative
networks estimate ($25.5B) sits against **one** open-source repo matching
`retail media stars:>=50`, and that repo is a 2020 ML tutorial. The money and
the open-source floor are completely decoupled here.

## Global players

| Player | Type | Strength | Weakness |
|---|---|---|---|
| Google | Protocol + surface | **UCP** (announced NRF Jan 2026); Microsoft adopted it in Merchant Center | Competing with its own ads economics |
| OpenAI + Stripe | Protocol + surface | **ACP**; ChatGPT is the highest-intent agent surface | Checkout trust and merchant control still unsettled |
| Shopify | Platform | All-in on agentic shopping; ships official **MIT** UCP tooling | Merchant-side only; no demand surface of its own |
| Walmart | Retailer | Native in-ChatGPT app ("Sparky"); keeps checkout in its own environment | US-centric |
| Amazon | Retailer | Largest catalogue and logistics | **Closed** — blocked Meta's agent from its retail site; hostile to third-party agents |
| Alibaba / ByteDance / Tencent | Platform | Shipping autonomous buy/book/pay in production; **Alipay "AI Pay"** accepts agent payments | China-domestic; limited portability |
| Visa / Amex / Mastercard | Payments | All three US networks now support agentic commerce; Amex ships an **ACE** dev kit with purchase protection | Visa's protocol code is **not** open source (see `agents/top.md`) |
| NVIDIA | Infrastructure | The only Apache-2.0 reference implementation covering **both** ACP and UCP | Hardware-aligned incentives |

## Opportunities by region

### North America

- **Protocol integration is the live deal.** The surfaces exist (ChatGPT, Copilot, Google) and discovery
  partners are already named — Target, Sephora, Nordstrom, Lowe's, Best Buy, The Home Depot, Wayfair. A
  retailer not reachable via UCP/ACP is invisible to that demand.
- **Consumer adoption is ahead of retailer readiness:** a CI&T survey reports **74% of US consumers have
  already used an AI shopping agent**, against ~1.5% of e-commerce actually flowing through agents.
- **Sell the disintermediation defence.** Retail Dive identifies data ownership and loss of the customer
  relationship as the primary risk: when discovery moves into an AI conversation, attribution collapses and
  personalisation signals thin out. First-party data capture + own-agent strategy is the counter.
- **Regulatory picture is the weakest-sourced of any region.** The FTC and a proposed "AI AGENT Act" are
  cited by secondary sources, but we could not verify specific obligations or their status. **Check FTC and
  NIST primary sources before making any compliance claim to a US client.**

#### Product-data plane — added 2026-11-22

- **The gatekeeper here is Google Merchant Center, not a regulator.** GTIN rules are the practical entry
  requirement for AI shopping surfaces: a GTIN means UPC/EAN-JAN/ISBN-13/ITF-14; `mpn` is required only
  when a product has no manufacturer-assigned GTIN; private-label goods must set `identifier_exists: false`
  rather than leave the field blank; and **invented GTINs or restricted GS1 prefixes (02, 04, 2, 05, 98,
  99) reduce visibility.** Google's published benchmark is a **~20% click increase** for retailers adding
  correct GTINs (one vendor inflates it to 40%).
- **A hard migration already passed:** the Content API for Shopping sunset on **2026-08-18**. Any client
  still on it is broken now, not later — confirm against Google's Merchant API changelog before quoting
  remediation.
- **Google has published no mapping** from Merchant Center attributes to what actually surfaces in AI
  Overviews / AI Mode. Anyone selling "AI Mode optimisation" as a deterministic service is selling a guess.
- **UCP is a North American institution and the only live protocol** (pushed 2026-11-21 vs ACP's
  2026-07-18 and AP2's 2026-06-17). Google introduced it in early 2026 and took it to NRF.
- **Opportunity:** *catalogue readiness audits* — GTIN coverage, prefix validity, attribute completeness,
  feed/markup agreement — scoped as a fixed-price diagnostic. It needs no regulatory trigger, the data to
  measure it is already in the client's PIM, and it is the prerequisite for every agentic-commerce project
  this KB recommends.
- ⚠️ **Source quality:** this region's product-data evidence is almost entirely agency and vendor blogs
  interpreting Google documentation. The GTIN mechanics are consistent across sources; the traffic and
  conversion figures are not.


#### Added 2026-11-22 (pass 2) — the store plane in North America: the only region with no fiscal driver

**North America is the one region where the store plane's value is not compliance.** There is **no federal
B2B e-invoicing mandate**, and sources agree none is on the horizon: without a federal VAT or a single
national indirect-tax authority there is no mechanism to compel one. The voluntary substitute is the
**DBNAlliance** exchange network, UBL-based, formally established January 2024 out of the Federal
Reserve-supported **Business Payments Coalition**; the only hard obligation is federal procurement, where
OMB Memorandum M-15-19 effectively requires suppliers to invoice electronically. Market structure instead
of mandate: one estimate counts **250+ e-invoicing service providers, 15+ formats and 40+ subsets** — i.e.
fragmentation is the North American problem, and interoperability work is the North American sale.

**So in NA the binding constraint on the store plane is surveillance law, not tax law.**

- **Biometric privacy is the hard edge.** Illinois **BIPA** is consistently described as the strictest:
  a published retention policy and an informed written release *before* a biometric identifier is
  collected. Only **Illinois, Texas and Washington** have statutes dedicated to private-sector biometric
  data; **20+ states** have comprehensive privacy laws that class biometrics as "sensitive". There is
  **no comprehensive federal biometric statute** as of Q2 2026.
- **Dated items, correctly labelled.** Illinois **HB 5521** (introduced February 2026) would add rules
  specifically for **retail loss-prevention cameras** — it is a **bill, not law**. Erie County, New York
  passed a biometric transparency ordinance on 30 April.
- **Surveillance pricing is a parallel exposure.** California, the FTC and New York are investigating or
  legislating against individualised prices set from personal data — which constrains the personalisation
  side of the same in-store data.
- **The design rule that follows, and it is directly actionable.** Vendors are moving away from facial
  recognition because **gesture- and behaviour-based detection does not identify an individual shopper and
  therefore stays outside the scope of biometric privacy laws.** Any Globant shelf-, queue- or
  shrink-vision build in North America should be **non-identifying by construction** — no face embeddings,
  no re-identification across visits — and should say so in the proposal, because that single property is
  what removes BIPA exposure.

**Opportunity.** The two measured open-source voids — `retail loss prevention theft detection stars:>=20`
→ **0** and `footfall people counting retail stars:>=50` → **0** — sit exactly where NA retailers have
budget and legal anxiety. A privacy-by-construction store-vision product (MIT `supervision` over a
non-AGPL detector, no biometric identifiers) is defensible IP *and* a compliance story.

**Source quality, stated plainly: North America remains the weakest-sourced region in this KB, a second
cycle running.** Nearly every item above comes from vendor or consultancy blogs. One source reports an FTC
proposed order barring a retailer from using facial recognition for surveillance for five years but does
**not name the retailer** — recorded here as **unverified**. Cycle 8 flagged the same weakness about an
alleged federal "AI AGENT Act"; that claim remains unverified and should not be used with a client.
#### Added 2026-11-22 (pass 3) — retail media in North America: a duopoly on the increment

North America is the largest and most concentrated retail media market, and the
concentration is the commercial fact that should shape any engagement here.

- **US retail media ad spend: $69.33B in 2026**, up **17.9%** from $58.79B in
  2025 (EMARKETER).
- **Amazon Ads and Walmart Connect together take 89.5% of the *incremental*
  spend in 2026** (EMARKETER). Not of the market — of the growth.
- **Adoption, measured two ways:** a Coresight survey of 100 North American
  retail executives (fielded **2026-09-02 to 09-04**, ±8 points) finds AI moved
  "from the lab into the core of operations" while **governance has not kept
  pace**. Ramp card-spending data in the same report: **49% of US retailers had
  paid AI subscriptions in August 2026, against 11% two years earlier.**

**What follows for a North America engagement.** Competing with the duopoly's
network is not the opportunity; being the reason a *second-tier* retailer's
network is worth buying is. Two concrete openings:

1. **Agent-readiness of the long tail.** The duopoly will be reachable by
   AdCP-speaking buying agents early. A regional grocer or specialty chain will
   not, and `prebid/salesagent` (Apache-2.0, alive) is a working starting point
   for the sales-agent role — see `compose/patterns.md` Pattern 15.
2. **Governance as a deliverable, not a slide.** The Coresight finding is a
   *measured* gap between deployment and control, in the region with **no
   binding AI statute to anchor it.** That makes governance a consulting
   product here rather than a compliance obligation.

**⚠️ Informed gap — North America is again the weakest-sourced region.** This
pass searched for retail-media-specific regulation (FTC, state AI statutes, ad
transparency duties) and **found nothing citable**: the regional searches
returned adoption and spend data and essentially no regulation. Cycle 8
recorded the same weakness and flagged a proposed "AI AGENT Act" as traceable
only to secondary vendor sources. **That remains unverified and is not promoted
here.** Treat US retail media compliance as driven by state privacy law and
self-regulatory advertising codes until this KB can cite a primary source —
and note the contrast with EMEA, where the dates are statutory and dated.

#### Added 2026-11-23 — returns & recovery in North America: the only region where disposition is *not* legally constrained

**Adoption is already deep in exactly the function this plane needs.** A
Coresight survey of 100 North American retail executives (September 2026)
found AI in production across an average of **4.8 of seven core functions**,
with customer service at **83%** and **fraud and loss prevention at 77%** —
making loss prevention the second most-deployed AI function in North American
retail. KPMG frames shrink as now spanning organised retail crime, **returns
abuse**, payments fraud and logistics in one envelope.

**The buying trigger is a measured confidence gap, not a capability gap.** An
NRF / Happy Returns report puts roughly **9% of returns as fraudulent**, and
finds **85% of merchants already use AI or ML against returns fraud while only
45% believe those tools are effective on their own**. That 85/45 split is the
most sellable number in this plane: the budget is already spent, the incumbent
tools are already distrusted, and — per `repos/foundations.md` → Step 6 — the
open-source alternatives the market would reach for are **dead since 2022**
(`DGFraud`, `UGFraud`).

**Agentic commerce is opening a new fraud surface here first.** eMarketer,
citing Chargeback911, reports that payment providers' current tools are
inadequate for AI-enabled chargeback fraud, **particularly where autonomous
agents are involved**. This joins directly to the agentic-commerce plane this
KB opened on 2026-11-21: the same ACP/AP2 rails that let an agent buy also let
an agent dispute.

**Scale and policy context:** Shopify reports **~16% of all sales returned in
2025, ~$850B**. On "keep it" / returnless refunds, the most specific adoption
figure available is a goTRG survey of 21 major retailers at **59%** — but that
is from the **2023** holiday season, so treat it as the latest available
number, **not** a 2026 one. Forrester's 2026 outlook predicts the end of
generous e-commerce returns on the grounds that free keep-it programmes became
open to abuse.

**The structural asymmetry — and it mirrors the store plane exactly.** On
2026-11-22 (pass 2) this KB recorded that North America is the only region
with **no fiscalisation driver** for the till. The same holds for the reverse
flow: there is **no federal AI statute and no destruction/disposition mandate**,
so returns policy here is governed by contract and state consumer law rather
than by a dated obligation. The consequence for engagement design is concrete:

> In North America the disposition decision is a **pure economic optimisation**
> — is this unit worth the freight back? In EMEA the identical decision is a
> **legally evidenced judgment**. Same code, different objective function, and
> the EMEA version needs an audit trail the North American version does not.

**Opportunities — North America**

- **Returns-abuse scoring that a retailer can actually own.** The incumbent
  tools are distrusted by 55% of their own users and the open-source graph-fraud
  toolboxes are four years stale. Build on
  [SantanderAI/gen-fraud-graph](https://github.com/SantanderAI/gen-fraud-graph)
  (Apache-2.0, 296★, 2026-10-01) to generate and benchmark, because returns-fraud
  data cannot be pooled across retailers. See Pattern 20.
- **"Keep it" decisioning as an optimiser.** The decision is freight + grading
  cost vs recoverable value. This is the one market where it can be built
  without a compliance layer, which makes it the cheapest place to prove the
  model before porting it to EMEA.
- **Agent-dispute defence.** Price the new chargeback surface that agentic
  checkout creates, before the payment providers close it.

#### Added 2026-11-23 (pass 5) — the price plane in North America: **who gets the price**, and this region is now the strictest

> **This inverts a cycle-8 finding.** Cycle 8 recorded *"North America is the
> weakest-sourced region"* — FTC and a proposed federal act visible only in
> vendor secondary sources. For **price**, NA is the opposite: the only region
> with outright **bans already in force**, enacted at state level, with a private
> right of action in one state. Generalisations about a region's regulatory
> weight do not survive a change of plane.

**The legal object here is *who* gets the price.** North America regulates
**personalised / surveillance pricing** — price that varies by what you know
about the shopper. It does *not* generally restrict price that varies by market
conditions. Every date below is **search-derived, not fetch-verified** (see the
provenance gap in `repos/foundations.md`).

| Jurisdiction | Instrument | Status / date | Shape |
|---|---|---|---|
| Maryland | Protection From Predatory Pricing Act | Signed **2026-04-28** | Reported as the **first state ban**; commentators note broad industry exemptions that may limit its reach. |
| Connecticut | Surveillance-pricing ban | Signed **2026-06-04**, effective **2026-10-01** | In force now. |
| New Jersey | Grocery/retail-focused ban | Enacted 2026 | **First with a private right of action**, via the NJ Consumer Fraud Act. Raises exposure from regulator-only to plaintiff-driven. |
| New York | Algorithmic pricing **disclosure** | In force | Disclosure model: say when a price was personalised, rather than prohibit it. |
| New York | One Fair Price Act | Passed legislature **June 2026**; awaiting signature, **decision deadline 2026-12-31** | **38 days after this pass.** The nearest dated uncertainty in the region. |
| Federal (FTC) | Proposed enforcement policy on personalized pricing | **August 2026** | Narrower than the state laws; read as a framework for state regulators under existing consumer-protection law rather than a new federal duty. |

**Volume:** roughly **40 bills across 24+ states** introduced in 2026, with three
states enacting. **Contradiction flagged rather than resolved:** Colorado is
reported both as having a surveillance-pricing bill **vetoed 2026-06-03** and as
regulating via **HB 1210**. Sources disagree; treat Colorado as *unresolved*.

**What this means for a build.** The compliance artefact NA requires is the
*opposite shape* to EMEA's. EMEA asks you to **produce** a number (the 30-day
reference price). NA asks you to **prove an absence** — that price did not vary
by consumer attributes. A price-history ledger keyed by *variant × context*
answers EMEA and **cannot** answer NA, which needs the pricing *inputs* logged
per quote. Design for the harder one. Pattern 22 and Pattern 25 set this out.

**Opportunity, placed.** NA is where **segment-level pricing with a defensible
audit trail** is a product, not a slide: the lawful lever (match competitor price
drops, which trade press reports is how leading retailers actually use dynamic
pricing) separated by construction from the unlawful one (price by person). The
New Jersey private right of action is the commercial reason a retailer will pay
for the audit trail rather than the model.

#### Added 2026-11-23 (pass 6) — the fulfilment plane

**The regulatory surface here is municipal, not federal, and it has a buildable 2027 date.**

New York City's Department of Consumer and Worker Protection sets a minimum pay rate for app-based
delivery workers: **$22.13/hour as of April 2026**, inflation-adjusted annually, with tips excluded
from the minimum. Grocery delivery apps (Instacart among them) were brought in from **January 2026**
at $21.44/hour. The piece that matters for a build is the next one: **DCWP begins enforcing
deactivation protections in January 2027** — a platform may not deactivate a worker without just
cause or a bona fide economic reason.

That is an algorithmic-accountability requirement wearing labour-law clothes. A delivery platform
operating in NYC in 2027 must be able to produce, per deactivation, the reason, the evidence and the
decision path. Nothing in the open-source estate does this.

**The counter-evidence, and it is good evidence.** An NBER working paper on Seattle's equivalent
minimum-pay standard found base pay per task roughly doubled while tips fell and available tasks
fell, with **no net increase in monthly earnings**. NYC's own October 2026 report says earnings rose
by more than $2 billion *and* that apps responded by limiting worker access to platforms and cutting
unpaid waiting time. Both things are true: the rules move money and the platforms re-optimise around
them. A client proposal that quotes only the city's number is quoting half the literature.

**Adoption, from the better-sourced surveys:** a Coresight survey of 100 North American retail
executives at $500M+ companies (fielded September 2026) reports AI in core operations with governance
lagging deployment; Ramp spending data in the same report puts US retailers' paid AI subscriptions at
**49% in August 2026, up from 11% two years earlier**. EMARKETER projects AI platforms will account
for **1.5% of US retail e-commerce sales in 2026** — small, and the first time this KB has a figure
for it at all.

**Opportunity:** *auditable dispatch and deactivation*. Build the decision log that the January 2027
NYC rule will require — every assignment, pay calculation and deactivation emitted as a typed,
replayable event. It is the same ledger shape as pass 5's price-event ledger, applied to labour
rather than price, and the same rule applies: the obligation is on the *explanation*, so the
explanation has to be a first-class record, not a log line.

**Honest gap:** no federal US rule, and no state-level survey, was verified in this pass. The NYC and
Seattle findings are solid and primary-adjacent; anything claiming a nationwide US delivery-labour
regime is not supported by what was measured here.

#### Added 2026-11-26 (pass 7) — the merchandise planning, buying & trade-funds plane

**Adoption is real and governance is not.** Coresight's August 2026 survey of 100 North American retail
executives at companies above $500M revenue found **49% holding paid AI subscriptions, up from 11% two
years earlier** — and its headline finding is that governance is failing to keep pace with what has
already been deployed. BRG's retail spotlight adds the shape of that gap: generative AI implementation is
running ahead of predictive and agentic, retailers report confidence in AI policies despite coverage
gaps, and agentic AI remains early. Consumer-side pull is steep: **AI traffic to US retail sites rose
1,324% between October 2024 and May 2026**. On the operations side Prologis reported in early 2026 that
nearly all of the top 30 North American retailers are deploying automation.

**Why this plane matters most here.** North America is where vendor-funded trade spend is largest and
most contested — grocery and CPG deduction disputes are settled in real money — and there is **no open
settlement engine anywhere** (see `intel/trends.md` §2: the entire category totals zero stars). A
retailer running trade funds on spreadsheets against a commercial TPM it cannot audit is the standard
situation, not the exception.

**Regulation — informed gap.** Searched this pass; no federal AI statute shaping retail AI in 2026 was
identified. The practical consequence is that in North America the buying-office control story is
**contractual and audit-driven, not statutory**: the thing that sells is a defensible record of how a buy
or an allowance was decided, because no regulator defines it for you. That is a weaker forcing function
than EMEA's, and a weaker reason for a client to act — price the engagement on the deduction recovery,
not on compliance.

**Named players:** Amazon Ads and Walmart Connect captured **89.5% of incremental retail-media spending in
2026**, which concentrates the vendor-funds counterparty side of this plane into very few hands.
Commercial planning incumbents to displace or integrate with: Oracle Retail Merchandise Financial
Planning, Blue Yonder, RELEX, Anaplan, Aptos.

### EMEA

- ⏰ **Hardest deadline in any region, and it is 11 days away.** EU AI Act **Article 50** transparency
  duties have applied since **2 August 2026**, and systems already on the market before that date have a
  transitional compliance deadline of **2 December 2026**. Any retailer running AI chatbots, generative
  product imagery or synthetic marketing at EU customers must disclose and label it.
- Note the counter-reading, and carry both: some analyses argue direct obligations fall on whoever *places
  an AI system on the market*, which is rarely a pure online retailer. The Digital Omnibus on AI also
  **postponed several high-risk deadlines to Dec 2027 / Aug 2028**. Article 50 labelling is the near-term
  certainty; high-risk classification is not.
- **The adoption-to-value gap is the sales story:** Retail Economics reports **95% of European retailers
  using or testing AI in marketing/e-commerce, but only 5% achieving scalable ROI**. That 90-point gap is
  precisely a delivery-partner opportunity.
- Platform fit: Shopware (DACH), PrestaShop (France/Southern Europe) — both covered in
  `verticals/solutions.md` with verified licences. GDPR stacks **on top of** the AI Act; neither replaces
  the other.

#### Product-data plane — added 2026-11-22

EMEA is the only region where product data is a **legal** obligation rather than a commercial advantage,
and it has the densest calendar of any region in this KB:

| Date | Instrument | What it does | Confidence |
|---|---|---|---|
| **2026-08-02** (in force) | EU AI Act Art. 50 | Shoppers must be able to tell they are talking to an AI; AI-generated/altered product imagery carries labelling duties. Allegro has required sellers to label such images since Aug 2026. | High |
| **2026-12-02** (10 days after this pass) | EU AI Act Art. 50 | Transitional deadline — **providers must mark AI outputs in a machine-readable format**. | High |
| **2026-08-12** (applies) | PPWR (in force 2025-02-11) | Harmonised packaging labelling, and in some cases a **QR code or standardised digital data carrier**. **PPWR does not itself mandate a DPP** — that comes from ESPR. | High |
| **2026-12-09** | Product Liability Directive | Transposition deadline; extends liability concepts to software and digital products. | Medium |
| **2026-12-30** | EUDR | Deforestation due diligence applies to retailers importing cocoa, coffee, wood or paper **themselves**; micro and small enterprises **2027-06-30**. | Medium-high |
| **2027-02-18** | Batteries Regulation | Battery passport — **the one DPP date that is consistent across every source**. | High |
| 2027 (indicative) | ESPR delegated acts | Iron & steel indicative Q4 2026; **textiles, tyres, aluminium 2027** (one source narrows to Q3–Q4 2027). Acts generally allow ≥18 months before application, so textile compliance lands ~2028–2029. | Low on dates |
| **Already in force (2026-07-19)** | ESPR destruction ban | Destroying unsold clothing is prohibited for large companies. Delegated Regulation **(EU) 2026/296** covers derogations. | Medium |

- **As of November 2026 no ESPR product-group delegated act has been adopted.** Every DPP platform in
  `verticals/solutions.md` is therefore building against a moving target, and any vendor promising
  "DPP compliance" today is selling a bet. The honest pitch is the *prerequisite* work: identifiers,
  attribute completeness, data carriers.
- **Opportunity:** a **single data-carrier programme** that satisfies PPWR labelling, the battery passport,
  EUDR traceability and Sunrise 2027 at once, built on `gs1/GS1_DigitalLink_Resolver_CE` (Apache-2.0) plus
  an EPCIS 2.0 event store (`openepcis/epcis-repository-ce`, Apache-2.0). One identifier programme, four
  compliance budgets. This is the single most fundable retail engagement in the region.
- ⚠️ **Informed gap:** this pass found **no credible EMEA retail AI-adoption rate**. Searching EMEA
  returned compliance detail and essentially nothing on adoption. Yesterday's Retail Economics figure (95%
  of EU retailers using or testing AI vs only 5% at scalable ROI) remains the KB's only datapoint and was
  not re-confirmed today.


#### Added 2026-11-22 (pass 2) — the store plane in EMEA: the mandate is live, and it already passed

**France's e-invoicing mandate went live on 1 September 2026 — 82 days before this pass.** This is the
first EMEA deadline in this KB that is in the *past* rather than the future, and the engagement shape
changes accordingly: the question is no longer readiness, it is remediation.

- **What applies now.** From 1 September 2026 **every VAT-registered business must be able to receive**
  structured e-invoices; **large enterprises and ETIs (mid-caps) must also issue** them and meet
  e-reporting obligations. **SMEs and micro-enterprises have until 1 September 2027 to begin issuing** —
  so the near-term pipeline is SME readiness against a known date.
- **Enforcement is genuinely contested and should be presented as such.** One source states DGFiP will not
  automatically sanction businesses with documented, good-faith implementation problems, and that the
  1 September obligation itself has not been suspended. Another states flatly that **there is no grace
  period in law**. Both can be true — administrative forbearance is not a legal grace period — and a client
  should be told which one they are relying on.
- **France designated DGFiP as the national Peppol Authority in July 2025**, which is why Peppol capability
  and French compliance are now the same engineering problem.
- **Other national rollouts, single-sourced and flagged as such:** Belgium's mandate from **1 January
  2026** and Poland's KSeF large-taxpayer phase from **1 February 2026** come from one timeline source and
  were not confirmed against the Belgian or Polish tax authorities.
- **The horizon is ViDA: 1 July 2030**, when all intra-EU B2B and B2G invoices must be structured
  e-invoices in **EN 16931** format, with Peppol as one route to comply.

**The EU AI Act date that is still imminent.** Article 50 transparency obligations have been in force since
2026-08-02 with a **transitional deadline of 2026-12-02 for systems already on the market — 10 days after
this pass.** The Digital Omnibus postponed the *high-risk* duties to December 2027 / August 2028, so
**Art. 50 labelling is the near-term certainty and high-risk classification is not** — the same reading as
cycle 8, now 10 days from the date rather than 11.

**A claim this pass refuses to carry.** A vendor source states that Germany's 2027 B2B rules include
"**e-Kasa** fiscalisation for B2C retail (aggregated under €3K)". **Recorded as not verified and probably
conflated:** *e-Kasa* is the **Slovak** fiscal-receipt system; Germany's POS fiscalisation regime is
KassenSichV/TSE. Do not put this in a German retail proposal without checking the Bundesfinanzministerium
directly. (Flagged because the €3K aggregation threshold is plausible enough to be repeated.)

**Opportunity, and it is a licence-literacy opportunity.** The reference open-source Peppol Access Point,
`OxalisCommunity/oxalis`, is **EUPL-1.1 or later** — declared in a file called `COPYRIGHT`, invisible to
every SPDX field, badge and source-tree SBOM scan, and reported as `NOASSERTION` by the GitHub API (see
`repos/foundations.md`). EUPL treats *communicating the work* as distribution, so **hosting an access point
as a managed service can trigger source provision much as AGPL would.** Very few delivery partners know
this. Arriving at an EMEA e-invoicing conversation able to explain it — and to offer the Apache-2.0
alternative, `phax/phase4`, which is also the *maintained* one (pushed 2026-11-18 vs Oxalis 2026-04-16) —
is a differentiator that costs nothing to acquire. Carried from cycle 8 and still the strongest EMEA
argument: **Retail Economics reports 95% of EU retailers using or testing AI but only 5% at scalable ROI**
— a 90-point gap that argues for a delivery partner over another pilot.
#### Added 2026-11-22 (pass 3) — retail media in EMEA: AI-generated ad creative is now a labelling problem

EMEA remains the region where the deadlines are real and dated, and this pass
**corrects the scope of the date cycle 8 recorded.**

**EU AI Act Article 50 — the precise shape, because the imprecise version
misleads.** Article 50 transparency obligations have been **in force since
2026-08-02** and were not postponed by the Digital Omnibus (which moved
high-risk duties to Dec 2027 / Aug 2028). Then:

- **2026-12-02** — *ten days after this pass* — is **narrower than "systems
  already on the market must comply"**. It binds **providers of systems that
  generate synthetic content** and were placed on the market before
  2026-08-02, and it covers **Article 50(2) in full: machine-readable marking
  and detectability.**
- It does **not** bind deployers, does **not** cover systems that do not
  generate synthetic content, and does **not** extend to paragraphs 1, 3 and 4
  — **those already apply.**
- **2027-02-02** — providers must implement an interoperability solution for
  watermark detection.

**Why this lands squarely on retail media:** AI-generated **ad creative is
synthetic content**. A retailer whose media network generates creative,
product imagery or virtual models with AI is inside Article 50, and the
machine-readable-marking duty falls on the **provider** of the generation
system while the retailer **deploying** it is already bound by paragraphs 1, 3
and 4. In practice the retailer owns the problem either way, because it is the
one putting the creative in front of a consumer. `compose/patterns.md`
Pattern 17 is the gate that implements this.

**Market and readiness:**

- **95% of European retailers use or test AI** in marketing and e-commerce
  while **only ~5% report scalable ROI** (Retail Economics, via Retail Insight
  Network) — the same ~90-point delivery gap cycle 8 recorded, now confirmed a
  second time from the same lineage of source.
- **McKinsey: €240–320B** of value across European retail over five years from
  end-to-end AI transformation.
- **Deloitte: 56% of European consumers have used AI to shop at least once**
  (n=13,500 across 15 countries), reaching 50% in roughly 18 months — **faster
  than e-commerce or smartphones did.**
- Deloitte expects retail media networks to become central to retailer revenue,
  including expansion into **non-endemic advertising** (selling ad space to
  brands that do not sell in the store).

**⚠️ Informed gap, explicitly not dressed up.** This pass searched for the
**DSA obligations on designated VLOP retail marketplaces** — in particular the
public advertisement repository duty, which would bite directly on large
marketplace retail media — and **could not confirm any of it from the results
returned.** The direction is plausible and commercially important; it is
**unverified here and must not be quoted** until a primary source (the DSA text
and the Commission's VLOP designation list) is read. Recorded as the first
thing a retail media pass in EMEA should close.

#### Added 2026-11-23 — returns & recovery in EMEA: the mandate is live, it is typed, and the code is zero

This is the strongest single finding of this pass. **EMEA is the only region
where the disposition decision is a legal obligation rather than a cost
trade-off, that obligation is already in force, and there is no open-source
implementation of it anywhere on GitHub.**

**ESPR Article 25 — the destruction ban, in force since 19 July 2026.** Under
Article 25 of **Regulation (EU) 2024/1781** (ESPR), large companies are barred
from destroying unsold apparel, clothing accessories and footwear. Reported
details, consistent across several compliance and law-firm sources:

- **Applies from 19 July 2026** for large companies; **medium-sized companies
  from 2030**; **micro and small enterprises exempt** from both the destruction
  ban and the disclosure obligations.
- Implementing measures adopted **February 2026**; derogations set out in
  **Delegated Regulation (EU) 2026/296** — reported to cover dangerous
  products, products legally non-compliant and unfit for purpose, and goods
  proven to infringe IP rights.
- There is a **disclosure obligation** on unsold products alongside the ban.
- The EU's own rationale cites **4–9% of unsold textiles destroyed each year**
  in Europe before ever being worn.
- **Stricter national rules may still apply**, notably **France's AGEC law**.

**The engineering consequence, and it is the detail that makes this a build.**
Sources are explicit that **recycling an unsold garment counts as destruction,
while preparing it for reuse does not**. That single line converts disposition
from a cost ranking into a **legally typed decision tree**: `reuse` and
`repair` are lawful outcomes, `recycle` and `destroy` are the restricted ones
requiring a derogation and a record. A disposition engine for EMEA is therefore
not an optimiser with a compliance report bolted on — the legal type *is* the
primary output, and the cost ranking runs inside it.

And per `repos/foundations.md` → Step 5: `disposition engine` returns **22
repositories worldwide, zero of them relevant**, and
`extended producer responsibility` returns **24 repositories, maximum 1 star**.
A live, dated, pan-EU obligation on large companies has attracted essentially
no open-source implementation. That is the clearest obligation-without-code
result in this knowledge base.

**Right to Repair — Directive (EU) 2024/1799, applying since 31 July 2026.**
Adopted 13 June 2024; Member States had to transpose and apply from **31 July
2026** (EUR-Lex consolidated text carries that date). Further reported detail:

- Transposition is **fragmented**: repair.eu reported around 30 July 2026 that
  only *a handful* of Member States had formally notified completion. Ireland
  did transpose on time, via the European Union (Common Rules Promoting the
  Repair of Goods) (No. 2) Regulations 2026.
- The **European online repair platform** is due by **31 July 2027**; Member
  States must notify at least one repair-promotion measure (e.g. repair
  vouchers) by **31 July 2029**.
- **Commission Delegated Directive (EU) 2026/74** (12 January 2026) added
  domestic local space heaters to Annex II from 31 July 2026.
- A caution worth repeating to clients: the directive does **not** create a
  right to repair every broken product — scope is set by Annex II.

**Two further dates landing in the same window:** the **PPWR** (packaging and
packaging waste) began applying **12 August 2026**, and the **EU AI Act's**
transparency provisions for AI-generated/manipulated content from **2 August
2026** — the latter already recorded in this KB from the retail-media pass. A
revision of the Consumer Protection Cooperation Regulation is expected **Q4
2026**.

**Adoption, and the gap that funds this work.** Retail Economics data
(reported June 2026) has **95% of European retailers using or testing AI in
marketing and e-commerce while only 5% report achieving scalable return on
investment** — a 19:1 ratio between experimentation and realised value. KPMG's
regional survey has the share of organisations expecting to scale AI use cases
rising 29% (2024) → 42% (2025) → **74% (2026)**. Deloitte reports **56% of
European consumers** have used AI to shop at least once.

**The one measured outcome in this plane, and it is European.** Zalando
attributes about **a fifth of its recent revenue growth** to AI-driven
personalisation **and reports cutting its return rate by 7%**. This is the only
quantified AI-reduces-returns result found in the entire pass, in any region —
and note what it implies: the return was prevented at the *recommendation*
step, which is the one step of the reverse flow that is already well equipped.

**Opportunities — EMEA**

- **The ESPR Article 25 disposition evidence engine. This is the flagship of
  the pass.** The obligation is live, it is typed (reuse ≠ recycling), it
  carries a disclosure duty, derogations must be justified per unit, and the
  open-source floor is literally zero. Assemble it from Apache KIE + anomalib +
  a DPP record — see Pattern 18.
- **A per-Member-State policy engine, not a single compliance mode.** Because
  transposition of the repair directive is fragmented and France's AGEC is
  stricter than ESPR, the sellable asset is the **jurisdiction matrix** — the
  same conclusion this KB reached for APAC in the media pass and for
  fiscalisation in the store pass.
- **Repair-management for consumer goods.** A dated EU duty since 31 July 2026
  with **no open-source platform in existence** (`right to repair` on GitHub
  returns automotive tooling). Odoo's `Repairs` app is the only credible
  starting point; see `verticals/solutions.md`.
- **Returns prevention as the proven play.** Zalando's 7% is the number to
  lead with, and it is reachable with the recommendation/personalisation stack
  this KB already documents — not with the empty fit-prediction layer.

#### Added 2026-11-23 (pass 5) — the price plane in EMEA: **what the reference price was**, and the only region with code

**The legal object here is the *reference* price** — the number a discount is
measured against. EMEA is the only region where the price duty has an existing,
well-defined computational form, and consequently the only region where
**open-source code implementing a pricing duty exists at all**.

| Instrument | Status / date | Duty |
|---|---|---|
| Omnibus Directive prior-price rule | In force | A announced reduction must be measured against the **lowest price of the preceding 30 days**. Member-state variation matters: **Poland did not adopt art. 6a(5)**, so each step of a gradual reduction is measured on its own. |
| Price Indication Directive — unit pricing | In force | Net quantity, unit, drained weight, defined exemptions, deposit handling. |
| Personalised-pricing disclosure | In force **since 2022** | Traders must indicate when a price was personalised by automated decision-making — **without** having to explain how it was calculated. |
| **Digital Fairness Act — proposal published 2026-11-11** | **Draft, 12 days old at this pass** | Would **repeal the Unfair Commercial Practices Directive**. Restricts misleading savings claims: a crossed-out price or percentage saving may not be based on an estimated or recommended price (RRP) as though it were a real prior price. Personalised pricing **prohibited where reasonably likely to harm minors or vulnerable consumers** — explicitly *not* a general ban, and *not* a ban on demand-responsive dynamic pricing. |
| DFA **Article 26** — AI shopping agents | Draft | Covers a retailer's own shopping assistant **and** independent agents buying across merchants. Consumers may set criteria for agent purchases, **including a maximum price**. Remedies include compensation, price reduction or contract termination. |

> **Article 26 is the first regulation found in any industry in this KB that
> writes a *price constraint set by the consumer* into the agent's contract.**
> A max-price mandate is not a prompt instruction — it is a term the merchant
> must honour. Every agentic-commerce build in this KB (ACP, UCP, AP2 — pass 1)
> acquires a hard constraint-checking requirement in EMEA if the DFA passes in
> this shape. Draft status flagged: this is a proposal, and law-firm commentary
> is the only source reachable from this session.

**The code, and it is one repo.**
[zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance)
(MIT, 0★, pushed 2026-11-22) implements the Omnibus reference price, unit prices,
GPSR, the withdrawal function of Directive (EU) 2023/2673, and the reviews and
personalised-pricing disclosures. Its design is the part worth copying even
outside Medusa: it **records every price a customer could see** per variant and
pricing context (region, currency, price lists and their schedules), from product
events plus an hourly sweep plus on-demand backfill; it **never edits a recorded
price**; it keeps **≥400 days**; and it **warns when the history is incomplete or
when a "reduced" price is not actually below the reference**. It encodes the
Polish specifics — gradual reductions, goods on offer under 30 days, perishables,
relaunch after a break, the label UOKiK expects — and documents the legal basis
of each rule with sources and dates in `docs/legal.en.mdx`.

**Opportunity, placed.** Two, and they are different sales.
1. **The compliance ledger as a product.** One MIT plugin for one platform in two
   languages is not coverage of a 27-member-state duty. The same engine for
   Saleor, Odoo, Shopware, Spree, Bagisto — plus the member-state matrix — is a
   real, dated, unserved gap, and the DFA's RRP restriction widens it.
2. **Agent price-constraint enforcement (DFA Art. 26).** Nothing in the protocol
   layer this KB tracks enforces a consumer-set maximum price. That is a
   buildable, EMEA-specific component with a named legal driver.

**Market context, provenance flagged.** Retail Economics' figure carried in this
KB from cycle 8 — **95% of EU retailers using or testing AI vs only 5% at
scalable ROI** — is the backdrop: the constraint is delivery capability, not
interest.

#### Added 2026-11-23 (pass 6) — the fulfilment plane

**EMEA has the hardest date on this plane and it is nine days away.**

The **EU Platform Work Directive (2024/2831) transposition deadline is 2 December 2026.** The
Commission declined to move it. As of mid-November 2026 many Member States had not finalised
legislation: Sweden reportedly paused transposition while seeking renegotiation, Hungary had not
started, and France, the Netherlands and Denmark were reportedly targeting 1 January 2027. **Plan for
a patchwork, not a single regime** — the directive's own review of intermediaries and subcontracting
is not due until December 2029.

The Directive's algorithmic-management provisions land directly on last-mile delivery: transparency
about automated systems that assign work and affect pay, and human review of automated decisions.
This is the *same* obligation NYC is enforcing from January 2027 and the *same* thing Brazilian
couriers are demanding (see LATAM below) — three regions, three legal instruments, one engineering
requirement.

**The second EMEA date, and vendors routinely conflate the two instruments:**

| Instrument | What it is | Who it binds | Date |
|---|---|---|---|
| **eFTI** (Reg. (EU) 2020/1056) | Regulatory freight information shared with *authorities* (B2A) | **Authorities must accept** data from certified eFTI platforms | **9 July 2027** |
| **eCMR** | The electronic consignment note, evidence of the *contract of carriage* (B2B) | Businesses, by agreement | Voluntary; industry commentary puts de facto adoption around 2029 |

Use of eFTI is **voluntary for businesses** — 9 July 2027 is an *authority acceptance* date, not a
corporate deadline. Trade press frequently cites 2026 as "the turning point"; the Commission's own
page does not. Treat any proposal built on a 2026 eFTI mandate as mis-sourced.

**Adoption:** McKinsey estimates €240–320bn of value available across European retail over five
years; a global TCS study puts autonomous decision-making at only 24% of retailers. Both are
consultancy figures — directional, not measured.

**Opportunity:** *the compliant dispatch engine*. A permissive routing core (OR-Tools or VROOM with
OSRM/Photon, all Apache/BSD/MIT) joined to an explanation layer that records why each courier got
each job, retains the human-review path, and can produce a per-decision record under whichever
national transposition applies. The routing half is free and solved; the compliance half is the
billable, defensible part — and it is where the open-source floor stops.

**Honest gap:** no EU-level delivery-labour *case law* and no finalised national transposition text
were read in this pass. The 2 December 2026 deadline and the 9 July 2027 eFTI date are well
sourced; the shape of any specific country's implementation is not yet knowable.

#### Added 2026-11-26 (pass 7) — the merchandise planning, buying & trade-funds plane

**The only region where the buying decision carries a statutory explainability hook.** The EU AI Act is
the one real regulatory driver found in any region this pass. Sources disagree on scope and timing —
transparency obligations for AI-generated and AI-manipulated content from **August 2026**, and key
provisions enforced from **2 August 2026** — so *verify against the official text before quoting dates to
a client*. The strategic point survives the date ambiguity: in EMEA, an automated assortment or
allocation decision is the kind of thing a retailer may have to explain, which turns an auditable
open-to-buy ledger from good practice into an asset.

**Value and adoption.** McKinsey estimates end-to-end AI transformation could unlock **€240–320 billion**
across European retail over five years — its own research, and a projection rather than a measured
outcome, so quote it as a frame and not a forecast. Against that, a TCS study found only **24% currently
use AI for autonomous decision-making**. Adoption is bifurcating: larger retailers with real data
infrastructure are moving from pilots into pricing, forecasting and customer experience, while smaller
firms stall on systems integration and investment capacity — which is precisely the segment that cannot
buy Oracle MFP or RELEX and for which an open planning spine is the only route.

**Why the open-source angle lands here specifically.** `frePPLe/frepple` is a European project (frePPLe
bv) with an MIT core, and ERPNext/OFBiz cover the merchandise-master substrate. For a mid-market European
retailer the assembly in `compose/patterns.md` Pattern 30 is not a cost play — it is the *only* way to
get an auditable buy at all.

**Named players:** Manhattan Associates, TTEC Digital, Kaspi.kz (its Kasper assistant), with McKinsey,
Deloitte, KPMG, NVIDIA and TCS as the advisory layer, and NRF Europe and the World Retail Congress as the
venues where this gets discussed.

### APAC

- **Largest stated intent of any region:** Deloitte reports **29% of APAC consumer businesses already
  adopting agentic AI, rising to an expected 76% within two years**, with over half already running live AI
  across IT, security, marketing, sales and support.
- **China is operational, not experimental** — Alibaba, ByteDance and Tencent have agents that buy, book and
  pay; **Alipay launched AI Pay** for accepting payments from autonomous agents in 2026. But it is also the
  strictest regime: mandatory registration, content labelling, penalties up to **¥50M**. Domestic stacks do
  not port.
- **India is the fastest-growing market** (highest CAGR per Fortune Business Insights), with a quoted ~33%
  consumer adoption and ~80% of businesses exploring agents — *quoted estimates, not independently
  verified*. The real constraints are **e-commerce** rules, not AI rules: foreign-ownership limits on
  inventory-led retail, marketplace neutrality requirements, and data localisation. Bagisto (MIT) is the
  natural platform fit.
- **Regulation is fragmented and worth tracking per country:** Singapore's IMDA published an **agentic AI
  governance framework in Jan 2026** (explicitly covering delegation chains and multi-agent coordination —
  the most directly useful document for agent work anywhere); **South Korea's AI Basic Act took effect Jan
  2026**; India's DPDP Act enforcement timeline needs re-checking.

#### Product-data plane — added 2026-11-22

APAC is the region where product identity is being driven by **national GS1 member organisations**, not by
regulators or platforms — a different buying centre from NA or EMEA.

- **India is the clearest opportunity.** GS1 India expanded its Chennai Development Centre specifically for
  AI-enabled supply chain and traceability work including 2D barcode migration; its stated goal is
  widespread standardised 2D adoption **by 2027**. Its 2025-26 annual report describes a pilot with
  **BigBasket's "Fresho"** tracking poultry and meat from farm to packaging to retail. And GS1 India's
  Bijoy Peter is quoted saying adoption *"is happening, but not at full potential"*, with most Indian use
  cases still limited to **inventory and point-of-sale** — i.e. the identifier is deployed and the
  downstream value is not yet built. That is a precisely-placed services gap.
- **Hong Kong / Greater Bay Area:** a November 2026 KPMG China + GS1 Hong Kong study frames retail priorities
  as building trust in AI, serving the silver economy with market-specific strategies, and strengthening
  brand confidence. GS1 HK's CEO argues **AI systems favour products backed by data they can interpret and
  trust** — the clearest regional statement of this pass's whole thesis. GS1 HK already operates `ezTRACK`
  (traceability) and `1QR` (GS1 Digital Link connecting 2D codes to certifications and sustainability data),
  so the integration target is concrete.
- **Mainland China:** Alipay's AI Pay accepts payments from autonomous agents, and Alibaba, Tencent and
  ByteDance all ship AI shopping apps. On traceability, the identified driver is **NMPA drug traceability**
  pushing EPCIS-compatible deployments — **pharma, not retail.**
- **Governance:** Singapore IMDA's *Model AI Governance Framework for Agentic AI* (Jan 2026) remains the
  most directly useful agentic-AI governance document found in any region.
- **Opportunity:** the gap between "2D barcode printed" and "2D barcode used" — GS1 HK's `1QR` and GS1
  India's 2027 target both create identifiers that nothing consumes yet. Consumer-facing resolution
  experiences and traceability analytics on top of existing GS1 member-organisation infrastructure.
- ⚠️ **Informed gaps:** no mainland-China **retail** AI adoption rate and no retail-specific product
  traceability regulation were found this pass. APAC track-and-trace market sizes (China ~$670M, Japan
  ~$400M, India ~$380M, 2026) come from one market-research vendor — directional only.


#### Added 2026-11-22 (pass 2) — the store plane in APAC: Peppol stopped being a European skill

**The single most useful cross-region finding of this pass: Singapore's GST e-invoicing mandate runs on
Peppol.** Businesses submit invoice data to IRAS through "InvoiceNow-Ready Solutions" that must connect to
the **Peppol network via an IMDA-accredited Access Point**, with a Peppol ID tied to the company's UEN.
**The same access-point capability — and the same EUPL-licensed Oxalis codebase — serves both EMEA and
APAC compliance.** One capability, two regions, and a reason to treat the EUPL finding above as global
rather than European.

- **Singapore timeline (IRAS/IMDA, phased):** mandatory adoption began with newly incorporated voluntary
  GST registrants in **November 2025**; since **1 April 2026 all new voluntary registrants** are covered
  and **IRAS can reject a GST registration application that lacks InvoiceNow adoption**. The phased
  extension to *all* GST-registered businesses was announced at the Ministry of Finance Committee of Supply
  Debate 2026 and runs **April 2028 → April 2031**. **Sources disagree on the middle waves** — IRAS's own
  page cites a mid-2026 date for pre-2026 registrants while an IRAS/IMDA-linked summary lists April 2028
  for businesses at or under S$200,000 annual sales. Use IRAS directly for a client commitment.
- **Also carried from cycle 8 and still the best governance document found in any region:** Singapore
  **IMDA's agentic-AI governance framework (January 2026)**, which covers delegation chains and
  multi-agent coordination. Worth reading for every industry, not just retail.
- **Japan — labour shortage is the driver, not customer experience.** Lawson has run AI-enabled "Lawson Go"
  stores since 2022 and worked with CloudPick on computer vision in 2025; government backing for AI and
  robotics in retail in 2026 includes **AI-enabled smart cash registers**. Deployment figures circulating
  for the region (CloudPick in 1,200+ Chinese locations; a 15,000-store FamilyMart/7-Eleven commitment)
  trace to a **single market-research page and are recorded here as unverified**.
- **China — the regional leader, and the strictest regime.** "New retail" from Alibaba and JD.com continues
  through AI-powered unmanned stores and instant-delivery networks; policy support is general
  (New Generation AI Development Plan), not retail-specific. Cycle 8's measurement stands: China has the
  strictest agent rules of any market — registration plus labelling, penalties up to ¥50M.
- **India — the open-source hook is fiscal, and it exists.** Self-checkout and digital payments adoption is
  recent and forecast to grow fastest in the region. The concrete asset is
  [resilient-tech/india-compliance](https://github.com/resilient-tech/india-compliance) (**GPL-3.0**, 286★,
  4725 refs, pushed 2026-11-20) — GST e-invoicing and e-way bills **as an ERPNext module**, the cleanest
  example in retail of compliance shipped inside the ERP rather than beside it. Cycle 8's finding holds:
  India's binding constraint is **e-commerce and FDI law** (inventory-led restrictions, marketplace
  neutrality, data localisation), **not AI law**.
- **Market size — a range, not a number.** One vendor puts APAC AI-in-retail at **US$3.37B (2025) →
  US$4.62B (2026)**; another reports APAC as **24.1% of the global market in 2025**. Cycle 8's Deloitte
  figure (29% → 76% adoption in two years) remains the adoption datapoint. All vendor-sourced.

**Opportunity.** Build the Peppol access-point capability once, sell it in both EMEA and Singapore, and
lead with the licence analysis nobody else brings. For Japan, the store plane's gap list is the pitch: the
smart-register and shelf-vision work has *no* open-source floor (see step 3 in `repos/foundations.md`), and
the driver is a labour shortage that will not reverse.
#### Added 2026-11-22 (pass 3) — retail media in APAC: the profit-engine framing, and real deployments

APAC is where retail media is being described not as an ad channel but as the
margin structure of the business.

- **Deloitte: APAC is "set to lead the agentic future of commerce"** and will
  drive roughly **two thirds of the world's new retail sales over the next five
  years.**
- **Criteo's APAC leadership frames retail media as "a profit engine, not just
  an ad channel"** — the sharpest statement of the thesis found in any region.
- **Named, concrete deployments** (useful because they are checkable, unlike
  most regional claims): **Uber Advertising partnered with Criteo in
  Australia**; **Zepto** (India, quick commerce) is extending its retail media
  **beyond its own app onto the open internet** with AI-personalised campaigns.
- **Bain, from NRF APAC 2026: "the technology is ready, but organizations are
  not."** The constraint is the operating model.
- **Lazada: three in four Southeast Asian e-commerce sellers say they still
  need additional support to adopt AI** — a measured, placed SMB enablement
  gap, and the APAC analogue of the EMEA 95%/5% delivery gap.

**What follows for an APAC engagement.** The open-internet extension Zepto is
doing is exactly the **off-site retail media** problem that the Prebid stack
(`prebid-server`, Apache-2.0, alive) plus an identity layer
(`IABTechLab/uid2-operator`, Apache-2.0, alive) solves with permissive code —
and it is a build, not a licence purchase. The SMB gap points the other way:
**seller-side** tooling that lets a marketplace's merchants buy their own
retail media without an agency, which is a product, not a consulting
engagement.

**⚠️ Informed gap.** Searched for **retail-media-specific regulation** across
APAC this pass and found **none citable** — the results returned adoption and
vendor commentary only. What this KB already holds remains the best available
anchor and applies directly to agent-mediated ad buying: **Singapore's IMDA
agentic-AI governance framework (Jan 2026), covering delegation chains and
multi-agent coordination** (recorded in cycle 8 as the most useful regulatory
document found in any region), plus China's registration-and-labelling regime
and South Korea's AI Basic Act (effective Jan 2026). None of these is
retail-media-specific; **saying so is the finding.**

#### Added 2026-11-23 — returns & recovery in APAC: the volume region, where prevention is the only lever that scales

**The region is where the growth is.** Deloitte (March 2026) projects APAC
will drive roughly **two thirds of the world's new retail sales over the next
five years**, and finds **~29% of retailers adopting agentic AI today, rising
to an expected 76% within two years**. Adyen (July 2026) reports the consumer
side lagging that enthusiasm: only **30% of consumers currently feel
comfortable letting an AI agent complete a purchase** on their behalf.

**Why returns behave differently here.** Deloitte notes APAC pioneered the
models now being exported globally, and that **social and livestream commerce
have become mass-market**. Livestream and social selling are impulse-weighted
and apparel-weighted, which is the highest-return-rate combination in retail.
That puts APAC's pressure on **Step 1 — prevention** rather than on
disposition, and Step 1 is precisely the empty step: `size recommendation
fashion` returns **73 repositories, the best of them 9★ and unlicensed**.

**⚠️ A source trap specific to this region — do not repeat it in a deck.**
A KPMG APAC figure reads *"more than half of retailers report returns
exceeding 10% from AI initiatives, with around one in five achieving returns
above 30%"*. Those are **returns on investment**, not merchandise returns.
Quoted in a returns-reduction deck it would be a flat factual error. KPMG
separately reported (April 2026) on APAC retailers deploying AI for **loss
prevention**, which *is* on-topic for this plane. The ambiguity of "returns"
is a property of this industry's vocabulary, and it corrupted the code search
in the same pass — see `intel/trends.md`.

**Regulation: an informed gap, stated rather than left silent.** Coverage of
NRF APAC 2026 and Deloitte's regional work both name **government regulation,
physical infrastructure and digital access** as the named obstacles, but
neither supplies a returns-specific or disposition-specific rule for any APAC
jurisdiction. **This pass found no APAC analogue to ESPR Article 25 and no
dated reverse-logistics mandate anywhere in the region.** That is a measured
absence, not an unexplored area: it means the APAC sale is an economics and
customer-experience sale, not a compliance sale. China's 7-day no-reason
return rule is widely described in secondary commentary but **was not verified
to a primary source in this session** (see the channel note below) and is
therefore not asserted here as a finding.

**Opportunities — APAC**

- **Returns prevention for livestream and social commerce.** The region's
  dominant channel generates the returns, and the fit-prediction layer that
  would stop them does not exist in open source. Highest-volume opportunity in
  this plane, and the only one that is a genuine build-from-scratch.
- **Reverse routing at density.** APAC's urban density is where the VRP stack
  pays off hardest; `or-tools`, `vroom` and `osrm` are all Apache-2.0/BSD-2 and
  all pushed within the last week.
- **Loss prevention, following KPMG's April 2026 signal.** Deployment is
  already under way regionally, and the open-source fraud toolboxes are dead —
  same structural opening as North America, without the chargeback overlay.
- **Agent-readiness gap as advisory.** 29% of retailers adopting agentic AI
  against 30% of consumers willing to let an agent buy: the mismatch is the
  consulting conversation, and the post-purchase flow (tracking, returns) is
  where Forrester expects agents to be accepted first.

#### Added 2026-11-23 (pass 5) — the price plane in APAC: **whether the whole price was shown**

**The legal object here is *completeness*** — not who gets the price, not what it
is measured against, but whether the number shown is the number paid. APAC
regulates **drip pricing and component pricing**.

| Jurisdiction | Instrument | Status / date | Shape |
|---|---|---|---|
| Australia | **Competition and Consumer Amendment (Unfair Trading Practices) Act 2026** | Passed, **Royal Assent received**; drip-pricing, unfair-trading and subscription provisions **commence 2027-07-01** | Transaction-based charges — charges *other than* the price of the goods, payable in connection with supply — must be displayed **at the same time as** the price. **Does not apply to offers made to businesses.** Sources disagree on the passage date (1 vs 2 July 2026); commencement is consistently reported as 2027-07-01. |
| Australia | Australian Consumer Law **s 48** (component pricing) | **Already in force** | Prohibits stating a partial price without prominently specifying the single total price. The pre-2027 obligation that already binds. |
| Australia | ACCC enforcement | **Live now** | Dendy Cinemas fined **A$19,800** for alleged drip pricing (mid-2025); **EconomyBookings** issued two infringement notices totalling **A$39,600** for misleading pricing conduct (**January 2026**). Manipulative digital-market practices — subscription traps, drip pricing, dark patterns — named an enforcement priority. |
| China | Algorithm rules by service type (recommendation, deep synthesis, generative AI, labelling) | In force; comprehensive AI Law reported in preparation, **not enacted** | Penalties run through existing cybersecurity and content law rather than a dedicated AI fine schedule. On price specifically: the state market regulator is reported to have **summoned the five largest e-commerce platforms over a "price war" in June 2026** — **vendor-blog source only, treat as unverified**. |
| India | Consumer-protection statutes, dark-pattern guidelines, algorithmic due diligence on significant data fiduciaries | In force, indirect | Price is reached **through** consumer-protection and data law, not a pricing rule. MeitY AI guidelines are non-binding; synthetic-content labelling is binding. |

**Informed gaps, written down rather than dressed up.**
- **No Australia-specific rule on *algorithmic* pricing** was located — the UTP
  regime is about disclosure of the full price, not about how the price was
  computed. That distinction matters and is easy to blur.
- **India's e-commerce pricing rules were searched and not found.** Two targeted
  queries returned Australian material only. Treat as *"not researched to a
  conclusion"*, not *"nothing exists"*. Cycle 8's finding that India's binding
  constraint is **e-commerce law (FDI limits on inventory-led retail, marketplace
  neutrality, data localisation) rather than AI law** remains this KB's best
  India answer, and it is from a prior pass.
- **Japan, South Korea and Singapore returned nothing on price.** Singapore's
  IMDA agentic-AI governance framework (Jan 2026, found in cycle 8) remains the
  region's most useful agent document, but it does not address pricing.

**What this means for a build.** The APAC artefact is a **quote-time fee
composition**: every transaction-based charge resolved and displayable at the
moment the price is shown. That is an engineering requirement on the *checkout
and quote path*, not on the pricing model — a different subsystem from EMEA's
ledger and NA's input log. And because it excludes B2B offers, a wholesale
surface and a consumer surface can lawfully differ.

**Opportunity, placed.** The commencement date is **2027-07-01**: far enough out
that remediation programmes are being scoped now, near enough that they are
funded. Australia is the clearest "assess, then remediate the quote path"
engagement on this plane, and s 48 plus live ACCC enforcement means the pre-2027
exposure is already real.

#### Added 2026-11-23 (pass 6) — the fulfilment plane

**APAC is the only region where last-mile delivery itself is an open protocol.**

India's **ONDC Open Delivery Protocol** lets a seller, brand or marketplace reach many last-mile
providers through a single integration, rather than integrating each carrier separately. Verified
events in 2026: **India Post booked and delivered its first ONDC order on 13 January 2026**, acting
as the logistics service provider across first-mile pickup to metro last-mile; **Uber launched Uber
Direct on ONDC in Bengaluru**, serving partners including Zepto; and EV fleet operator **Bounce
joined the Open Delivery Protocol**. ONDC reports passing 500 million cumulative transactions, with
200,000+ retail merchants active by July 2026 and 80,000+ merchants using ONDC Logistics
specifically. The network-scale figures are ONDC's own and should be labelled as such.

**The licence finding that decides how to engage.** The protocol specs are **not** open-source
licensed, unlike every Western agentic-commerce standard this KB tracks:

| Spec | License | Stars | Last push |
|---|---|---|---|
| https://github.com/beckn/protocol-specifications | **CC BY-NC-SA 4.0** — NonCommercial, ShareAlike | 456 | 2025-10-10 |
| https://github.com/ONDC-Official/ONDC-Protocol-Specs | **CC BY-ND 4.0** — NoDerivatives | 146 | 2025-01-31 |
| UCP / ACP / AP2 / x402 (for contrast) | Apache-2.0 | — | — |

The **implementations are permissive**: `beckn/beckn-onix` is MIT (101★, 2026-11-19) and Google
Cloud's `dpi-accelerator-beckn-onix` is Apache-2.0 (11★, 2026-11-13). So the build path is clean.
The operative rule for a studio: **build on ONIX; do not vendor, fork or re-publish the specification
text inside a client deliverable**, and do not publish a "profiled" ONDC spec — ND forbids
derivatives of the document. Writing software to a published spec is a different act from copying the
spec, and only the second is restricted here.

**Adoption:** Deloitte puts agentic AI adoption in APAC retail at 29% today rising to a projected 76%
within two years, and expects the region to drive about two-thirds of new global retail sales over
five years. Singapore remains the most useful regulatory jurisdiction for agent work — its IMDA
agentic-AI governance framework (January 2026, recorded in cycle 8) covers delegation chains and
multi-agent coordination, which no other region has published.

**Opportunity:** *be the ONIX integrator*. The single-integration-to-many-carriers model is exactly
the problem every other region solves with per-carrier plugins (see `repos/foundations.md` Step 6,
where the global result is zero carrier-neutral libraries). An MIT reference node plus a client's
carrier contracts is a deliverable; the protocol expertise is the moat.

**Honest gap:** no independent verification of ONDC logistics *order volumes* was found — only
network-level claims and partner announcements. China and Japan were not measured on this plane in
this pass; Japan's driver-hours constraint and China's instant-retail logistics are named here as
unexamined, not as covered.

#### Added 2026-11-26 (pass 7) — the merchandise planning, buying & trade-funds plane

**The largest prize and the worst substrate.** Deloitte's March 2026 report (released in Hong Kong,
30 March 2026) puts Asia-Pacific on course to drive **about two-thirds of the world's new retail sales
over the next five years**, with agentic AI adoption going from **~29% today to 76% within two years** —
survey-based, so directional. That makes APAC the region where a planning engagement has the most volume
behind it.

**But the binding constraint here is upstream of the buy.** KPMG names **fragmented omnichannel data** as
the limit on AI adoption in APAC retail, and Deloitte flags gaps in regulation, physical infrastructure
and digital access. An open-to-buy cannot be planned on a merchandise master that does not reconcile
across channels. **Sequence APAC engagements accordingly: product-data reconciliation first (see the
product-data plane above), planning second.** Selling an assortment optimiser into fragmented master data
is how this plane fails here, and the solver is never the reason.

**Regulation — informed gap.** Singapore emphasises **voluntary, accountability-based AI governance over
prescriptive regulation**, and IMDA with Enterprise Singapore have launched digital solution categories
to help retail SMEs adopt AI — which makes Singapore the easiest APAC entry point for an auditable
planning build, since accountability frameworks reward exactly the audit trail Pattern 30 produces.
**No specific current retail-AI regulation for China, Japan or Australia was found this pass.** Gap, not
absence.

**Consumer trust is a live constraint:** 53% of consumers globally are very or extremely worried about
privacy (KPMG, same source) — relevant because the buy side touches supplier and vendor data more than
consumer data, which is an argument for starting agentic work in the buying office rather than the
storefront.

**Named players:** Alibaba, Lazada and the super-apps (Grab) lead the agentic push; Fainders.AI launched a
cashier-less MicroStore in South Korea in 2024. NRF APAC 2026 ran in Singapore, 2–4 June, with agentic AI
dominating the agenda.

### LATAM

- 🎯 **The clearest, best-evidenced opportunity in this file.** An April 2026 scan of **75 LATAM e-commerce
  sites** found that **AI agents can browse LATAM stores but cannot buy from them.** Demand-side adoption is
  the highest in the world while the merchant side is unreachable. That is a concrete, scoped engagement:
  make the checkout agent-completable (UCP/ACP + Pix).
- **Conversational commerce is the channel, not a side channel.** Brazil: an Opinion Box survey of 1,126
  users found **82% already talk to brands on WhatsApp and 60% have purchased through it**. Mexico: AIMX
  2026 puts WhatsApp at **91% active presence** among internet users, while **AMVO reports e-commerce at
  just 17.7% of retail sales** — the gap between messaging reach and e-commerce share *is* the opportunity.
- **The payment rail is already there:** Pix integrates natively into WhatsApp chats in Brazil; Mexico added
  QR payments inside WhatsApp Business in 2025. `bacen/pix-api` is the spec — but it has **no LICENSE
  file**, so generate clients from it rather than vendoring it.
- **Regulatory opening, Brazil:** competition authority **CADE** found Meta's ban on rival AI chatbots in
  WhatsApp anticompetitive, and WhatsApp reportedly opened to rival AI chatbot providers in Brazil from
  **2026-03-06**. *Not verified against CADE or Meta primary sources — confirm before building a client
  strategy on it.* Mexico's relevant regime is **LFPDPPP**; we found no Mexico-specific rules for AI agents
  on messaging channels, and no current status on a data-protection update.
- ⚠️ **Source-quality warning specific to this region:** LATAM figures come overwhelmingly from vendors with
  an interest in the outcome, and they contradict each other — Brazil's WhatsApp user base is given as both
  **165M and 197M**, Mexico's penetration as both **73% and 94.3%**, and a widely repeated "$18.2B WhatsApp
  AI commerce" figure traces only to vendor blogs. Earlier cycles of this KB quoted several of these as
  settled fact. Verify against AMVO, AIMX or Euromonitor before putting any of it in a client deck.

#### Product-data plane — added 2026-11-22

- **The regional institution is active and measurable.** GS1 LATAM created the *Premio a la Excelencia
  GS1 LATAM 2026* for projects combining GS1 standards with AI, machine learning, 2D codes, blockchain and
  automation, awarded **2026-11-10 in São Paulo** — i.e. there is now a regional shortlist of named
  reference projects to mine for partners and case studies.
- **The most useful single number found for LATAM this pass:** GS1 México reports that roughly **3,000
  companies per year request a barcode for the first time, most of them small.** That is a continuously
  replenished population of merchants who have *just* acquired an identifier and have nothing built on it —
  the cleanest entry point in the region, and consistent with yesterday's measured finding that agents can
  browse LATAM e-commerce sites but cannot buy.
- **Adoption, honestly stated:** one LATAM analysis places retail and e-commerce **second in AI adoption
  behind financial services**, while noting that most pilots have not reached production. Its spend-growth
  figure carries an unresolved `[VERIFY]` marker in the source itself and is therefore **not** reproduced
  here.
- **Sunrise 2027 reaches LATAM through the trade press,** which correctly notes that a GS1 Digital Link QR
  can carry lot, expiry date and origin — the attributes that make traceability and freshness claims
  possible in grocery, the region's largest retail segment.
- **Opportunity:** "**identifier to shelf**" — take a merchant who has a GTIN and nothing else, and deliver
  the full step 1→3 chain: resolver (`gs1/GS1_DigitalLink_Resolver_CE`, Apache-2.0), attribute completeness
  rules (`pandera`, MIT), and a UCP/ACP-ready feed. Low ticket, high volume, repeatable across the 3,000/yr
  Mexican cohort and its Brazilian equivalent, and it closes the browse-but-cannot-buy gap from the
  merchant side.
- ⚠️ **Informed gap:** no quantitative data linking LATAM AI adoption to traceability was found, and no
  retail-specific AI norms. Regional AI regulation (Brazil PL 2338 / ANPD; Mexico LFPDPPP / INAI guidance on
  automated decisions) is sourced only to a consultancy marketing blog — unverified, and it should be
  checked against the Brazilian Congress and INAI before client use. Yesterday's warning about
  contradictory LATAM vendor figures applies here unchanged.


#### Added 2026-11-22 (pass 2) — the store plane in LATAM: the region is *ahead* here, and it is measured

**For a fourth consecutive industry pass, LATAM out-evidenced its own narrative — and this time it is not
close.** Fiscalisation is the best-equipped layer in the entire retail open-source landscape, and
**Brazil and Mexico have the largest and most permissive fiscal corpora of any region measured**:

- 🇧🇷 **Brazil NF-e — the largest open-source fiscal corpus found anywhere.**
  [nfephp-org/sped-nfe](https://github.com/nfephp-org/sped-nfe) **LGPL-3.0**, 1635★, pushed 2026-11-13;
  [wmixvideo/nfe](https://github.com/wmixvideo/nfe) **Apache-2.0**, 770★ / 411 forks, 2026-11-16;
  [TadaSoftware/PyNFe](https://github.com/TadaSoftware/PyNFe) **LGPL-3.0**, 599★;
  [nfewizard-org/nfewizard-io](https://github.com/nfewizard-org/nfewizard-io) GPL-3.0, 330★, 2026-11-08.
  Four maintained implementations across Java, PHP, Python and Node.
- 🇲🇽 **Mexico CFDI — the most permissive fiscal stack in retail, full stop.**
  [phpcfdi/sat-ws-descarga-masiva](https://github.com/phpcfdi/sat-ws-descarga-masiva) **MIT** 198★;
  [SAT-CFDI/python-satcfdi](https://github.com/SAT-CFDI/python-satcfdi) **MIT** 169★;
  [eclipxe13/CfdiUtils](https://github.com/eclipxe13/CfdiUtils) **MIT** 146★;
  [phpcfdi/resources-sat-catalogs](https://github.com/phpcfdi/resources-sat-catalogs) **Unlicense** (public
  domain) 97★ / 424 refs. A Mexican fiscal integration can be built with **zero copyleft obligation**.
- 🇨🇱 **Chile is the hard case, and the gap is specific.** The only maintained DTE core,
  [LibreDTE/libredte-lib-core](https://github.com/LibreDTE/libredte-lib-core), is **AGPL-3.0** (228★ / 166
  forks). Its LGPL-3.0 API clients call LibreDTE's **hosted** service, so "permissive" there means
  depending on someone else's SaaS. And `factura electronica DTE SII stars:>=20` returns **0 results** —
  there is no alternative to find.

**⚠️ The AGPL inversion lands hardest in LATAM.** Cycle 8's most useful commercial fact — *Odoo is LGPL-3.0,
so proprietary modules are allowed* — **does not survive contact with LATAM compliance.** The OCA
localisations that make an Odoo POS lawful are each **AGPL-3.0**: `OCA/l10n-brazil` (376★),
`OCA/l10n-mexico` (20★ / **56 forks**), `OCA/l10n-chile` (10★ / **41 forks**). Full analysis and the three
mitigations are in `verticals/solutions.md`; the one-line version is **keep fiscal issuance behind a
process boundary, or build it on the permissive national libraries instead.**

**A measured gap, written down because it is exactly what a Chilean or Brazilian store engagement needs:**
there is **no permissively licensed open-source POS with a LATAM fiscal module.** The one repo that targets
precisely that shape — `dansanti/l10n_cl_dte_point_of_sale`, "Boleta / Factura Electrónica para Punto de
ventas Odoo" — has **no licence file and has been dead since 2018-06-14**. The till exists (MIT), the
fiscal libraries exist (MIT/Apache/LGPL), **the join between them does not.** That join is a small, cheap,
high-leverage piece of Globant IP.

**Regulation — dated and concrete.** Brazil's **PL 2338/2023** passed the Senate in December 2024 and was
still pending in the Chamber of Deputies as of May 2026; **ANPD runs an AI regulatory sandbox with three
companies until December 2026** — a named, dated window worth watching. **Mexico has no specific AI law**;
a Senate bill introduced April 2025 has seen no significant progress. The regional map is fragmenting
rather than converging: Brazil's bill, Chile's framework, Colombia's CONPES on AI and Mexico's sectoral
rules are all moving at different speeds.

**Adoption.** Retail is the **second-ranked LATAM sector for enterprise AI**, behind financial services,
with demand forecasting and recommendations as the main use cases; the 2026 shift reported is from
recommendation engines toward autonomous agents handling **returns, post-sale service and B2B
procurement** — note that two of those three are *post-purchase*, a plane this KB still has thin coverage
of. Carried from cycle 8 and still the best-placed LATAM datapoint: an **April 2026 scan of 75 LATAM
e-commerce sites found agents can browse but cannot buy.**

**Caveat carried forward, deliberately.** LATAM vendor figures contradict each other (Brazil WhatsApp users
165M vs 197M; Mexico penetration 73% vs 94.3%; the "$18.2B" WhatsApp-commerce figure traces only to vendor
blogs) and **cycles 3 and 7 of this KB quoted them as settled fact.** The fiscal measurements in this
section are different in kind: they are repository-level facts, re-measured on 2026-11-22 by reading
licence files and `ls-remote` ref counts, not vendor claims.
#### Added 2026-11-22 (pass 3) — retail media in LATAM: the clearest market, with a named conflict of interest

LATAM retail media is the most structurally legible of the four regions and the
most hazardous to source, because the best figures come from the company that
dominates it.

- **Mercado Libre has held more than half of Latin America's retail media ad
  spend since 2022** (EMARKETER).
- **Brazil and Mexico together will account for 82% of LATAM retail media
  investment in 2026** (Mercado Ads).
- **Growth roughly 42% in Brazil and 40% in Mexico — about twice the global
  average** (EMARKETER).
- In **Mexico**, Mercado Libre's serious rivals are **Walmart and Amazon**;
  Brazil's market is the larger of the two.

**⚠️ Name the conflict of interest, because the numbers above depend on it.**
The EMARKETER report carrying the Brazil/Mexico growth figures was **produced
in collaboration with Mercado Ads** — i.e. the headline sizing of LATAM retail
media is co-authored by the company holding **>50% share** of it. That does not
make the figures wrong; it makes them **directional and interested**, and they
must always be cited with the collaboration attached. This is the third
consecutive retail cycle in which LATAM's narrative rested on vendor-supplied
numbers: cycle 8 found `$215.31B LATAM` and `WhatsApp $18.2B` carried as
settled fact from earlier cycles with no source, and contradictory vendor
figures for Brazilian WhatsApp users (165M vs 197M) and Mexican penetration
(73% vs 94.3%).

**Flagged, not promoted:** a single secondhand blog claim of **>50% YoY Mercado
Ads revenue growth in Mexico, Brazil and Argentina.** One source, not
independently verified. Recorded here so a later cycle does not find it
elsewhere and promote it to fact — which is exactly how `$18.2B` entered this
KB.

**What follows for a LATAM engagement.** The concentration is the opportunity's
shape: with one player above 50%, **every other retailer in the region is
either outside retail media or buying into Mercado Ads' surface**, and the
second tier has no network of its own. Combined with cycle 8's measured LATAM
finding that **agents can browse but cannot buy on 75 scanned LATAM e-commerce
sites** (April 2026), the regional play is the full stack a second-tier
retailer lacks: make the catalogue agent-readable, then make the inventory
agent-sellable (`compose/patterns.md` Patterns 15–16). The permissive Prebid +
UID2 + Meridian combination is buildable today and carries no licence fee into
a price-sensitive market.

**⚠️ Informed gap.** Searched for **retail media regulation in Brazil and
Mexico** and found **nothing** — not advertising rules, not platform rules, not
retail-media-specific data rules. One source mentioned "evolving data privacy"
with no detail. Brazil's LGPD and Mexico's federal data-protection regime
obviously apply to audience matching, but **this pass cannot cite a
retail-media-specific obligation in either country, and says so rather than
implying coverage.**

#### Added 2026-11-23 — returns & recovery in LATAM: a shorter statutory clock than the EU, and a logistics cost problem

**Market.** Latin America is reported as the fastest-growing retail
e-commerce region, at roughly **$191B in 2025**, with **Brazil and Mexico
together accounting for over 55% of volume**.

**The statutory clock is shorter here than in Europe, and that is the design
constraint.** Brazil's Consumer Defence Code **Article 49 (CDC)** gives a
**7-day right of withdrawal**, counted from receipt of the product for
distance sales — against the EU's 14 days. Reported detail worth carrying into
a build:

- The right applies to contracts concluded **outside the commercial
  establishment**, and majority doctrine and case law extend it to
  **e-commerce**, on the reasoning that the consumer had no physical access to
  the product before buying.
- It does **not**, as a rule, apply to in-store purchases — those depend on
  each retailer's own exchange policy.
- **An opened package is not an express exception** in Article 49. Refusing a
  withdrawal solely because packaging was opened is not supported by the text.

**The engineering consequence:** a 7-day clock running from delivery, with no
opened-package defence, means the **authorisation step must be automated and
fast** — there is no room for a multi-day manual review. That is the opposite
emphasis from EMEA, where the pressure is on evidencing the *disposition*
weeks later. Mexico's PROFECO regime and each country's distance-selling rules
need the same treatment per jurisdiction.

**Cross-border customs shape the reverse flow more than returns law does.**
Mexico handles cross-border e-commerce under a simplified import regime with
rates by country of origin; Argentina uses a small-shipments courier regime;
Brazil layers federal and state taxes with detailed customs documentation. A
returned cross-border unit is a **re-import**, and that, not consumer law, is
what makes LATAM reverse logistics expensive.

**What the market is actually doing about cost:** sources point to automated
collection points, **locker networks**, and third-party/alliance partners as
the mechanisms for cutting last-mile and returns cost, and describe returns
policy as becoming a **trust and loyalty factor** rather than a pure cost
line. Reverse logistics' environmental footprint is named as a driver, without
a specific rule attached.

**⚠️ Informed gap — stated explicitly, because silence would look like
coverage.** This pass **found no primary-source 2026 returns or
reverse-logistics regulation** for Brazil, Mexico, Colombia or Chile, and **no
new consumer-protection or reverse-logistics mandate** in the region. The
Article 49 detail above rests on Brazilian legal commentary, trade press and
law-firm material — **not** on the Planalto statute text, which could not be
fetched in this session (see the channel note). Before any of this enters a
client deliverable, Article 49 must be read against the official Planalto text
and Mexico's requirements against PROFECO. Treat the region as **"no mandate
found", not "no mandate exists."**

**Opportunities — LATAM**

- **Fast statutory authorisation.** A 7-day clock with no opened-package
  defence is a straightforward, high-volume automation: authorise inside the
  window or lose the argument. Pairs with the Mage-OS MIT RMA module, the only
  permissively licensed RMA component in existence. See Pattern 21.
- **Locker-network consolidation routing.** The region's chosen cost remedy is
  collection points, and consolidating reverse pickups across lockers is
  exactly a pickup-and-delivery VRP — `vroom` + `osrm` (both BSD-2) or `PyVRP`
  (MIT). This is the single most direct fit between a verified repo and a
  stated regional need found in this pass.
- **Re-import cost modelling.** The expensive part of a LATAM return is
  customs, not consumer law. A duty/landed-cost model attached to the
  disposition decision is differentiated advisory work.
- **Returns policy as loyalty instrument.** Positioned as retention rather
  than compliance — the regional framing the sources actually support.

#### Added 2026-11-23 (pass 5) — the price plane in LATAM: **where the money goes**

**The legal object here is *decomposition*** — and it is genuinely different from
the other three regions. Brazil does not ask who got the price, or what it was
measured against, or whether it was complete. It asks **how the money is split**.

| Jurisdiction | Instrument | Status / date | Duty |
|---|---|---|---|
| Brazil | **Senacon Portaria nº 61/2026** | Issued **2026-03-24**, effective **2026-04-23** (30 days from publication to comply) — **in force ~7 months** | Transport and delivery platforms must show, **in each transaction**, how the amount paid is divided among the **platform, the driver/courier, and the establishment**. |
| Brazil | Senacon/DPDC technical note (Nota Técnica nº 3/2026) | Published 2026 | Legal basis: platforms use proprietary algorithms to set the final price, allocate service, evaluate performance and split the price among participants. States that **opacity about price composition may constitute an abusive practice** where it impedes consumer understanding of the price. |
| Mexico | Profeco review of dynamic tariffs | **Requested February 2026** by the President; **no enacted norm found** | Directed at Uber/Didi dynamic fares. An announced intention, not a duty. |

**The stated intent is the useful part:** *"A proposta não é acabar com o preço
dinâmico, mas torná-lo mais compreensível"* — the aim is not to end dynamic
pricing but to make it comprehensible. LATAM's duty is therefore **additive, not
restrictive**: it does not constrain the pricing model at all, it constrains the
*explanation*. That is the cheapest of the four regional duties to satisfy and
the one most easily retrofitted — provided the price was composed from
attributable parts in the first place, which is exactly what a monolithic
"final price" field prevents.

**Informed gaps, explicit.**
- **Portaria 61/2026 binds transport and delivery platforms, not retailers
  generally.** Extending it to retail is an inference, not a finding. Stated
  here as a *shape that regulators in the region have chosen*, which is useful
  for anticipating the next instrument — not as a current retail obligation.
- **PL 2338/2023 (Brazil's AI bill) was searched and not found** in relation to
  pricing. Two targeted Portuguese-language queries returned Senacon's
  transport/delivery material instead.
- **Profeco's position on personalised pricing was searched and not found.**
  Mexico has an announced review and no instrument.
- **No dynamic- or personalised-pricing instrument was found for Argentina,
  Colombia or Chile.** Not searched to exhaustion. Record as *"no instrument
  found"*, never *"no instrument exists"*.
- **A counter-caution from cycle 8 still applies and is worth repeating here,
  because this plane is full of vendor numbers:** LATAM figures in this KB have
  contradicted each other before (Brazil WhatsApp users 165M vs 197M; Mexico
  penetration 73% vs 94.3%), and earlier cycles quoted them as settled fact.
  The **"5–15% revenue uplift from dynamic pricing"** figure that recurs in
  Brazilian trade press is attributed to McKinsey through vendor blogs, with no
  reachable primary source. **Directional at best.**

**Opportunity, placed.** Two.
1. **Price decomposition as an architecture, sold as transparency.** A retailer or
   marketplace in Brazil that can attribute every component of a displayed price
   to a recipient satisfies Portaria 61 at the surface and gains the substrate
   for margin analytics underneath. The same ledger serves both; almost no
   commerce platform stores price this way by default.
2. **Marketplace price-split tooling for the delivery/quick-commerce segment**,
   which is where the obligation actually bites today and where the region's
   engineering spend already concentrates (this KB's WhatsApp-commerce findings
   from cycle 8 sit on the same surface).

#### Added 2026-11-23 (pass 6) — the fulfilment plane

**For the fourth industry pass running, LATAM out-evidenced its own narrative — and this time it is
the strongest result on the plane.**

The carrier hand-off step measures as **zero worldwide**: `shipping carrier label api stars:>=100`
→ 0, `shipping label carrier stars:>=30` → 0, `tracking number carrier stars:>=50` → 0. That step is
**filled for six LATAM countries in one MIT-licensed, actively maintained repository**,
https://github.com/codespar/mcp-dev-latam (279★, pushed 2026-11-13), already shaped as MCP tools for
agents. Verified by cloning the repo and reading the tool definitions:

| Package | Country | Tools |
|---|---|---|
| `packages/ecommerce/melhor-envio` | Brazil | `calculate_shipping`, `create_shipment`, `generate_label`, `get_tracking_history`, `list_agencies`, `cancel_shipment` |
| `packages/ecommerce/correios` | Brazil | `calculate_shipping`, `buy_label_range`, `create_prepost`, `create_reverse`, `find_cep` |
| `packages/ecommerce/superfrete` | Brazil | multi-carrier freight |
| `packages/mexico/skydropx` | Mexico | multi-carrier shipping |
| `packages/argentina/andreani` | Argentina | carrier integration |
| `packages/colombia/coordinadora` | Colombia | carrier integration |

`create_reverse` also fills part of the returns plane's empty "authorize the return" step from pass 4.

**The regulatory surface, and it changes delivery unit economics directly.** Brazil:

- A rule in force since **3 April 2026** grants motorcycle couriers a **30% hazard-pay supplement**
  (periculosidade), amending the traffic code and Law 12.009/2009. Press coverage notes it does *not*
  reach platform couriers working through iFood, Uber or 99 — so the cost lands unevenly across
  employment models rather than uniformly across the market.
- **PLP 152**, the platform-work bill, remained unresolved at last reading. Its draft pays the full
  minimum rate only for the *first* delivery in a multi-order trip (50% for the second, 25% for the
  third); courier organisations are demanding full pay per delivery **and algorithmic transparency** —
  the "caixa preta" (black box) of the apps.
- **Senacon**, the consumer authority, began monitoring payment transparency at delivery and
  ride-hailing apps in **April 2026**, giving companies 30 days to adapt, with fines or suspension for
  non-compliance.

Note the convergence: Brazil's couriers are demanding the same algorithmic transparency that the EU
Platform Work Directive mandates from 2 December 2026 and that NYC enforces as just-cause deactivation
from January 2027. **One engineering requirement, three regions, three legal vehicles.**

**Opportunity:** *the agent-reachable LATAM delivery leg*. The region's carrier layer, fiscal document
layer (NF-e) and payment rail (Pix) are all reachable through permissive, agent-shaped code today.
A storefront that can quote freight, print the label, emit the fiscal document and track the parcel —
all through MCP tools under MIT — is buildable now in Brazil and Mexico and is not buildable from
open source in the United States or Germany. Sell it as what it is: a regional capability advantage,
not a localisation task.

**Honest caution, carried forward from cycle 8:** LATAM vendor statistics in this sector contradict
each other (Brazilian WhatsApp user counts of 165M vs 197M; Mexican penetration 73% vs 94.3%) and
earlier cycles of this KB quoted some as settled fact. The findings above are deliberately of a
different kind — repository contents and dated legal instruments, both re-checkable — rather than
market-size claims. The one adoption figure quoted this pass for the region (Adyen: 42% of Mexican
consumers using AI assistants when shopping, up from 15% a year earlier) comes from a single vendor
survey and is labelled accordingly.

#### Added 2026-11-26 (pass 7) — the merchandise planning, buying & trade-funds plane

**Consumer-side adoption is sprinting; the platform layer underneath is measurably broken.** The Adyen
Retail Report 2026 found **42% of Mexican consumers now use AI assistants when shopping, against 15% a
year earlier**. Regionally, **38% of LATAM companies have implemented generative AI but only 23% generate
measurable economic value**. And Retail Garage 2026 (Google Cloud with R/GA) found that **80% of major
Latin American e-commerce platforms show critical deficiencies in technical performance and AI
adoption**.

Read those three together and the conclusion is uncomfortable but useful: in LATAM the demand signal has
arrived ahead of the systems, and the gap between 38% implementing and 23% getting value is where the
services work actually is.

**Market pull is the strongest of any region.** Euromonitor projects Mexican retail sales **+40% over
five years, 15 percentage points above the LATAM average**, with e-commerce **+58%** over the same period.
Walmart (through its OpenAI partnership) and Alibaba have launched AI-first shopping modes, pushing
Mexican merchants toward generative engine optimisation; Stripe is pushing agent-driven payments in the
region.

**Why this plane fits LATAM's actual buyer.** The regional retailer that cannot afford Oracle MFP or
RELEX — which is most of them — currently plans its buy in spreadsheets. The MIT/Apache assembly in
Pattern 30 is the only auditable open-to-buy available to that buyer at any price, and LATAM is where the
share of retailers in that position is highest. This is a *capability* sale, not a cost-reduction sale,
and it should be priced as one.

**Regulation — explicit informed gap.** Searched this pass across the region: **no national AI law
specific to retail surfaced in any LATAM market.** The single regulatory reference found was GDPR invoked
as a *benchmark* by a payments vendor discussing agentic payments and privacy — a standard someone chose
to cite, not a LATAM rule. Prior passes of this KB recorded that LATAM broadly tracks the EU model and
that Chile and Uruguay have moved first on AI legislation generally; **none of that was re-verified for
retail this pass and none of it should be quoted to a client as a retail obligation.** Treat LATAM retail
AI regulation as unresearched here rather than non-existent.

## Globant positioning

1. **Lead with protocol reachability, not models.** The scarce skill is making a retailer's catalogue and
   checkout completable by an agent across UCP *and* ACP. The permissive reference implementation exists;
   almost nobody has deployed it.
2. **Sell the EMEA deadline now** — Article 50's 2 Dec 2026 transitional date is immediate, concrete and
   requires disclosure/labelling work that is fast to scope.
3. **Own the LATAM merchant gap.** "Agents can browse but cannot buy" is a measured, regional,
   buildable finding, and Globant's LATAM footprint is the natural advantage.
4. **Build the price/markdown engine as proprietary IP.** It is the one high-value retail capability with no
   open-source floor — permissive platform underneath, Globant IP on top.
5. **Bring the ROI gap honestly.** 95% adoption / 5% scalable ROI in EMEA is the argument for a delivery
   partner over another pilot.

### Added 2026-11-22 (pass 2) — positioning that follows from the store plane

6. **Lead with fiscalisation, not with agents, in LATAM and EMEA.** It is the only retail capability that is
   legally compulsory, dated, country-specific and already well supplied with open source — which means the
   engagement is integration and licence judgement, not R&D, and it cannot be deferred by a client.
7. **Own the AGPL inversion as a differentiator.** "Odoo is LGPL so your modules stay closed" is the
   industry's standard line and it is wrong for any deployment that needs a LATAM fiscal localisation
   (`OCA/l10n-*` are all AGPL-3.0). Being the partner who catches that before the contract is signed is
   worth more than any model benchmark.
8. **Build the till-to-fiscal join.** A permissive POS exists (`opensourcepos`, MIT) and permissive fiscal
   libraries exist (Mexico MIT, Brazil Apache-2.0). The connector between them does not exist in usable
   form in any LATAM country. Small, concrete, reusable across clients.
9. **Make store vision non-identifying by construction, and say so.** It removes BIPA/state biometric
   exposure in North America, it sidesteps the EU AI Act's biometric-categorisation questions, and it is
   the only way to enter a category where open source offers nothing (`loss prevention` → 0 repos,
   `footfall counting` → 0 repos).
10. **Treat shelf, queue and roster as product, not integration.** The only maintained components are
    generic (Timefold Apache-2.0; `supervision` MIT); the retail-specific layer is student projects on
    AGPL-licensed YOLO weights. Price and describe it as IP development — this is now the second confirmed
    proprietary-IP zone in retail alongside markdown/assortment optimisation.

### Added 2026-11-22 (pass 3) — positioning that follows from the retail media plane

Retail media is the first plane this KB has mapped where **the money is
enormous and the open-source floor is absent.** The product-data plane had a
floor (GS1, EPCIS). The store plane had one (POS, fiscalisation). Retail media
has **one repo matching `retail media stars:>=50`, and it is a 2020 ML
tutorial.**

1. **Sell assembly, not integration.** There is no retail media platform to
   configure. The capability is composed from `prebid-server` + `uid2-operator`
   + `meridian`/`pymc-marketing` + `pinot`/`superset`, all Apache-2.0, all
   committing within four days of this pass. The assembly *is* the deliverable,
   which is a better commercial position than layering on a vendor platform.
2. **Own the clean room, because nobody maintains one.** Every open-source data
   clean room found is dormant 752–1258 days, in the segment vendors call the
   fastest-growing part of retail media (measurement & attribution, 22.6%
   CAGR). The primitives are alive and permissive. **This is the single
   strongest build-proprietary-IP position in the retail KB**, alongside
   markdown/assortment optimisation (cycle 8) and shelf vision (pass 2).
3. **Be protocol-neutral, but notice the asymmetry.** Cycle 8's conclusion that
   neutrality beats betting on a winner still holds for commerce. In
   advertising, AdCP has 8,610 refs and commits today while `IABTechLab/AAMP`
   has **two files**. Hedging is cheap; pretending the two are equivalent is
   not. Build on AdCP, keep the adapter boundary, revisit if AAMP ships code.
4. **Licence audit per deployed component, not per project.** Snowplow is the
   case to cite in any engagement review: Apache-2.0 on the umbrella repo,
   **Snowplow Limited Use License on the collector and enrich services that
   actually run**, BSD-3 on the browser tracker, and a 0-byte `LICENSE.md`
   beside the real one.
5. **Governance sells in North America; labelling sells in EMEA.** NA has a
   measured deployment-versus-control gap and no binding statute, so governance
   is a consulting product. EMEA has Article 50 in force since 2026-08-02, a
   provider marking duty catching up on **2026-12-02**, and watermark-detection
   interoperability on **2027-02-02** — so creative labelling is a compliance
   build with a date on it.

### Added 2026-11-23 — positioning that follows from the returns & recovery plane

**The one-line pitch.** Retail loses roughly a sixth of its sales to returns
(Shopify: ~16% of 2025 sales, ~$850B), the EU now legally constrains what a
retailer may do with the goods that come back, and the decision step that
obligation targets has **zero open-source implementations**. Globant can build
the thing that does not exist, on a stack that is entirely Apache-2.0, BSD-2
and MIT.

**Why this plane suits a studio rather than a product vendor.** Every other
step of the reverse flow is either already solved by permissive, actively
maintained software (reverse routing: eight solvers, `or-tools` at 14430★) or
is a commercial SaaS category with no open floor (returns platforms). The
missing piece is the **integration judgment** — grading feeding a typed
disposition rule feeding a route — which is bespoke per client, per
jurisdiction and per product category. That is studio work, not licence work.

**The regional objective function changes, the code does not.** This is the
most reusable framing to come out of the pass:

| Region | What drives the disposition decision | What to sell first |
|---|---|---|
| **North America** | Pure economics — no federal mandate. Freight vs recoverable value. | Returns-abuse scoring (85% deployed / 45% trusted) and "keep it" optimisation |
| **EMEA** | **Legal obligation, live since 19 July 2026**, and typed: reuse ≠ recycling | The ESPR Article 25 disposition evidence engine; per-Member-State policy matrix |
| **APAC** | Volume from livestream/social commerce; no mandate found | Returns *prevention*; dense-city reverse routing |
| **LATAM** | Statutory speed — Brazil CDC Art. 49, 7 days from receipt | Fast automated authorisation; locker consolidation routing |

**Sequencing recommendation.** Prove the model in **North America**, where the
decision is unconstrained economics and therefore cheap to validate, then port
it to **EMEA**, where the identical engine carries a legal obligation and
commands a compliance budget. The EMEA version needs an audit trail the North
American one does not — build the evidence layer from the start even where it
is not required, because it is the entire value in the larger market.

**The honest caveat to put in front of a client.** Unlike the store plane,
where this KB can point to maintained fiscal libraries per country, **this
plane has no domain-specific open-source floor**: the only retail-specific
reverse-logistics optimiser in existence (Argonne's RELOG) carries **no
licence at all**. Promise an assembly of general-purpose permissive
components, verified and named, and do **not** promise an open-source returns
platform. There isn't one.

### Added 2026-11-23 (pass 5) — positioning that follows from the price plane

1. **Lead with the correction, not the plane.** This KB told itself for four
   cycles that retail pricing had no open-source floor, and the claim shaped a
   recommendation ("build product matching as proprietary IP") that was based on
   a **search false negative**. The floor exists: `splink` (MIT), `dedupe` (MIT),
   `pymc-marketing`'s `BayesianBLP` (Apache-2.0, documented for retailer-scanner
   data), `pyblp` (MIT). A studio that assembles and verifies these starts an
   engagement weeks ahead of one that quotes a build.

2. **Sell the assembly, and keep exactly one thing proprietary.** The honest
   split on this plane is now measurable: OBSERVE, MATCH, MODEL, SET and EXECUTE
   are all permissive and alive. **OPTIMISE is the only genuinely empty step**,
   and every repo that attempted it specifically for retail — three of three —
   **has no licence grant**. The markdown/promotion optimiser is where Globant IP
   belongs, and it is a *smaller* build than "a pricing platform" because the
   elasticity estimates arrive from Apache-2.0 code.

3. **The compliance ledger is the actual product, and it is four products.**
   Each region attaches a different legal object to the same number — NA *who*,
   EMEA *against what*, APAC *whether complete*, LATAM *to whom split*. They are
   four projections of one immutable price-event log, and a ledger designed for
   one will not answer the others (Pattern 22). Exactly **one** open-source
   implementation of **one** projection exists, at 0 stars, one day old, for one
   platform, in one member state's specifics.

4. **Two dated near-term hooks, both verifiable against a calendar.** New York's
   One Fair Price Act must be signed or not by **2026-12-31**; the EU's Digital
   Fairness Act proposal of **2026-11-11** puts a consumer-set **maximum price**
   into the agent contract (Art. 26) and would repeal the UCPD. Australia's
   **2027-07-01** commencement is the scoping window. These are the conversations
   a retailer is already having.

5. **Do not sell dynamic pricing. Sell defensible pricing.** Trade press reports
   leading retailers use dynamic pricing mainly to *match competitors' price
   drops* rather than to raise prices, while three US states have banned
   personalised pricing outright and one attached a private right of action. The
   margin story is contested and the exposure story is not. Position the audit
   trail as the deliverable and the optimiser as what it protects.

6. **A regional generalisation died this pass — keep it dead.** Cycle 8's
   "North America is the weakest-sourced region" was true of returns and
   agentic-commerce regulation and is false of price, where NA is the strictest
   region with the only in-force bans. **Regulatory weight is per-plane, not
   per-region.** Re-measure it every time the plane changes.

### Added 2026-11-23 (pass 6) — positioning that follows from the fulfilment plane

**1. Sell the promise, not the route.** The routing problem is solved by Apache/BSD/MIT code that a
client can download: OR-Tools (14,430★), VROOM (1,924★), jsprit, PyVRP, Timefold, plus OSRM, Valhalla,
GraphHopper and Photon under permissive licences. Proposing "AI route optimisation" as the
differentiator is proposing to re-sell free mathematics. The **delivery promise** — which node, which
date, with what confidence — has 7 repositories worldwide and none above 1 star. That is the build.

**2. "Assemble, do not adopt" is the licence strategy on this plane.** The finished-looking platforms
are AGPL-3.0 (Fleetbase 4,799★, Openship 1,680★) or Elastic License (OpenOMS). The components are
permissive. A client-owned, closed fulfilment system is entirely reachable from OFBiz or InvenTree +
OR-Tools/VROOM + Photon/Pelias; it is not reachable by starting from the platform that demos best.

**3. The cross-region thesis, and it is new to this KB: algorithmic accountability toward the
courier is now a delivery requirement in every region at once.** EU Platform Work Directive
transposition 2 December 2026; NYC just-cause deactivation enforcement January 2027; Brazil's PLP 152
and the Senacon transparency monitoring; and APAC approaching the same territory through open
protocol interoperability rather than labour law. One artefact satisfies all of them: a typed,
replayable decision record for every assignment, pay calculation and deactivation. Globant can build
it once and place it four times.

**4. LATAM is, on this plane, the best-equipped region in the world — say so.** The carrier label and
tracking step that is empty everywhere else is MIT-licensed and agent-shaped for Brazil, Mexico,
Argentina and Colombia. For once the regional story is not "catching up"; it is a capability a North
American or European client cannot buy from open source at all.

**5. Protocol neutrality extends to the fulfilment fields, and it now has a concrete defect to
justify it.** UCP and ACP both type a delivery timestamp pair, and the pairs mean different events
(hand-off vs. arrival — see `intel/trends.md`). Any merchant selling through both an OpenAI surface
and a Google surface needs an adapter that knows the difference. That is a small, specific,
demonstrable piece of expertise, and it is exactly the kind of thing a client discovers after launch.

### Added 2026-11-26 (pass 7) — positioning that follows from the merchandise planning & trade-funds plane

The plane has an unusual property for this KB: **the gap is global.** No region has an open merchandise
planning or trade-funds implementation, so unlike the fiscal-receipt or returns planes there is no
"pick the right market" move available. That cuts both ways — the opportunity does not need
localisation to be real, and it cannot be won by arriving in a region first.

**What Globant can honestly claim.** The solver and forecasting layer is permissive, mature and pushed
daily (~21,500 stars across OR-Tools, PuLP, Pyomo and HiGHS). The merchandise-master substrate exists
(ERPNext, OFBiz, Odoo, frePPLe). **The missing piece is domain definitions encoded as auditable
software** — the open-to-buy ledger, the size-curve roll-up, the vendor-funds accrual-to-settlement
chain. That is consulting-shaped work with a software artifact at the end, which is exactly the shape
Globant sells. It is also defensible: a competitor cannot download it either.

**What Globant must not claim.** Do not promise an "all open source merchandise planning stack". The
semantics layer does not exist, five of the ten candidate artifacts have no license file, and the only
open planning spine (frePPLe) is dual-licensed with functionality behind a commercial tier. Any proposal
that implies assembly-only delivery will be wrong about the hardest 70% of the work.

**Ranked by where the money and the emptiness overlap:**

1. **Vendor-funds settlement (North America first).** The category total is literally zero stars, trade
   spend is a top line item in consumer-goods retail, and the disputes are cash. Highest defensibility.
2. **Auditable open-to-buy (EMEA first).** The EU AI Act gives the audit trail a statutory hook no other
   region provides, and European mid-market retailers are the segment priced out of Oracle MFP/RELEX.
3. **Assortment & space optimisation (LATAM first).** Strongest market growth (Mexico +40% retail,
   +58% e-commerce over five years) against the weakest incumbent platform layer (80% of major LATAM
   e-commerce platforms show critical technical deficiencies).
4. **Planning on reconciled data (APAC last, deliberately).** Biggest volume — two-thirds of the world's
   new retail sales — but fragmented omnichannel data is upstream of the buy. Sell product-data
   reconciliation here first; an assortment optimiser on unreconciled master data will fail and the
   solver will not be the reason.
