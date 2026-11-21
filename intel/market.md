---
industry: retail
region: Global
updated: 2026-11-21
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
