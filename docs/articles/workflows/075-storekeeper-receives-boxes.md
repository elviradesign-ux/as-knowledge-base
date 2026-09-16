---
title: "Сторкипер принимает коробки"
slug: storekeeper-receives-boxes
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Storekeeper]
roles: [Storekeeper]
modules: [Warehouse, Tasks]
entities: [Box, Warehouse Task, Product]
workflows: [WF-007, WF-040]
related_screens: [SCR-202, SCR-220, SCR-221, SCR-M04]
related_entities: [Box, Warehouse Task, Product]
related_articles: [my-warehouse, 004-box]
seo_title: "Как сторкиперу принять коробки — Seller Exchange"
seo_description: "Пошаговый сценарий: как сторкипер принимает коробки на складе в Seller Exchange — взятие задачи, приёмка и распределение."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-007, WF-040)
  - SCREEN_CATALOG.md (SCR-202, SCR-220, SCR-221, SCR-M04)
  - ENTITY_STATES.md (статусы на складе; типы задач)
  - articles/screens/my-warehouse.md, articles/foundations/004-box.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Понятие коробки — в
> [Что такое коробка](../foundations/004-box.md). UI-детали — в
> [Screen Guide «Мой склад»](../screens/my-warehouse.md).

# Сторкипер принимает коробки

## Кратко

Сценарий описывает, как **Storekeeper** принимает поступившие коробки: берёт
складскую задачу, принимает коробку и распределяет её на складе. Сценарий:
**WF-007** (взятие/выполнение задачи — **WF-040**).

## Кому и когда пригодится

- **Storekeeper** — при поступлении коробок на склад.

## Предварительные условия

- Роль Storekeeper; есть новые складские задачи/входящие коробки.

## Шаги

1. Откройте **Задачи — новые** ([SCR-220](../../SCREEN_CATALOG.md)).
2. Возьмите задачу в работу (переходит в **Мои** —
   [SCR-221](../../SCREEN_CATALOG.md), статус задачи по типу `receive`).
3. Примите коробку — `ReceiveBoxModal` (из модалки редактирования задачи).
4. Разметьте/отредактируйте коробку на
   [Моём складе](../screens/my-warehouse.md) ([SCR-202](../../SCREEN_CATALOG.md));
   при необходимости добавьте коробку (`CreateBoxModal`,
   [SCR-M04](../../SCREEN_CATALOG.md)).
5. Коробка переходит в статус на складе: `ACCEPTED_IN_PROCESSING` → `IN_STOCK`.

Статусы/типы задач — [Entity States](../../ENTITY_STATES.md).

## Результат

- Коробка принята и находится на складе (`IN_STOCK`), готова к дальнейшей
  обработке (перемещение в партию — по DM8).
- После приёмки байер получает уведомление «Ожидает подтверждения заказа».

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет новых задач | Нет входящих коробок | Проверить раздел «Задачи — новые» |
| Не сохраняется приёмка | Неполные данные коробки | Заполнить данные в `ReceiveBoxModal` |

## Связанные материалы

- Экран: [Мой склад](../screens/my-warehouse.md)
- Концепт: [Коробка](../foundations/004-box.md)
- Статусы/задачи: [Entity States](../../ENTITY_STATES.md)
- Следующий шаг (blocked DM8): [Сторкипер формирует партию](077-storekeeper-forms-batch.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] UI-детали — ссылкой на Screen Guide, не дублируются.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-007/040).
- [ ] Ревью вторым человеком.
