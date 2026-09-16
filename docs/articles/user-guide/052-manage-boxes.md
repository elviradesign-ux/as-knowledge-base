---
title: "Управление коробками"
slug: manage-boxes
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Storekeeper]
roles: [Client, Storekeeper]
modules: [Warehouse]
entities: [Box, Super Box, Batch]
workflows: [WF-007, WF-035]
related_screens: [SCR-200, SCR-202, SCR-M05]
related_entities: [Box, Super Box, Batch]
related_articles: [warehouse-in-stock, my-warehouse, 004-box, 053-create-batch]
seo_title: "Управление коробками в Seller Exchange"
seo_description: "Как управлять коробками на складе в Seller Exchange: группировка, редактирование, объединение и подготовка к отправке в партию."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - articles/screens/warehouse-in-stock.md, my-warehouse.md
  - articles/foundations/004-box.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятие — в
> [Что такое коробка](../foundations/004-box.md). UI-детали — в Screen Guides.

# Управление коробками

## Кратко

[Коробки](../foundations/004-box.md) на складе можно группировать, редактировать,
объединять и готовить к отправке в партию. Клиент работает со своими коробками,
сторкипер — со складскими.

## Что можно делать

- **Клиент** — [Коробки на складе](../screens/warehouse-in-stock.md)
  ([SCR-200](../../SCREEN_CATALOG.md)): группировка (`GroupingBoxesModal`,
  [SCR-M05](../../SCREEN_CATALOG.md)), объединение, перераспределение, запрос
  отправки в партию.
- **Сторкипер** — [Мой склад](../screens/my-warehouse.md)
  ([SCR-202](../../SCREEN_CATALOG.md)): приёмка, размеры, перемещение в партию.

## Шаги (клиент)

1. Откройте [Коробки на складе](../screens/warehouse-in-stock.md).
2. Сгруппируйте/отредактируйте коробки при необходимости.
3. Запросите отправку коробок в партию (`RequestToSendBatchModal`).

## Результат

- Коробки подготовлены; отправка в партию — см.
  [Создать партию](053-create-batch.md) _(в подготовке, зависит от DM8)_.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не отправляется в партию | Неактуальный тариф | Обновить тариф коробки |
| Не группируются | Разные параметры/статусы | Проверить совместимость |

## Связанные материалы

- Экраны: [Коробки на складе](../screens/warehouse-in-stock.md), [Мой склад](../screens/my-warehouse.md)
- Понятие: [Коробка](../foundations/004-box.md)

## Чеклист ревью

- [x] UI/действия — ссылками на Screen Guides, не дублируются.
- [x] Метаданные — front matter полон.
- [x] Отправка в партию помечена как зависящая от DM8.
- [ ] Ревью вторым человеком.
