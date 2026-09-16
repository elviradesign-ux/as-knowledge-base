---
title: "Байер обрабатывает заказ"
slug: buyer-processes-order
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Buyer]
roles: [Buyer]
modules: [Orders, Finance]
entities: [Order, Payment, Supplier, Box]
workflows: [WF-006, WF-022, WF-023, WF-024]
related_screens: [SCR-103, SCR-104, SCR-105, SCR-M03]
related_entities: [Order, Payment, Supplier, Box]
related_articles: [orders-list, 003-order, 017-payment]
seo_title: "Как байеру обработать заказ — Seller Exchange"
seo_description: "Пошаговый сценарий: как байер обрабатывает заказ в Seller Exchange — от взятия в работу и оплаты поставщику до трек-номера и приёмки."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-006, WF-022, WF-023, WF-024)
  - SCREEN_CATALOG.md (SCR-103, SCR-104, SCR-105, SCR-M03)
  - ENTITY_STATES.md (Статусы заказа)
  - articles/screens/orders-list.md, articles/foundations/003-order.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Понятие заказа — в
> [Что такое заказ](../foundations/003-order.md). UI-детали — в
> [Screen Guide «Список заказов»](../screens/orders-list.md).

# Байер обрабатывает заказ

## Кратко

Сценарий описывает, как **Buyer** проводит заказ по жизненному циклу: берёт в
работу, оплачивает поставщику, вносит трек-номер и подтверждает приёмку. Сценарий:
**WF-006** (+ WF-022 взять свободный, WF-023 оплата, WF-024 трек-номер/приёмка).

## Кому и когда пригодится

- **Buyer** — при обработке заказов клиентов.

## Предварительные условия

- Роль Buyer; есть заказы (свободные или взятые в работу).

## Шаги

1. Откройте [Список заказов](../screens/orders-list.md) байера
   ([SCR-103](../../SCREEN_CATALOG.md)) или **Свободные заказы**
   ([SCR-105](../../SCREEN_CATALOG.md)).
2. Возьмите заказ в работу (свободный — WF-022) — статус `AT_PROCESS`.
3. Подготовьте к оплате — `READY_FOR_PAYMENT`; отредактируйте заказ при
   необходимости (`EditOrderModal`, [SCR-M03](../../SCREEN_CATALOG.md)).
4. Оплатите поставщику (полностью/частично, WF-023) — `PARTIALLY_PAYMENT` →
   `PAID_TO_SUPPLIER` (при доплате возможен `NEED_CONFIRMING_TO_PRICE_CHANGE`).
5. Внесите трек-номер — `TRACK_NUMBER_ISSUED` (WF-024).
6. Подтвердите приёмку — `NEED_CONFIRMING_RECEIVING` → `IN_STOCK`.

Коды статусов — [Entity States → Статусы заказа](../../ENTITY_STATES.md).

## Результат

- Заказ доведён до `IN_STOCK` (товар на складе) и далее к отгрузке.
- Оплаты поставщику зафиксированы в финансах (см. [Что такое платёж](../foundations/017-payment.md)).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Заказ ждёт клиента | `NEED_CONFIRMING_TO_PRICE_CHANGE` | Клиент подтверждает доплату |
| Не подтверждается приёмка | Нет данных о поступлении | Проверить `NEED_CONFIRMING_RECEIVING` |

## Связанные материалы

- Экран: [Список заказов](../screens/orders-list.md)
- Концепт: [Заказ](../foundations/003-order.md), [Платёж](../foundations/017-payment.md)
- Статусы: [Entity States](../../ENTITY_STATES.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] UI-детали — ссылкой на Screen Guide, не дублируются.
- [x] Шаги/статусы — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md)/ENTITY_STATES.
- [ ] Ревью вторым человеком.
