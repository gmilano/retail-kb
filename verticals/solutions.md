---
industry: retail
region: Global
updated: 2026-11-21
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
