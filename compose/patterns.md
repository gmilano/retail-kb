---
industry: retail
region: Global
updated: 2026-11-23
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

## Pattern 7 — Catalogue readiness pipeline (the prerequisite nobody sells yet)

Added 2026-11-22. **Problem:** the client has an agentic-commerce project and a catalogue the agent cannot
read. Measured reality: nothing open source judges whether a catalogue is right (`repos/foundations.md`,
step 3), so this is composed from generic engines plus retail rule packs you own.

**Wiring:**

1. **Ingest** from the client's PIM. If greenfield, [`unopim/unopim`](https://github.com/unopim/unopim)
   (MIT, 11080★) — the only permissive maintained PIM. If they run Akeneo (OSL-3.0) or Pimcore (**POCL,
   not open source** — check this before quoting), integrate, do not fork.
2. **Normalise identity** with [`gs1/GS1DigitalLinkToolkit.js`](https://github.com/gs1/GS1DigitalLinkToolkit.js)
   (Apache-2.0): validate GTIN check digits and GCP length, reject restricted prefixes (02, 04, 2, 05, 98,
   99), and translate element strings ↔ Digital Link URIs.
3. **Validate attributes** with [`unionai-oss/pandera`](https://github.com/unionai-oss/pandera) (MIT) for
   Python-scale catalogues or [`awslabs/deequ`](https://github.com/awslabs/deequ) (Apache-2.0) on Spark for
   multi-million-SKU retailers. **The rule pack is the deliverable and the IP** — completeness per category,
   unit-of-measure sanity, price/availability freshness, image presence, cross-field consistency.
4. **Deduplicate** supplier overlaps with [`dedupeio/dedupe`](https://github.com/dedupeio/dedupe) (MIT).
   Use [`zinggAI/zingg`](https://github.com/zinggAI/zingg) (AGPL-3.0) only behind a service boundary.
5. **Enrich the gaps** with
   [`NVIDIA-AI-Blueprints/Retail-Catalog-Enrichment`](https://github.com/NVIDIA-AI-Blueprints/Retail-Catalog-Enrichment)
   (Apache-2.0) — images in, structured attributes and copy out — with a **human review queue**, because
   enrichment writes into the record of truth.
6. **Emit** an ACP `schema.feed.json`-shaped feed (20 objects / 62 properties, spec version `2026-04-17`)
   and a Merchant Center feed, then assert the two agree with the on-page schema.org markup.

**Why it sells:** it is the common prerequisite of every other pattern in this file, it is measurable before
and after (GTIN coverage %, attribute completeness %, feed/markup agreement %), and **the licences are
clean end to end** — MIT and Apache-2.0 at every step.

**Honest scoping note:** step 3's rule packs and taxonomy mapping do not exist in open source
(`product taxonomy classification stars:>=50` → **0**). Budget them as build, not integrate.

## Pattern 8 — One identifier programme, four compliance budgets (EMEA)

Added 2026-11-22. **Problem:** an EMEA retailer faces PPWR data carriers, the battery passport
(**2027-02-18**), EUDR (**2026-12-30** for own-import cocoa/coffee/wood/paper), and Sunrise 2027 as four
separate projects with four budgets. They share one prerequisite.

**Wiring:**

1. **Resolver** — deploy [`gs1/GS1_DigitalLink_Resolver_CE`](https://github.com/gs1/GS1_DigitalLink_Resolver_CE)
   (Apache-2.0, 65★, pushed 2026-11-02). One GTIN resolves to spec sheet, passport, recall notice, recycling
   instructions — per-link, per-market, per-language.
2. **Prove it correct** with [`gs1/GS1DL-resolver-testsuite`](https://github.com/gs1/GS1DL-resolver-testsuite)
   (Apache-2.0). Conformance evidence is the audit artefact; it is why this is a compliance deliverable and
   not an IT project.
3. **Event store** — [`openepcis/epcis-repository-ce`](https://github.com/openepcis/epcis-repository-ce)
   (Apache-2.0) for EPCIS 2.0 commission/ship/receive events, which is what EUDR due diligence actually
   needs. Join identity to events via
   [`openepcis/openepcis-epc-digitallink-translator`](https://github.com/openepcis/openepcis-epc-digitallink-translator).
   **Scope the CE/Business-Edition boundary in writing** — OpenEPCIS is open-core.
4. **Test without client data** using
   [`openepcis/epcis-testdata-generator`](https://github.com/openepcis/epcis-testdata-generator) (Apache-2.0).
5. **Trade messages** — `pydifact` (MIT) or `EDI.Net` (MIT) where supplier data arrives as EDIFACT/X12,
   which in European grocery it still does.
6. **Passport presentation** — model on
   [`eclipse-tractusx/digital-product-pass`](https://github.com/eclipse-tractusx/digital-product-pass)
   (Apache-2.0) but **do not depend on it: 14 months without a push.** Treat DPP presentation as the last
   and most replaceable layer, because **no ESPR product-group delegated act has been adopted yet.**

**Why it sells:** the identifier work is required under every scenario, so it is defensible even if every
DPP date slips — and the dates slipping is the base case, not the risk case.

## Pattern 9 — "Identifier to shelf" for LATAM merchants (high volume, low ticket)

Added 2026-11-22. **Problem:** GS1 México reports ~**3,000 companies a year requesting a first barcode**,
mostly small, and yesterday's measured finding was that agents can browse LATAM e-commerce but cannot buy.
Both halves of that gap sit in the same merchant.

**Wiring (deliberately thin — this must be repeatable, not bespoke):**

1. **Identity** — register the GTIN correctly, then publish it through the shared
   `GS1_DigitalLink_Resolver_CE` (Apache-2.0) deployment as a multi-tenant service. One resolver, many
   merchants.
2. **Minimum viable attributes** — a fixed `pandera` (MIT) rule pack per retail category. Target the ACP
   floor first (`Variant.required` is only `id` + `title`), then the Merchant Center bar, which is the one
   that actually governs visibility.
3. **Storefront** — Medusa (MIT) or Bagisto (MIT) from `verticals/solutions.md`; no new platform decision.
4. **Checkout the agent can complete** — UCP and/or ACP through
   `NVIDIA-AI-Blueprints/Retail-Agentic-Commerce` (Apache-2.0). Note UCP is the only actively maintained
   protocol (pushed 2026-11-21 vs ACP 2026-07-18); if you implement one, implement UCP.
5. **Payment** — Pix in Brazil. Per yesterday's finding, `bacen/pix-api` has **no licence file**: generate
   clients at build time from the published spec, never vendor the repo.
6. **Conversational surface** — WhatsApp, per the regional patterns already in this file.

**Why it sells:** the cohort is continuously replenished, the deliverable is identical each time, and the
outcome is measurable as "this merchant is now purchasable by an agent" — the exact gap the April 2026 scan
of 75 LATAM e-commerce sites measured.

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
- **Do not call Pimcore open source.** Since **June 2025** it ships under the bespoke **Pimcore Open Core
  License (POCL)**, a 24927-byte vendor agreement. Listicles — including well-known "open source
  alternative" articles — still say GPLv3. Read the file.
- **Do not promise "DPP compliance" in 2026.** No ESPR product-group delegated act has been adopted. Sell
  the identifier and attribute work that every version of the rule will require.
- **Do not treat ACP conformance as agent visibility.** ACP's feed schema requires only `id` and `title` on
  a variant; the surfaces (Merchant Center and its trust layers) set the real bar, and they want GTINs.
- **Do not promise a taxonomy classifier as integration work.** `product taxonomy classification
  stars:>=50` returns **0**, and ACP's own `Category.taxonomy` is an unconstrained string. That is a build.
- **Do not read a star count as momentum.** ACP and AP2 both gained stars this quarter while their default
  branches sat untouched for 127 and 158 days respectively. Always pull `pushed_at` from the same call.
- **Do not conclude a licence is missing because `LICENSE` 404s.** Akeneo's is in **`LICENCE.txt`** —
  British spelling, `.txt` extension, **148 bytes**, pointing at OSL-3.0. A probe of 2 branches × 12 common
  filenames missed it; a shallow clone found it in one call. When a control request succeeds and `README.md`
  also 404s, your filenames are wrong, not the repo.

---

## Pattern 10 — The lawful till: a permissive POS joined to a permissive fiscal library

**The gap this closes.** There is no permissively licensed open-source POS with a working LATAM fiscal
module. The till exists under MIT, the fiscal libraries exist under MIT/Apache/LGPL, and the join between
them is either missing or AGPL. `dansanti/l10n_cl_dte_point_of_sale` — the one repo aimed exactly at this
shape — has **no licence file and died on 2018-06-14**.

**Wiring, Mexico (the zero-copyleft build).**

1. **Till:** [opensourcepos/opensourcepos](https://github.com/opensourcepos/opensourcepos) — **MIT**,
   4530★, pushed 2026-11-22. PHP/CodeIgniter 4 + MySQL, multi-tier tax already modelled.
2. **CFDI issuance:** [eclipxe13/CfdiUtils](https://github.com/eclipxe13/CfdiUtils) — **MIT**, 146★ — to
   build and stamp CFDI 4.0 documents from the sale record.
3. **SAT catalogues:** [phpcfdi/resources-sat-catalogs](https://github.com/phpcfdi/resources-sat-catalogs) —
   **Unlicense**, 97★ / 424 refs — product/tax code tables, refreshed from SAT.
4. **Reconciliation:** [phpcfdi/sat-ws-descarga-masiva](https://github.com/phpcfdi/sat-ws-descarga-masiva) —
   **MIT**, 198★ — bulk-download issued CFDIs back from SAT to reconcile the register against the authority.
5. **Agent surface:** expose steps 2–4 as MCP tools so an assistant can answer "which of yesterday's sales
   never got stamped?" — the question a store manager actually asks.

**Total copyleft obligation of this build: none.** That is unique to Mexico and is the reason to start a
multi-country LATAM programme there.

**Brazil variant.** Replace steps 2–4 with [wmixvideo/nfe](https://github.com/wmixvideo/nfe)
(**Apache-2.0**, 770★ / 411f, Java) if the stack is JVM, or
[nfephp-org/sped-nfe](https://github.com/nfephp-org/sped-nfe) (**LGPL-3.0**, 1635★, PHP) if it is PHP —
LGPL means link dynamically and the till stays closed. Do **not** reach for `OCA/l10n-brazil`: it is
AGPL-3.0 (see Pattern 11).

**Chile variant — state the constraint rather than the solution.** The only maintained DTE core,
`LibreDTE/libredte-lib-core`, is **AGPL-3.0**, and `factura electronica DTE SII stars:>=20` returns **0**.
Either accept AGPL for the issuance component and isolate it behind a process boundary (Pattern 11), or
consume LibreDTE's hosted API through its LGPL-3.0 client and accept the third-party dependency. There is
no third option as of 2026-11-22.

---

## Pattern 11 — Isolating the AGPL fiscal component (the pattern that saves the Odoo engagement)

**The problem, precisely.** Odoo core is **LGPL-3.0**, so proprietary modules are permitted — the fact
cycle 8 correctly identified as retail's most commercially useful. But the OCA localisations that make an
Odoo POS *lawful* in LATAM are each **AGPL-3.0**: `OCA/l10n-brazil` (376★), `OCA/l10n-mexico` (20★/56f),
`OCA/l10n-chile` (10★/41f) — verified by reading `LICENSE` at source, 34523 bytes, first line
`GNU AFFERO GENERAL PUBLIC LICENSE`. A hosted Odoo that issues NF-e, CFDI or DTE mixes LGPL core with AGPL
modules, and AGPL's network clause reaches the service the client's customers touch.

**Wiring.**

1. **Keep the AGPL code in its own deployable.** A "fiscal issuer" service containing the OCA localisation
   (or LibreDTE), with **no Globant IP inside it** and no shared process with the merchandising stack.
2. **Define the boundary as a documented HTTP/queue contract** — `POST /issue`, `GET /status/{id}`,
   `POST /cancel` — carrying the sale, returning the authority's response and document ID. The contract,
   not the code, is what the client's other systems depend on.
3. **Comply deliberately and cheaply.** Publish the fiscal-issuer source (it is the unmodified upstream
   plus configuration), with a `NOTICE` naming the AGPL components and a link to the corresponding source.
   Cost: near zero, since there is nothing proprietary to disclose.
4. **Put Globant IP strictly on the other side** — pricing, markdown, assortment, store-task orchestration,
   the agent layer — where Odoo's LGPL core and MPL-2.0 `mcp-server-odoo` leave it closed.
5. **Agent access:** [ivnvxd/mcp-server-odoo](https://github.com/ivnvxd/mcp-server-odoo) (**MPL-2.0**, 419★,
   pushed 2026-11-22). MPL is file-level copyleft: new files you add stay proprietary; changes to its own
   files must be published. For a TypeScript stack use
   [marcfargas/odoo-toolbox](https://github.com/marcfargas/odoo-toolbox) (LGPL-3.0, 44★).

**Why this is the pattern and not a footnote:** the alternative — discovering the AGPL dependency after the
statement of work is signed — forces either a licence breach or a rebuild of the compliance layer, which is
the one layer whose deadline is set by a tax authority.

---

## Pattern 12 — Non-identifying store vision (the only North America-safe shelf build)

**The gap this closes.** `retail loss prevention theft detection stars:>=20` → **0**;
`footfall people counting retail stars:>=50` → **0**; `shelf monitoring retail stars:>=30` → **1**
(unlicensed, self-described simulation). Meanwhile the legal exposure in North America is biometric:
Illinois BIPA requires a published retention policy and informed written release *before* collection, and
20+ states classify biometrics as sensitive data.

**The design constraint that resolves both at once:** gesture- and behaviour-based detection **does not
identify an individual shopper** and therefore stays outside the scope of biometric privacy law. Build so
that no face embedding and no cross-visit re-identifier ever exists.

**Wiring.**

1. **Detection/tracking substrate:** [roboflow/supervision](https://github.com/roboflow/supervision) —
   **MIT**, 51699★ / 4964f, pushed 2026-11-20. Detector-agnostic tracking, polygon zones, line counters,
   annotators. This is the whole reason the pattern is licensable.
2. **Detector — and this is the trap.** Do **not** ship `ultralytics/ultralytics`: it is **AGPL-3.0**
   (34523-byte `LICENSE`, first line `GNU AFFERO GENERAL PUBLIC LICENSE`), and a hosted store-analytics
   service triggers its network clause. Use an Apache-2.0 or MIT-licensed detector and weights, and verify
   the **weights** licence separately from the code — carrying forward the media-pass rule that for native
   and model dependencies you resolve the licence of what you *link and ship*, not of the repo.
3. **Shelf semantics:** define zones per bay and count occupancy, not products, as the v1 signal. The
   planogram-compliance literature is 502 repos whose best entry has 17 stars
   ([laitalaj/cvpce](https://github.com/laitalaj/cvpce), MIT, 11★, dead 2021 — the only one whose stated
   purpose is planogram compliance). Treat it as prior art to read, not code to depend on.
4. **Privacy posture as a deliverable:** no face detection in the pipeline at all; per-frame counts and
   dwell aggregates only; retention in hours; a written data-flow statement. In Illinois, Texas and
   Washington this is the difference between a product and a lawsuit.
5. **Action loop:** feed gaps and queue lengths to the store-task layer — which has **no open source at all**
   (`retail execution store audit mobile stars:>=5` → 0 results), so it is Globant-built by necessity.

---

## Pattern 13 — Rostering as a solver problem, not a prompt

**The gap this closes.** `workforce scheduling stars:>=150` returns one repo, `Staffjoy/v2` (MIT, 1686★),
**dead since 2022-12-06**. Retail's largest controllable cost has no maintained open-source platform.

**Wiring.**

1. **Engine:** [TimefoldAI/timefold-solver](https://github.com/TimefoldAI/timefold-solver) — **Apache-2.0**,
   1879★ / 244f, pushed 2026-11-20. The maintained successor to OptaPlanner
   (`apache/incubator-kie-optaplanner`, 3512★, now redirecting elsewhere in its own description). Model
   shifts, skills, availability, contracted hours, break rules and fairness as hard/soft constraints.
2. **Demand input:** the forecasting repos already in this KB (`NeuralForecast`, `StatsForecast`, both
   Apache-2.0) convert footfall and transaction history into labour demand per 15-minute bucket.
3. **Labour rules as data, per country.** This is the billable work and it does not generalise: Brazilian
   CLT rest rules, French working-time law, Mexican NOM provisions. Keep them as declarative constraint
   configuration, not code, so one engine serves every market.
4. **Agent role — and keep it narrow.** The LLM does *not* build the roster. It explains why a shift is
   unfilled, proposes a swap and re-runs the solver, then surfaces the score delta. Solver for feasibility,
   agent for negotiation.
5. **Do not pitch this as integration.** With the only platform four years dead, this is product
   development — the second confirmed proprietary-IP zone in retail alongside markdown/assortment
   optimisation.

---

## Method notes added 2026-11-22 (pass 2)

- **`search/repositories` with a `repo:owner/name` qualifier beats the false-negative problem.** It resolved
  **7 of 7** slugs that keyword search had missed, and returns stars, forks, licence and `pushed_at` —
  which `gh api repos/<slug>` cannot, since it still 403s for non-attached repos. The false negatives are a
  keyword-*ranking* artefact, not a missing index. `ls-remote` remains the authority on existence.
- **`NOASSERTION` means GitHub's classifier failed, not that a licence is absent.** Four cases this pass,
  four real licences on reading the file: `opensourcepos` = MIT behind a 26-name copyright roster,
  `sped-nfe` = LGPL-3.0, `odoo` = LGPL-3.0, `oxalis` = **EUPL-1.1 declared in a file named `COPYRIGHT`**.
- **Add `COPYING.LGPL` and `COPYRIGHT` to the licence-probe filename list.** Oxalis ships both, and they
  disagree; the operative declaration was in `COPYRIGHT`.
- **The control request must not assume `README.md` exists either.** `SAT-CFDI/python-satcfdi` 404s on
  `LICENSE`, `LICENSE.md`, `COPYING` *and* `README.md` across both branches while `ls-remote` reports 205
  refs — the project is all-lowercase reStructuredText (`license`, `readme.rst`). The media-pass rule held;
  the fix was a shallow clone, one call.
- **An oversized MIT file is a copyright roster, not another licence.** Byte fingerprints confirmed today:
  **34523 = AGPL-3.0**, **35149 = GPL-3.0 plain**, **34916 = GPL-3.0 Markdown**, **7650–8851 = LGPL-3.0**,
  **16725 = MPL-2.0**, **11325–11358 = Apache-2.0 full**, **10173–10850 = Apache-2.0 appendix-stripped**,
  **~1050–1130 = MIT**.
- **For compliance code, rank by forks, not stars.** `OCA/l10n-mexico` 20★/56f and `OCA/l10n-chile` 10★/41f
  are production dependencies with ratios above 2.8. Nobody stars a tax localisation; they fork it to patch
  it. A star-gated sweep discards exactly the repos a regional engagement needs.
- **The keyword-collision list for this plane**, so the next pass does not re-learn it: `self-checkout`
  matches "**self-hosted**" payment gateways; `rfid inventory` matches home asset managers and a
  **3D-printer filament manager**; `queue management` matches software job queues; `pos system` matches
  **pose estimation** (`AlphaPose`, 8630★) and PowerShell SSH. Cycle 8's Minecraft-mod incident
  (`hopperOptimizations` carried as retail inventory intelligence) was the same failure mode.

## Pattern 14 — Assemble a clean room from live primitives (the one nobody maintains)

**Why this pattern exists.** The data clean room is where a retailer and a
brand compare audiences without either handing over its customer list. It is
the layer every retail media network buys from a vendor, and vendors size it at
**$2.8B (2025) → $14.6B (2034)** with measurement & attribution the fastest
application (22.6% CAGR, Dataintelo). **Every open-source clean room is
dead:** `tiktok-privacy-innovation/PrivacyGo-DataCleanRoom` 752d,
`Snowflake-Labs/sfquickstart-data-clean-room` 986d (and a Snowflake-bound demo,
not a product), `qascade/dcr` 1258d and AGPL-3.0. **Do not fork any of them.**
The primitives, however, are alive and permissive.

**Parts (all measured 2026-11-22, all Apache-2.0):**

| Part | Repo | Licence | Last commit | Role |
|---|---|---|---|---|
| Private matching | [OpenMined/PSI](https://github.com/OpenMined/PSI) | Apache-2.0 (11356B, `master`) | 2026-09-20 (63d) | ECDH PSI; returns intersection **or only its size**. C++/JS/Go/Python/Rust |
| Private join + aggregate | [google/private-join-and-compute](https://github.com/google/private-join-and-compute) | Apache-2.0 (11357B, `master`) | 2026-03-09 (258d) | Intersection **plus a sum over the matched rows** — the actual clean-room operation |
| Noise & budget | [google/differential-privacy](https://github.com/google/differential-privacy) | Apache-2.0 (13499B) | 2026-11-20 (2d) | DP aggregation and **privacy-budget accounting** across C++/Go/Java/Python |
| Serving layer | [apache/pinot](https://github.com/apache/pinot) | Apache-2.0 (11356B, `master`) | 2026-11-21 (1d) | Query results at ad-event volume |
| Advertiser UI | [apache/superset](https://github.com/apache/superset) | Apache-2.0 (11585B, `master`) | 2026-11-22 (0d) | Self-service dashboards without building a front end |

**Wiring:**

1. **Normalise identifiers on both sides before any crypto.** Retailer hashes
   its customer identifiers; brand hashes its own. Use
   `IABTechLab/uid2-operator` (Apache-2.0, 0d) if a shared pseudonymous
   identifier is wanted, rather than inventing a hashing scheme.
2. **Match with `private-join-and-compute`, not plain PSI**, whenever the
   question is "how much did matched customers spend" rather than "who
   overlaps". Plain `OpenMined/PSI` is the right choice for **overlap size
   only** — and overlap-size-only is often all the brand is contractually
   permitted to learn.
3. **Put `google/differential-privacy` in front of every returned
   aggregate**, with a per-partner privacy budget that is *persisted*. The
   dead clean rooms all shipped matching; what they lacked, and what makes a
   clean room a clean room, is **query restriction, budget accounting and audit
   logging.** That is the part you are building.
4. **Materialise approved aggregates into Pinot**, expose them through Superset
   per advertiser. Never let an advertiser query the raw join.
5. **Log every query, its budget draw and its requester.** This is the audit
   surface a retailer's legal team will ask for, and it is the reason this is a
   product rather than a script.

**What you are honestly selling:** not cryptography — the cryptography is
Google's and OpenMined's — but **governance around it**: budgets, query
allow-lists, audit, and multi-tenant isolation. That is also precisely why
`compose` work here is defensible IP (see `intel/market.md` positioning).

**⚠️ Do not** reach for `tiktok-privacy-innovation/PrivacyGo` (667d) even
though its **DPCA-PSI** — intersection statistics under differential privacy —
is conceptually the closest thing to this pattern in one package. It is
dormant. Read it for the design, build on the live primitives.

## Pattern 15 — Make retail media inventory agent-sellable (AdCP sales agent)

**Why.** Agent-mediated ad buying became buildable in 2026. The duopoly
(Amazon Ads, Walmart Connect — **89.5% of US incremental spend**) will be
reachable by buying agents early; a second-tier retailer will not. This is the
pattern that closes that gap, and it is the advertising counterpart to
cycle 8's "agent-reachable storefront".

**Parts:**

| Part | Repo | Licence | Last commit | Role |
|---|---|---|---|---|
| Protocol | [adcontextprotocol/adcp](https://github.com/adcontextprotocol/adcp) | Apache-2.0 (10767B) | 2026-11-22 (0d) | AdCP: discovery, media buying, creative, audience activation, reporting |
| Sales agent | [prebid/salesagent](https://github.com/prebid/salesagent) | Apache-2.0 (10767B) | 2026-11-23 (0d) | Exposes inventory to agents over **MCP + A2A**; 16 AdCP tools, GAM integration, multi-tenant, admin UI |
| Auction | [prebid/prebid-server](https://github.com/prebid/prebid-server) | Apache-2.0 (10759B, `master`) | 2026-11-19 (3d) | Server-side auction behind the agent |
| Identity | [IABTechLab/uid2-operator](https://github.com/IABTechLab/uid2-operator) | Apache-2.0 (11348B) | 2026-11-22 (0d) | Pseudonymous identity for audience targeting |

**Wiring:**

1. **Stand up `prebid-server`** as the auction, with the retailer's onsite
   placements as inventory. This part is mature and uncontroversial.
2. **Put `prebid/salesagent` in front of it** as the AdCP sales-agent role.
   It speaks MCP and A2A, so an agent on either transport can discover
   inventory, buy it, submit creative and pull reporting.
3. **Pin the protocol version and guard the pin in CI.** Copy the upstream
   approach exactly: `salesagent` pins the `adcp` SDK in `pyproject.toml` and
   enforces it with `tests/unit/test_adcp_spec_version.py`, which **fails the
   build on spec drift.** This is the single most important engineering
   decision in the pattern, because the protocol is pre-1.0 and `v2.0.0`
   already shipped breaking changes.
4. **Keep an adapter boundary at the protocol edge.** AdCP and IAB's AAMP are
   **not wire-compatible**. AdCP is the only one buildable today
   (8610 refs vs AAMP's 5 refs and two files), so build on AdCP — but do not
   let its object model leak into the retailer's domain code.
5. **Attach identity via `uid2-operator`** so audience segments are sellable
   without exposing customer records.

**⚠️ Status discipline.** `prebid/salesagent` self-describes as **alpha**, "a
pre-1.0 implementation of a pre-release protocol", and "one of several AdCP
sales-agent implementations, not a sole or canonical reference". Put that
sentence in the client deck. The codebase is substantial and functional; the
standard under it is not finished.

## Pattern 16 — Closed-loop measurement that survives an audit

**Why.** Retail media's competitive battlefront is **measurement
transparency** (Mordor). An advertiser that cannot verify incrementality
eventually stops paying. The open-source measurement layer is good — **as long
as you pick the two libraries that are still alive.**

**Parts:**

| Part | Repo | Licence | Last commit | Role |
|---|---|---|---|---|
| MMM (default) | [google/meridian](https://github.com/google/meridian) | Apache-2.0 (11357B) | 2026-11-20 (2d) | Bayesian MMM, geo-level priors, dynamic baseline via splines/random walks, principled uncertainty |
| MMM + CLV | [pymc-labs/pymc-marketing](https://github.com/pymc-labs/pymc-marketing) | Apache-2.0 (11356B) | 2026-11-22 (0d) | MMM **and customer lifetime value and Bass diffusion** in one Bayesian framework |
| Calibration | [facebookincubator/GeoLift](https://github.com/facebookincubator/GeoLift) | MIT (1092B, `LICENSE.md`) | 2026-04-01 (235d) | Geo experiments producing a real lift estimate |
| Reporting | [apache/druid](https://github.com/apache/druid) / [apache/pinot](https://github.com/apache/pinot) | Apache-2.0 | 2026-11-21 (1d) | Serve the numbers |

**Wiring:**

1. **Run a geo holdout with `GeoLift` first.** A model calibrated to nothing is
   an opinion. GeoLift gives a measured lift for a known spend.
2. **Feed that lift into the MMM as a prior.** This is why Meridian is the
   default: geo-level priors and explicit uncertainty are native to it, so a
   lift test enters as evidence rather than a fudge factor.
3. **Use `pymc-marketing` instead when the engagement also needs CLV** — it
   covers MMM, CLV and Bass diffusion in one library, which avoids maintaining
   two Bayesian stacks for one client.
4. **Report intervals, never point ROAS.** Both libraries are Bayesian; the
   posterior is the deliverable. A single ROAS number is what the advertiser
   stops trusting.
5. **Materialise into Druid/Pinot, surface in Superset.**

**⚠️ Do not start here:** `facebookexperimental/Robyn` (MIT) is **dormant
~513 days** and its **default branch is a feature branch**
(`accuracy/allocator_v2_fixes`, 2024-11-21) — a plain clone gets non-release
code, despite 2026 commentary still calling it an "open-source giant".
`google/lightweight_mmm` (523d) is **Google's own superseded predecessor to
Meridian.** Both are plausible picks from a listicle and both are wrong.

**⚠️ And do not promise MMM is now easy.** The consistent finding across
commentary is that open source lowered the **software** barrier, not the
**expertise** barrier. Staff it accordingly.

## Pattern 17 — EMEA gate: label AI-generated ad creative (Article 50)

**Why, with the right scope.** EU AI Act **Article 50 transparency has been in
force since 2026-08-02** and was not postponed by the Digital Omnibus.
**2026-12-02** — days after this pass — binds **providers of systems that
generate synthetic content placed on the market before 2026-08-02**, covering
**Article 50(2) in full: machine-readable marking and detectability.** It does
**not** bind deployers, non-synthetic systems, or paragraphs 1/3/4, which
already apply. **2027-02-02** adds a watermark-detection interoperability duty
on providers. **AI-generated ad creative is synthetic content**, so a retail
media network generating creative, product imagery or virtual models is in
scope.

**Wiring — a gate in the creative pipeline, not a policy document:**

1. **Classify every creative asset at ingest**: human-made, AI-assisted, or
   AI-generated. Store the classification as a required field; reject assets
   without it. This is the step that makes the rest provable.
2. **Apply machine-readable marking at generation time**, not at publication.
   Marking must survive the resize/transcode chain, so mark the master and
   re-verify after each derivative is produced.
3. **Separate provider duties from deployer duties in the engagement
   contract.** If the client generates creative with a third-party model, the
   **provider** carries the Article 50(2) marking duty and the **retailer**
   carries paragraphs 1/3/4 as deployer. Both need to be written down; the
   retailer owns the consumer-facing exposure either way.
4. **Keep a detectability test in CI.** Treat "can an independent detector read
   our marking?" as a build check, and re-run it before **2027-02-02** when
   interoperability becomes a duty.
5. **Log the labelling decision per asset, per market.** Article 50 is EU; the
   same creative may ship unmarked elsewhere, and the log is what proves the
   EU path was taken.

**⚠️ Scope honestly.** This KB previously carried 2026-12-02 as a blanket
"systems already on market" deadline. That was too broad. Quoting the wrong
scope to a client is worse than quoting no date, because it is checkable.

## Anti-patterns added 2026-11-22 (pass 3)

- **❌ Quoting a retail media market size without saying which market.** WARC
  says **$200.4B** (ad spend); Mordor says **~$25.5B** (networks/technology).
  The 8x gap is a definition, not a disagreement. Always state which.
- **❌ Treating AAMP and AdCP as equivalent options to hedge between.** AdCP:
  8610 refs, commits today, working implementations. `IABTechLab/AAMP`: two
  files, one commit, 61 days. Keep an adapter boundary, but build on AdCP.
- **❌ Reading a licence from the repo a listicle links.** Snowplow's umbrella
  repo says Apache-2.0; `stream-collector` and `enrich` — the services you
  deploy — are **Snowplow Limited Use License v1.1**. Audit per deployed
  artefact.
- **❌ Trusting a press release over a LICENSE file.** The Trade Desk announced
  UID2 as **BSD-2**; the repo is **Apache-2.0** (11348B).
- **❌ Vendoring `InteractiveAdvertisingBureau/openrtb`.** It has **no licence
  file** (root tree verified). Implement from the spec.
- **❌ Cloning Robyn or Matomo and expecting `main`.** Their default branches
  are `accuracy/allocator_v2_fixes` and `6.x-dev`. Resolve the default branch
  before building or measuring.
- **❌ Forking a dormant clean room** because it is the only thing shaped like
  the requirement. All three are 752–1258 days dead. Assemble from live
  primitives (Pattern 14).
- **❌ Believing a keyword search in retail.** `retail media network
  stars:>=10` returns three Windows DxDiag dumps; `data clean room stars:>=20`
  returns 18 hits of which 3 are real. Open every row.
- **❌ Writing star counts into this KB.** They are not measurable through the
  available channel (`gh api repos/<slug>` → 403 for non-attached repos), and
  this KB has shipped fabricated star curves twice. Record refs and last-commit
  dates, which **are** measurable.

---

## Pattern 18 — The ESPR Article 25 disposition engine (EMEA flagship; nothing like it exists)

**The problem.** Since **19 July 2026**, an EU large company may not destroy
unsold apparel, clothing accessories or footwear, must disclose unsold
quantities, and must justify any derogation. Crucially the rule is **typed**:
preparing a unit for **reuse** is lawful, **recycling** it counts as
destruction. So "cheapest disposition" is no longer a legal answer — the
output must be a defensible classification with evidence attached.

**Why this is a build and not a licence purchase.** `disposition engine`
returns **22 repositories worldwide and none are about retail**;
`extended producer responsibility` returns **24 repositories, maximum 1 star**.
There is no product and no open-source floor. Every component below is
verified permissive and alive as of 2026-11-23.

**The wiring.**

1. **Grade the unit.**
   [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib)
   (Apache-2.0, 6416★, pushed 2026-11-20) scores defect/anomaly on inbound
   images. Output: a condition score plus the defect mask that will serve as
   evidence. *Use this slug — `openvinotoolkit/anomalib` is the old name.*
2. **Type the decision, don't score it.**
   [apache/incubator-kie](https://github.com/apache/incubator-kie)
   (Apache-2.0, 6344★, pushed 2026-11-20) — Drools rules encoding, per
   jurisdiction: `reuse` and `repair` as permitted outcomes; `recycle` and
   `destroy` gated behind a Delegated Regulation (EU) 2026/296 derogation with
   a mandatory justification field. The condition score from step 1 is an input
   to the rule, never the decision itself.
3. **Rank cost only inside the legal type.** Once the lawful set is
   determined, order it by recoverable value minus freight — not before.
4. **Route the unit to the chosen destination.**
   [VROOM-Project/vroom](https://github.com/VROOM-Project/vroom) (BSD-2-Clause,
   1924★) over [Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend)
   (BSD-2-Clause, 8237★) for the distance matrix. Reverse flows are
   pickup-and-delivery VRPs; [graphhopper/jsprit](https://github.com/graphhopper/jsprit)
   (Apache-2.0) models pickups and deliveries in one tour natively.
5. **Persist the evidence.** Write the decision, the rule version, the
   derogation justification and the grading artefact into the Digital Product
   Passport record already documented in `verticals/solutions.md`. The
   disclosure obligation is satisfied by querying this store, not by a
   spreadsheet exercise at year end.

**The part clients will not expect, and the part worth charging for:** the rule
set must be **per Member State**, because France's AGEC is stricter than ESPR
and transposition of the companion repair directive is fragmented. Sell the
jurisdiction matrix, not a single compliance mode.

**Do not use** `ANL-CEEESA/RELOG` — Argonne's reverse-logistics optimiser is
the only domain-specific tool in existence and it has **no licence file on any
branch**. Default copyright applies.

---

## Pattern 19 — Grade-to-route: the agent that decides a return's fate

**The gap this fills.** The reverse flow's tool layer is strong and its **agent
layer is two repos wide**, neither of which decides anything: `returns agent`
returns 2464 repos and **zero relevant** ones. The closest thing to a
refund-decision agent in open source,
`LikhithV02/Customer-Support-Agent` (*"approves, denies or escalates
refunds"*), has **no licence** and 9★. So the deciding agent must be built.

**The wiring — a tool-calling agent over four verified tools.**

| Tool the agent calls | Repo | License | What it returns |
|---|---|---|---|
| `grade_unit(images)` | [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | Apache-2.0 | condition score + defect mask |
| `lawful_dispositions(sku, jurisdiction)` | [apache/incubator-kie](https://github.com/apache/incubator-kie) | Apache-2.0 | the permitted set, typed |
| `route_cost(origin, candidates)` | [VROOM-Project/vroom](https://github.com/VROOM-Project/vroom) + [Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend) | BSD-2-Clause | freight cost per destination |
| `resale_value(sku, grade)` | [budna-marketplace/recommerce](https://github.com/budna-marketplace/recommerce) | MIT | new-vs-pre-owned comparison |

**The design rule that matters.** The LLM **orchestrates and explains; it does
not decide legality.** `lawful_dispositions` is a hard gate: the agent may
choose freely within the set the rules engine returns and may never choose
outside it. This is the same separation Pattern 13 applied to rostering —
solver decides, prompt explains — and it is what makes the output auditable.

**Where the agent earns its keep:** writing the human-readable justification
for the derogation, reconciling a customer's description of the fault against
the grading model's mask, and escalating the disagreements. That is genuine
judgment work sitting on top of deterministic components.

**Start from** `Pragatheswar-72/support-agent` (MIT, 6★) as a *shape* for the
orchestrator — a LangGraph router to specialist agents — not as a dependency.

---

## Pattern 20 — Returns-abuse scoring a retailer can actually own (North America)

**Why now.** ~**9% of returns are fraudulent**; **85% of merchants already run
AI/ML against returns fraud** and only **45% think it works unaided**
(NRF / Happy Returns). The budget exists and the incumbent is distrusted by
more than half its own users — the rare case where the sales motion is
displacement, not education.

**Why you cannot just adopt the obvious libraries.** The graph-fraud toolboxes
every listicle recommends are **dead**:
[safe-graph/DGFraud](https://github.com/safe-graph/DGFraud) (Apache-2.0, 766★)
last pushed **2022-04-20**; `safe-graph/UGFraud` (Apache-2.0, 134★)
**2022-04-18**; `awslabs/realtime-fraud-detection-with-gnn-on-dgl`
(Apache-2.0, 225★) **2024-03-31**. Read them for architecture; do not deploy
them.

**The wiring.**

1. **Model the behaviour as a graph, not a row.** Returns abuse is relational —
   one address, many accounts; one payment instrument, many "damaged on
   arrival" claims. A per-transaction classifier structurally cannot see it.
2. **Generate before you train.**
   [SantanderAI/gen-fraud-graph](https://github.com/SantanderAI/gen-fraud-graph)
   (Apache-2.0, 296★, pushed 2026-10-01) produces synthetic fraud graphs for
   benchmarking. This is not a convenience: returns-fraud data **cannot be
   pooled across retailers** for competitive and privacy reasons, so a shared
   synthetic benchmark is the only way to compare models honestly.
3. **Implement the detector on a maintained GNN stack** (PyTorch Geometric or
   DGL) rather than resurrecting a 2022 toolbox.
4. **Feed the decision, not a dashboard.** The score's consumer is the
   authorisation step (`mage-os/module-rma`, MIT, is the reference
   implementation) and the "keep it" calculation.
5. **Keep the "keep it" call economic.** In North America there is no
   disposition mandate, so the decision is freight + grading cost vs
   recoverable value. The same engine ported to EMEA must instead run inside
   Pattern 18's legal gate.

**Watch the adjacent surface:** payment tooling is reported inadequate against
AI-enabled chargeback fraud where **autonomous agents** act for the shopper.
A retailer deploying agentic checkout is opening this exposure now.

---

## Pattern 21 — LATAM: beat the 7-day clock, then consolidate the pickups

**The constraint.** Brazil's CDC **Article 49** gives a **7-day right of
withdrawal from receipt** for distance sales — half the EU's 14 — and an
opened package is **not** an express exception to it. There is no room for
multi-day manual review: authorise inside the window or lose the argument.

**Part A — automate authorisation.**

1. [mage-os/module-rma](https://github.com/mage-os/module-rma) (MIT, 23★,
   pushed 2026-11-17) as the RMA spine. It is the **only permissively licensed
   standalone RMA component in open source**, so it is also the only one that
   can be re-licensed into a client's closed product.
2. A **statutory clock** per jurisdiction, driven from the delivery event —
   7 days Brazil (CDC Art. 49), 14 days EU, and each other market's own rule.
   Encode it in [apache/incubator-kie](https://github.com/apache/incubator-kie)
   (Apache-2.0) alongside the disposition rules, so one engine holds both the
   inbound deadline and the outbound legality.
3. **Auto-approve inside the window** for in-scope distance sales; route only
   out-of-scope cases (in-store purchases, which Art. 49 does not cover as a
   rule) to a human.

**Part B — make the freight affordable.** The region's own chosen remedy is
collection points and **locker networks**, and consolidating reverse pickups
across lockers is exactly a capacitated pickup VRP:

- [PyVRP/PyVRP](https://github.com/PyVRP/PyVRP) (MIT, 734★, pushed 2026-11-19)
  for a Python-first team, or
  [VROOM-Project/vroom](https://github.com/VROOM-Project/vroom) (BSD-2-Clause)
  for a service you call.
- [valhalla/valhalla](https://github.com/valhalla/valhalla) — **MIT**, 6481★ —
  where time-dependent costing matters. ⚠️ GitHub reports its licence as
  `NOASSERTION` because `LICENSE.md` is a 44-byte pointer; the real `COPYING`
  is plain MIT. **Expect to have to explain this to a client's licence gate.**

**Part C — price the re-import.** A returned cross-border unit is a customs
event: Mexico's simplified regime charges by country of origin, Argentina uses
a courier small-shipments regime, Brazil layers federal and state taxes. In
LATAM the customs line, not consumer law, is what makes a return expensive —
model it inside the disposition decision.

**⚠️ Verify before you deliver.** The Article 49 detail above rests on
Brazilian legal commentary and trade press, **not** on the Planalto statute
text, which could not be fetched in this session. This pass found **no
primary-source 2026 returns regulation** for Brazil, Mexico, Colombia or
Chile. Treat the region as *"no mandate found"*, not *"no mandate exists"*, and
read Art. 49 against the official text before it reaches a client.

---

## Pattern 22 — The price-event ledger with four regional projections

**The problem.** Four regions attach four different legal objects to the same
number (`intel/market.md` → Opportunities by region). Teams build the ledger for
whichever region is in front of them, and the ledger then cannot answer the other
three — not because of effort, but because it stored the wrong thing.

**The one build that serves all four.** An **append-only price-event log** that
records, at every price change *and* at every quote:

```
price_event {
  variant_id, context {region, currency, price_list_id, schedule_id, channel},
  base_price, applied_promotions[], fee_components[{code, amount, recipient}],
  pricing_inputs {segment_id, cohort_rules_version, competitor_feed_rev,
                  model_version, NO per-person attributes},
  displayed_total, observed_at, source {event | hourly_sweep | backfill}
}
```

**The four projections, and why none substitutes for another:**

| Region | Projection | Needs from the log |
|---|---|---|
| **EMEA** | `min(base_price)` over trailing 30 days per `variant × context`, with step-wise handling where art. 6a(5) was not adopted | Complete price history **per pricing context**, not per variant alone |
| **North America** | Proof of the **absence** of per-consumer variation | `pricing_inputs` — the *inputs*, not the outcomes. An outcome-only ledger cannot answer a counterfactual |
| **APAC** | `displayed_total` including every transaction-based fee **at display time** | `fee_components` captured on the **quote** path, not the catalogue path |
| **LATAM** | Money split **by recipient per transaction** | `fee_components[].recipient` — a monolithic `final_price` field destroys this irreversibly |

**Wiring.** Take the capture design from
[zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance)
(MIT) — three capture paths (events + hourly sweep + on-demand backfill), never
edit a recorded price, ≥400-day retention, warn on incomplete history and on a
"reduction" that is not below the reference. Keep the log in Postgres beside the
platform ([medusajs/medusa](https://github.com/medusajs/medusa) MIT,
[saleor/saleor](https://github.com/saleor/saleor) BSD-3, or
[odoo/odoo](https://github.com/odoo/odoo) LGPL-3.0 — all permit a proprietary
module on top). Expose each projection as a read model, one per region.

**Why it is a pattern and not a product.** Only the **EMEA** projection exists in
open source, at 0★ and one day old, for one platform, in one member state's
specifics. The other three are greenfield. **Do not promise a product; promise
one ledger and the projection the client's region needs first.**

**Hard rule.** Never put per-person attributes in `pricing_inputs`. Three US
states ban personalised pricing and New Jersey attached a **private right of
action** — a log that *contains* person-level pricing inputs is discovery
material rather than a defence. Segment-level only (Pattern 25).

---

## Pattern 23 — Licensed elasticity → your own optimiser (the assembly that replaces the missing engine)

**The problem.** Retail markdown/promotion optimisation has **no licensed,
maintained open-source implementation** — and the best algorithmic answer that
exists, [cvxgrp/elasticity-estimation](https://github.com/cvxgrp/elasticity-estimation)
(Stanford/Boyd group, *Estimating Price Elasticity Matrices*, April 2026), has
**no licence file**. Clients still need the capability.

**The assembly — every dependency permissive, verified 2026-11-23:**

```
Scanner / POS sales panel  ─┐
Competitor price feed      ─┤
   (changedetection.io,     │
    Apache-2.0, 35967★)     │
                            ▼
[splink MIT 2594★] ── match products across retailers
                            │
                            ▼
[pymc-marketing Apache-2.0 1314★]
   customer_choice/BayesianBLP  ── posterior cross-price elasticities
   (documented for Nielsen / IRI / retailer-scanner panels)
   └─ MixedLogit for individual-level choice
   └─ [pyblp MIT 297★] as the classical cross-check
                            │
                            ▼
[py-why/EconML MIT 4861★ | uber/causalml Apache-2.0 6047★]
   ── heterogeneous price response by SEGMENT (never by person)
                            │
                            ▼
╔═════════════════════════════════════════════════════════╗
║  MARKDOWN / PROMOTION OPTIMISER  —  GLOBANT IP           ║
║  Expressed on [cvxpy Apache-2.0] or [or-tools Apache-2.0]║
║  Objective: margin over the lifecycle, subject to        ║
║  inventory, min-margin, price-ladder and legal floors    ║
╚═════════════════════════════════════════════════════════╝
                            │
                            ▼
[offerkit MIT 58★] promotions  │  platform price lists  │  Pattern 22 ledger
```

**Why this is better than "build a pricing platform".** The elasticity work — the
part a client assumes is the hard science — arrives under Apache-2.0 and MIT,
fitted to exactly the data shape retailers already have (scanner panels). What
remains proprietary is the **constrained decision**, which is a smaller,
better-specified build and the only step with no licensed option.

**Three warnings, each from a measurement this pass:**
1. **Read `cvxgrp/elasticity-estimation`'s paper; vendor nothing.** No grant on
   `main`. Reimplementing the published method is lawful; copying the repo is not.
2. **Do not reach for `pymc_marketing/mmm/price_response.py`.** It prices a
   *delivered media unit*, not a product. The retail module is
   `customer_choice/bayesian_blp.py`.
3. **`dedupe` (MIT, 4531★) is dormant since 2025-07-29.** Prefer `splink`.
   Avoid `zingg` inside a shipped product — **AGPL-3.0** (34523 B verified).

---

## Pattern 24 — Competitive price intelligence that survives the matching step

**Supersedes Pattern 6**, which states that the matching floor is zero. It is not.

```
[dgtlmoon/changedetection.io Apache-2.0 35967★]  ← deployable as-is, price watchers
        or [apify/crawlee Apache-2.0 26521★] / [scrapy/scrapy BSD-3 65542★]
        or [apify/apify-mcp-server MIT 17199★]  ← typed MCP access (already in KB)
                            │
                            ▼
[moj-analytical-services/splink MIT 2594★]  ── probabilistic product matching
   ONE comparison model per category; GTIN/GS1 where present (pass 1's
   product-data plane), probabilistic matching only where it is not
                            │
                            ▼
Pattern 22 ledger  →  competitor_feed_rev stamped on every pricing decision
                            │
                            ▼
Pattern 23 elasticity  →  your optimiser
```

**The step everyone skips.** Price collection is easy and well supplied;
**knowing two listings are the same product is the actual bottleneck**, and this
KB previously recorded that layer as empty on the strength of one query that
returns a false negative. GTIN presence resolves it cheaply where it exists —
cycle 8's product-data finding that **GTIN is not required by the ACP feed spec**
is exactly why probabilistic matching is still needed.

**Regional corpora that already exist** (useful as test fixtures, and as proof the
category is tractable): [supermarkt/checkjebon](https://github.com/supermarkt/checkjebon)
(MIT, 259★, Dutch supermarkets) and
[ByteSizedMarius/rewerse-engineering](https://github.com/ByteSizedMarius/rewerse-engineering)
(MIT, 98★, REWE Germany). **Do not** depend on
[ivorpad/mercadona-cli](https://github.com/ivorpad/mercadona-cli) (338★) — **no
licence file**, despite being the most agent-shaped of the three.

**Legal gate before this ships.** Collection is lawful in general; using a
competitor feed to coordinate rather than to compete is not. Keep
`competitor_feed_rev` and `model_version` on every decision (Pattern 22) so the
record shows the system reacted to *public* prices. The only open-source work on
algorithmic collusion is academic replication code
([matteocourthoud/Algorithmic-Collusion-Replication](https://github.com/matteocourthoud/Algorithmic-Collusion-Replication)
MIT 22★ dead 2023-06-20; [becmn/algorithmic-collusion](https://github.com/becmn/algorithmic-collusion)
MIT 0★ 2026-10-30) — evidence the risk is studied, **not an audit tool**.

---

## Pattern 25 — North America safe mode: segment pricing with a discoverable defence

**The driver, with dates.** Maryland (signed 2026-04-28), Connecticut (signed
2026-06-04, effective 2026-10-01) and New Jersey (**private right of action** via
the NJ Consumer Fraud Act) ban personalised pricing; New York requires
disclosure; **New York's One Fair Price Act must be signed or not by 2026-12-31**.
All search-derived, not fetch-verified.

**The build.**
1. **Segment, never person.** Price varies by store, channel, region, time,
   inventory and competitor price — all in `pricing_inputs`. Person-level
   attributes are **not collected into the pricing path at all**, so the defence
   is architectural rather than a policy document.
2. **Pin the lawful lever.** Trade press reports leading retailers use dynamic
   pricing mainly to **match competitor price drops**. Implement that as an
   explicit, named rule with its own `rule_id`, so the common case is
   self-evidencing.
3. **Log inputs, not just outcomes.** The NA question is a counterfactual —
   *would this shopper have seen a different price?* Only an input log answers it.
   This is the projection the EMEA ledger cannot serve (Pattern 22).
4. **Disclose where required.** New York's model is disclosure; reuse the
   personalised-pricing disclosure surface from
   [zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance)
   (MIT) even outside Medusa — it is the only implementation of that disclosure
   found anywhere.
5. **Keep the optimiser inside the fence.** The Pattern 23 optimiser consumes
   segment-level elasticities from `EconML`/`causalml`. If a feature engineer can
   add a person-level covariate without review, the architectural defence is gone.

**Why the private right of action changes the sale.** Regulator-only exposure
gets a policy. A private right of action gets **plaintiffs with discovery**, and
a ledger built to produce a defence is worth more than a model built to produce a
margin. This is the commercial reason a North American retailer funds the audit
trail — and it is why the audit trail, not the optimiser, is the lead deliverable.

---

## Anti-patterns added 2026-11-23 (pass 5)

- **Do not quote a measured zero as "nothing exists" — including this KB's own.**
  Four cycles carried *"product matching entity resolution stars:>=200 = 0"* into
  a build recommendation. `splink` (MIT 2594★), `dedupe` (MIT 4531★) and `zingg`
  (AGPL 1275★) all exist; the query still returns zero. **Before writing a gap,
  re-ask it two other ways and look up by name the three libraries you would
  expect to exist.**
- **Do not cite or vendor `cvxgrp/elasticity-estimation`.** Best available method,
  **no licence grant**. Same failure as pass 4's RELOG.
- **Do not grep a good repo for a concept and trust the path.**
  `pymc_marketing/mmm/price_response.py` prices media impressions, not products.
- **Do not promise an open-source markdown or clearance engine.** Three retail
  attempts, **three with no licence file**.
- **Do not treat "dynamic pricing" search results as retail.** In open source the
  term overwhelmingly means **electricity tariffs**.
- **Do not select `lago` or `meteroid` for retail pricing.** SaaS metering and
  subscription billing, and both **AGPL-3.0** — a fit error and a licence error.
- **Do not assume `search/repositories` HTTP 422 means a rename.** `facebook/Ax`
  is live (4642 refs, MIT at `main`) and returns 422. Pass 4's rule needed this
  second half.
- **Do not reuse a region's regulatory weight across planes.** Cycle 8's "North
  America is the weakest-sourced region" is false for price, where NA has the only
  in-force bans.
- **Do not build one compliance ledger and assume it travels.** Four regions, four
  projections, and the EMEA one provably cannot answer the NA question.

## Method notes added 2026-11-23 (pass 5)

1. **The vocabulary probe paid for itself again, and cost one Bash call.** 46
   candidate terms grepped against all eight files *before* any web search:
   `elasticit`, `dynamic pric`, `competitor pric`, `price scrap`, `unit price`,
   `drip pricing`, `shrinkflation`, `algorithmic collusion`, `personalized
   pricing`, `clearance`, `revenue management`, `coupon`, `bundl`, `cross-sell`
   all at **literal zero**. The 19 `markdown` hits were the **file format** —
   check what a hit actually is before counting it as coverage.
2. **A plane can be *referenced* across a whole KB and still be *unresearched*.**
   "Pricing" appeared in all eight files as the thing with no open-source floor,
   which read like coverage and was a four-cycle-old unexamined assertion. **Grep
   for the plane's vocabulary, not for its name.**
3. **422 ≠ rename** (restates pass 4). 422 means search cannot see the repo;
   `ls-remote` plus a raw licence read settles whether it moved or is simply
   missing from the index.
4. **Short licence files cut both ways.** `uber/causalml`'s 561 B `LICENSE` is a
   *valid* Apache-2.0 grant by reference; Meilisearch's 468 B file was a
   multi-licence redirect. **Short ≠ invalid; short = read it.**
5. **Nine filename variants are the minimum licence probe:** `LICENSE`,
   `LICENSE.txt`, `LICENSE.TXT`, `LICENSE.md`, `LICENCE`, `LICENCE.txt`,
   `COPYING`, `COPYING.txt`, `LICENSE-APACHE`. `Pyomo` declares BSD-3-Clause only
   in `LICENSE.md`; pass 4 added `LICENSE.TXT` for `osrm-backend`.
6. **The byte-size fingerprint table from cycle 8 verified correct again:**
   `zingg` = 34523 B = AGPL-3.0, exactly as tabulated.
7. **`search/repositories` with `repo:owner/name` remains the only metadata
   channel** (stars + licence + `pushed_at` in one call); `gh api repos/<slug>`
   is still 403 in-session, and `curl -sI github.com` still blind through the
   proxy. **Existence is `git ls-remote`, full stop.**
