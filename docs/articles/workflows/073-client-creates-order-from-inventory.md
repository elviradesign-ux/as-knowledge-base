---
title: "Клиент создаёт заказ из инвентаря"
slug: client-creates-order-from-inventory
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client]
roles: [Client]
modules: [Inventory, Orders]
entities: [Order, Product, Box, Inventory]
workflows: [WF-030, WF-031]
related_screens: [SCR-120, SCR-M01]
related_entities: [Order, Product, Box]
related_articles: [inventory-products, create-order-modal, orders-list, 003-order]
seo_title: "Как клиенту создать заказ из инвентаря — Seller Exchange"
seo_description: "Пошаговый сценарий: как клиент создаёт заказ из инвентаря в Seller Exchange — выбор товаров, распределение по коробкам и подтверждение."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-030, WF-031)
  - SCREEN_CATALOG.md (SCR-120, SCR-M01)
  - ENTITY_STATES.md (Статусы заказа)
  - articles/screens/inventory-products.md, create-order-modal.md, orders-list.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Сквозной путь по ролям. UI-детали — в
> связанных Screen Guides; понятия — в Foundation-статьях.

# Клиент создаёт заказ из инвентаря

## Кратко

Сценарий описывает, как **Client** создаёт заказ на закупку из
[инвентаря](../screens/inventory-products.md): выбирает товары, распределяет их по
коробкам и подтверждает заказ. Сценарий: **WF-030** (+ WF-031 — распределение по
коробкам).

## Кому и когда пригодится

- **Client** — когда нужно заказать закупку товара (в т.ч. дозакупку).

## Предварительные условия

- Роль Client; подключён магазин Amazon (иначе инвентарь пуст).
- Товары есть в [инвентаре](../screens/inventory-products.md).

## Шаги

1. Откройте [Инвентарь — товары](../screens/inventory-products.md)
   ([SCR-120](../../SCREEN_CATALOG.md)).
2. Отметьте чекбоксами нужные товары.
3. Нажмите **To order** / *К заказу* — откроется
   [модалка создания заказа](../screens/create-order-modal.md)
   ([SCR-M01](../../SCREEN_CATALOG.md)).
4. Задайте количество по каждому товару.
5. Распределите товар по коробкам (**Add a box**) — это шаг **WF-031**.
6. Задайте дедлайн заказа.
7. Подтвердите — заказ оформляется.

## Результат

- Создан заказ со статусом `NEW` (или `FORMED` для отложенного).
- Заказ виден в [списке заказов](../screens/orders-list.md); далее идёт по
  [жизненному циклу статусов](../../ENTITY_STATES.md) (обработка байером — WF-006).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет кнопки создания | Не отмечены товары | Отметить строки перед **To order** |
| Появилась проверка отложенного заказа | По товару уже есть pending-заказ | Разобрать `CheckPendingOrderModal` |
| Инвентарь пуст | Не подключён магазин | Подключить магазин (`/shops/my-shops`) |

## Связанные материалы

- Экраны: [Инвентарь](../screens/inventory-products.md),
  [Модалка создания заказа](../screens/create-order-modal.md),
  [Список заказов](../screens/orders-list.md)
- Концепт: [Что такое заказ](../foundations/003-order.md)
- Статусы: [Entity States](../../ENTITY_STATES.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] UI-детали — ссылками на Screen Guides, не дублируются.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-030/031).
- [ ] Ревью вторым человеком.
