---
title: "Создать первый товар"
slug: create-first-product
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client]
roles: [Client]
modules: [Inventory, Product]
entities: [Product, ASIN]
workflows: [WF-030]
related_screens: [SCR-120, SCR-121]
related_entities: [Product, ASIN, Inventory]
related_articles: [047-connect-amazon-store, 050-create-first-order, inventory-products, 001-product, 026-asin]
seo_title: "Как создать первый товар в Seller Exchange"
seo_description: "Как добавить первый товар в инвентарь Seller Exchange: указать ASIN и данные товара, чтобы начать с ним работать."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-120, SCR-121)
  - articles/screens/inventory-products.md
  - articles/foundations/001-product.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятие товара — в
> [Что такое товар](../foundations/001-product.md). UI-детали — в
> [Инвентарь — товары](../screens/inventory-products.md).

# Создать первый товар

## Кратко

Добавьте [товар](../foundations/001-product.md) в
[инвентарь](../screens/inventory-products.md) — укажите
[ASIN](../academy/026-asin.md) и данные, чтобы начать с ним работать.

## Предварительные условия

- Роль Client; желательно [подключён магазин](047-connect-amazon-store.md).
- Известен ASIN товара.

## Шаги

1. Откройте [Инвентарь — товары](../screens/inventory-products.md)
   ([SCR-120](../../SCREEN_CATALOG.md)).
2. Нажмите **Add product** / *Добавить товар* (или **Add your product**).
3. Укажите [ASIN](../academy/026-asin.md) и основные данные.
4. Подтвердите создание (*Are you sure you want to create a product?*).

## Результат

- Товар отображается строкой в инвентаре; можно открыть его
  [детали](../screens/product-detail.md) ([SCR-121](../../SCREEN_CATALOG.md)).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не создаётся товар | Пустой/некорректный ASIN | Указать корректный ASIN |
| Нет данных о продажах | Не подключён магазин | [Подключить магазин](047-connect-amazon-store.md) |

## Связанные материалы

- Экран: [Инвентарь — товары](../screens/inventory-products.md)
- Далее: [Создать первый заказ](050-create-first-order.md)
- Понятия: [Товар](../foundations/001-product.md), [ASIN](../academy/026-asin.md)

## Чеклист ревью

- [x] Действия — из локализации; UI — ссылкой на Screen Guide.
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
