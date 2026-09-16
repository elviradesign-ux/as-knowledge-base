---
title: "Клиент отправляет коробки в партию"
slug: client-sends-boxes-into-batch
article_type: Workflow Guide
section: Workflows
status: blocked
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client]
roles: [Client]
modules: [Warehouse, Batches]
entities: [Box, Batch, Shipment]
workflows: [WF-035]
related_screens: [SCR-200, SCR-240]
related_entities: [Box, Batch, Shipment]
related_articles: [warehouse-in-stock, 004-box, 005-batch]
seo_title: "Клиент отправляет коробки в партию — Seller Exchange (в подготовке)"
seo_description: "Сценарий отправки коробок в партию в Seller Exchange. Статья заблокирована до уточнения жизненного цикла партии (DM8)."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-035)
  - SCREEN_CATALOG.md (SCR-200, SCR-240)
  - DOMAIN_MODEL.md (§8 Batch; §11)
  - DOMAIN_MODEL_OPEN_QUESTIONS.md (DM8)
validation_status: "blocked (DM8)"
---

> ⚠️ **BLOCKED.** Статья не пишется до уточнения жизненного цикла **партии** и
> сущности **Shipment**. Ниже — причина и вопросы к закрытию.

# Клиент отправляет коробки в партию — BLOCKED

## Статус: BLOCKED (DM8)

Сценарий описывает, как **Client** отправляет коробки со склада в
[партию](../foundations/005-batch.md) для отгрузки на Amazon (**WF-035**). Он
опирается на статусы партии и на трактовку Shipment, которые **пока не
подтверждены**.

## Причина блокировки

- **Жизненный цикл партии не задокументирован.** В базе знаний есть только
  вкладки (ожидающие / отправленные / архив), но **нет числовых кодов статусов и
  переходов** партии — см. [ENTITY_STATES](../../ENTITY_STATES.md) и
  [DOMAIN_MODEL §8](../../DOMAIN_MODEL.md).
- **Shipment не подтверждён как сущность.** Неясно, отдельная это сущность или
  жизненный цикл коробки — [DOMAIN_MODEL §11](../../DOMAIN_MODEL.md).

## Какие вопросы нужно закрыть

1. **DM8 — Batch lifecycle:** какие статусы у партии и переходы между ними
   (создание → запрос отправки → в пути → принята)? Есть ли числовые коды?
2. **Shipment:** это отдельная сущность или жизненный цикл коробки? Как
   соотносится с `REQUESTED_SEND_TO_BATCH` / `IN_BATCH` / `IN_BATCH_ON_THE_WAY`?
3. **Роль клиента vs сторкипера** в формировании/отправке партии (границы WF-035
   и WF-041).

Трекер вопросов — [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md).

## Черновой каркас (заполнить после DM8)

- **Кратко:** _TODO — после подтверждения lifecycle партии._
- **Предварительные условия:** коробки на складе (см.
  [Коробки на складе](../screens/warehouse-in-stock.md)).
- **Шаги:** _TODO_ (запрос на отправку партии `RequestToSendBatchModal` →
  формирование партии → отправка).
- **Результат:** _TODO_ (партия отправлена; статусы — после DM8).

## Связанные материалы

- Экран: [Коробки на складе](../screens/warehouse-in-stock.md)
- Концепт: [Коробка](../foundations/004-box.md), [Партия](../foundations/005-batch.md)
- Открытые вопросы: [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md) (DM8)

## Чеклист (разблокировка)

- [ ] DM8 — Batch lifecycle подтверждён.
- [ ] Shipment — сущность или lifecycle (решено).
- [ ] Границы WF-035 / WF-041 уточнены.
- [ ] После этого — написать шаги и перевести в `review`/`approved`.
