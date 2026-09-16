---
title: "What is an Order"
slug: order
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: draft
difficulty: beginner
locale: en
translation_of: 003-order.md
audience: [New sellers, Platform team]
roles: [Client, Buyer, Admin]
modules: [Orders]
entities: [Order, Order Item, Order Status, Order Type, Product, Supplier, Box, Payment]
workflows: [WF-005, WF-006, WF-030, WF-031]
related_screens: [SCR-100, SCR-101, SCR-102, SCR-103, SCR-104, SCR-M01, SCR-M03]
related_entities: [Product, Box, Supplier, Payment]
related_articles: [001-product, 002-inventory, 004-box]
seo_title: "Order in Seller Exchange — from creation to shipment"
seo_description: "What an Order is in Seller Exchange: how it is created, its lifecycle statuses, and how it turns into boxes handled by buyers and storekeepers."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - 003-order.md (RU source of truth)
validation_status: "confirmed (note: Order Item — Needs validation)"
---

> **EN translation of [003-order.md](003-order.md) (RU source of truth).**
> Update the RU source first, then re-sync this translation.

# What is an Order

An **Order** is a client's request to purchase a [Product](001-product.en.md). It is
the heart of the operational flow: a client creates it, a **Buyer** processes it,
and a **Storekeeper** eventually receives the goods as boxes.

## Overview

An Order captures what a client wants to buy and tracks it from creation all the
way to shipment. Along the way it connects to the supplier who fulfils it, the
payment made to that supplier, and the boxes the goods are packed into. Its
**status** tells everyone where the order currently stands.

## Why it matters

The Order ties the platform's operational chain together — product, supplier,
payment, box and batch all meet on the Order. Reading an order's status is the
fastest way to understand what needs to happen next.

## How an Order is created

Clients create orders from a few entry points — most commonly from the
[Inventory](002-inventory.en.md) by selecting Products and choosing **To order**,
which opens the Create Order modal ([SCR-M01](../../SCREEN_CATALOG.md)). During
creation the goods can be distributed into boxes. The full steps are in the
Workflow Catalog (WF-030, WF-031).

## Lifecycle and statuses

An Order moves through a defined chain of statuses, roughly:

> FORMED / NEW → PENDING → READY_TO_PROCESS → AT_PROCESS → READY_FOR_PAYMENT →
> PARTIALLY_PAYMENT → PAID_TO_SUPPLIER → TRACK_NUMBER_ISSUED →
> NEED_CONFIRMING_RECEIVING → IN_STOCK → AWAITING_SHIPMENT → SHIPPED

An order can also be cancelled by the buyer or the client. Orders have a **type**
(LONG, STANDARD, URGENT, PROBLEMATIC). The canonical status codes and transitions
are maintained in [Entity States → Order statuses](../../ENTITY_STATES.md) — use
that as the source of truth rather than memorizing the chain.

## How an Order is fulfilled

Once the goods are purchased, they are packed into **[Boxes](004-box.en.md)**, which
are received at the warehouse and later grouped into a **[Batch](005-batch.md)**
for shipment to Amazon. The order's status follows this journey up to `SHIPPED`.

## What an Order holds

An Order groups the items being purchased and links to the supplier and payment.

> A distinct **Order Item** concept (the link between an order and its purchased
> items) is referenced in the model but is **not yet fully confirmed** in the
> Domain Model — treat it as a related concept pending validation.

## How it relates to other concepts

- An Order is **created by** a Client and **processed by** a Buyer.
- It **creates** Boxes and **references** a Supplier and a Payment.

See [Entity Relationships](../../ENTITY_RELATIONSHIPS.md) for the full catalogue.

## Who works with it

- **Client** — creates and tracks their own orders.
- **Buyer** — picks up and processes orders (including free/vacant orders).
- **Admin** — oversight across orders.

Each role sees only the orders in its scope — see
[Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Where you see it

| Screen | What you do there |
|---|---|
| [SCR-100 / SCR-101](../../SCREEN_CATALOG.md) | My orders / order detail (Client) |
| [SCR-103 / SCR-104](../../SCREEN_CATALOG.md) | Buyer orders (status tabs) / detail |
| [SCR-M01](../../SCREEN_CATALOG.md) | Create Order modal |

## Related workflows

- **WF-005** — buy a card from the exchange and create an order (Client).
- **WF-006** — process an order through its status lifecycle (Buyer).
- **WF-030 / WF-031** — create an order and distribute boxes (Client).

## Glossary terms

[Order](../../GLOSSARY.md) · [Order status](../../GLOSSARY.md) ·
[Box](../../GLOSSARY.md) · [Supplier](../../GLOSSARY.md)

## FAQ

| Question | Answer |
|---|---|
| Why is my order waiting on me? | It may be at `NEED_CONFIRMING_TO_PRICE_CHANGE` — the buyer needs your confirmation on a price change. |
| What does a "free" order mean? | An unassigned order a buyer can pick up (vacant orders). |
| Where do the exact statuses live? | In [Entity States](../../ENTITY_STATES.md). |

## Related articles

- [001 — Product](001-product.en.md)
- [004 — Box](004-box.en.md)
- [005 — Batch](005-batch.md)
