---
title: "Работа с инвентарём"
slug: use-inventory
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Admin]
roles: [Client, Admin]
modules: [Inventory]
entities: [Inventory, Product]
workflows: [WF-030]
related_screens: [SCR-120, SCR-121, SCR-122]
related_entities: [Inventory, Product, Order]
related_articles: [049-create-first-product, 050-create-first-order, inventory-products, 002-inventory, 037-inventory-forecasting]
seo_title: "Работа с инвентарём в Seller Exchange"
seo_description: "Как работать с инвентарём в Seller Exchange: таблица товаров, пресеты колонок, прогноз запасов и создание заказов."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - articles/screens/inventory-products.md
  - articles/foundations/002-inventory.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятие — в
> [Что такое инвентарь](../foundations/002-inventory.md). UI-детали — в
> [Инвентарь — товары](../screens/inventory-products.md).

# Работа с инвентарём

## Кратко

[Инвентарь](../foundations/002-inventory.md) — ваш каталог товаров с аналитикой.
Здесь вы следите за остатками, настраиваете вид таблицы и создаёте заказы.

## Что можно делать

- **Смотреть данные** — остатки, продажи, финансы, реклама (колонки; определения —
  в [справочнике полей](../../GLOSSARY.md)).
- **Настраивать вид** — пресеты и колонки (сохранить/применить пресет).
- **Планировать** — [прогноз запасов](../academy/037-inventory-forecasting.md),
  избегать [out of stock](../academy/038-out-of-stock.md).
- **Создавать заказы** — [создать заказ](050-create-first-order.md) по выбранным
  товарам.

Пошаговые действия на экране — в
[Инвентарь — товары](../screens/inventory-products.md).

## Шаги (типовой сценарий)

1. Откройте [Инвентарь — товары](../screens/inventory-products.md)
   ([SCR-120](../../SCREEN_CATALOG.md)).
2. Настройте колонки под задачу и сохраните пресет.
3. Оцените остатки и прогноз; при риске дефицита — создайте заказ.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Инвентарь пуст | Не подключён магазин | [Подключить магазин](047-connect-amazon-store.md) |
| Пропали колонки | Другой пресет | Применить/пересохранить нужный пресет |

## Связанные материалы

- Экран: [Инвентарь — товары](../screens/inventory-products.md)
- Управление запасами: [Как управлять запасами](../pillar/083-how-to-manage-inventory.md)

## Чеклист ревью

- [x] UI/поля — ссылками, не дублируются.
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
