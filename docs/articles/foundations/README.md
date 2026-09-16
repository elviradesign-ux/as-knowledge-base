# Foundations / Core Entities

First article series of the Seller Exchange Knowledge Base (Marketplace Academy
track). Beginner-level concept articles that define the core entities every user
meets first, and link out to the systems of record (Glossary, Entity States,
Entity Relationships) instead of duplicating them.

**Язык-источник — RU** (`00X.md`, `locale: ru`), по
[LOCALIZATION_GUIDE](../../LOCALIZATION_GUIDE.md). Переводы — `00X.<lang>.md`,
создаются из финального RU-источника.

| # | Статья (RU, источник) | Перевод EN | Сущность | Статус | Валидация |
|---|---|---|---|---|---|
| 001 | [Что такое товар](001-product.md) | [en](001-product.en.md) | Product | **approved** | confirmed (Product↔Inventory Item: NV) |
| 002 | [Что такое инвентарь](002-inventory.md) | [en](002-inventory.en.md) | Inventory | **approved** | confirmed |
| 003 | [Что такое заказ](003-order.md) | [en](003-order.en.md) | Order | **approved** | confirmed (Order Item: NV) |
| 004 | [Что такое коробка](004-box.md) | [en](004-box.en.md) | Box (+ Super Box) | **approved** | confirmed (Shipment entity: NV) |
| 005 | [Что такое партия](005-batch.md) | — | Batch | **draft · needs validation · blocked (DM8)** | **partial — DM8** |
| 006 | [Что такое магазин](006-store.md) | — | Store | **approved** | confirmed |
| 007 | [Что такое пользователь](007-user.md) | — | User | **approved** | confirmed (Account/User/Client — DM3) |
| 008 | [Что такое роль](008-role.md) | — | Role | **approved** | confirmed (термин. расхождения) |
| 009 | [Что такое право доступа](009-permission.md) | — | Permission | **approved** | confirmed |
| 010 | [Что такое пресет прав](010-permission-preset.md) | — | Permission Preset | **approved** | confirmed (без lifecycle, DM10) |
| 011 | [Что такое поставщик](011-supplier.md) | — | Supplier | **approved** | confirmed |
| 012 | [Что такое карточка поставщика](012-supplier-card.md) | — | Supplier Card | **approved** | confirmed |
| 013 | [Что такое карточка товара](013-product-card.md) | — | Product Card | **approved** | confirmed (Research Product↔Idea: NV, DM4) |
| 014 | [Что такое идея](014-product-idea.md) | — | Product Idea | **approved** | confirmed |
| 015 | [Что такое заявка на услугу](015-service-request.md) | — | Service Request | **approved** | confirmed |
| 016 | [Что такое предложение](016-proposal.md) | — | Proposal | **approved** | confirmed |
| 017 | [Что такое платёж](017-payment.md) | — | Payment | **approved** | confirmed |
| 018 | [Что такое возврат](018-return.md) | — | Return | **approved** | confirmed (Return↔Order: NV) |
| 019 | [Что такое уведомление](019-notification.md) | — | Notification | **approved** | confirmed |
| 020 | [Что такое тикет поддержки](020-support-ticket.md) | — | Support Ticket | **approved** | confirmed |
| 021 | [Что такое отчёт](021-report.md) | — | Report | **approved** | confirmed (набор отчётов: NV, DM19) |
| 022 | [Что такое кампания](022-campaign.md) | — | Campaign | **approved** | confirmed |
| 023 | [Что такое PPC-метрики](023-ppc-metrics.md) | — | PPC Metrics | **approved** | confirmed |

> Серия **Marketplace Terms** — **завершена** (`articles/academy/`, 20/20 approved):
> hub [Термины маркетплейса](../academy/025-marketplace-terms.md) (`approved`) +
> **19 терминов** (ART-026…044: ASIN, SKU, ASIN vs SKU vs FNSKU, FBA, FBM,
> MOQ, Brand, Category, Variation, Barcode/UPC/EAN, SP-API, Forecasting,
> Out of Stock, Restock, Buy Box, PPC Basics, ACoS/TACoS/ROAS, Unit Economics,
> Private Label vs Wholesale). Screen Guide
> [Инвентарь — товары](../screens/inventory-products.md) — `approved`. Полный
> трекинг — [CONTENT_ROADMAP](../../CONTENT_ROADMAP.md).

## Current Progress

**Foundation Series** (статей в папке: 23)

- Approved: **22** (001–004, 006–023 кроме 005)
- Draft: **1** (005)
- Blocked: **1** (005 — DM8)
- Осталось: ART-024 (Voice of Customer — needs validation, DM12)
- Core-entity веха (Product, Inventory, Order, Box, Batch): **4 / 5 = 80%**
  (остаётся 005, blocked — DM8)

```
Core-entity веха   ████████░░  80%   (4 / 5)
Foundation-волна   █████████▎  92%   (22 / 24)
```

## Conventions
- **Concept article ≠ screen article.** These explain *what a thing is*; hands-on
  steps live in `articles/screens/*` (e.g. [Inventory — products](../screens/inventory-products.md)).
- **RU-first.** Пишем и утверждаем RU-источник; EN/ZH/UA — переводы из него.
  EN-переводы 001–004 — предварительные (`status: draft`), синхронизируются после
  апрува RU.
- **One fact, one place.** Fields → [GLOSSARY](../../GLOSSARY.md); statuses →
  [ENTITY_STATES](../../ENTITY_STATES.md); relationships →
  [ENTITY_RELATIONSHIPS](../../ENTITY_RELATIONSHIPS.md).
- **No disputed claims stated as fact.** Unconfirmed points are marked
  *Needs validation* and tracked in
  [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md).

## Do not finalize yet
- **005 — Batch** stays `draft` until **DM8** (Batch lifecycle) and the Shipment
  entity question are resolved. EN-перевод 005 создаём только после этого.
