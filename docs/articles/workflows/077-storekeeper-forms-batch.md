---
title: "Сторкипер формирует партию"
slug: storekeeper-forms-batch
article_type: Workflow Guide
section: Workflows
status: blocked
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Storekeeper]
roles: [Storekeeper]
modules: [Warehouse, Batches]
entities: [Batch, Box, Shipment]
workflows: [WF-041]
related_screens: [SCR-202, SCR-240, SCR-241]
related_entities: [Batch, Box, Shipment]
related_articles: [my-warehouse, batches-sent, 005-batch]
seo_title: "Сторкипер формирует партию — Seller Exchange (в подготовке)"
seo_description: "Сценарий формирования партии сторкипером в Seller Exchange. Статья заблокирована до уточнения жизненного цикла партии (DM8)."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-041)
  - SCREEN_CATALOG.md (SCR-202, SCR-240, SCR-241)
  - DOMAIN_MODEL.md (§8 Batch; §11)
  - DOMAIN_MODEL_OPEN_QUESTIONS.md (DM8)
validation_status: "blocked (DM8)"
---

> ⚠️ **BLOCKED.** Статья не пишется до уточнения жизненного цикла **партии** и
> сущности **Shipment**. Ниже — причина и вопросы к закрытию.

# Сторкипер формирует партию — BLOCKED

## Статус: BLOCKED (DM8)

Сценарий описывает, как **Storekeeper** формирует
[партию](../foundations/005-batch.md) из коробок и отправляет её (**WF-041**). Он
опирается на статусы партии и трактовку Shipment, которые **пока не подтверждены**.

## Причина блокировки

- **Жизненный цикл партии не задокументирован** — нет числовых статусов и
  переходов (только вкладки ожидающие/отправленные/архив). См.
  [ENTITY_STATES](../../ENTITY_STATES.md), [DOMAIN_MODEL §8](../../DOMAIN_MODEL.md).
- **Shipment не подтверждён как сущность** — отдельная сущность или жизненный
  цикл коробки ([DOMAIN_MODEL §11](../../DOMAIN_MODEL.md)).

## Какие вопросы нужно закрыть

1. **DM8 — Batch lifecycle:** статусы партии, переходы, наличие числовых кодов;
   генерация Prep ID (`GeneratePrepIdModal`) в цепочке.
2. **Shipment:** сущность или жизненный цикл коробки; связь с `IN_BATCH` /
   `IN_BATCH_ON_THE_WAY` / `FINISH_PREP_CENTR_USA`.
3. **Границы WF-041 vs WF-035** (сторкипер vs клиент) в формировании/отправке.

Трекер вопросов — [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md).

## Черновой каркас (заполнить после DM8)

- **Кратко:** _TODO — после подтверждения lifecycle партии._
- **Предварительные условия:** коробки на [Моём складе](../screens/my-warehouse.md)
  готовы к партии.
- **Шаги:** _TODO_ (собрать коробки в партию `EditBatchModal` → сгенерировать
  Prep ID → отправить; результат — в [Отправленных партиях](../screens/batches-sent.md)).
- **Результат:** _TODO_ (партия отправлена; статусы — после DM8).

## Связанные материалы

- Экраны: [Мой склад](../screens/my-warehouse.md), [Отправленные партии](../screens/batches-sent.md)
- Концепт: [Партия](../foundations/005-batch.md)
- Открытые вопросы: [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md) (DM8)

## Чеклист (разблокировка)

- [ ] DM8 — Batch lifecycle подтверждён.
- [ ] Shipment — сущность или lifecycle (решено).
- [ ] Генерация Prep ID и границы WF-041/WF-035 уточнены.
- [ ] После этого — написать шаги и перевести в `review`/`approved`.
