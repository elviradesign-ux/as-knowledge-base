---
title: "Склад — коробки на складе"
slug: warehouse-in-stock
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client]
roles: [Client]
modules: [Warehouse]
entities: [Box, Super Box, Product, Batch, Tariff]
workflows: [WF-035]
related_screens: [SCR-200, SCR-M04, SCR-M05]
related_entities: [Box, Batch, Tariff, Product]
related_articles: [004-box, 005-batch, create-order-modal]
seo_title: "Склад — коробки на складе: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану коробок на складе (Client) в Seller Exchange: группировка и редактирование коробок, тарифы и отправка коробок в партию."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-200)
  - reference/modals.md (модалки коробок)
  - ENTITY_STATES.md (статусы на складе/отгрузки)
  - localizations/*.tokens.json (actions_*)
  - figma-mcp/sources/mhtml/ (захваты)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятие коробки — в
> [Что такое коробка](../foundations/004-box.md). Визуальные источники — mhtml.

# Склад — коробки на складе

## Кратко

Экран показывает **коробки клиента на складе**: их можно редактировать,
группировать, объединять, перераспределять и отправлять в партию. Route:
`/warehouse/in-stock` (`InStockBoxesView`, [SCR-200](../../SCREEN_CATALOG.md)).

## Кому и когда пригодится

- **Client** — управлять своими коробками на складе перед отправкой на Amazon.

## Предварительные условия

- Роль Client; на складе есть коробки (иначе список пуст).

## Элементы экрана

- **Таблица коробок** (CustomDataGrid) с двумя режимами:
  сгруппированный и без группировки (см. mhtml `...-Grouped` / `...-NoGroups`).
- Поля коробки: статус, содержимое, пункт назначения, тариф
  (полные — в [GLOSSARY](../../GLOSSARY.md)).
- Статусы на складе — по [Entity States](../../ENTITY_STATES.md).

## Действия

Названия — из локализации (`actions_*`), EN / *RU*; модалки — из
[reference/modals.md](../../reference/modals.md):

- **Add a box** / *Добавить коробку* (`CreateBoxModal`, [SCR-M04](../../SCREEN_CATALOG.md)).
- Группировать коробки — `GroupingBoxesModal` ([SCR-M05](../../SCREEN_CATALOG.md)),
  объединить — `MergeBoxesModal`.
- Редактировать одну/несколько — `EditBoxModal`, `EditMultipleBoxesModal`.
- Перераспределить — `RedistributeBoxModal`; переместить в партию —
  `MoveBoxToBatchModal`.
- Запросить отправку партии — `RequestToSendBatchModal` (сценарий **WF-035**).
- Открыть коробку — `BoxModal`; тариф — `TariffModal`.

## Результат

- Коробки готовы к отправке; по запросу формируется
  **[партия](../foundations/005-batch.md)** _(партия — draft/blocked DM8)_.
- Статус коробки двигается по [жизненному циклу склада](../../ENTITY_STATES.md)
  (IN_STOCK → REQUESTED_SEND_TO_BATCH → …).

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [SCR-M05](../../SCREEN_CATALOG.md) `GroupingBoxesModal` | Группировка коробок |
| [005-batch](../foundations/005-batch.md) Партия | Куда уходят коробки (blocked DM8) |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/`:

- `Client-Warehouse-Boxes-Grouped.*.mhtml` (light/dark, En/Uk) — режим группировки.
- `Client-Warehouse-Boxes-NoGroups.*.mhtml` (light/dark, En/Uk) — без группировки.
- `Client-Boxesinstock.Dark.En.mhtml` — коробки на складе _(только Dark/En)_.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не отправляется в партию | Неактуальный тариф | Обновить тариф коробки (`TariffModal`) |
| Пустой список | Нет коробок на складе | Дождаться приёмки складом |
| Не группируются коробки | Разные параметры/статусы | Проверить совместимость перед группировкой |

## Связанные материалы

- Концепт: [Что такое коробка](../foundations/004-box.md), [Партия](../foundations/005-batch.md)
- Статусы: [Entity States](../../ENTITY_STATES.md); Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из локализации и [reference/modals.md](../../reference/modals.md).
- [x] Визуальные источники — mhtml указаны (часть — только Dark/En).
- [ ] Ревью вторым человеком.
