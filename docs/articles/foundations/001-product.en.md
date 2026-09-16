---
title: "What is a Product"
slug: product
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: draft
difficulty: beginner
locale: en
translation_of: 001-product.md
audience: [New sellers, Platform team]
roles: [Client, Buyer, Researcher, Supervisor, Admin]
modules: [Inventory, Product Exchange, Orders, Warehouse, Product Launch]
entities: [Product, ASIN, FNSKU, Barcode, Brand, Category, Tag, Variation, Supplier Card, Strategy]
workflows: [WF-001, WF-030]
related_screens: [SCR-120, SCR-121, SCR-123, SCR-124]
related_entities: [ASIN, Product Card, Inventory, Supplier, Order, Box]
related_articles: [002-inventory, 003-order, 004-box]
seo_title: "Product in Seller Exchange — the core catalog entity"
seo_description: "What a Product is in Seller Exchange: its identifiers (ASIN, FNSKU), attributes, lifecycle statuses, and how it connects to inventory, orders and suppliers."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - 001-product.md (RU source of truth)
validation_status: "confirmed (note: Inventory Item vs Product distinction — Needs validation)"
---

> **EN translation of [001-product.md](001-product.md) (RU source of truth).**
> Update the RU source first, then re-sync this translation.

# What is a Product

A **Product** is the central catalog entity in Seller Exchange. Almost
everything else on the platform — inventory, orders, boxes, suppliers,
analytics — points back to a Product. If you understand the Product, the rest of
the platform becomes much easier to follow.

## Overview

A Product represents a single item you sell (or plan to sell) on Amazon. Each
Product is tied to an **ASIN** — the Amazon identifier that uniquely names the
item on the marketplace. Around that identifier the platform keeps everything you
need to work with the item: stock levels, sales, costs, supplier data and its
progress through research and sourcing.

> In current documentation, rows in your **[Inventory](002-inventory.en.md)** are
> treated as Products — your inventory is, in practice, your list of Products.
> The exact technical distinction between a "Product" and an "Inventory Item" may
> depend on implementation and is still being confirmed.

## Why it matters

The Product is the anchor concept of the whole platform:

- Your **Inventory** is a table of Products.
- An **Order** is a request to purchase a Product.
- A **Box** physically holds Products.
- Reports, advertising metrics and returns are all measured per Product.

Because so many concepts reference it, getting the Product right — correct ASIN,
brand, category and supplier — keeps everything downstream accurate.

## Identifiers and key attributes

A Product carries several identifiers and attributes. The full list of columns
lives in the Inventory field reference, so it is not repeated here — see
[Inventory — field reference](../../GLOSSARY.md).

**Identifiers**
- **ASIN** — the Amazon Standard Identification Number; the primary key of the
  item on Amazon. It is checked by the ASIN checker.
- **FNSKU** — Amazon's internal code for tracking the item in FBA warehouses.
- **Barcode** — the printed code on the item. *UPC* and *EAN* are attributes of
  the barcode rather than separate concepts.

**Attributes**
- **Brand** and **Category** — where the item sits in the Amazon catalog.
- **Tag** — free keywords you use to group and find Products internally.
- **Strategy** — the sourcing strategy for the item (for example, Private Label
  or Wholesale).
- **Transparency Code** — whether the item participates in Amazon Transparency.

**Grouping**
- A Product can be a standalone item or a **Variation** of another. A Variation
  is itself a Product; a **Parent Product** expresses the relationship and
  dependency between related items.

> *SKU, UPC and EAN are attributes of a Product or its Barcode — not separate
> tracked entities.*

## Lifecycle and statuses

A Product (as a product card) moves through a research-and-sourcing lifecycle,
from creation by a Researcher, through review by a Supervisor, to a supplier
being found and the card published on the exchange. There are two branches: a
standard flow and a "from client" flow when the client initiates the item.

The exact status codes and transitions are maintained in one place — see
[Entity States → Product statuses](../../ENTITY_STATES.md). Do not memorize the
numbers; use that reference as the source of truth.

## How a Product relates to other concepts

The precise relationships (and their direction) are catalogued in
[Entity Relationships](../../ENTITY_RELATIONSHIPS.md). In short, a Product:

- **has** an ASIN, FNSKU and Barcode; **belongs to** a Brand and a Category;
- **appears in** your Inventory;
- is **packed into** Boxes and is part of an Order;
- **references** a Supplier through a Supplier Card.

## Who works with it

Different roles touch a Product at different stages: **Researchers** create
product cards, **Supervisors** review them, **Buyers** find suppliers, and
**Clients** manage their own catalog. Each role sees only the Products it is
allowed to — for example, a Client sees their own Products. Access rules are
described in [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Where you see it

| Screen | What you do there |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Inventory — products | Browse and manage your Products |
| [SCR-121](../../SCREEN_CATALOG.md) Product detail | Open a single Product's data |
| [SCR-124](../../SCREEN_CATALOG.md) Product Card | Work with the card during research/review |

## Related workflows

- **WF-001** — create a product card (Researcher).
- **WF-030** — create an order from inventory (Client).

See [Workflow Catalog](../../WORKFLOW_CATALOG.md) for the full steps.

## Glossary terms

[Product Card](../../GLOSSARY.md) · [ASIN](../../GLOSSARY.md) ·
[Supplier / Supplier Card](../../GLOSSARY.md) · [Strategy](../../GLOSSARY.md)

## FAQ

| Question | Answer |
|---|---|
| Is a Product the same as an Inventory Item? | In current documentation your Inventory rows are treated as Products. A finer technical distinction may exist and is still being confirmed. |
| What is a Variation? | A Variation is a Product linked to a Parent Product (for example, a different colour or size). |
| Are SKU / UPC / EAN separate entities? | No — they are attributes of a Product or its Barcode. |

## Related articles

- [002 — Inventory](002-inventory.en.md)
- [003 — Order](003-order.en.md)
- [004 — Box](004-box.en.md)

---

*Open point (Needs validation): the relationship between a Product in research
status and an **Idea** (Product Launch) is still being clarified — see DM4 in
[DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md).*
