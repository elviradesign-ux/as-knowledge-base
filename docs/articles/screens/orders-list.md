---
title: "Список заказов"
slug: orders-list
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer, Admin]
roles: [Client, Buyer, Admin]
modules: [Orders]
entities: [Order, Order Status, Product]
workflows: [WF-005, WF-006]
related_screens: [SCR-100, SCR-101, SCR-102, SCR-103, SCR-104, SCR-105, SCR-M01, SCR-M03]
related_entities: [Order, Product, Box, Payment]
related_articles: [003-order, order-status, create-order-modal]
seo_title: "Список заказов: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану списка заказов в Seller Exchange: как клиент и байер видят заказы, статусные вкладки и переход к деталям заказа."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-100…105, SCR-M01, SCR-M03)
  - ENTITY_STATES.md (Статусы заказа)
  - reference/routes-by-role.md (вкладки заказов)
  - WORKFLOW_CATALOG.md (WF-005, WF-006)
  - figma-mcp/sources/mhtml/ (захваты заказов)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятие заказа — в
> [Что такое заказ](../foundations/003-order.md). Статусы — в
> [Entity States](../../ENTITY_STATES.md). Визуальные источники — mhtml (см. ниже).

# Список заказов

## Кратко

Экран показывает заказы в виде таблицы с разбивкой по статусным вкладкам. Вид
зависит от роли: **Client** видит свои заказы, **Buyer** — заказы в работе и
свободные, **Admin** — надзорный список.

## Кому и когда пригодится

- **Client** — отслеживать свои заказы и их статусы.
- **Buyer** — брать и обрабатывать заказы.
- **Admin** — надзор за заказами.

## Предварительные условия

- Доступ к разделу «Заказы» (см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md)).
- Для Client — созданные заказы (иначе список пуст).

## Элементы экрана

Список заказов — таблица (CustomDataGrid) со статусными вкладками. Раскладка по
роли (route + компонент — из [reference/routes-by-role.md](../../reference/routes-by-role.md)):

**Client** ([SCR-100](../../SCREEN_CATALOG.md) / [SCR-102](../../SCREEN_CATALOG.md)):
- Мои заказы (`/orders/my-orders`), Ожидающие заказы (`/orders/pending-orders`).

**Buyer** ([SCR-103](../../SCREEN_CATALOG.md) / [SCR-105](../../SCREEN_CATALOG.md)):
- Мои заказы (`/my-orders/*`) — 8 статусных вкладок: all, not-paid,
  ready-for-payment, partially-paid, need-track-number, inbound,
  confirmation-required, closed-and-canceled.
- Свободные заказы (`/free-orders`), Ожидающие заказы (`/pending-orders`).

**Admin** ([SCR-107](../../SCREEN_CATALOG.md)): `/orders` → `/orders/:id`.

Строка заказа показывает ключевые поля (ID, товар, статус, дедлайн и т.д.);
статус — по [Entity States → Статусы заказа](../../ENTITY_STATES.md).

## Действия

- Открыть детали заказа — клик по строке (Client → `ClientOrderView`;
  Buyer → детальный экран [SCR-104](../../SCREEN_CATALOG.md)).
- **Cancel order** / *Отменить заказ*, **Cancel selected orders** / *Отменить
  выбранные заказы* (по правам роли).
- Buyer: взять свободный заказ в работу; редактировать заказ — модалка
  `EditOrderModal` ([SCR-M03](../../SCREEN_CATALOG.md)).
- Создать заказ — **To order** / *К заказу* (`CreateOrderModal`,
  [SCR-M01](../../SCREEN_CATALOG.md)); чаще из [инвентаря](inventory-products.md).

## Результат

- Заказ виден в соответствующей статусной вкладке.
- Обработка байером двигает заказ по [жизненному циклу статусов](../../ENTITY_STATES.md)
  (WF-006) вплоть до `SHIPPED`.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [SCR-101 / SCR-104](../../SCREEN_CATALOG.md) | Детали заказа (Client / Buyer) |
| [SCR-M01](../../SCREEN_CATALOG.md) `CreateOrderModal` | Создание заказа |
| [SCR-M03](../../SCREEN_CATALOG.md) `EditOrderModal` | Редактирование заказа (Buyer) |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/` (light/dark, En/Uk/Ua):

- **Client:** `Client-Myorders.*.mhtml`, `Client-Myorders-Statuses.*.mhtml`
  (статусные вкладки), `Client-PendingOrders.*.mhtml`,
  `Client-MyOrders-OrderInfo.*.mhtml` (детали заказа).
- **Buyer:** `OrdersBuyer.*.mhtml`.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Заказ «завис» | Ждёт действия — напр. `NEED_CONFIRMING_TO_PRICE_CHANGE` | Подтвердить изменение цены |
| Не вижу свободные заказы | Роль ≠ Buyer / нет вакантных | Проверить роль и вкладку «Свободные» |
| Пустой список | Нет заказов / фильтр статуса | Сменить вкладку/статус |

## Связанные материалы

- Концепт: [Что такое заказ](../foundations/003-order.md)
- Сценарии: WF-005 (создать), WF-006 (обработать) — [Workflow Catalog](../../WORKFLOW_CATALOG.md)
- Статусы: [Entity States](../../ENTITY_STATES.md); Роуты: [reference/routes-by-role.md](../../reference/routes-by-role.md)

## Чеклист ревью

- [x] Терминология и статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Вкладки/роуты — по [reference/routes-by-role.md](../../reference/routes-by-role.md), не выдуманы.
- [x] Визуальные источники — mhtml-захваты указаны (Client + Buyer).
- [ ] Ревью вторым человеком.
