---
industry: retail
region: Global
updated: 2026-11-23
---

# 🏭 Vertical Platforms — Retail & Consumer

> Real, running commerce/ERP systems you can customise and put an agent layer on top of, instead of
> building a storefront from scratch. **Every license below was read, not inferred** — this layer is where
> retail's licensing traps live, and the public listicles get it wrong consistently.
>
> *This file previously contained a single placeholder row (`| — | — | — | — | Por completar |`) that had
> been live in the KB as data since 2026-07-02.*

## Read this first — the license shape of the retail platform layer

Retail is **unusually lucky**: unlike media (where the platform layer is almost uniformly copyleft), retail
has genuinely permissive, production-grade commerce platforms. That means you rarely need to accept
copyleft to ship a storefront.

The traps are concentrated in the **ERP/CRM** layer and in a few platforms that *look* permissive:

- **`nopSolutions/nopCommerce` is the sharpest trap.** Its "nopCommerce Public License v4.0" is AGPL v3
  **plus a requirement that a visible "powered by nopCommerce" link appear on every single user-interface
  screen**, in the same position, linking to nopcommerce.com — removable only via a paid copyright-removal
  key. That is a hard blocker for any white-label retail client.
- **`vendure-ecommerce/vendure` is GPLv3** (dual-licensed with a commercial VCL), not MIT as commonly
  listed. Default, without a paid agreement, is GPLv3.
- **`PrestaShop/PrestaShop` is OSL-3.0 for core and AFL-3.0 for modules** — two different licenses in one
  repo, which a single "license" field cannot express.
- **`twentyhq/twenty` (CRM) is AGPLv3 + per-file commercial EE + MIT SDK packages.** Public sources
  disagree (one says BSL-1.1, another GPLv3); **both are wrong**. There is an explicit "Twenty Application
  Exception" additional permission under AGPL §7 for building apps against its interfaces.
- **`odoo/odoo` is LGPLv3, not GPL.** This is the single most commercially useful licensing fact in retail
  and it is routinely reported wrong: LGPL means **you can build and sell proprietary Odoo modules**.
- `innocommerce/innoshop` and `beikeshop/beikeshop` are both **Open Software License** — not permissive.

## Platforms — permissive (preferred starting points)

| Platform | Repo | License | Stars | Last push | Stack | Use case |
|---|---|---|---|---|---|---|
| Medusa | [medusajs/medusa](https://github.com/medusajs/medusa) | MIT (1,075 B, read) | 37,346 | 2026-11-21 | Node/TS | Headless commerce. The most adoptable permissive core; modular enough to attach agents per domain |
| Bagisto | [bagisto/bagisto](https://github.com/bagisto/bagisto) | MIT | 28,392 | 2026-11-18 | Laravel/PHP | Full storefront + admin, strong in India/MEA markets |
| Saleor | [saleor/saleor](https://github.com/saleor/saleor) | BSD-3-Clause | 23,591 | 2026-11-20 | Python/GraphQL | GraphQL-native headless commerce; cleanest API surface for agent tooling |
| Spree | [spree/spree](https://github.com/spree/spree) | BSD-3-Clause | 15,848 | 2026-11-20 | Rails | Mature, extensible; good for marketplace models |
| Sylius | [Sylius/Sylius](https://github.com/Sylius/Sylius) | MIT | 8,576 | 2026-11-18 | Symfony/PHP | B2B-leaning commerce with strong domain modelling |
| Shopware | [shopware/shopware](https://github.com/shopware/shopware) | MIT | 3,475 | 2026-11-20 | Symfony/PHP | Strong in DACH/EMEA mid-market |
| Apache OFBiz | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1,151 | 2026-11-20 | Java | ERP + CRM + commerce in one framework. **Use this slug** — `apache/ofbiz` is **archived** (last push 2020-04-27) and is what the listicles still link to |

## Platforms — copyleft or restricted (viable, but structure the engagement around it)

| Platform | Repo | License | Stars | Last push | Constraint |
|---|---|---|---|---|---|
| Odoo | [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (read, 43,529 B) | 56,000 | 2026-11-21 | LGPL → proprietary modules **are** allowed. The strongest retail ERP story in open source |
| ERPNext | [frappe/erpnext](https://github.com/frappe/erpnext) | GPL-3.0 | 41,489 | 2026-11-21 | Full ERP incl. inventory/POS. GPL → keep customisations as separate apps, expect disclosure |
| Twenty (CRM) | [twentyhq/twenty](https://github.com/twentyhq/twenty) | AGPL-3.0 + EE files + MIT SDKs | 61,273 | 2026-11-21 | Build **against** its interfaces using the AGPL §7 Application Exception and the MIT SDKs |
| WooCommerce | [woocommerce/woocommerce](https://github.com/woocommerce/woocommerce) | GPL-2.0 | 10,607 | 2026-11-21 | Huge SMB install base. Reach it via the Apache-2.0 `bighadj22/Wocart` AI layer rather than forking core |
| nopCommerce | [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce) | **NPL** = AGPL-3.0 + mandatory per-screen attribution | 10,186 | 2026-11-19 | ⚠️ Avoid for white-label work — see above |
| PrestaShop | [PrestaShop/PrestaShop](https://github.com/PrestaShop/PrestaShop) | OSL-3.0 core / AFL-3.0 modules | 9,259 | 2026-11-20 | Strong in France/Southern Europe/LATAM. Write **modules** (AFL-3.0, permissive-ish), not core patches |
| Vendure | [vendure-ecommerce/vendure](https://github.com/vendure-ecommerce/vendure) | GPL-3.0 (dual w/ commercial VCL) | live (refs=3,168) | — | Modern TS stack, but GPL by default |
| beikeshop | [beikeshop/beikeshop](https://github.com/beikeshop/beikeshop) | Open Software License | 1,988 | 2026-11-17 | Laravel, multilingual; OSL is copyleft |
| innoshop | [innocommerce/innoshop](https://github.com/innocommerce/innoshop) | Open Software License | 670 | 2026-11-19 | Laravel; OSL is copyleft |

## Gap: there is no open-source retail price/markdown engine

Every platform above handles catalogue, cart and checkout. **None** ships pricing optimisation, and no
credible open-source project fills it (see `repos/foundations.md` → Measured gaps). Assortment, markdown
and promotion optimisation are therefore the highest-margin place to build proprietary IP on top of a
permissive base — the client cannot get it off the shelf.

## How to add the AI layer

1. **Pick a permissive base** (Medusa or Saleor if greenfield; Odoo if the client needs ERP breadth and you
   want to sell proprietary modules under LGPL).
2. **Expose the domain as typed tools, not prose** — wrap catalogue/order/inventory as an MCP server. This
   is the step that actually determines whether agents work (see trends #3).
3. **Speak a protocol, not a bespoke API** — implement UCP and/or ACP via the NVIDIA blueprint so the
   client is reachable from ChatGPT and Google surfaces.
4. **Add agents per domain** — merchandising, demand planning, service — each with a scoped tool set.
5. **Keep a human approval step on anything that moves money or price.** Agent-initiated payment consent is
   exactly what AP2 exists to record.

---

## Added 2026-11-22 — PIM, WMS and Digital Product Passport platforms

Yesterday's audit covered storefronts and ERP. The layer missing from this KB entirely was **where product
data actually lives**: the PIM. It is also, measured today, the layer with the *worst* public licence
reporting in all of retail — **three of five PIM licence claims in circulation are wrong.**

### Product Information Management — read the licence table before the feature table

| Platform | Repo | License (as verified 2026-11-22) | ★ / forks | Last push | Verdict for client work |
|---|---|---|---|---|---|
| UnoPim | [unopim/unopim](https://github.com/unopim/unopim) | **MIT** — read, 1078 B, full MIT text, Webkul Software | 11080★ / 193f | 2026-11-20 | ✅ **The only permissive, maintained PIM.** Laravel/PHP, PIM + DAM, vendor markets it with agentic-AI features. Its own vendor page claims MIT in one place and Apache-2.0 in another; the file says MIT. |
| Akeneo Community Edition | [akeneo/pim-community-dev](https://github.com/akeneo/pim-community-dev) | **OSL-3.0** — declared in a **148-byte file named `LICENCE.txt`** (British spelling, `.txt`) | 1053★ / 536f | 2026-11-22 | ⚠️ The de-facto industry standard PIM, but OSL-3.0 is strongly reciprocal with an external-deployment trigger. Not in Globant's permissive set. Also note the copyright line still reads **2013–2017** on a repo pushed today. |
| Pimcore | [pimcore/pimcore](https://github.com/pimcore/pimcore) | ❌ **Pimcore Open Core License (POCL)** — a bespoke 24927-byte vendor agreement, "Last Update: June 2025". **Not an OSI licence.** | 3891★ / 1513f | 2026-11-22 | ❌ **Do not describe Pimcore as open source.** Every listicle — including long-standing "open source alternative" write-ups — still calls the community edition GPLv3. It has not been GPL since June 2025. Highest fork count in the layer (1513), so it does have the real install base; that makes the misreporting more dangerous, not less. |
| AtroPIM / AtroCore | [atrocore/atropim](https://github.com/atrocore/atropim) | GPL-3.0 — read, `master/LICENSE.txt`, 35150 B | 213★ / 36f | 2026-11-19 | ⚠️ Honest, maintained, genuinely configurable. GPL-3.0 rules out proprietary derivative modules. |
| Pimify | [pimify/pimify](https://github.com/pimify/pimify) | Apache-2.0 — read, 11357 B | 23★ / 4f | 2026-11-14 | ⚠️ Correct licence, Python/Django, but 23★ / 4 forks. A starting point to fork, not a platform to stake a programme on. |

**The commercially useful sentence:** in the PIM layer exactly **one of five options is both permissive and
maintained** — UnoPim (MIT). Note also the star/fork anomaly: UnoPim has 11080★ against 193 forks (57:1),
while Akeneo has 1053★ against 536 forks (2:1) and Pimcore 1513 forks. **Stars measure attention; forks
measure deployment.** UnoPim is the right licence bet; Akeneo and Pimcore are where the installed base is.
Plan migrations accordingly rather than assuming the star leader is what the client is running.

### Warehouse / inventory platforms

| Platform | Repo | License | ★ / forks | Last push | Notes |
|---|---|---|---|---|---|
| GreaterWMS | [GreaterWMS/GreaterWMS](https://github.com/GreaterWMS/GreaterWMS) | Apache-2.0 | 4462★ / 1180f | 2026-10-26 | ✅ Largest permissive WMS; originated in Ford Asia-Pacific after-sales logistics. Python/Vue. Strong fork count = real deployments. |
| OpenWMS | [openwms/org.openwms](https://github.com/openwms/org.openwms) | Apache-2.0 | 764★ / 223f | 2026-07-13 | ✅ Java/Spring, modular, more "framework" than product. 4 months since last push. |
| OpenBoxes | [openboxes/openboxes](https://github.com/openboxes/openboxes) | EPL-1.0 | 935★ / 518f | 2026-11-22 | ⚠️ Very active (pushed the day of this pass), strong in health-supply logistics. EPL-1.0 is weak copyleft — file-level reciprocity, generally workable, but it is **not** on the MIT/Apache list. |
| OCA WMS (Odoo) | [OCA/wms](https://github.com/OCA/wms) | AGPL-3.0 | 229★ / 228f | 2026-11-18 | ⚠️ The right answer **if the client already runs Odoo** — and remember Odoo core is LGPL-3.0, so proprietary modules are allowed, but these OCA modules are AGPL. Fork count ≈ star count: pure practitioner repo. |

### Digital Product Passport platforms (EMEA-driven, early)

| Platform | Repo | License | ★ / forks | Last push | Notes |
|---|---|---|---|---|---|
| Eclipse Tractus-X Digital Product Pass | [eclipse-tractusx/digital-product-pass](https://github.com/eclipse-tractusx/digital-product-pass) | Apache-2.0 — read, 11505 B | 50★ / 31f | 2025-09-18 | ✅ Best-licensed DPP viewer, Catena-X/automotive lineage, so it assumes a dataspace. **14 months without a push** — use as a reference implementation, not a dependency. |
| open-dpp | [open-dpp/open-dpp](https://github.com/open-dpp/open-dpp) | AGPL-3.0 — read, 34523 B | 35★ / 19f | 2026-11-22 | ⚠️ The most active DPP platform (pushed the day of this pass), TypeScript. AGPL: run it as a service, do not embed. |
| DPPO (ontology) | [LiUSemWeb/DPPO](https://github.com/LiUSemWeb/DPPO) | ❌ **no licence file** | 11★ | 2026-06-30 | Digital Product Passport ontology from Linköping University. Useful vocabulary, **no grant of rights** — model after it, do not copy it in. |

**State of this sub-layer, stated honestly:** DPP tooling is pre-standard. No ESPR product-group delegated
act has been adopted yet (see `intel/market.md` → EMEA), so every platform here is building against a
moving target. The defensible engagement today is **getting identity and attributes right** (steps 1–3 in
`repos/foundations.md`), because that work is required by DPP, by Sunrise 2027 *and* by agentic commerce —
regardless of which DPP platform eventually wins.

---

## Added 2026-11-22 (pass 2) — till platforms, fiscal platforms and the AGPL inversion

### Point-of-sale platforms that can be customised with AI on top

The retail equivalent of Odoo-for-ERP or OpenMRS-for-healthcare. Verified 2026-11-22 by `ls-remote` plus a
read of the licence file; API licence fields are noted where they disagree with the file.

| Platform | Repo | Licence (read at source) | ★ | Last push | Customisation posture |
|---|---|---|---|---|---|
| **Odoo** (POS + stock + fiscal) | [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (API says `NOASSERTION`) | 56025★ | 2026-11-22 | The reference choice. LGPL ⇒ proprietary add-on modules are permitted, which is why Odoo is the standard base for billable vertical work. **But read the AGPL inversion below before promising it for LATAM.** |
| **ERPNext / Frappe** | [frappe/erpnext](https://github.com/frappe/erpnext) | **GPL-3.0** (`license.txt`, Markdown) | 41543★ | 2026-11-22 | POS, warehouse, and the India GST localisation in-tree. GPL ⇒ a modified distribution must be opened; hosting it for one client is fine. |
| **Open Source Point of Sale** | [opensourcepos/opensourcepos](https://github.com/opensourcepos/opensourcepos) | **MIT** (2537 B incl. 26-name roster) | 4530★ | 2026-11-22 | The only permissive *and* maintained standalone till. PHP/CodeIgniter 4 + MySQL, Docker install, multi-tier tax. The clean base when the client wants to own the result outright. |
| **NexoPOS** | [Blair2004/NexoPOS](https://github.com/Blair2004/NexoPOS) | **GPL-3.0** | 1310★ | 2026-11-22 | Laravel/Vue, registers, inventory, most actively developed dedicated POS measured. |
| **Apache OFBiz** | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | **Apache-2.0** | 1151★ / 770f | 2026-11-22 | Still the only Apache-licensed full ERP with a POS module. **Use this slug:** `apache/ofbiz` is archived (last push 2020-04-27) and is what most listicles still link — carried forward from cycle 8. |

**Not usable, despite appearances:** [tngoman/Store-POS](https://github.com/tngoman/Store-POS), 1058★ — the
single highest-starred result for `point of sale retail stars:>=300` — **ships no licence file**.

### Fiscalisation platforms — the layer that makes a till lawful

A POS without fiscalisation is a demo. These are the platform-grade projects, not just libraries:

| Platform | Repo | Licence | ★ | Scope |
|---|---|---|---|---|
| **LibreDTE** (Chile) | [LibreDTE/libredte-app-community](https://github.com/LibreDTE/libredte-app-community) | **AGPL-3.0** | 42★ | Full web application for Chilean DTE/boleta issuance against the SII. Core library `libredte-lib-core` is also AGPL-3.0 (228★ / 166 forks, pushed 2026-11-19). The PHP/Python **API clients are LGPL-3.0**, but they call LibreDTE's *hosted* service — so the permissive path is a dependency on someone else's SaaS, not self-hosting. |
| **Oxalis** (Peppol AP) | [OxalisCommunity/oxalis](https://github.com/OxalisCommunity/oxalis) | **EUPL-1.1+** (declared in `COPYRIGHT`; repo also ships `COPYING.LGPL`) | 150★ | The reference Peppol Access Point, originally built by the Norwegian government agency Difi. Required shape for EU **and** Singapore InvoiceNow. Dormant since 2026-04-16 — the live alternative is `phax/phase4` (Apache-2.0, pushed 2026-11-18). |
| **india-compliance** (India) | [resilient-tech/india-compliance](https://github.com/resilient-tech/india-compliance) | **GPL-3.0** | 286★ / 4725 refs | GST e-invoicing and e-way bills as a Frappe/ERPNext app. The cleanest example in retail of fiscal compliance shipped *as an ERP module* rather than a library. |
| **Odoo OCA localisations** | [OCA/l10n-brazil](https://github.com/OCA/l10n-brazil) · [OCA/l10n-mexico](https://github.com/OCA/l10n-mexico) · [OCA/l10n-chile](https://github.com/OCA/l10n-chile) | **AGPL-3.0** — all three | 376★ / 20★ / 10★ | The modules that make an Odoo POS legal in Brazil, Mexico and Chile. See below. |

### ⚠️ The AGPL inversion — the single most commercially important fact in this pass

Cycle 8 established, correctly, that **Odoo core is LGPL-3.0, not GPL**, and concluded that *proprietary
Odoo modules are allowed* — calling it the most useful licence fact in retail.

**That conclusion inverts the moment the deployment needs LATAM fiscal compliance.** The OCA country
localisations — `l10n-brazil`, `l10n-mexico`, `l10n-chile` — are each **AGPL-3.0**, verified by reading
`LICENSE` at source: 34523 bytes, first line `GNU AFFERO GENERAL PUBLIC LICENSE`, byte-identical to
Ultralytics'. A hosted Odoo that issues NF-e, CFDI or DTE therefore combines LGPL core with **AGPL**
modules, and AGPL's network clause reaches the service your client's customers touch.

Practical consequences, in order of usefulness:

1. **Do not tell a LATAM client "Odoo is LGPL so your modules stay closed."** It is true of the core and
   false of the part that makes them legal.
2. **Keep the fiscal boundary at a process edge.** Run issuance as a separate service speaking a documented
   API, so the AGPL obligation attaches to a replaceable compliance component, not to the client's
   merchandising IP.
3. **Or avoid the Odoo localisation entirely** and build issuance on the permissive national libraries:
   Mexico MIT (`phpcfdi/*`, `python-satcfdi`), Brazil Apache-2.0 (`wmixvideo/nfe`) or LGPL-3.0
   (`sped-nfe`). Chile has no permissive option — `libredte-lib-core` is AGPL-3.0 and there is nothing else:
   `factura electronica DTE SII stars:>=20` returns **0 results**.
4. **Forks, not stars, tell you these are in production.** `l10n-mexico` 20★ / 56 forks, `l10n-chile`
   10★ / 41 forks. They are patched per client, which is also why their licence matters.

### Workforce platforms — the genuinely empty shelf

There is no open-source retail workforce-management platform. `workforce scheduling stars:>=150` returns
exactly one repo, [Staffjoy/v2](https://github.com/Staffjoy/v2) (MIT, 1686★), **abandoned since
2022-12-06**. The honest build is [TimefoldAI/timefold-solver](https://github.com/TimefoldAI/timefold-solver)
(Apache-2.0, 1879★, pushed 2026-11-20) as the constraint engine, with the labour rules, the UI and the
mobile app as Globant-owned work. That is a product, not an integration — and it is the correct way to
describe it in a proposal.

## Added 2026-11-22 (pass 3) — retail media platforms, and the licence trap inside one of them

A retail media network needs four platform pieces: something to **serve** the
ad, something to **identify** the shopper, something to **collect** the
behaviour, and something to **report** to the advertiser. All four exist in
open source. Only one of them is retail-specific, and that one is none of them
— there is **no open-source retail media platform** (see the gap note below).

Every row measured 2026-11-22: refs by `ls-remote`, last commit by bare
`--depth 1` clone, licence read at `raw.githubusercontent.com` with byte size.

### Serve, identify, collect, report

| Platform | Repo | Licence (read at source) | refs | Last commit | Customise with AI on top? |
|---|---|---|---|---|---|
| **Revive Adserver** | [revive-adserver/revive-adserver](https://github.com/revive-adserver/revive-adserver) | ⚠️ **GPL-2.0** (15235B, `master`) | 858 | 2026-11-22 (0d) | The only mature OSS ad server. Alive, but copyleft — wrap, don't embed |
| **Prebid Server** | [prebid/prebid-server](https://github.com/prebid/prebid-server) | Apache-2.0 (10759B, `master`) | 4327 | 2026-11-19 (3d) | Self-hosted auction. Permissive. Add bid-shading / yield models as modules |
| **UID2 Operator** | [IABTechLab/uid2-operator](https://github.com/IABTechLab/uid2-operator) | Apache-2.0 (11348B) | 4067 | 2026-11-22 (0d) | Run your own identity service. The prerequisite for selling audiences |
| **Apache Pinot** | [apache/pinot](https://github.com/apache/pinot) | Apache-2.0 (11356B, `master`) | 17558 | 2026-11-21 (1d) | Advertiser-facing campaign reporting at ad-event volume |
| **Apache Druid** | [apache/druid](https://github.com/apache/druid) | Apache-2.0 (19315B, `master`) | 17408 | 2026-11-21 (1d) | Same role; pick on team familiarity, not features |
| **Apache Superset** | [apache/superset](https://github.com/apache/superset) | Apache-2.0 (11585B, `master`) | 30919 | 2026-11-22 (0d) | The advertiser self-service dashboard, without building a UI |
| **Matomo** | [matomo-org/matomo](https://github.com/matomo-org/matomo) | ⚠️ **GPL-3.0** (35146B) | 12619 | 2026-11-23 (0d) | First-party analytics, self-hosted. Alive but copyleft. ⚠️ default branch is **`6.x-dev`** |

### ⚠️ Snowplow: one product, three licences, and a zero-byte licence file

Snowplow is the usual open-source answer for the first-party behavioural
pipeline a retail media network runs on. Its licence is routinely reported as
Apache-2.0. **That is true only of the repository nobody deploys.**

| Repo | What it is | Licence (read at source) | refs | Last commit |
|---|---|---|---|---|
| [snowplow/snowplow](https://github.com/snowplow/snowplow) | Umbrella / meta repo | **Apache-2.0** (11359B) — and also ships a **0-byte `LICENSE.md`** | 2984 | 2026-10-19 (34d) |
| [snowplow/stream-collector](https://github.com/snowplow/stream-collector) | The collector you actually run | ⚠️ **Snowplow Limited Use License Agreement v1.1 (Nov 2024)** (6637B) | 514 | 2026-10-24 (29d) |
| [snowplow/enrich](https://github.com/snowplow/enrich) | The enrichment you actually run | ⚠️ **Snowplow Limited Use License Agreement v1.1** (6637B) | 1061 | 2026-10-24 (29d) |
| [snowplow/snowplow-javascript-tracker](https://github.com/snowplow/snowplow-javascript-tracker) | The tag in the storefront | **BSD-3-Clause** (1546B) | 5941 | 2026-11-07 (15d) |

So the two server-side components that carry every event — collector and
enrich — are under a **proprietary limited-use licence**, while the repo an
SBOM scanner or a listicle points at declares Apache-2.0, and the browser
tracker is BSD-3. A team that reads "Snowplow is Apache-2.0" and builds a
client's retail media data pipeline on it has mislicensed the core of the
platform.

**The 0-byte `LICENSE.md` deserves its own note.** `snowplow/snowplow` ships
both `LICENSE` (Apache-2.0, 11359B) and `LICENSE.md` at **zero bytes**. Tooling
that prefers the `.md` variant, or that merely tests for a filename, reads an
empty grant. Cycle 8 established that **a short licence file is a pointer, not
a licence**; this pass adds the degenerate case — **an empty licence file is
not a licence either, and it can mask a real one sitting beside it.**

**Generalised rule, and it is the most reusable thing in this pass: the licence
of a product is not the licence of its repository — it is the licence of each
component you deploy.** Audit per artefact, not per project. Cycle 8 reached
the same place from Meilisearch (a 468-byte pointer declaring `MIT AND
OpenLDAP AND BUSL-1.1`); Snowplow is the same lesson with the components split
across four repos instead of one file.

### ⚠️ Second default-branch trap this pass

`matomo-org/matomo`'s default branch is **`6.x-dev`**, not `main` or `master`.
With `facebookexperimental/Robyn` (default `accuracy/allocator_v2_fixes`), that
is **two of this pass's repos whose default branch is neither `main` nor
`master`**. Anyone cloning for a client build gets development code; any ingest
measuring liveness via the default branch measures the wrong branch. **Resolve
the default branch, then measure `main`/`master` by name too.**

### Gap: there is no open-source retail media platform

Searched 2026-11-22. `retail media stars:>=50` returns **one** repo and it is a
2020 machine-learning tutorial. `retail media network stars:>=10` returns
**three** and all three are Windows DxDiag dumps. `clean room advertising
stars:>=50` returns **zero**.

Meanwhile `ad server stars:>=200` returns **51**. The generic adtech platform
layer is populated; the retail-shaped layer does not exist. There is no Odoo of
retail media, no OpenMRS of retail media — **nothing to fork.** A retail media
capability is assembled from the permissive rows above, which is what
`compose/patterns.md` Patterns 14–16 do, and it is therefore a place where
Globant's integration work is the product rather than a thin layer over
someone else's platform. This joins markdown/assortment optimisation (cycle 8)
and shelf vision (pass 2) on the short list of retail capabilities with **no
open-source floor at all**.

---

## Added 2026-11-23 — returns, repair and disposition platforms

### Gap first: there is no open-source returns management platform

Stated before the table, because this is the commercially important fact. The
returns-platform market is entirely commercial — ReverseLogix, Loop, Narvar,
AfterShip, goTRG, SAP Intelligent Returns Management, Pivotree/YANTRA. A
dedicated search for open-source equivalents found **no open-source returns
management platform of any size**, and the code-level searches agree:
`reverse logistics` → 364 repos whose only non-trivial entry is an unlicensed
national-lab research tool; `disposition engine` → 22 repos, zero relevant.

This is the same shape as the retail-media gap recorded on 2026-11-22 (pass 3)
and the price/markdown gap recorded earlier: **a large, well-funded software
category with no open-source floor at all.**

### What does exist: returns as a module inside a platform you already run

Returns in open source are not a product, they are a module. These are
verified by fetching the module definition from the repository, not inferred
from marketing pages:

| Platform | License | The returns/repair capability, verified | Verification |
|---|---|---|---|
| **Odoo** (Community) | LGPL-3.0 | Ships a first-class **`Repairs`** app (`addons/repair`), summary *"Repair damaged products"*, explicitly covering the **warranty concept**, stock impact of a repair, and repair quotations. Present in 17.0, 18.0 and master. | `addons/repair/__manifest__.py` → HTTP 200 on all three branches |
| **ERPNext** | GPL-3.0 | Ships a **`Warranty Claim`** doctype (`erpnext/support/doctype/warranty_claim`), plus credit-note/return flows against Delivery Note. | `warranty_claim.json` → HTTP 200 on `develop` |
| **Mage-OS / Magento** | MIT (module) | [mage-os/module-rma](https://github.com/mage-os/module-rma) — a standalone **MIT** RMA module, 23★/14f, pushed 2026-11-17. The only permissively licensed standalone RMA component found anywhere. | `git ls-remote` + `LICENSE` 1071 B |

The licence consequence is the one this KB already documented on 2026-11-22
(pass 2) and it applies again, unchanged: **Odoo's LGPL and ERPNext's GPL make
the returns module safe to deploy and configure, and unsafe to fork into a
proprietary hosted product.** The Mage-OS RMA module is the only piece of this
layer that can be freely re-licensed into a client's closed codebase.

### The disposition layer has no platform — assemble it

Since 19 July 2026 an EU large company must decide and evidence the
disposition of unsold apparel and footwear (ESPR Article 25 — see
`intel/market.md` → EMEA). No platform implements this. The honest assembly,
all permissive:

| Component | Repo | License | Role |
|---|---|---|---|
| Decision/rules engine | [apache/incubator-kie](https://github.com/apache/incubator-kie) | Apache-2.0 | Drools rules expressing *reuse / repair / recycle / destroy* per jurisdiction. 6344★, pushed 2026-11-20. |
| Condition grading | [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | Apache-2.0 | Defect/anomaly scoring on the inbound unit. 6416★, pushed 2026-11-20. |
| Reverse route | [VROOM-Project/vroom](https://github.com/VROOM-Project/vroom) + [Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend) | BSD-2-Clause | Route the graded unit to the chosen destination. |
| Product identity & evidence | Digital Product Passport stack already in this file | mixed — see the DPP section above | Carries the disposition record. |

**Note the licence inversion against the rest of retail:** the *platform* layer
here is copyleft (Odoo LGPL, ERPNext GPL) while the *disposition* components
are all Apache-2.0/BSD/MIT. That is the opposite of the store plane, where the
platforms were permissive and the fiscal libraries copyleft.

### ⚠️ Repair platforms: the EU created a duty and open source did not respond

The Right to Repair Directive (EU) 2024/1799 has applied since **31 July
2026**, and `right to repair` on GitHub returns **272 repos whose top results
are all automotive** — `jakka351/Opium-Den-OEM` (65★, unlicensed, Chinese
vehicle OEM tooling) and VW component-protection documentation. There is **no
consumer-goods repair-management platform** in open source. Odoo's `Repairs`
app, above, is the closest thing that exists, and it was not built for this
directive.

This is a genuine, dated, unserved platform gap in EMEA.

---

## Added 2026-11-23 (pass 5) — the price plane: what the platforms do and do not ship

### Correction to this file

The section above headed *"Gap: there is no open-source retail price/markdown
engine"* says that *"no credible open-source project fills it"* and that
assortment, markdown and promotion optimisation have no floor. **Half of that
survives re-measurement and half does not.** Corrected:

- **Promotions and discounting: there is now a real, permissive, agent-native
  option.** [offerkit/offerkit](https://github.com/offerkit/offerkit) (**MIT**,
  `LICENSE` 1073 B read, 58★, pushed 2026-11-20).
- **Elasticity estimation: well equipped and permissive** — see
  `repos/foundations.md` → MODEL.
- **Markdown/clearance optimisation: the gap is real**, and the stronger
  statement is that all three retail-specific attempts **carry no licence
  grant**, not merely that they are absent.

### Price capability by platform — what is in-tree today

| Platform | Repo | License | Price capability in-tree | What is missing |
|---|---|---|---|---|
| **Medusa** | [medusajs/medusa](https://github.com/medusajs/medusa) | **MIT** (`LICENSE` 1075 B, read in cycle 8; API still reports `NOASSERTION`) | Price lists with schedules, region/currency pricing contexts, promotion module | No elasticity, no markdown optimiser. Compliance available as a **third-party MIT plugin** (below) — the only platform with one. |
| **Saleor** | [saleor/saleor](https://github.com/saleor/saleor) | **BSD-3-Clause** | Channel-based pricing, discounts, vouchers, promotions via API | No compliance layer, no price-history ledger, no optimiser. |
| **Odoo** | [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (43529 B, read in cycle 8 — **not** GPL) | Pricelists with rules and formulas, discounts, coupon/promotion programmes | No elasticity, no reference-price ledger. **LGPL means a proprietary pricing module is permitted** — the most commercially useful licence fact in this KB, and it applies directly here. |
| **OfferKit** | [offerkit/offerkit](https://github.com/offerkit/offerkit) | **MIT** | Discount engine (fixed/percentage, caps, product and collection eligibility), **stackable atomic redemptions**, gift-card balance ledger, loyalty tiers and points ledger, referrals, customer segments, validation rules | Not a pricing engine: it decides *offers*, never the base price. No elasticity, no markdown. |

**Why OfferKit is worth a row of its own.** It is the first platform-layer repo in
this KB built **agent-first rather than agent-adapted**: the MCP server is a
first-class surface, and **every mutating endpoint declares its risk level**
(`safe` / `mutating` / `destructive`) so an LLM host can render the appropriate
confirmation. Procedures opt into MCP exposure declaratively via `.meta()`.
Distribution is one Docker image (`ghcr.io/offerkit/offerkit`) bringing up web,
worker, Postgres and Redis; OpenTelemetry-ready. The README states **MIT
first-party packages, no CLA, no paywalled commercial features** — which, given
how often this KB has caught that claim being false at the platform layer
(nopCommerce's mandatory UI link, Meilisearch's BUSL Enterprise parts, Snowplow's
three licences in one product), is a claim to verify at integration time rather
than accept. The `LICENSE` file itself reads clean MIT at 1073 B.

**Caveat proportional to its size:** 58★ and 173 refs. This is an early project.
Appropriate as a *component you fork and own*, not as a dependency you assume will
be maintained for the life of a client platform.

### The compliance plugin — the only one of its kind, and the shape to copy

[zanreal-labs/medusa-consumer-compliance](https://github.com/zanreal-labs/medusa-consumer-compliance)
(**MIT**, 1064 B read, 0★, pushed **2026-11-22**). Medusa v2 plugin covering the
Omnibus 30-day lowest price, unit prices, GPSR safety information, the online
withdrawal function of Directive (EU) 2023/2673, and the reviews and
**personalised-pricing** disclosures. Documentation in English and Polish; the
legal basis of every rule, with sources and dates, in `docs/legal.en.mdx`. It
states plainly that it supports compliance and does not guarantee it.

**The reusable design, independent of Medusa:**
- Records **every price a customer could see**, per variant **and pricing
  context** (region and currency, price lists and their schedules as applied).
- Three capture paths — product/price events, an **hourly sweep**, and on-demand
  **backfill** — because event streams drop.
- **Never edits a recorded price.** Append-only by construction.
- Retains at least the regulatory window, **400 days by default**.
- **Warns when the history is incomplete**, and when a "reduced" price is not
  actually below the reference. The second check is the one that catches a
  merchandising mistake before a regulator does.
- Encodes member-state variation explicitly: **Poland did not adopt art. 6a(5)**,
  so each step of a gradual reduction is measured on its own; plus goods on offer
  for under 30 days, perishables, relaunch after a break, and the label UOKiK
  expects.

**The platform gap this establishes, stated precisely.** One MIT plugin, for one
platform, in one member state's specifics, at 0 stars, one day old, covering one
of the four regional duties on this plane. Saleor, Odoo, Shopware, Spree and
Bagisto have **nothing equivalent**, and the Digital Fairness Act proposal of
2026-11-11 would widen the duty (RRP-based savings claims restricted, a
consumer-set **maximum price** written into the agent contract by Art. 26). This
is a **dated, named, unserved platform gap in EMEA** — the second such gap this
KB has recorded, alongside the ESPR Art. 25 disposition engine from pass 4.

### Measured: the platform layer does not price, and nothing adjacent fills it

**[measured 2026-11-23]** `promotion engine stars:>=50` returns **2 repos** —
OfferKit and a 2018 Chinese "new retail" demo (`cinoliu/Promotion-engine`, MIT,
98★, dead 2018-10-16). `discount engine stars:>=30` returns **5**, of which the
only real ones are a 2017 Rails coupon gem (`fnando/coupons`, MIT, 141★, dead
2017-05-25) and `ByteSizedMarius/rewerse-engineering` (MIT, 98★ — a German grocer
API client, not an engine). `Smile-SA/elasticsuite-for-retailer` (OSL-3.0, 18★)
is **dead since 2024-08-29** and carries the same Open Software License family
this KB flagged for innoshop and beikeshop in cycle 8.

**Deliberate exclusion, because the names mislead:**
[getlago/lago](https://github.com/getlago/lago) (AGPL-3.0, 10,910★) and
[meteroid-oss/meteroid](https://github.com/meteroid-oss/meteroid) (AGPL-3.0,
1,369★) are the two largest repos that appear under retail pricing vocabulary.
They are **SaaS metering and subscription billing** — usage tracking, invoicing,
plan management. They do not price merchandise, and they are **AGPL**, so
selecting one by name would be both a fit error and a licence error.

---

## Added 2026-11-23 (pass 6) — fulfilment and last-mile platforms

Real systems that run a fulfilment operation and can take an AI layer on top. Licences read from the
raw file on the default branch, 2026-11-23.

### Platform table — read the licence column first

| Platform | Repo | License | Stars | Last push | What it is | Can you white-label it? |
|---|---|---|---|---|---|---|
| Fleetbase | https://github.com/fleetbase/fleetbase | AGPL-3.0 | 4,799 | 2026-11-20 | Modular logistics & supply-chain OS: dispatch, drivers, fleet-ops, storefront extensions | Only with the AGPL obligation accepted, or a commercial licence from the vendor |
| Openship | https://github.com/openshiporg/openship | AGPL-3.0 | 1,680 | 2026-11-17 | Order router: channels (Shopify/Woo) → 3PLs and fulfilment partners | Same constraint |
| Apache OFBiz | https://github.com/apache/ofbiz-framework | Apache-2.0 | 1,151 | 2026-11-22 | ERP with order management, inventory and shipment in-tree | **Yes** — the only permissive full platform at this step |
| OpenBoxes | https://github.com/openboxes/openboxes | EPL-1.0 | 936 | 2026-11-22 | WMS: stock movements, lots, picking | Yes, with EPL file-level source obligations |
| InvenTree | https://github.com/inventree/InvenTree | MIT | 7,890 | 2026-11-23 | Inventory system of record with a strong plugin API | **Yes, unconditionally** |
| Traccar | https://github.com/traccar/traccar | Apache-2.0 | 8,176 | 2026-11-22 | GPS fleet tracking, 200+ device protocols | **Yes** |
| Beckn ONIX | https://github.com/beckn/beckn-onix | MIT | 101 | 2026-11-19 | Network node for a Beckn/ONDC open commerce network | **Yes** |
| HotWax Fulfillment | https://github.com/hotwax/fulfillment | Apache-2.0 | 9 | 2026-11-17 | Store-fulfilment app (in-store pick/pack/ship) | Yes, but it is small — read it as a worked example |
| OpenOMS | https://github.com/openoms-org/openoms | **Elastic License 2.0** | 33 | 2026-09-02 | Order management for e-commerce | **No — ELv2 is not open source.** It forbids offering the software to third parties as a managed service |

### ⚠️ The licence inversion on this plane, and it is the opposite of the price plane

On the price plane (pass 5) the platforms shipped nothing and the components were permissive. Here
the **components are permissive and the platforms are copyleft**: every solver, routing engine and
geocoder worth using is Apache/BSD/MIT, while the two largest platforms (Fleetbase, Openship) are
AGPL-3.0 and the most-advertised OMS is Elastic License.

The practical consequence for an engagement: **assemble, do not adopt.** A fulfilment platform built
from OFBiz or InvenTree plus OR-Tools/VROOM plus Photon/Pelias is entirely permissive end to end and
can be delivered as a client-owned, closed product. Starting from Fleetbase or Openship because they
look finished imports AGPL into the core of the client's operations.

### Gap: there is no open-source delivery-promise engine, and no platform ships one

None of the platforms above computes a delivery date. OFBiz and InvenTree hold stock; Fleetbase and
Openship route orders once the promise is already made; OpenBoxes moves stock inside a warehouse.
The number the shopper actually sees — "arrives Thursday" — is computed nowhere in the open-source
estate (see `repos/foundations.md` → Step 1, 7 repos worldwide, none above 1 star).

### Gap: the fiscal/legal document layer for freight is empty in Europe and full in LATAM

An EU shipment increasingly needs an electronic consignment note (eCMR) and, from 9 July 2027,
authorities must accept freight data from certified eFTI platforms. The open-source response to that
is **one repository with zero stars and no licence**. Meanwhile a Brazilian shipment's fiscal document
(NF-e) and its carrier labels are covered, under MIT, in https://github.com/codespar/mcp-dev-latam.
A European retailer has more regulation and less code than a Brazilian one on exactly this step.
