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
