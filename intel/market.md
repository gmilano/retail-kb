---
industry: retail
region: Global
updated: 2026-11-22
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
