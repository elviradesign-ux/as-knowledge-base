---
title: "What is Inventory"
slug: inventory
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: draft
difficulty: beginner
locale: en
translation_of: 002-inventory.md
audience: [New sellers, Platform team]
roles: [Client, Admin]
modules: [Inventory]
entities: [Inventory, Product, Listing, Report, Tag, Return]
workflows: [WF-030]
related_screens: [SCR-120, SCR-121, SCR-122]
related_entities: [Product, Order, Box, Report, Return]
related_articles: [001-product, 003-order]
seo_title: "Inventory in Seller Exchange — your product catalog with analytics"
seo_description: "What Inventory is in Seller Exchange: the product catalog with stock, sales and finance analytics, its columns, and how orders start here."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - 002-inventory.md (RU source of truth)
validation_status: confirmed
---

> **EN translation of [002-inventory.md](002-inventory.md) (RU source of truth).**
> Update the RU source first, then re-sync this translation.

# What is Inventory

**Inventory** is your product catalog with analytics — one table that brings
together everything you know about each [Product](001-product.en.md): how much
stock you have, how it sells, what it costs, and how it performs in advertising.

## Overview

Where a Product is a single item, Inventory is the *place where all your Products
live together*. Each row is a Product, and each column is a metric or attribute —
from available units and days of supply to profit, ROI and advertising cost.
Inventory is also where day-to-day work begins: you select Products here to
create orders and to plan restocks.

## Why it matters

Inventory is the operational hub for a seller:

- It gives a single view of stock health across warehouses (China, USA, AWD).
- It surfaces the numbers behind restock and pricing decisions.
- It is the starting point for creating an [Order](003-order.en.md).

## What the table shows

The Inventory table can display around 180 columns, grouped by purpose. The full
list of columns — with definitions — is kept in one place and not repeated here:
see [Inventory — field reference](../../GLOSSARY.md). The main groups are:

- **Identification** — ASIN, FNSKU, brand, category, tags.
- **Stock & warehouses** — available, reserved, inbound, China/USA/AWD stock.
- **Stock age & fees** — inventory age buckets and long-term storage charges.
- **Sales** — orders, units shipped, sales over 7/30/60/90 days.
- **Customer experience** — PCX/NCX, ratings, reviews.
- **Finance** — prices, fees, profit, margin, ROI.
- **Advertising** — ad sales, TACOS, ACOS, clicks, CPC, CTR.
- **Recommendations** — Amazon's suggested price, ship-in quantity and removals.

## Presets and columns

Because the table is wide, you can tailor it. The set and order of columns (plus
filters) is saved as a **preset**, so you can switch between views for different
tasks. Columns can be selected, added and removed. The step-by-step actions live
in the screen guide — this concept article does not repeat them.

## How it relates to other concepts

- Inventory **contains** Products.
- A Product is the source for **Order** creation and links to **Reports**,
  **Returns** and its **Listing**.

Relationship details are catalogued in
[Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Who works with it

Inventory is used by the **Client** (their own catalog) and by the **Admin** (in
an oversight capacity). Each user sees only the Products they are allowed to —
see [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Where you see it

| Screen | What you do there |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Inventory — products | The main table |
| [SCR-121](../../SCREEN_CATALOG.md) Product detail | Open a single Product |
| [SCR-122](../../SCREEN_CATALOG.md) Inventory — reports | Listing reports |

For the hands-on walkthrough, see the screen guide:
[Inventory — products](../screens/inventory-products.md).

## Related workflows

- **WF-030** — create an order from inventory: select rows, then **To order**.

## Glossary terms

[Product Card](../../GLOSSARY.md) · [Data filters](../../GLOSSARY.md) ·
[CustomDataGrid](../../GLOSSARY.md)

## FAQ

| Question | Answer |
|---|---|
| Why is my inventory empty? | Usually because no Amazon store is connected yet — connect a store so data can sync. |
| How do I keep a custom column layout? | Save it as a preset and reapply it later. |
| Where are the step-by-step actions? | In the screen guide, [Inventory — products](../screens/inventory-products.md). |

## Related articles

- [001 — Product](001-product.en.md)
- [003 — Order](003-order.en.md)
- Screen guide: [Inventory — products](../screens/inventory-products.md)
