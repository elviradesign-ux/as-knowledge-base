---
title: "Создать первый заказ"
slug: create-first-order
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client]
roles: [Client]
modules: [Orders, Inventory]
entities: [Order, Product, Box]
workflows: [WF-030, WF-031]
related_screens: [SCR-120, SCR-M01]
related_entities: [Order, Product, Box]
related_articles: [049-create-first-product, 051-use-inventory, create-order-modal, 073-client-creates-order-from-inventory, 003-order]
seo_title: "Как создать первый заказ в Seller Exchange"
seo_description: "Как создать первый заказ в Seller Exchange: выбрать товары из инвентаря, распределить по коробкам и подтвердить заказ."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - articles/workflows/073-client-creates-order-from-inventory.md
  - articles/screens/create-order-modal.md
  - articles/foundations/003-order.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Краткая инструкция; полный сценарий — в
> [Клиент создаёт заказ из инвентаря](../workflows/073-client-creates-order-from-inventory.md).

# Создать первый заказ

## Кратко

Создайте [заказ](../foundations/003-order.md) из
[инвентаря](051-use-inventory.md): выберите товары, распределите по коробкам и
подтвердите.

## Предварительные условия

- Роль Client; в инвентаре есть [товары](049-create-first-product.md).

## Шаги

1. Откройте [Инвентарь — товары](../screens/inventory-products.md)
   ([SCR-120](../../SCREEN_CATALOG.md)).
2. Отметьте нужные товары.
3. Нажмите **To order** / *К заказу* — откроется
   [модалка создания заказа](../screens/create-order-modal.md)
   ([SCR-M01](../../SCREEN_CATALOG.md)).
4. Задайте количество, распределите по коробкам, укажите дедлайн.
5. Подтвердите.

## Результат

- Заказ создан (статус `NEW`/`FORMED`) и виден в
  [списке заказов](../screens/orders-list.md).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет кнопки создания | Не отмечены товары | Отметить строки перед **To order** |
| Проверка отложенного заказа | Есть pending-заказ по товару | Разобрать `CheckPendingOrderModal` |

## Связанные материалы

- Полный сценарий: [Клиент создаёт заказ из инвентаря](../workflows/073-client-creates-order-from-inventory.md)
- Экран: [Модалка создания заказа](../screens/create-order-modal.md)
- Понятие: [Заказ](../foundations/003-order.md)

## Чеклист ревью

- [x] UI/шаги — ссылками на Screen/Workflow Guide, не дублируются.
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
