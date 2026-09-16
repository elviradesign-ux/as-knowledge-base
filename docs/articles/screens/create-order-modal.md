---
title: "Модалка создания заказа"
slug: create-order-modal
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer]
roles: [Client, Buyer]
modules: [Orders, Inventory]
entities: [Order, Order Item, Product, Box]
workflows: [WF-030, WF-031]
related_screens: [SCR-M01, SCR-M02, SCR-M04, SCR-M08, SCR-120]
related_entities: [Order, Product, Box]
related_articles: [003-order, inventory-products, orders-list]
seo_title: "Модалка создания заказа: гайд по экрану Seller Exchange"
seo_description: "Гайд по модалке создания заказа в Seller Exchange: выбор товаров из инвентаря, распределение по коробкам, дедлайн и подтверждение заказа."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-M01, SCR-M02, SCR-M04, SCR-M08)
  - reference/modals.md (CreateOrderModal, NewOderModal, CreateBoxModal, DeadlineModal)
  - WORKFLOW_CATALOG.md (WF-030, WF-031)
  - localizations/*.tokens.json (actions_*)
  - figma-mcp/sources/mhtml/ (захваты модалки)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятие заказа — в
> [Что такое заказ](../foundations/003-order.md). Визуальные источники —
> mhtml-захваты (см. ниже).

# Модалка создания заказа

## Кратко

**Модалка создания заказа** (`CreateOrderModal`, [SCR-M01](../../SCREEN_CATALOG.md))
собирает заказ из выбранных товаров: задаёт количество, распределяет товар по
коробкам и подтверждает заказ. Чаще открывается из
[инвентаря](inventory-products.md) кнопкой **To order**.

## Кому и когда пригодится

- **Client** — создать заказ на закупку товара.
- **Buyer** — в рамках обработки заказов.

## Предварительные условия

- Отмечены строки товаров в [инвентаре](inventory-products.md) (или открыто из
  идей/биржи/склада — см. точки вызова в [reference/modals.md](../../reference/modals.md)).
- Роль Client (или Buyer).

## Элементы модалки

Высота модалки адаптивна к числу товаров (захваты для 1/2/3/5 товаров — см. ниже):

- **Список товаров** — выбранные позиции с количеством.
- **Коробки** — распределение товара по коробкам (ключевая фича).
- **Дедлайн** — срок по заказу (`DeadlineModal`, [SCR-M08](../../SCREEN_CATALOG.md)).
- **Итог** — сводка заказа перед подтверждением.

## Действия

Названия — из локализации (`actions_*`), EN / *RU*:

1. **To order** / *К заказу* — открыть модалку по выбранным товарам.
2. Задать количество; при необходимости — проверка количества (`CheckQuantityModal`).
3. **Add a box** / *Добавить коробку*, **Add another box** / *Добавить ещё коробку*
   (`CreateBoxModal`, [SCR-M04](../../SCREEN_CATALOG.md)); распределить товар по
   коробкам — сценарий **WF-031**.
4. **Add boxes for this order** / *Добавьте коробки по данному заказу**.
5. Задать дедлайн (`DeadlineModal`).
6. Подтвердить — оформляется новый заказ (`NewOderModal`,
   [SCR-M02](../../SCREEN_CATALOG.md)).

> Если по товару есть отложенный заказ — появится проверка `CheckPendingOrderModal`.

## Результат

- Создаётся заказ со статусом `NEW` (или `FORMED` для отложенного) — далее
  [жизненный цикл](../../ENTITY_STATES.md) в [списке заказов](orders-list.md).
- Товар распределён по коробкам, готовым к дальнейшей обработке.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Инвентарь — товары | Откуда открывается модалка |
| [orders-list](orders-list.md) Список заказов | Куда попадает созданный заказ |
| [SCR-M04](../../SCREEN_CATALOG.md) `CreateBoxModal` | Создание коробки внутри модалки |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/` (light/dark, En/Uk):

- `Client-Inventory-CreateOrderModal.*.mhtml` — базовая модалка.
- `Client-Inventory-CreateOrderModal-{1,2,3,5}.*.mhtml` — адаптив по числу товаров.
- `Client-Inventory-RowSelected-{1,2,3,5}.*.mhtml` — выбор строк перед созданием.
- `Client-CheckPendingOrderModal.*.mhtml` — проверка отложенного заказа.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет кнопки создания | Не отмечены товары | Отметить строки в инвентаре перед **To order** |
| Появилась проверка отложенного заказа | По товару уже есть pending-заказ | Разобрать `CheckPendingOrderModal` |
| Не сходится количество | Ошибка распределения по коробкам | Проверить количество (`CheckQuantityModal`) |

## Связанные материалы

- Концепт: [Что такое заказ](../foundations/003-order.md)
- Сценарии: WF-030 (создать), WF-031 (распределить по коробкам)
- Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Действия — из локализации (`actions_*`), не выдуманы.
- [x] Модалки — по [reference/modals.md](../../reference/modals.md).
- [x] Визуальные источники — mhtml-захваты указаны.
- [ ] Ревью вторым человеком (product accuracy).
