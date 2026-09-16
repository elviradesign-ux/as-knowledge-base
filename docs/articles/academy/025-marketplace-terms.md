---
title: "Термины маркетплейса"
slug: marketplace-terms
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
modules: [Inventory, Orders, Warehouse, Suppliers, Advertising, Users, Integrations]
entities: [ASIN, SKU, FNSKU, Barcode, Product, Product Card, Variation, Brand, Category, Tag, Order, Box, Batch, Warehouse, Supplier, Campaign, User, Role, Integration]
workflows: []
related_screens: []
related_entities: [Product, Order, Box, Supplier, User, Role, Campaign]
related_articles: [026-asin, 027-sku, 028-asin-vs-sku-vs-fnsku, 029-fba, 030-fbm, 031-moq, 032-brand, 033-category, 034-variation, 035-barcode-upc-ean, 036-amazon-sp-api, 037-inventory-forecasting, 038-out-of-stock, 039-restock, 040-buy-box, 041-ppc-basics, 042-acos-tacos-roas, 043-unit-economics, 044-private-label-vs-wholesale, 001-product, 002-inventory, 003-order, 004-box]
seo_title: "Термины маркетплейса — справочник Seller Exchange Academy"
seo_description: "Навигационный справочник ключевых терминов маркетплейса Amazon и Seller Exchange: идентификаторы товара, заказы, склад, поставщики, реклама, доступы."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md
  - DOMAIN_MODEL.md
  - ENTITY_STATES.md
  - CONTENT_ROADMAP.md (ART-025…044)
validation_status: "confirmed (hub-навигатор; Shipment и Connected App помечены Needs validation)"
---

> **Hub-статья Marketplace Academy (язык-источник ru).** Это **навигатор**, а не
> словарь: короткие пояснения и ссылки на отдельные статьи. Полные определения —
> в [GLOSSARY](../../GLOSSARY.md) и статьях терминов.

# Термины маркетплейса

## Кратко

Справочник помогает быстро сориентироваться в ключевых терминах Amazon и
Seller Exchange и перейти к подробным статьям. Определения даны коротко; источник
правды по терминам — [GLOSSARY](../../GLOSSARY.md), по статусам —
[ENTITY_STATES](../../ENTITY_STATES.md).

## Как пользоваться этим справочником

- Термины сгруппированы по темам.
- Короткое пояснение → ссылка на статью или справочник.
- Пометка _(планируется)_ — статья ещё не написана (см.
  [CONTENT_ROADMAP](../../CONTENT_ROADMAP.md)).
- Пометка _(Needs validation)_ — факт ещё уточняется.

## Идентификаторы товара

- **ASIN** — идентификатор товара на Amazon. [ASIN](026-asin.md)
- **SKU** — артикул продавца (атрибут товара). [SKU](027-sku.md)
- **FNSKU** — внутренний код Amazon для FBA. [ASIN vs SKU vs FNSKU](028-asin-vs-sku-vs-fnsku.md)
- **ASIN vs SKU vs FNSKU** — в чём разница. [Сравнение](028-asin-vs-sku-vs-fnsku.md)
- **Barcode / UPC / EAN** — штрихкод; UPC/EAN — атрибуты баркода.
  [Barcode / UPC / EAN](035-barcode-upc-ean.md)

## Товар и каталог

- **Product (товар)** — центральная сущность каталога. [001 — Товар](../foundations/001-product.md)
- **Product Card (карточка товара)** — рабочее представление товара.
  [013 — Карточка товара](../foundations/013-product-card.md)
- **Variation (вариация)** — товар, связанный с родительским. [Вариация](034-variation.md)
- **Brand (бренд)** — торговая марка. [Бренд](032-brand.md)
- **Category (категория)** — раздел каталога Amazon. [Категория](033-category.md)
- **Tag (тег)** — ключевое слово для группировки. [GLOSSARY](../../GLOSSARY.md)

## Продажи и заказы

- **Order (заказ)** — запрос на закупку товара. [003 — Заказ](../foundations/003-order.md)
- **Order Status (статус заказа)** — этап жизненного цикла заказа.
  [Entity States](../../ENTITY_STATES.md)
- **Order Type (тип заказа)** — LONG / STANDARD / URGENT / PROBLEMATIC.
  [Entity States](../../ENTITY_STATES.md)
- **Return (возврат)** — возврат товара. [018 — Возврат](../foundations/018-return.md)

## Инвентарь и планирование запаса

- **Inventory (инвентарь)** — каталог товаров с аналитикой. [002 — Инвентарь](../foundations/002-inventory.md)
- **Inventory Forecasting (прогноз запасов)** — на сколько хватит запаса. [Прогноз запасов](037-inventory-forecasting.md)
- **Out of Stock (дефицит)** — товар закончился. [Out of Stock](038-out-of-stock.md)
- **Restock (дозакупка)** — своевременное пополнение. [Restock](039-restock.md)
- **Buy Box** — блок покупки на Amazon. [Buy Box](040-buy-box.md)

## Склад и логистика

- **Box (коробка)** — единица хранения и отправки. [004 — Коробка](../foundations/004-box.md)
- **Super Box (SB)** — контейнер для коробок (не самостоятельная сущность).
  [004 — Коробка](../foundations/004-box.md)
- **Batch (партия)** — группа коробок для отправки.
  [005 — Партия _(draft, blocked DM8)_](../foundations/005-batch.md)
- **Warehouse (склад)** — место хранения и обработки. [GLOSSARY](../../GLOSSARY.md)
- **Destination (пункт назначения)** — куда отправляется коробка. [GLOSSARY](../../GLOSSARY.md)
- **Tariff (тариф)** — логистический тариф. [GLOSSARY](../../GLOSSARY.md)
- **FBA / FBM** — модели выполнения заказов. [FBA](029-fba.md) · [FBM](030-fbm.md)
- **Shipment (отгрузка)** — движение товара между складами.
  _Needs validation:_ отдельная сущность или жизненный цикл коробки (DM8).

## Поставщики и сорсинг

- **Supplier (поставщик)** — источник закупки. [011 — Поставщик](../foundations/011-supplier.md)
- **Supplier Card (карточка поставщика)** — предложение поставщика.
  [012 — Карточка поставщика](../foundations/012-supplier-card.md)
- **Product Idea (идея)** — кандидат на запуск товара. [014 — Идея](../foundations/014-product-idea.md)
- **Strategy (стратегия)** — стратегия сорсинга. [Entity States](../../ENTITY_STATES.md)
- **MOQ** — минимальная партия у поставщика. [MOQ](031-moq.md)
- **Private Label vs Wholesale** — стратегии продаж. [Сравнение](044-private-label-vs-wholesale.md)

## Реклама и аналитика

- **Campaign (кампания)** — рекламная кампания Amazon. [022 — Кампания](../foundations/022-campaign.md)
- **PPC Basics (основы PPC)** — вводная по платной рекламе. [Основы PPC](041-ppc-basics.md)
- **PPC Metrics** — метрики платной рекламы. [023 — PPC-метрики](../foundations/023-ppc-metrics.md)
- **ACoS / TACoS / ROAS** — показатели эффективности рекламы. [ACoS/TACoS/ROAS](042-acos-tacos-roas.md)
- **Unit Economics (юнит-экономика)** — прибыль на единицу товара. [Юнит-экономика](043-unit-economics.md)
- **Report (отчёт)** — аналитический срез данных. [021 — Отчёт](../foundations/021-report.md)
- **Voice of Customer** — срез по возвратам/клиентскому опыту
  (concession_rate, badge_status). [GLOSSARY](../../GLOSSARY.md) _(статья — ART-024, needs validation)_

## Пользователи и доступы

- **User (пользователь)** — участник платформы с ролью. [007 — Пользователь](../foundations/007-user.md)
- **Role (роль)** — модель доступа (RBAC). [008 — Роль](../foundations/008-role.md)
- **Permission (право доступа)** — атомарное правило доступа. [009 — Право доступа](../foundations/009-permission.md)
- **Permission Preset (пресет прав)** — набор доступов. [010 — Пресет прав](../foundations/010-permission-preset.md)
- **Sub-user (саб-пользователь)** — участник команды пользователя.
  [007 — Пользователь](../foundations/007-user.md)

## Поддержка, уведомления, финансы

- **Support Ticket (тикет поддержки)** — обращение пользователя. [020 — Тикет поддержки](../foundations/020-support-ticket.md)
- **Notification (уведомление)** — оповещение о событиях. [019 — Уведомление](../foundations/019-notification.md)
- **Payment (платёж)** — денежное движение по заказу. [017 — Платёж](../foundations/017-payment.md)

## Магазины и интеграции

- **Store (магазин)** — подключённый аккаунт Amazon. [006 — Магазин](../foundations/006-store.md)
- **Amazon SP-API** — интеграция с данными Amazon. [Amazon SP-API](036-amazon-sp-api.md)
- **Integration (интеграция)** — источник внешних данных (Amazon SP, SellerBoard).
  [GLOSSARY](../../GLOSSARY.md)
- **Connected App** — _в разработке; Needs validation_ (пока нет подтверждения
  «магазина приложений», DM6).

## Чеклист ревью

- [x] Метаданные — front matter полон (`status: approved`, `locale: ru`).
- [x] Не словарь — короткие пояснения + ссылки; полные определения в GLOSSARY/статьях.
- [x] Нет дублирования справочников — определения не переписаны.
- [x] Ссылки ведут на существующие статьи; несуществующие помечены _(планируется)_.
- [x] Неопределённости помечены: **Shipment** и **Connected App** — *Needs validation*
  (флагами, не утверждениями) — approve допустим, как в approved 004/021.
- [x] Batch помечена как draft/blocked (DM8), не финализируется.
