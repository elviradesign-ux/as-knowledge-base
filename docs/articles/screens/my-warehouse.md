---
title: "Мой склад (Storekeeper)"
slug: my-warehouse
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Storekeeper]
roles: [Storekeeper]
modules: [Warehouse]
entities: [Box, Super Box, Batch, Warehouse Task]
workflows: [WF-007, WF-041]
related_screens: [SCR-202]
related_entities: [Box, Batch, Warehouse Task]
related_articles: [004-box, 005-batch]
seo_title: "Мой склад (Storekeeper): гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану «Мой склад» для сторкипера в Seller Exchange: работа с коробками, размеры, перемещение в партию и объединение."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-202)
  - reference/modals.md (модалки склада)
  - ENTITY_STATES.md (статусы на складе; типы задач)
  - figma-mcp/sources/mhtml/ (захват)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Роль **Storekeeper**. Понятие коробки — в
> [Что такое коробка](../foundations/004-box.md). Визуальный источник — mhtml.

# Мой склад (Storekeeper)

## Кратко

«Мой склад» — рабочий экран **сторкипера**: приёмка и обработка коробок, их
размеры, объединение и перемещение в партию. Route: `/my-warehouse`
(`MyWarehouseView`, [SCR-202](../../SCREEN_CATALOG.md)).

## Кому и когда пригодится

- **Storekeeper** — принимать коробки и готовить их к отправке.

## Предварительные условия

- Роль Storekeeper; поступившие коробки/задачи.

## Элементы экрана

- **Таблица коробок** на складе сторкипера (CustomDataGrid).
- Поля коробки: статус, размеры, содержимое, партия
  (полные — в [GLOSSARY](../../GLOSSARY.md)).
- Статусы — по [Entity States](../../ENTITY_STATES.md) (склад/отгрузка).

## Действия

Модалки — из [reference/modals.md](../../reference/modals.md):

- Открыть/редактировать коробку сторкипера — `StorekeeperModal`,
  `EditBoxStorekeeperModal`.
- Редактировать размеры — `EditBoxDimensionsModal`.
- Объединить коробки — `MergeBoxesModal`; переместить в партию —
  `MoveBoxToBatchModal`.
- Приёмка коробки — `ReceiveBoxModal` (из модалки задачи, сценарий **WF-007**).
- Редактировать партию — `EditBatchModal` (формирование партии — **WF-041**).

## Результат

- Коробки приняты, размечены и перемещены в партию.
- Партия формируется и уходит на отправку _(партия — draft/blocked DM8)_.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [004-box](../foundations/004-box.md) Коробка | Понятие коробки |
| [005-batch](../foundations/005-batch.md) Партия | Формирование партии (blocked DM8) |

## Визуальные источники (mhtml)

- `Storekeeper.Warehouse.Dark.En.mhtml` — экран «Мой склад» _(только Dark/En)_.

> Желательны захваты в Light-теме и других языках.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Коробка не перемещается в партию | Неверный статус/тариф | Проверить статус и тариф коробки |
| Нет новых коробок | Нет входящих задач приёмки | Проверить раздел «Задачи» |
| Не сохраняются размеры | Неполные данные | Заполнить размеры в `EditBoxDimensionsModal` |

## Связанные материалы

- Концепт: [Что такое коробка](../foundations/004-box.md)
- Задачи и статусы: [Entity States](../../ENTITY_STATES.md); Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология/статусы — по источникам.
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из [reference/modals.md](../../reference/modals.md).
- [x] Визуальный источник — mhtml (только Dark/En).
- [ ] Ревью вторым человеком; желательны Light/иные языки.
