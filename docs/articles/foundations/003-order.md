---
title: "Что такое заказ"
slug: order
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Admin]
modules: [Orders]
entities: [Order, Order Item, Order Status, Order Type, Product, Supplier, Box, Payment]
workflows: [WF-005, WF-006, WF-030, WF-031]
related_screens: [SCR-100, SCR-101, SCR-102, SCR-103, SCR-104, SCR-M01, SCR-M03]
related_entities: [Product, Box, Supplier, Payment]
related_articles: [001-product, 002-inventory, 004-box]
seo_title: "Заказ в Seller Exchange — от создания до отгрузки"
seo_description: "Что такое заказ в Seller Exchange: как он создаётся, его жизненный цикл статусов и как он превращается в коробки, которыми занимаются байеры и сторкиперы."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
translations: [003-order.en.md]
source_documents:
  - DOMAIN_MODEL.md (§4 Order, Order Item, Order Status, Order Type, Payment)
  - ENTITY_RELATIONSHIPS.md (#26, #28–35, #37, #81)
  - ENTITY_STATES.md (Статусы заказа, Типы заказа)
  - GLOSSARY.md (Заказ, Статус заказа)
  - SCREEN_CATALOG.md (SCR-100…107, SCR-M01, SCR-M03)
  - WORKFLOW_CATALOG.md (WF-005, WF-006, WF-030, WF-031)
validation_status: "confirmed (примечание: Order Item — Needs validation)"
---

> **Канонический источник (ru).** Английский перевод — переключатель языка
> в шапке сайта. При правках сначала меняем источник.

# Что такое заказ

**Заказ** — это запрос клиента на закупку [товара](001-product.md). Это сердце
операционного потока: клиент создаёт заказ, **Buyer** его обрабатывает, а
**Storekeeper** в итоге принимает товар в виде коробок.

## Кратко

Заказ фиксирует, что клиент хочет купить, и ведёт это от создания до отгрузки. По
пути заказ связывается с поставщиком, который его выполняет, с оплатой этому
поставщику и с коробками, в которые упаковывается товар. **Статус** заказа
показывает всем, на каком этапе он сейчас находится.

## Что это такое

Заказ — операционный запрос на закупку одного или нескольких товаров. Он
объединяет закупаемые позиции и связывает их с поставщиком, оплатой и коробками.

> **Order Item** рассматривается как связанное понятие (позиция заказа), но пока
> не полностью подтверждён в Domain Model — трактуйте его как смежное понятие,
> ожидающее валидации.

## Зачем это нужно

Заказ связывает операционную цепочку платформы — товар, поставщик, оплата,
коробка и партия сходятся на заказе. Прочитать статус заказа — самый быстрый
способ понять, что должно произойти дальше.

## Основные атрибуты и типы

- **Статус** — текущий этап заказа (см. ниже).
- **Тип заказа** — LONG, STANDARD, URGENT, PROBLEMATIC
  (см. [Entity States → Типы заказа](../../ENTITY_STATES.md)).
- **Товары и коробки** — что закупается и как упаковывается.
- **Поставщик и оплата** — кто выполняет заказ и как проходит расчёт.

Полные поля не дублируются — см. источники в разделе «Термины и справочники».

## Жизненный цикл и статусы

Заказ проходит определённую цепочку статусов, примерно:

> FORMED / NEW → PENDING → READY_TO_PROCESS → AT_PROCESS → READY_FOR_PAYMENT →
> PARTIALLY_PAYMENT → PAID_TO_SUPPLIER → TRACK_NUMBER_ISSUED →
> NEED_CONFIRMING_RECEIVING → IN_STOCK → AWAITING_SHIPMENT → SHIPPED

Заказ также может быть отменён байером или клиентом. Полная таблица кодов и
переходов не дублируется — канонический источник:
[Entity States → Статусы заказа](../../ENTITY_STATES.md).

## Связи с другими сущностями

- Заказ **создаётся** клиентом и **обрабатывается** байером.
- Он **порождает** коробки и **ссылается** на поставщика и оплату.

Полный каталог — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Кто работает с этой сущностью

- **Client** — создаёт и отслеживает свои заказы.
- **Buyer** — берёт и обрабатывает заказы (включая свободные/вакантные).
- **Admin** — надзор за заказами.

Каждая роль видит только заказы в своей области — см.
[Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-100 / SCR-101](../../SCREEN_CATALOG.md) | Мои заказы / детали заказа (Client) |
| [SCR-103 / SCR-104](../../SCREEN_CATALOG.md) | Заказы байера (статусные вкладки) / детали |
| [SCR-M01](../../SCREEN_CATALOG.md) | Модалка создания заказа |

## Связанные сценарии

- **WF-005** — купить карточку с биржи и создать заказ (Client).
- **WF-006** — провести заказ по жизненному циклу статусов (Buyer).
- **WF-030 / WF-031** — создать заказ и распределить коробки (Client).

## Термины и справочники

- Термины: [Заказ](../../GLOSSARY.md), [Статус заказа](../../GLOSSARY.md),
  [Коробка](../../GLOSSARY.md), [Поставщик](../../GLOSSARY.md).
- Статусы и типы: [Entity States](../../ENTITY_STATES.md).
- Связи: [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Почему заказ ждёт меня? | Возможно, он в статусе `NEED_CONFIRMING_TO_PRICE_CHANGE` — байеру нужно ваше подтверждение по изменению цены. |
| Что значит «свободный» заказ? | Неназначенный заказ, который может взять байер (вакантные заказы). |
| Где хранятся точные статусы? | В [Entity States](../../ENTITY_STATES.md). |

## Связанные статьи

- [001 — Товар](001-product.md)
- [004 — Коробка](004-box.md)
- [005 — Партия](005-batch.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md); статусы дословно из [ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон (`locale: ru`, `status: approved`, `localization_status: ru-source`).
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Нет дублирования справочников — полная таблица статусов дана ссылкой.
- [x] Неопределённость помечена: **Order Item** — *Needs validation*.
- [x] Внутренние ссылки сохранены.
