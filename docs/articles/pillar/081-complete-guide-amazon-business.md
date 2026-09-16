---
title: "Полный гайд по построению Amazon-бизнеса"
slug: complete-guide-amazon-business
article_type: SEO / Pillar
section: Pillar
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Внешняя аудитория]
roles: [Client, Researcher, Supervisor, Buyer, Storekeeper]
modules: [Product Research, Suppliers, Orders, Warehouse, Inventory, Advertising]
entities: [Product, Product Card, Supplier, Order, Box, Batch]
workflows: [WF-001, WF-002, WF-003, WF-006, WF-007]
related_screens: []
related_entities: [Product, Supplier, Order, Box]
related_articles: [080-what-is-seller-exchange, 070-researcher-creates-product-card, 072-buyer-searches-supplier, 073-client-creates-order-from-inventory, 074-buyer-processes-order, 075-storekeeper-receives-boxes]
seo_title: "Полный гайд по построению Amazon-бизнеса в Seller Exchange"
seo_description: "Полный гайд: как построить бизнес на Amazon в Seller Exchange — от ресёрча товара и поиска поставщика до заказа, склада и аналитики."
owner: TBD
last_updated: 2026-07-08
review_by: 2026-10-08
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md
  - DOMAIN_MODEL.md (сквозной процесс)
validation_status: confirmed
---

> **Pillar-статья (ru-источник).** Связывает сквозной процесс платформы с
> пошаговыми сценариями. Детали шагов — в Workflow Guides.

# Полный гайд по построению Amazon-бизнеса

Эта страница проводит по всему пути товара на платформе — от идеи до продажи —
и ведёт к пошаговым сценариям на каждом этапе.

## Этапы

### 1. Ресёрч товара
Ресёрчер создаёт [карточку товара](../foundations/013-product-card.md) с ASIN и
данными. → [Ресёрчер создаёт карточку товара](../workflows/070-researcher-creates-product-card.md).

### 2. Проверка
Супервайзер проверяет карточку и принимает решение. →
[Супервайзер проверяет карточку](../workflows/071-supervisor-checks-product-card.md).

### 3. Поиск поставщика
Байер находит [поставщика](../foundations/011-supplier.md) и заполняет
[карточку поставщика](../foundations/012-supplier-card.md). →
[Байер ищет поставщика](../workflows/072-buyer-searches-supplier.md).

### 4. Заказ
Клиент создаёт [заказ](../foundations/003-order.md) из
[инвентаря](../foundations/002-inventory.md). →
[Клиент создаёт заказ из инвентаря](../workflows/073-client-creates-order-from-inventory.md).

### 5. Обработка заказа
Байер проводит заказ по статусам и оплачивает поставщику. →
[Байер обрабатывает заказ](../workflows/074-buyer-processes-order.md).

### 6. Склад
Сторкипер принимает [коробки](../foundations/004-box.md) и готовит к отправке. →
[Сторкипер принимает коробки](../workflows/075-storekeeper-receives-boxes.md).
_(Формирование и отправка партии — в подготовке, зависит от DM8.)_

### 7. Продажи и аналитика
Отслеживайте продажи, [прогноз запасов](../academy/037-inventory-forecasting.md),
[юнит-экономику](../academy/043-unit-economics.md) и
[рекламу](../foundations/023-ppc-metrics.md).

## Что почитать дальше

- [Как управлять запасами Amazon](083-how-to-manage-inventory.md)
- [Как избежать out of stock](084-how-to-prevent-out-of-stock.md)
- [Как организовать команду продавца](085-organize-seller-team.md)

## Чеклист ревью

- [x] Этапы — из сквозного процесса [DOMAIN_MODEL](../../DOMAIN_MODEL.md) и WORKFLOW_CATALOG.
- [x] Тон educational, без маркетинга.
- [x] Ссылки на существующие Workflow/Foundation-статьи.
- [x] Batch-этап помечен как зависящий от DM8.
- [ ] SEO/маркетинг-ревью перед публикацией.
