---
industry: retail
region: Global
updated: 2026-11-22
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
