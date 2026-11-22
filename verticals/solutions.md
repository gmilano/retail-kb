---
industry: retail
region: Global
updated: 2026-11-22
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
